## Info
- Title : 451. Sort Characters By Frequency
- Description : https://leetcode.com/problems/first-unique-character-in-a-string/description/ 
- Provider : leetcode  

## Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
같은 우선순위일 경우 한 문자가 전부 나온 후 다른게 나와야 한다는 걸 생각해야함 
## Approach
<!-- Describe your approach to solving the problem. -->
PriorityQueue 우선순위 큐를 사용해서 출현 횟수를 우선순위 값으로 두는게 포인트 또한, 같은 우선순위일 경우 한 문자가 전부 나온 후 다른게 나와야 한다는 걸 생각해야함

## Code
https://leetcode.com/problems/sort-characters-by-frequency/solutions/4692341/topic
```go
import (
	"container/heap"
)

// An Item is something we manage in a priority queue.
type Item struct {
	value    string // The value of the item; arbitrary.
	priority int    // The priority of the item in the queue.
	// The index is needed by update and is maintained by the heap.Interface methods.
	index int // The index of the item in the heap.
}

// A PriorityQueue implements heap.Interface and holds Items.
type PriorityQueue []*Item

func (pq PriorityQueue) Len() int { return len(pq) }

func (pq PriorityQueue) Less(i, j int) bool {
	// We want Pop to give us the highest, not lowest, priority so we use greater than here.
	return pq[i].priority > pq[j].priority
}

func (pq PriorityQueue) Swap(i, j int) {
	pq[i], pq[j] = pq[j], pq[i]
	pq[i].index = i
	pq[j].index = j
}

func (pq *PriorityQueue) Push(x interface{}) {
	n := len(*pq)
	item := x.(*Item)
	item.index = n
	*pq = append(*pq, item)
}

func (pq *PriorityQueue) Pop() interface{} {
	old := *pq
	n := len(old)
	item := old[n-1]
	old[n-1] = nil  // avoid memory leak
	item.index = -1 // for safety
	*pq = old[0 : n-1]
	return item
}

// update modifies the priority and value of an Item in the queue.
func (pq *PriorityQueue) update(item *Item, value string, priority int) {
	item.value = value
	item.priority = priority
	heap.Fix(pq, item.index)
}

func frequencySort(s string) string {
    prior := make(map[string]int)
    for _, v := range s {
        prior[string(v)]++
    }
	// Create a priority queue, put the items in it, and
	// establish the priority queue (heap) invariants.

	pq := make(PriorityQueue, len(prior))
	i := 0
	for value, priority := range prior {
		pq[i] = &Item{
			value:    value,
			priority: priority,
			index:    i,
		}
		i++
	}
    heap.Init(&pq)

	// Take the items out; they arrive in decreasing priority order.
    ret := ""
	for pq.Len() > 0 {
		item := heap.Pop(&pq).(*Item)
        for i:=0; i < item.priority; i++ {
            ret += item.value
        }
	}
    return ret
}
```



## Performance
![image](https://github.com/hojin-kr/algorithm/assets/22079767/128da876-9e85-4d69-a812-1c7c232fdffc)
