<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:LOGESH S    </h3>
<h3>Register Number: 2305001014         </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm
1. Initialize:

* open_set = {start}, g[start] = 0, parents[start] = None.

2. While open_set not empty:
   
*  Pick node n with lowest f(n) = g[n] + H[n].
* If n is goal → reconstruct and return path
* Compute cost g[n] + weight.
* If better, update g[m], parents[m], add m to open_set.

4. If loop ends without reaching goal → path doesn’t exist.

## PROGRAM
```python
graph, H = {}, {}
def AStar(start, goal):
    open_set, g, parents = [start], {start:0}, {start:None}
    while open_set:
        n = min(open_set, key=lambda x: g[x]+H[x])
        if n==goal:
            path=[]
            while n: path.append(n); n=parents[n]
            print("Path found:", path[::-1]); return
        open_set.remove(n)
        for m,w in graph.get(n,[]):
            cost=g[n]+w
            if m not in g or cost<g[m]:
                g[m]=cost; parents[m]=n
                if m not in open_set: open_set.append(m)
    print("Path does not exist!")
n,e=map(int,input().split())
for _ in range(e):
    u,v,w=input().split(); w=int(w)
    graph.setdefault(u,[]).append((v,w))
    graph.setdefault(v,[]).append((u,w))
for _ in range(n):
    node,h=input().split(); H[node]=int(h)
AStar(input(),input())

```

SAMPLE INPUT
10 14
A B 6
A F 3
B D 2
B C 3
C D 1
C E 5
D E 8
E I 5
E J 5
F G 1
G I 3
I J 3
F H 7
I H 2
A 10
B 8
C 5
D 7
E 3
F 6
G 5
H 3
I 1
J 0
A
J
<hr>
Sample Output
<img width="493" height="612" alt="Screenshot 2025-10-06 134443" src="https://github.com/user-attachments/assets/dddf5cb1-ac1b-4e63-a1e6-dc38389bf8a5" />
<hr>

RESULT:
The program successfully implements the A* Search Algorithm and finds the shortest path from the given start node to the goal node

## RESULT
