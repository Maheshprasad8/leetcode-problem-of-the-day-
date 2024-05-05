237. Delete Node in a Linked List
     5th May 24
class Solution {
public:
    void deleteNode(ListNode* node) {
        ListNode* temp=node->next;
        node->val=temp->val;
        node->next=temp->next;
        delete temp;
    }
};
