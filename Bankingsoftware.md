// A c program for banking 


#include<stdio.h>
#include<string.h>
#include<stdlib.h>

struct user {

char acholdername[40];
char phone[50];
char ac[50];
char password[50];
float balance;
}; /*creating structure*/

int main(){
struct user user,usr;
char filename[50],phone[50],password[50],acholdername[40];
FILE *fp,*fptr;
int opt,choice;
int amount,interest;
char cont = 'y';
printf("\t \t @Good wishes");
printf("\t *Welcome To Smart NC banking app*");
printf("\n___________________________________________________________________________________________");
printf("\n Enter what u want to do within here now");
printf("\n\n\t[1].Register your account");
printf("\n\t[2].Login to your account");

printf("\n\nPlease enter your choice:\t");
scanf("%d",&opt);
if(opt == 1)
{
printf("\n ******* ^-^ *******\t");
printf("\nEnter account holder Name:\t");
scanf("%s",user.acholdername);
printf("\nEnter minimum 5 digit account number:\t");
scanf("%s",user.ac);
printf("\n Enter your phone number:\t");
scanf("%s",user.phone);
printf("\nEnter your new password:\t");
scanf("%s",user.password);
user.balance=0;
stpcpy(filename,user.acholdername);
fp=fopen(strcat(filename,".txt"),"w");
fwrite(&user,sizeof(user),1,fp);
if(fwrite != 0)
{
 printf("Your account has been Succesfully registered");
}
}
else if(opt == 2)
{

printf("\nEnter your registered Phone No.:\t");
scanf("%s",phone);
printf("\nEnter your registered acholdername:\t");
scanf("%s",acholdername);
printf("\nEnter your registered Password:\t");
scanf("%s",password);
fp = fopen(strcat(acholdername,".txt"),"r");
if(fp == NULL)
{
printf("Account number not registered");
}
else {
fread(&user,sizeof(struct user),1,fp);
fclose(fp);
if(!strcmp(password,user.password))
{
while(cont == 'y')
{
printf("\n\tWelcome %s",user.acholdername);
printf("\n___________________________________________________________________________");
printf("\nPress 1 for balance inquiry");
printf("\nPress 2 for adding fund");
printf("\nPress 3 for cash withdraw");
printf("\nPress 4 for online transfer");
printf("\nPress 5 for calculation of Interest"); /* but yo garna aayena */
printf("\nPress 6 for ATM card form ");
printf("\nPress 7 for changing password\n\n");

printf("Enter your choice:\t");
scanf("%d",&choice);
switch(choice)
{
case 1:
printf("Your current balance is Rs. %.lf",user.balance);
break;

case 2:
printf("Enter amount to be added:\t");
scanf("%d",&amount);
user.balance += amount;
fp = fopen(phone,"w");
fwrite(&user,sizeof(struct user),1,fp);
if(fwrite !=0) printf("\n\nYou have depostied Rs.%d",amount);
fclose(fp);
break;

case 3:
printf("Enter withdrawl amount:\t");
scanf("%d",&amount);
if(amount % 10 != 0) {
printf("\nSorry amount should be multiple of 10");
}
else if(amount>user.balance) 
{printf("\nSorry insufficeint balance");}
else {
user.balance -= amount;
fp = fopen(phone,"w");
fwrite(&user,sizeof(struct user),1,fp);
if(fwrite !=0)
printf("\n\nYou have withdrawn Rs.%d",amount);
fclose(fp);
}
break;

case 4:
printf("Please enter the acount holder name to trasnfer balance:\t");
scanf("%s",acholdername);
printf("Enter the amount to transfer:\t");
scanf("%d",&amount);
if(amount > user.balance) 
printf("\nSorry insufficent balance");
else {
fptr = fopen(strcat(acholdername,".txt"),"r");
if(fptr==NULL) 
printf("Sorry number is not registered");
else {
fread(&usr,sizeof(struct user),1,fptr);
fclose(fptr);

usr.balance += amount;

fptr = fopen(phone,"w");
fwrite(&usr,sizeof(struct user),1,fptr);
if(fwrite != 0){
printf("ACcount:%s",usr.ac);
// printf("\npassword%s",usr.password);
printf("\nphone:%s",usr.phone);
printf("\nbalance:%f",usr.balance);
printf("\nYour trasfer is completed. You have trasnfered Rs.%d to %s",amount,usr.phone);
fclose(fptr);
user.balance -= amount;
strcpy(filename,user.acholdername);
fp = fopen(strcat(filename,".txt"),"w");
fwrite(&user,sizeof(struct user),1,fp);
fclose(fp);
}
}
}
break;
    case 5:
    printf("\nEnter your balance");
    scanf("%d",&amount);
    interest=(amount*6)/100;
    printf("The interest is Rs:%d",interest);
    break;
    case 6:
    printf("click the link to fill up the form for ATM\t");
    printf("https://docs.google.com/forms/d/e/1FAIpQLSf0myUyvEKF7FkkvGZPPTejopeLNmooKL-s2YPZTT4aPllmvQ/viewform?usp=sf_link");
    break;
case 7:
printf("\n\nPlease enter your old password:\t");
scanf("%s",password);
if(!strcmp(password,user.password)){
printf("\n\nPlease enter your new password:\t");
scanf("%s",password);
strcpy(user.password,password);
strcpy(filename,user.acholdername);
fp = fopen(strcat(filename,".txt"),"w");
fwrite(&user,sizeof(struct user),1,fp);
fclose(fp); 
printf("\nPassword succesfullly changed");
}
else printf("\nSorry your password is wrong");

default:
break;
}//switch ends here
printf("\n\nDo you want to continue?[y/n]:\t");
scanf("%s",&cont);
}
}
else {
printf("You Entered Invalid password");
} 
}
printf("\n\n***Thank you for banking with NC.bank\t Have a great day!***\n");

printf("____________________________________________________________________________________");
}

return 0;
} 
