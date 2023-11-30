import UIKit

class LinkedListNode<T> {
    typealias ListNode = LinkedListNode<T>
    var value: T
    var nextNode: ListNode?
    var previousNode: ListNode?
    
    init(value: T) {
        self.value = value
    }
}


struct LinkedList<T> {
    typealias ListNode = LinkedListNode<T>
    
    private var head: ListNode?
    
    var first: ListNode? {
        return head
    }
    
    var last: ListNode? {
        guard var head = head else { return nil }
        while let next = head.nextNode {
            head = next
        }
        return head
    }
    
    mutating func node(at index: Int) -> ListNode {
        if index == 0 {
            return head!
        } else {
            var node = head?.nextNode
            for _ in 1..<index {
                node = node?.nextNode
                if node == nil { break }
            }
            return node!
        }
    }
    
   
    
    
    mutating func append(value: T){
        var newNode = ListNode(value: value)
        
        if let lastNode = last {
            newNode.previousNode = lastNode
            lastNode.nextNode = newNode
        } else {
            head = newNode
        }
    }
    
    mutating func insert(at index: Int, value: T) {
        var newNode = ListNode(value: value)
        
        if index == 0 {
            newNode.nextNode = head
            head?.previousNode = newNode
            head = newNode
        } else {
            var prev = self.node(at: index - 1)
            var next = prev.nextNode
            
            newNode.previousNode = prev
            newNode.nextNode = prev.nextNode
            
            prev.nextNode = newNode
            next?.previousNode = newNode
        }
    }
    
    private mutating func remove(node: ListNode) -> T {
        var prev = node.previousNode
        var next = node.nextNode
        
        if let prev = prev {
            prev.nextNode = next
        } else {
            head = next
        }
        next?.previousNode = prev
        
        node.previousNode = nil
        node.nextNode = nil
        
        return node.value
    }
    
    mutating func removeAt(_ index: Int) -> T {
        let needNode = node(at: index)
        
        return remove(node: needNode)
    }
    
}


var listSample = LinkedList<Int>()
listSample.append(value: 10)
listSample.insert(at: 0, value: 200)
listSample.node(at: 0).value
listSample.insert(at: 0, value: 17)
listSample.node(at: 1).value
listSample.removeAt(0)





