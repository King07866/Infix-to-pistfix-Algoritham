# Infix-to-pistfix-Algoritham
This Algorithm helps you how to convert infix ezpreaauons in Postfix expression
def call(value):
    global temp
    temp = 0 
    if(value == '+'):
        # global add
        temp = 1
    elif(value == '-'):
        global sub 
        temp = 2
    elif(value == '*'):
    #    global mul 
       temp = 3
    elif(value == '/'):
        # global div
        temp = 4
    elif(value == '^'):
        # global power
        temp = 5

Q = ['A','+','(','B','*','C','-','(','D','/','E','^','F',')','*','G',')','*','H']
P = []
STACK = []
STACK.append('(')
Q.append(')')
a = 0

while (len(STACK)):
    if(Q[a] != '(' and Q[a] != ')' and Q[a] != '+' and Q[a] != '-' and Q[a] != '*' and Q[a] != '/' and Q[a] != '^'):
        P.append(Q[a])
           
    elif(Q[a] == '('):
        STACK.append(Q[a])

    elif(Q[a] == '+' or Q[a] == '-' or Q[a] == '*' or Q[a] == '/' or Q[a] == '^'):
        call(Q[a])
        statment1 = temp
        call(STACK[len(STACK) - 1])
        statment2 = temp
        while(STACK[len(STACK) - 1] != '(' and statment1 < statment2):
                if(statment1 <= statment2):
                    P.append(STACK[len(STACK) - 1])
                    STACK.pop()
        else:
            STACK.append(Q[a])

    elif(Q[a] == ')'):
        while(STACK[len(STACK) - 1] != '('):
            P.append(STACK[len(STACK) - 1])
            STACK.pop()
        if(STACK[len(STACK) - 1] == '('):
            STACK.pop()
    a += 1
print(STACK)

print(P)
    
