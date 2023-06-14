# Automate_bash_to_noob
This Program is done for noob who are new to Linux and have no Knowledge of Commands.
Hi Everyone This is Macronol
You know Linux is the Popular Operating System use across the Globe. You need to Learn Linux Fast I can help you out.
Now Follow my Instructions 

1. Start your VM
2. Open the Terminal
3. Open any editor since your new Open gedit for now
4. Type gedit file.sh
5. Copy the code below and save it
6. Since you are new you may forget now to run the script so i made an Automation
7. First open bashrc
8. nano ~/.bashrc (shell script that Bash runs whenever it is started.)
9. then scroll down to the end and paste the below code.
10. alias Google='bash file.sh'
11. Now save the file since it is nano ctrl +  o to save and ctrl + x to exit
12. Now open new terminal and type Google you might get surprise

##The Code comes here:
#!/bin/bash



# check weather user is root 
if [[ $EUID -ne 0 ]]; then
  echo "Be root user and try again!!"
  exit 1
fi

# Create a directory for the output.
mkdir -p output

echo "Hi There, I am you Google How can I help you"

i="y"

while [ $i = "y" ] 

do 

	# Menu items

	echo "Please select an option:"

	echo "1. List all files in a directory"

	echo "2. Count the number of lines in a file"

	echo "3. Search for a specific string in a file"

	echo "4. Check system resource usage"

	echo "5. Need any Command Info. We can help you out"

	echo "6. Ohh need to know where you are right now"

	echo "7. Need to create a folder but idk now" 

	echo "8. Need help in removing Folder"

	echo "9. I can move files for you"

	echo "10. need a copy of something"

	echo "11. I can create files also"

	echo "12. Peep inside a file"

	echo "13. Peep Top of the file"

	echo "14. Peep Bottom of the file"

	echo "15. Forgot total word after clossing i can help you"

	echo "16. I have a file but sort me"

	echo "17. Sorted but i can see duplicates now"

	echo "18. Cant find what changed in this file when i copied"

	echo "19. Wish me something"

	echo "20. file is not executing i can help"

	echo "21. Need a current directory size"

	echo "22. How many process is running?"

	echo "23. Can't run (process lock)"

	echo "24. where this command come from"

	echo "25. Do you want to type something i can give you an editor"

	echo "26. Exit"

	read -p "Enter your choice: " choice

	case $choice in

	    1)

		read -p "Enter the directory path: " directory

		ls -al "$directory"

		;;

	    2)

		read -p "Enter the directory path: " directory

		ls "$directory" > output/files.txt

		for file in $(cat output/files.txt); do

		  wc -l "$directory/$file" >> output/lines.txt

		done

		sort -n output/lines.txt > output/sorted.txt

		echo "Top 10 files with the most lines:"

		head -10 output/sorted.txt

		;;

	    3)

		read -p "Enter the file path: " file

		read -p "Enter the string to search: " search_string

		grep "$search_string" "$file"

		;;

	    4)

		top

		;;

	    5) 

		read -p "Enter the Command for info " Command

		man "$Command"

		;;

	    6)

	       pwd    

	       ;;

	    7)  

	       read -p "Enter the name of the Directory" dir

	       mkdir "$dir"

	       ;;

	    8)

	       read -p "Enter the folder name" fol

	       rmdir "$fol"

	       ;;

	    9)

	       read -p "Enter the source " source

	       read -p "Enter the Destination" dest 

	       mv "$source" "$dest"

	       echo "You moved a file"

	       ;;

	    10)

	       read -p "Enter the file" old_file

	       read -p "Enter the new file name" new_file

	       cp "$old_file" "$new_file"

	       echo "You file is copied now"

	       ;;

	    11) 

	       read -p "Enter the file name" file

	       touch "$file"

	       ;;  

	    12)

	       read -p "Enter the file name" file1

	       cat "$file1"

	       ;;

	    13)

	       read -p "Enter the file name" file2

	       head "$file2"

	       ;;

	    14)  

	       read -p "Enter the file name" file3

	       less "$file3"

	       ;;

	    15)

	      read -p "Enter the file name" file

	      cat "$file" | wc -l

	      ;;

	    16)

	      read -p "Enter the file name" file

	      cat "$file" | sort 

	      ;;

	    17)

	      read -p "Enter the file name" file

	      cat "$file" | uniq

	      ;; 

	    18)

	      read -p "Enter me the first file name " file1

	      read -p "Now enter me the second file name" file2

	      diff "$file1" "$file2"

	      ;;

	    19)

	      read -p "Say me something to repeat" word

	      echo "$word"

	      ;;   

	    20)

	      read -p "Enter me the file name" file

	      chmod +x "$file"

	      ;;

	    21)

	      du -sh

	      ;;

	    22)

	      ps -a

	      ;;

	    23)

	       read -p "Go to ps -sh and get the Process Id"

	       read -p "Enter the Process ID " id

	       kill -9 "$id"

	       ;;

	    24)

	       read -p "Enter the command" comm

	       which "$comm"

	       ;;

	    25)

	       echo "Enter me which editor you want" 

	       echo "1.nano"

	       echo "2.vim"

	       echo "3.gedit"

	       read ch

	       case $ch in

	       1) nano file.txt

	       ;;

	       2) vim file.txt

	       ;;

	       3) gedit file.txt

	       ;;

	      *) echo "invalid choice"

	      esac

	      ;;

	    26)

		echo "Exiting..."

		exit 0

		;;

	    *)

		echo "Invalid choice. Please try again."

		;;

	esac

	echo "Do you need some more else y or n"

	read i

	if [ $i != "y" ]

	then 

	exit 

	fi 

done 

echo "See you, Bye!!"
