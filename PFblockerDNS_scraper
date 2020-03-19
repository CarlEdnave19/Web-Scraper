'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
Author: Christian Carlo M. Ednave
Date Created: March 19, 2020
Purpose: This script is used for getting the DNS list from the shallalist block list
at github and create a local file that can be used by PFblockerng package on pfsense. 

Credits to Mr. Chris Buijs for the list, and Mr. Steven Black's pattern for DNS list pattern.
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
import urllib.request
import os



def get_data():
    link = "https://raw.githubusercontent.com/cbuijs/shallalist/master/downloads/domains"   # I change this manually, but I am planning to improve this sometime soon
    openlinks = urllib.request.urlopen(link).read().decode()                                # this line opens the link, reads its content and decodes it
    if not os.path.exists("Web_List"):                                                      # checks if the folder exist
        os.makedirs("Web_List")                                                             # if not, make a folder for it

    text_file = open("Web_List/Web1.txt","w+")                                              # create or open an existing text file
    print("gathering")
    for i in openlinks.split("\n"):
        try:
            if i == "":                                                                     # the purpose of this line is to check wether it hit the last line, so that it will not create a blank line
                break
            else:
                text_file.write("0.0.0.0 {}\n".format(i))                                   # I used Mr. Steven's pattern for making the local list
        except(UnicodeDecodeError):                                                         # sometimes I get this weird error
            print("Error occured. Exception is handled!")
    print("done")
    text_file.close()

get_data()

