# Count-Substrings-with-Exactly-K-Distinct-Characters
You are given a string s of lowercase English alphabets and an integer k. Your task is to count all possible substrings of s that contain exactly k distinct characters.  Input : A string s consisting of lowercase English letters. An integer k, where 1 ≤ 𝑘 ≤ 26 The length of the string satisfies 1 ≤ 𝑛 ≤ 104 Example - s = "pqpqs", k = 2
def countSubstringsWithKDistinct(s, k):
    def atMost(k):
        count = {}
        left = res = 0
        for right, ch in enumerate(s):
            count[ch] = count.get(ch, 0) + 1
            while len(count) > k:
                count[s[left]] -= 1
                if count[s[left]] == 0:
                    del count[s[left]]
                left += 1
            res += right - left + 1
        return res
    return atMost(k) - atMost(k-1)
s = "pqpqs"
k = 2
print(countSubstringsWithKDistinct(s, k)) 
