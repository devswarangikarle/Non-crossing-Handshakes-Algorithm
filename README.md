# Non-crossing-Handshakes-Algorithm
There are N people sitting on a round table. Any person can do a handshake with any other person.       1 2         3      4  Handshake with 2-3 and 1-4 will cause cross.  In how many ways these N people can make handshakes so that no two handshakes cross each other.  N would be even.


def count_handshakes(N):
    if N % 2 != 0 or N < 2 or N > 20:
        return 0 
    dp = [0] * (N + 1)
    dp[0] = 1
    dp[2] = 1

    for i in range(4, N + 1, 2):
        for j in range(0, i, 2):
            dp[i] += dp[j] * dp[i - 2 - j]

    return dp[N]

try:
    N = int(input().strip())
    result = count_handshakes(N)
    print(result)
except ValueError:
    print(0)
