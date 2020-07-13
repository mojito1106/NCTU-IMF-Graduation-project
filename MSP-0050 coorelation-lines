# -*- coding: utf-8 -*-
"""
Created on Tue Sep 24 21:15:56 2019

@author: 徐筠婷 易情恩
"""

# Python program for Kruskal's algorithm to find 
# Minimum Spanning Tree of a given connected,  
# undirected and weighted graph 
  
from collections import defaultdict 
#Class to represent a graph 
class Graph: 
  
    def __init__(self,vertices): #初始化
        self.V= vertices #No. of vertices   
        self.graph = [] # default dictionary  
                                # to store graph 
          
   
    # function to add an edge to graph 
    def addEdge(self,u,v,w): #u；起點編號、v:終點編號、w:點之間的長度 
        self.graph.append([u,v,w]) 
  
    # A utility function to find set of an element i 
    # (uses path compression technique) 
    def find(self, parent, i): 
        if parent[i] == i: 
            return i 
        return self.find(parent, parent[i]) 
  
    # A function that does union of two sets of x and y 
    # (uses union by rank) 
    def union(self, parent, rank, x, y): 
        xroot = self.find(parent, x) 
        yroot = self.find(parent, y) 
  
        # Attach smaller rank tree under root of  
        # high rank tree (Union by Rank) 
        if rank[xroot] < rank[yroot]: 
            parent[xroot] = yroot 
        elif rank[xroot] > rank[yroot]: 
            parent[yroot] = xroot 
  
        # If ranks are same, then make one as root  
        # and increment its rank by one 
        else : 
            parent[yroot] = xroot 
            rank[xroot] += 1
  
    # The main function to construct MST using Kruskal's  
        # algorithm 
    def KruskalMST(self): 
  
        result =[] #This will store the resultant MST
        count =[0]*49
        w =[0]*49
        l=[]
        #rk =[]
    
  
        i = 0 # An index variable, used for sorted edges 
        e = 0 # An index variable, used for result[] 
  
            # Step 1:  Sort all the edges in non-decreasing  
                # order of their 
                # weight.  If we are not allowed to change the  
                # given graph, we can create a copy of graph 
        self.graph =  sorted(self.graph,key=lambda item: item[2]) 
        self.graph.reverse()
        parent = [] ; rank = [] 
  
        # Create V subsets with single elements 
        for node in range(self.V): 
            parent.append(node) 
            rank.append(0) 
      
        # Number of edges to be taken is equal to V-1 
        while e < self.V -1 : #邊的數量是點的數量減一
  
            # Step 2: Pick the smallest edge and increment  
                    # the index for next iteration 
            u,v,w =  self.graph[i] 
            i = i + 1
            x = self.find(parent, u) 
            y = self.find(parent ,v) 
  
            # If including this edge does't cause cycle,  
                        # include it in result and increment the index 
                        # of result for next edge 
            if x != y: 
                e = e + 1     
                result.append([u,v,w]) 
                self.union(parent, rank, x, y)             
            # Else discard the edge 
  
        # print the contents of result[] to display the built MST 
        #print "Following are the edges in the constructed MST"
        for u,v,weight  in result: 
            #print str(u) + " -- " + str(v) + " == " + str(weight) 
            print ("%d -- %d == %d" % (u,v,weight))
            count[u]=count[u]+1 #算每個點的線數
            count[v]=count[v]+1
            #w[u]
            
        num=0
        a=0
        for i in count:
            
            print ("位置[%d]：%d" % (a, i))
         
    
            num= num+i
            a=a+1
        print(num)
      
        a=0
        for i in count:
            w=round(i/num, 3)                
            print ("位置[%d]：%d(權重:%f)" % (a, i, w))
            
            a=a+1
  
# Driver code 
            
filename = 'C:/Users/LOVESS/Desktop/資財專題/(2版)台股49成分股、相關係數（扣除大盤與台積電）/相關係數(超額報酬)(P值0.05)/2019-2 超額報酬.txt'
lines=[]
g = Graph(49)
with open(filename, 'r',encoding="utf-8") as file_to_read:
    while True:
            line = file_to_read.readline() # 整行讀取資料
            if not line:
                break
            line_arr=line.split(' ')
    #        print(line_arr)
            lines.append(line_arr)
      
    
#    x=float(lines[0][1])#這樣取值後再仍進你們的函式
#    print(x)
x1=0
lines=lines[0:]
for i in range(49):
    for j in range(49):
        if i>j:
            tempc=round(float(lines[i][j])*100,0)     
            if tempc<0:
                tempc=abs(tempc)
            g.addEdge(i, j, tempc)
 #           print(tempc)
        else:
            pass
            
g.KruskalMST() 
