给定两个非空链表来表示两个非负整数。位数按照逆序方式存储，它们的每个节点只存储单个数字。将两数相加返回一个新的链表。

你可以假设除了数字 0 之外，这两个数字都不会以零开头。

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */
class Solution {
    func getValFromNode(_ node: ListNode?) -> Int {
        guard let node = node else { return 0 }
        return node.val
    }
    
    func getNextNode(_ node: ListNode?) -> ListNode? {
        guard let node = node else { return nil }
        return node.next
    }
    
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        
        if(l1==nil)&&(l2==nil) {
            return nil
        }
        
        var ll1 = l1
        var ll2 = l2
        
        let head = ListNode(0)
        var point = head
        var carry = 0
        
        while (ll1 != nil) || (ll2 != nil) || carry != 0 {
            let total = getValFromNode(ll1) + getValFromNode(ll2) + carry
            point.val = total % 10
            carry = total / 10
            
            ll1 = getNextNode(ll1)
            ll2 = getNextNode(ll2)
            if ll1 != nil || ll2 != nil || carry != 0 {
                point.next = ListNode(0)
                point = point.next!
            }
        }
        
        return head
    }

}
```
