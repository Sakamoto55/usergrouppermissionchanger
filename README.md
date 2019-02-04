# usergrouppermissionchanger.sh
This script will change the user, group, and permissions of the upload directory to: nobody, ecards, 775. 

#This for loop checks the /upload directory to see if username of all files = nobody. If not, they will be changed to nobody.

        for username in $(cd /upload && ls)

        do

               if [ $(stat -c "%U" /upload/$username) != nobody ]

               then

               chown nobody /upload/$username

               fi
        done

#This for loop checks the /upload directory to see if all group names = ecards. If not, they will be changed to ecards.

        for group in $(cd /upload && ls)

        do

                if [ $(stat -c "%G" /upload/$group) != ecards ]

                then

                chgrp ecards /upload/$group

                fi

        done

#This last for loop checks the /upload directory to see if there are any directories with permissions that are not 775. If there are, they will be changed to 775.


        for permissions in $(cd /upload && ls -d */)

        do

               if [ $(stat -c "%a" /upload/$permissions) != 775 ]

               then

               chmod 775 /upload/$permissions

               fi


        done
~                                                                                                                                                                          
~                                                                                                                                                                          
~                                                                                                                                                                          
~                                        
