Replace a Particular word by Another word from a Given String in C++
Here, in this page we will discuss the program to Replace a Particular word by Another word from a Given String in C++ programming language.

Replace a Particular word by Another word from a Given String in C++
While loop in C
Method Discussed :
Method 1 : Brute force approach
Method 2 : In-place Replacing
Let’s discuss both the methods one by one in brief,

Method 1 :
Declare a string variable say ans = “” to store the required string.
Iterate over the characters of the string S using variable i and perform the following steps:
If the prefix substring of the string S is equal to S1 from the index i, then add the string S2 in the string ans.
Otherwise, add the current character to the string ans.
After completing the above steps, print the string ans as the result.
Method 1 : Code in C++
Run
#include <bits/stdc++.h>
using namespace std;
 
// Function to replace all the occurrences
// of the substring S1 to S2 in string S
void modifyString(string& s, string& s1,
                  string& s2)
{
    // Stores the resultant string
    string ans = "";
 
    // Traverse the string s
    for (int i = 0; i < s.length(); i++) {
 
        int k = 0;
 
        // If the first character of
        // string s1 matches with the
        // current character in string s
        if (s[i] == s1[k]
            && i + s1.length()
                   <= s.length()) {
 
            int j;
 
            // If the complete string
            // matches or not
            for (j = i; j < i + s1.length(); j++) {
 
                if (s[j] != s1[k]) {
                    break;
                }
                else {
                    k = k + 1;
                }
            }
 
            // If complete string matches
            // then replace it with the
            // string s2
            if (j == i + s1.length()) {
                ans.append(s2);
                i = j - 1;
            }
 
            // Otherwise
            else {
                ans.push_back(s[i]);
            }
        }
 
        // Otherwise
        else {
            ans.push_back(s[i]);
        }
    }
 
    // Print the resultant string
    cout <<"Modified String : "<< ans;
}
 
// Driver Code
int main()
{
    string S = "Let's Learn C";
    string S1 = "C";
    string S2 = "C++";
    cout<<"Original String : "<<S<<endl;
    modifyString(S, S1, S2);
 
    return 0;
}
Output
Original String : Let's Learn C
Modified String : Let's Learn C++
Related Pages
Juggling algorithm for array rotation
 
Balanced Parenthesis Problem
 
Toggle each character in a string

Find the ASCII value of a character

Length of the string without using strlen() function

Method 2 :
This method involves inplace update of string. It is more efficient as it uses only extra space for the new characters to be inserted.

Method 2 : Code in C++
Run
#include < bits/stdc++.h >
using namespace std;
int main ()
{
    string s = "Let's Learn C";
    cout << "Original String : " << s << endl;
  
    string x = "C", y = "C++";

    reverse (s.begin (), s.end ());
    reverse (x.begin (), x.end ());
    reverse (y.begin (), y.end ());

    int ls = s.length (), lx = x.length (), ly = y.length ();
    int d = ly - lx;
    int ct = 0;
    int i = 0, j = 0;

    while (i < ls){
      
        string temp = "";
      
        for (int k = 0; k < lx; k++){
	        temp += s[i + k];
	    }

        if (temp == x){
	        ct++;
	        i = i + lx;
        }
      
        else{
	        i = i + 1;
	    }
    }

    for (int i = 0; i < ct * d; i++)
        s += ' ';
  
    i = ls - 1;
    j = ls + ct * d - 1;
  
    while (i >= 0 && j >= 0){
        string temp = "";
        
        for (int k = 0; k < lx; k++){
	        if (i < (lx - 1 - k))
	            break;
	        temp += s[i - (lx - 1 - k)];
	    }
      
        if (temp == x){
	        int k = ly - 1;
	        while (k >= 0)
	            s[j--] = y[k--];
	        i = i - lx;
	    }
        
        else{
	        s[j--] = s[i--];
	    }
    }
    
    reverse (s.begin (), s.end ());
    cout << "Modified String : " << s << endl;

    return 0;
}
Output
Original String : Let's Learn C
Modified String : Let's Learn C++
