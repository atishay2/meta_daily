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
