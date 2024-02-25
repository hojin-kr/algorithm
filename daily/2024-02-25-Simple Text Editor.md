## Info
- Title : Simple Text Editor
- Description : [https://www.hackerrank.com/challenges/one-week-preparation-kit-balanced-brackets](https://www.hackerrank.com/challenges/one-week-preparation-kit-simple-text-editor)
- Provider : hackerRank

## Intuition
논리적 문제 이해
## Approach
<!-- Describe your approach to solving the problem. -->
각 에디터 기능에 대해 어떤 기술로 구현 할지에 대해 고민

## Code
```
# Enter your code here. Read input from STDIN. Print output to STDOUT

class myEditor:
    def __init__(self):
        self.text = ""
        self.rollback = []
    
    
def editorInput(editor, command):
    commands = command.split(" ")
    operation = commands[0]
    
    if '1' in operation:
        editor.rollback.append(editor.text)
        editor.text += commands[1]
    elif '2' in operation:
        # delet
        editor.rollback.append(editor.text)
        editor.text = editor.text[0:len(editor.text) - int(commands[1])]
    elif '3' in operation:
        print(editor.text[int(commands[1])-1])
    elif '4' in operation:
        editor.text = editor.rollback.pop()
    else:
        print("Not Supported")
        



if __name__ == '__main__':
    cnt = int(input().strip())
    
    editor = myEditor()
    for v in range(cnt):
        inputs = input().rstrip().strip()
        editorInput(editor, inputs)
    
    
```
