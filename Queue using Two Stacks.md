class QueueUsingTwoStacks:
    def __init__(self):
        self.stack_in = []  
        self.stack_out = []  
    def enqueue(self, value):
        self.stack_in.append(value)
    def dequeue(self):
        self._shift_stacks()
        if self.stack_out:
            self.stack_out.pop()
    def front(self):
        self._shift_stacks()
        if self.stack_out:
            return self.stack_out[-1]
    def _shift_stacks(self):
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
if __name__ == "__main__":
    q = int(input().strip())  
    queue = QueueUsingTwoStacks()

    for _ in range(q):
        query = input().strip().split()
        command = int(query[0])

        if command == 1:  
            value = int(query[1])
            queue.enqueue(value)
        elif command == 2:  
            queue.dequeue()
        elif command == 3:  
            print(queue.front())

#Test Case As per HackerRank
10
1 42
2
1 14
3
1 28
3
1 60
1 78
2
2
#Output
14
14
