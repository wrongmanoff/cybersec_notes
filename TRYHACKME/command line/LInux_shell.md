# linux shell

MOst distributions use **bash(Bourne Again Shell)** as default shell but i use zsh 

## basic commands 

```shell
cd ..
ls 
grep THM direcitorny.txt
pwd 
whoami
```

## TYpes of linux shell

in windows we have cmd + powershell 
Linux has different types of shells are there . To see which shell ur using : 

```shell
echo $SHELL
```

THe diffrent types of shells are : bash, rbash, zsh, dash, tmux, screen 

## Bourne Again SHell

It is the default in most linux distributions. It has replaced shells like sh, ksh, and csh it came comibned all of their features. Features : 

- offers tab completion features,it will automatically complete command based on possible match or given you multiple suggestions 
- it keeps history files and logs all of your commands. you can use up and downa arrow keys to navigate through them. type ***history*** 

## Friendly Interactive Shell (FISH)

it's more focues on user frinedliness than other shells. features : 

- very simple syntax
- has auto spell correction 
- customized command prompt wiht cool themes
- it also provides scripting, tab completion, and ocmmand history
- syntax highilight is built in to the shell 

## Z Shell

zsh is not installed by default in linux distributions. it is a modern shell contains featueres : 

- tabl completion, scripiting
- just like fish , has auot spell correction 
- it has extensive cutomization th at mya mkae it slower than other shells

## Shell Scripiting

shell scripting is nothing but a set of commands. 

1. first we need to create a file using any text editor ending with .sh : 

   ```shell
   nano first_script.sh
   ```

1. Every script should start from shebang.  staring wiht !# follwed by the name of the interpreter to use while executing the script as we use bash here, here is hte shebang : 

   ```\
   #!/bin/bash
   ```

2. vairbales are used to store data. To print something we use echo. To take input form the user we use read 

   ```
   #!/bin/bash
   echo "Hey, what's you name?"
   read name #here name is the variable and input data is stsored in the name variable
   echo "Welcome, $name"
   ```

3. saving is done by ctrl + x and press y and then enter  or we can also do crtl + o then enter then crtl + x 

4. to make it executable we need to add execution permission 

   ```shell
   chmod +x first_script.sh
   ```

5. **looping** can also be done 

   ```
   #!/bin/bash
   for i in {1..10};
   do
   echo $i
   done
   ```

6. **conditional statements** the code only runs if the conditons are met 

   ```
   #!/bin/bash
   #!/bin/bash
   echo "Please enter your name first:"
   read name
   if [ "$name" = "Stewart" ]; then
           echo "Welcome Stewart! Here is the secret: THM_Script"
   else
           echo "Sorry! You are not authorized to access the secret."
   fi
   ```

   

