# meta_daily
LC : 1650. Lowest Common Ancestor of a Binary Tree III

![image](https://github.com/atishay2/meta_daily/assets/52835993/b5f406f9-c31e-4891-a8f4-7b41cd1a9443)
![image](https://github.com/atishay2/meta_daily/assets/52835993/9a69bfcf-f320-49f4-84da-e2084fa0a29e)

    class Solution:
      def lowestCommonAncestor(self, p: 'Node', q: 'Node') -> 'Node':
            seen = set()
    
            while p :
                seen.add(p)
                p = p.parent
            while q :
                if q in seen :
                    return q
                q = q.parent

LC : 708. Insert into a Sorted Circular Linked List (R E V I S E)

![image](https://github.com/atishay2/meta_daily/assets/52835993/24988ad9-58a4-41fc-986b-77e64a4565db)
![image](https://github.com/atishay2/meta_daily/assets/52835993/ee733215-ebee-4a3a-b745-9ee6ab26e62f)

    class Solution:
        def insert(self, head: 'Optional[Node]', insertVal: int) -> 'Node':
            
            if not head:
                new_node = Node(insertVal)
                new_node.next = new_node
                return new_node
        
            cur = head 
            while cur.next != head:
                
                if cur.val <= insertVal <= cur.next.val:
                    
                    new_node = Node(insertVal)
                    new_node.next = cur.next
                    cur.next = new_node
                    return head
            
                elif cur.val > cur.next.val and (cur.next.val >=insertVal or cur.val <= insertVal):
                    
                    new_node = Node(insertVal)
                    new_node.next = cur.next
                    cur.next = new_node
                    return head
                cur = cur.next
            new_node = Node(insertVal)
            new_node.next = cur.next
            cur.next = new_node
                    
            return head 

LC : 314. Binary Tree Vertical Order Traversal (Revisit)

![image](https://github.com/atishay2/meta_daily/assets/52835993/f2989267-1754-44cd-ac05-7790dc4cc4d8)
![image](https://github.com/atishay2/meta_daily/assets/52835993/a7e1f04f-ba2d-4d95-8c2c-59d71e1a92d1)

    class Solution:
        def verticalOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
            if not root: return []
            dic = {} 
            
            def dfs(node, level, depth):
                if node is None: return 
                
                if level not in dic : dic[level] = [(depth, node.val)]
                else : dic[level].append((depth,node.val))
                
                left = dfs(node.left, level + 1, depth+1)
                right = dfs(node.right, level - 1, depth+1)
    
            dfs(root, 0, 0)
            res = []
            
            for x in range(max(dic.keys()), min(dic.keys())-1, -1):
                dic[x].sort()
                cur = []
                
                for a,b in (dic[x]):
                    cur.append(b)
                res.append(cur)
            return res
