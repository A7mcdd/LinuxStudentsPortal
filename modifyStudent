while true; do

echo
echo "==== Modify Student Menu ===="
echo
echo " 1) Delete a student"
echo " 2) Modify student info"
echo " 3) Return to Main Menu"
echo 
echo "============================="
echo

echo "Enter your choice:"
read mod_choice

case $mod_choice in
 1)
  echo
  echo "Enter Student ID to delete:"
  read id

  checkExit=$(grep "^$id:" students)
  if [ -z "$checkExit" ]; then
   echo
   echo "Error: Student ID does not exist!"
  else
   grep -v "^$id:" students > temp
   mv temp students
   echo 
   echo "Student deleted successfully!"
  fi
  ;;
 2)
  echo
  echo "Enter Student ID to modify:"
  read id
  
  checkExit=$(grep "^$id:" students)
  if [ -z "$checkExit" ]; then
   echo
   echo "Error: Student ID does not exist!"
  else
   old_name=$(grep "^$id:" students | cut -d: -f2)
   old_date=$(grep "^$id:" students | cut -d: -f3)
   old_email=$(grep "^$id:" students | cut -d: -f4)
   echo
   echo "What do you want to modify?"
   echo "1) Full Name"
   echo "2) Date of Birth"
   read edit_choice
   
   case $edit_choice in
    1)
     while true; do
      echo
      echo "Enter Full Name (First Last):"
      read new_name

      case $new_name in
       *[' ']*)break;;
       *)echo "Error: You must enter both First and Last name"
       continue;;
      esac
     done

     grep -v "^$id:" students > temp
     mv temp students
     echo "$id:$new_name:$old_date:$old_email" >> students
     echo

     # btw we could make the email change but thats doesn't make sense but if you want we can do this by
     # firstname=$(echo $new_name | cut -d' ' -f1 | tr 'A-Z' 'a-z' )
     # idpart=$(echo $id | cut -c3-4)
     # echo "$id:$new_name:$old_date:$old_email" >> students
     # email="${firstname}_${idpart}@birzeit.edu"
     
     echo "Name updated successfully!"
     ;;
    2)
     echo
     echo "Enter New Date of Birth (dd/mm/yyyy):"
     read new_date
     case $new_date in
      [0-3][0-9]/[0-1][0-9]/[0-9][0-9][0-9][0-9])
       grep -v "^$id:" students > temp
       mv temp students
       echo "$id:$old_name:$new_date:$old_email" >> students
       echo
       echo "Date of Birth updated successfully!";;
      *) echo; echo "Invalid date format! Modification failed.";;
     esac;;
    *)echo; echo "Invalid choice.";;
   esac
  fi;;
 3)
  echo "Reutrning to Main Menu..."
  break;;
 *)
 echo; echo "Invalid choice.";;
esac

done
