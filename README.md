# Tata_technologies Bowling game code

#include <iostream>
#include <vector>

using namespace std;

int calculate_bowling_score(const vector<int>& throws) {
    int score = 0;
    int strike_bonus_count = 0;

    // Iterate through each frame (throw) in the throws vector
    for (int i = 0; i < throws.size(); ++i) {
        // Check for strike (10 pins knocked down in the first throw)
        if (throws[i] == 10) {
            // Add 10 for the strike + bonus of next two throws
            score += 10;
            // Check if strike bonus has been applied
            if (i + 1 < throws.size() && i + 2 < throws.size()) {
                score += throws[i + 1] + throws[i + 2];
            } else if (i + 1 < throws.size()) {
                score += throws[i + 1];
            }
            i += 1;  // Skip the next two throws (strike's bonus)
        } else { // Not a strike
            score += throws[i];
            if (i + 1 < throws.size()) {
                // Check for spare (all pins knocked down in two throws)
                if (throws[i] + throws[i + 1] == 10) {
                    score += throws[i + 1];
                    i += 1;  // Skip the next throw (spare's bonus)
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
    // Example throws for a player (replace with actual input)
    vector<int> throws = {10, 6, 4, 8, 2, 9, 0, 5, 7, 3, 10, 10, 8, 2, 10};

    // Calculate and display the score
    int total_score = calculate_bowling_score(throws);
    cout << "Total score: " << total_score << endl;

    return 0;
}
