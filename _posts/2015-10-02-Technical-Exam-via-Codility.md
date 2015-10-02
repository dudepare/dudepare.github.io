---
layout: post
---

I am actively looking for work at the moment. I am a long time C++ programmer and now I want to work more on Python projects. I applied to some of the Python job openings and got shortlisted for one recently. They required me to take a test on Codility.com but I was told I did not pass the test. 

Prior to taking the test, I took the demo problem. I was able to come up with the solution but with the help of google search... not a very pleasant experience. Anyway, I solved a few problems. I failed a lot of times on both Correctness and Performance scales but development is a process. 

Here are some of my answers to the codility lessons:

# [Equi](http://blog.codility.com/2011/03/solutions-for-task-equi.html)

    def equi(A):
        if len(A) == 0:
            return -1

        sum = 0
        # compute for the sum
        for i in range(len(A)):
            sum += A[i]

        lsum = 0
        for k in range(len(A)):
            rsum = sum - lsum - A[k]
            if rsum == lsum:
                return k
            lsum += A[k]

        return -1

# [Tape Equilibrium](https://codility.com/programmers/task/tape_equilibrium)

    def tape_equi(A):
        lsum = A[0]
        rsum = 0
        min_diff = -1
        total = sum(A)

        for i in range(len(A) - 1):
            rsum = total - lsum
            current_diff = abs(lsum - rsum)
            if min_diff == -1:
                min_diff = current_diff
            else:
                min_diff = min(min_diff, current_diff)
            lsum += A[i+1]

        return min_diff

# [FrogJmp](https://codility.com/programmers/task/frog_jmp)

*I tried the approach Math.ceil(abs(Y-X))/D) codility seems to ignore import statements.*

    def frogjump(X, Y, D):
        return (abs(Y-X) + (D-1))//D

# [PermMissingElem](https://codility.com/programmers/task/perm_missing_elem)

    def missing(A):
        size = len(A)
        if size == 0:
            return 1
        total = 0
        for i in range(1, size+2):
            total +=i

        return total - sum(A)

# [FrogRiverOne](https://codility.com/programmers/task/frog_river_one)

    def frog_river_one(X,A):
        leaf_pos = [1] * (X+1)
        total = sum(leaf_pos)
        for i in range(len(A)):
            total -= leaf_pos[A[i]]
            leaf_pos[A[i]] = 0
            if total == 1:
                return i

        return -1

This is where I stopped solving codility problems. I think my time will be better served if I continue contributing to open source projects.