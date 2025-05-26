# Final-Project-Task-2

# Task 2
#include <iostream>  
#include <vector>  
#include <string>  
#include <unordered_map>  
  
std::string wordWithMostDuplicates(const std::vector<std::string>& words) {  
    std::string result = "";  
    int max_duplicates = 0;  
      
    for (const auto& word : words) {  
        std::unordered_map<char, int> char_count;  
          
        //count the frequency of each character  
        for (char c : word) {  
            char_count[c]++;  
        }  
          
        //count characters that  more than once 
        int duplicates = 0;  
        for (const auto& pair : char_count) {  
            if (pair.second > 1) {  
                duplicates += pair.second - 1; // Count extra occurrences  
            }  
        }  
          
        //fix result if this word has more duplicates  
        if (duplicates > max_duplicates) {  
            max_duplicates = duplicates;  
            result = word;  
        }  
    }  
      
    return result;  
}  
  
int main() {  
    std::vector<std::string> words = {  
        "lipstick", "bronzer", "blush", "foundation", "mascara", "eyeliner", "concealer", "highlighter", "lipliner", "powder"  
    };  
      
    std::string word_with_most_dups = wordWithMostDuplicates(words);  
      
    std::cout << "Makeup word with most duplicate letters: " << word_with_most_dups << std::endl;  
      
    return 0;  
}  
