# Tata_technologies Bowling game code

#include <iostream>
#include <vector>

using namespace std;

int calculate_bowling_score(const vector<int>& throws) {
    int score = 0;
    int strike_bonus_count = 0;

    
    for (int i = 0; i < throws.size(); ++i) {
       
        if (throws[i] == 10) {
           
            score += 10;
           
            if (i + 1 < throws.size() && i + 2 < throws.size()) {
                score += throws[i + 1] + throws[i + 2];
            } else if (i + 1 < throws.size()) {
                score += throws[i + 1];
            }
            i += 1;  
        } else { // Not a strike
            score += throws[i];
            if (i + 1 < throws.size()) {
               
                if (throws[i] + throws[i + 1] == 10) {
                    score += throws[i + 1];
                    i += 1;  
                } else {
                    score += throws[i + 1];
                    i += 1;
                }
            }
        }
    }

    return score;
}

int main() {
   
    vector<int> throws = {10, 6, 4, 8, 2, 9, 0, 5, 7, 3, 10, 10, 8, 2, 10};

   
    int total_score = calculate_bowling_score(throws);
    cout << "Total score: " << total_score << endl;

    return 0;
}
