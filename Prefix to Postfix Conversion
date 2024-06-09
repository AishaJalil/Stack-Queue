#include <iostream>
#include <string>
using namespace std;

template <class N>
class Node {
public:
    N data;
    Node* next;

    Node(N data) {
        this->data = data;
        next = NULL;
    }
};

template <class N>
class Stack {
public:
    Node<N>* top;

    Stack() {
        top = NULL;
    }

    void push(N data) {
        Node<N>* newNode = new Node<N>(data);
        newNode->next = top;
        top = newNode;
    }

    N pop() {
        if (top != NULL) {
            N temp = top->data;
            Node<N>* nexttop = top->next;
            delete top;
            top = nexttop;
            return temp;
        }
    }

    N peek() {
        if (top != NULL)
            return top->data;
    }

    bool isEmpty() {
        return top == NULL;
    }
};

int prec(char c) {
    if (c == '+' || c == '-')
        return 1;
    else if (c == '*' || c == '/' || c == '%')
        return 2;
    else if (c == '^')
        return 3;
    return -1;
}

bool isOperator(char c) {
    if (c == '+' || c == '-' || c == '*' || c == '/' || c == '%' || c == '^')
        return true;
    return false;
}

string PrefixtoInfix(string str) {
    Stack<string> Infix;
    int size = str.length();
    char c;
    string result, op1, op2;

    for (int i = size - 1; i >= 0; i--) {
        c = str[i];
        if (isOperator(c)) {
            while (!Infix.isEmpty() && Infix.peek() != ".") {
                op1 = Infix.peek();
                Infix.pop();
            }
            Infix.pop();
            while (!Infix.isEmpty() && Infix.peek() != ".") {
                op2 = Infix.peek();
                Infix.pop();
            }

            string temp = "(" + op1 + c + op2 + ")";
            Infix.push(temp);
        } else {
            if (c == '.')
                Infix.push(".");
            else
                Infix.push(string(1, c));
        }
    }

    return Infix.peek();
}

void  InfixtoPostfix(string str)
{
//	cout<<str<<endl;
	
	Stack<char> s1;
	int lenght = str.length();
	string result;
	char c;
	for(int i=0; i<lenght; i++)
	{
		c= str[i];
		
		if( (c >= 'A' && c<= 'Z') || (c>= 'a' && c<= 'z' )|| (c>= '0' && c<= '9'))
		result += c;
		else if(c == '(')
		s1.push(c);
		else if(c == ')')
		{
			while(!s1.isEmpty() && s1.peek()!= '(' )
			{
				result += s1.pop();
				
			}
			s1.pop();
		}
		else
		{
			while( ! s1.isEmpty() && prec(str[i])<= prec(s1.peek()))
			{
				result += s1.pop();
			}
			s1.push(c);
		}
	}
	while(! s1.isEmpty())
	{
		result+= s1.pop();
	}
	cout<<"Postfix Expression: "<<result;

	
}
int main() {
    string infix = PrefixtoInfix("*-A./B.C.-/A.K.L.");
    cout <<"Infix Expression: "<< infix << endl;
    InfixtoPostfix(infix);
}
