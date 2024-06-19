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
