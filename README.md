# Soduko

def print_mat(A):
    for i in range(len(A)):
        print(A[i])

def check_row(A,n):
    x = n // len(A)
    y = n % len(A)
    val=A[x][y]
    count = 0
    for i in range(len(A)):
        if A[x][i]==val:
            count += 1
    return count==1

def check_col(A,n):
    x = n // len(A)
    y = n % len(A)
    val=A[x][y]
    count = 0
    for i in range(len(A)):
        if A[i][y]==val:
            count += 1
    return count==1

def check_box(A,n):
    x = n // len(A)
    y = n % len(A)
    val = A[x][y]
    x_start= x-x%3
    y_start= y-y%3
    count = 0
    for i in range(3):
        for j in range(3):
            if A[x_start+i][y_start+j]==val:
                count += 1
    return count==1

def check_validity(A,n):
    return check_row(A,n) and check_col(A,n) and check_box(A,n)

def det_fixed(A):
    B=[A[:] for i in range(len(A))]
    for i in range(len(A)):
        for j in range(len(A)):
            if A[i][j]!=0:
                B[i][j]=True
            else:
                B[i][j]=False
    return B

def check_fixed(n,B):
    x = n // len(A)
    y = n % len(A)
    return B[x][y]

def go_back(B,n):
    count=1
    n-=1
    while check_fixed(n,B):
        count+=1
        n-=1
    return count



A = [
    [8, 0, 0, 0, 7, 0, 0, 0, 6],
    [0, 3, 0, 0, 0, 0, 0, 9, 0],
    [0, 0, 0, 2, 0, 1, 0, 0, 0],
    [0, 0, 9, 4, 1, 5, 6, 0, 0],
    [3, 0, 0, 0, 0, 0, 0, 0, 1],
    [0, 0, 6, 8, 3, 9, 4, 0, 0],
    [0, 0, 0, 1, 0, 6, 0, 0, 0],
    [0, 9, 0, 0, 0, 0, 0, 6, 0],
    [7, 0, 0, 0, 9, 0, 0, 0, 2]
]
Fixed_nums=det_fixed(A)

n=0
while n<81:
    x = n // len(A)
    y = n % len(A)
    if check_fixed(n,Fixed_nums):
        n+=1
        continue
    while True:
        A[x][y]+=1
        if A[x][y]==10:
            A[x][y]=0
            n-=go_back(Fixed_nums,n)
            break
        elif check_validity(A,n):
            n+=1
            break

print_mat(A)






