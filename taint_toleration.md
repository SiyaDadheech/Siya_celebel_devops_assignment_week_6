First let's understand what taint and toleration is?  

Taint (Applied to Nodes) → Restricts Nodes so that only allowed Pods can be 
scheduled on them.  
Toleration (Applied to Pods) → Allows Pods to run on tainted Nodes.  

> Apply Taints to node.
Here we 3 type of effects 
1. NoSchedule 
2. PreferNoShedule 
3. NoExecute
   
   Effect of Taint:
   
• You applied a high-cpu taint on worker-node1.  

• Worker-node2 has no taint, meaning pods can be scheduled there without any 
restrictions.  


Effect of Tolerations:  

• You added tolerations in the deployment file, allowing pods to be scheduled on 
worker-node1 as well.  

• However, tolerations only provide permission; they do not guarantee that the 
pod will be scheduled on that node.  


