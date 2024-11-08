# LeetCode20Solution

#include <stack>
#include <unordered_map>
using namespace std;

class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        unordered_map<char, char> bracket_map = {
            {')', '('},
            {'}', '{'},
            {']', '['}
        };

        for (char c : s) {
            // If the character is a closing bracket
            if (bracket_map.count(c)) {
                // Pop the top element or use a dummy value if the stack is empty
                char top_element = st.empty() ? '#' : st.top();
                st.pop();

                // Check if the popped element matches the expected opening bracket
                if (top_element != bracket_map[c]) {
                    return false;
                }
            } else {
                // Push open bracket onto the stack
                st.push(c);
            }
        }

        // If stack is empty, all brackets are matched; otherwise, return false
        return st.empty();
    }
};
