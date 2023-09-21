# Task_Manager
import datetime 

#====Login Section====

usernames = []
passwords = []

username = input('Please enter your username: ')
password = input('Please enter your password: ')
print('')

with open('user.txt', 'r') as file:

    for lines in file:
        temp = lines.strip()
        temp = temp.split(', ')
        usernames.append(temp[0])
        passwords.append(temp[1])

while (username not in usernames) or (password not in passwords):

    print('You have entered an invalid username or password')
    username = input('Please enter your username again: ')
    password = input('Please enter your password again: ')
    
while True:
        
    #presenting the menu to the user and 
    # making sure that the user input is coneverted to lower case.
    menu = input('''Select one of the following Options below:
r - Registering a user
a - Adding a task
va - View all tasks
vm - view my task
s - statistics
e - Exit
: ''').lower()
    print('')
              
    if menu == 'r':

    # Write ode so that only the usersame 'admin' from the user.txt file is allowed to register users'''
        
        '''
        new_username = input('Please enter your username: ')
        new_password = input('Please enter your password: ')
        confirmed_password = input('Please confirm your password: ')

        while new_password != confirmed_password:
        print('Your password does not match')
        confirmed_password = input('Please confirm your password: ')

        if new_password == confirmed_password:
            with open('user.txt', 'a') as file:
                file.write(f'\n{new_username}, {new_password}')'''
        
        with open('user.txt', 'a+') as file:

            if username == 'admin' and password == 'adm1n':
                new_username = input('Enter the username: ')
                new_password = input('Enter the password:')
                file.write(f'\n{new_username}, {new_password}')

            else:
                print('Sorry you are not allowed to register a new user')
            
            print('')

    elif menu == 'a':
        # Write code that will allow a user to add a new task to task.txt file
        username = input("Enter the name of the person the task is assigned to: ")
        task_tile = input('Enter the title of the task: ')
        task_description = input('Enter the description of the task: ')
        task_date = input('Enter the date of the task (in DD/MM/YYYY)"): ') 
        current_date = datetime.date.today()
        task_complition = input('Please indicate if the taks has been completed (Yes or No): ') 
        with open('tasks.txt', 'a') as file:
            file.write(f'\n{username}, {task_tile}, {task_description}, {task_date}, {current_date}, {task_complition}')

        print('')

    elif menu == 'va':
        # Write code so that the program will read the task from task.txt file and print it out
        with open('tasks.txt', 'r') as file:
            for lines in file:
                temp = lines.strip()
                temp = temp.split(', ')
                temp = temp[0: ]
                print('Task\t\t', temp[1],'\nAssigned to:\t', temp[0],'\nDate assigned:\t', temp[3], '\nDue date:\t', temp[4], '\nTask Copmplete?\t', temp[5], '\nTask description:\n', temp[2], '\n')

    elif menu == 'vm':
    # Write code the that will read the task from task.txt file and print to the console 
        log_in1 = input('Enter your username: ')
        print('')
        with open('tasks.txt', 'r') as file:
            for lines in file:
                temp = lines.strip()
                temp = temp.split(', ')
                temp = temp[0: ]
                if log_in1 == temp[0]:
                        print('Task\t\t', temp[1],'\nAssigned to:\t', temp[0],'\nDate assigned:\t', temp[3], '\nDue date:\t', temp[4], '\nTask Copmplete?\t', temp[5], '\nTask description:\n', temp[2], '\n')
  
    elif menu == 's':
    # Write Code the that will allow 'admin' user to display statistics
    # When this menu option is selected, the total number of tasks and the total number of users should be displayed

        if username == 'admin' and password == 'adm1n':

            tasks = []
            users = []

            with open('tasks.txt', 'r') as file:
                
                lines = file.readlines()
                tasks = (len(lines))
            
            with open('user.txt', 'r') as file:

                lines = file.readlines()
                users = (len(lines))

            print('')
            print(f'The total number of tasks is {tasks} and the total number of users is {users}')
            print('')
        
        print('You are not allowed to diplay statistics')
        print('')

    elif menu == 'e':
        print('Goodbye!!!')
        exit()

    else:
        print("You have made a wrong choice, Please Try again")
