#include "User.h"
#include "Book.h"
#include "UserList.h"
#include "BookList.h"
void main_menu(){
   cout <<"Select one of the following choices : " <<endl;
   cout<<"1- Books Menu"<<endl;
   cout<<"2- Users Menu"<<endl;
   cout<<"3- Exit "<<endl;
}
void user_menu(){
              cout<<" USERS MENU"<<endl;
              cout<<"1- Create a USER and add it to the list "<<endl;
              cout<<"2- Search for a user " <<endl;
              cout<<"3- Display all users "<<endl;
              cout<<"4- Back to the main "<<endl;
}
void search_user_menu(){
            cout<<"SEARCH FOR A USER"<<endl;
            cout<<"1- Search by name"<<endl;
            cout<<"2- Search by id"<<endl;
            cout<<"3- Return to users Menu"<<endl;
}
void delete_user_menu(){
cout<<"1- Delete user "<<endl;
cout<<"2- Return to users Menu"<<endl;
}
void book_menu(){
cout<<"BOOKS MENU"<<endl;
cout<<"1- Create a book and add it to the list "<<endl;
cout<<"2- Search for a book"<<endl;
cout<<"3- Display all books (with book rating)"<<endl;
cout<<"4- Get the highest rating"<<endl;
cout<<"5- Get all books of a user "<<endl;
cout<<"6- Back to the main menu"<<endl;
}
void search_book_menu(){
            cout<<"SEARCH FOR A BOOK"<<endl;
            cout<<"1- Search by name"<<endl;
            cout<<"2- Search by id"<<endl;
            cout<<"3- Return to Books Menu"<<endl;
}
void search_book_name()
{
    cout<<"1- Update author"<<endl;
    cout<<"2- Update name"<<endl;
    cout<<"3- Update Category"<<endl;
    cout<<"4- Delete Book"<<endl;
    cout<<"5- rate book"<<endl;
    cout<<"6- Get back to books menu"<<endl;
}
int main()
{
    bool b1 = true, b2 = true, b3 = true,b4=true,b5=true ;
   bool b6 = true , b7 = true,b8 = true,b9 = true ;
   int choice1,choice2,choice3,choice4,choice5;
   int choice6,choice7,choice8,choice9 ;
   UserList *U ;
    BookList *B;
   while (b1){
        main_menu();
        cin >> choice1 ;
        switch (choice1){
        case 1:
        /////////////////////////////////////////////
        {
        int NumberOfBooks;
        cout<<"How many books will be added?"<<endl;
        cin >> NumberOfBooks;
         B= new BookList(NumberOfBooks);
        b6 = true ;
        while (b6){
            book_menu();
            cin >> choice6;
            switch(choice6){
          case 1 :
         {
            Book b1 ;
            cin >> b1 ;
            ///////////////////////////////////////
            b8 = true ;
            while (b8 ){
               cout<<"1- Assign Author"<<endl;
               cout<<"2- Continue"<<endl;
               cin >> choice8;
               switch (choice8){
              case 1 :
               //////////////////////////
               {
               cout<<"Enter author (user ) id : "<<endl;
               int id ;
               cin >> id;
               User *u4 ;
               u4 = U->searchUser(id );
               if (u4 == nullptr){
                 cout<<"No Author Found with id = " <<id <<endl;
               }
               else {
               b1.setAuthor(*u4 );
              B->addBook(b1);
               b8 = false;
               }
               }
               /////////////////////////
              break;
              case 2 :
               B->addBook(b1);////////////////////
               b8 = false;
               break;
              default :
               b8 = false;
               }
            }
            ///////////////////////////////////////
           }
             break;
          case 2 :
          {
              ///////////////////////////////////////////////////////////////////////
              b7 = true ;
              while (b7){
                 search_book_menu();
                 cin >> choice7;
                 switch (choice7){
                  case 1 :
                      {
                          string ss;
                          cout<<"Enter Name : "<<endl;
                          cin >> ss ;
                          Book *b2 ;
                          b2 = B->searchBook(ss);
                          if (b2 == nullptr){
                       cout<<"Name Not Found  " <<endl;
                       b9 = false;
                     }
                    else {
                        b9 = true ;
                        cout<<*b2 ;
                        ///////////////////////////////////////////////////////////////////
                        while (b9){
                        search_book_name();
                        cin >> choice9;
                        switch (choice9){
                        case 1 :
                            //--------------------
                          {
                             cout<<"Enter author (user ) id : "<<endl;
                              int id ;
                              cin >> id;
                              /////////////////////////////////////////
                              User *uu ;
                               uu = U->searchUser(id );
                              if (uu == nullptr){
                                cout<<"No Author Found with id = " <<id <<endl;
                             }
                              else {
                               Book *bb;
                              bb = B->searchBook(ss);
                               bb->setAuthor(*uu);
                               b2 = bb;
                              }
                              /////////////////////////////////////////
                            }
                            //-------------------
                           break;
                        case 2 :
                            //--------------------
                            {
                             cout<<"Enter new name: "<<endl;
                             string str;
                             cin>>str;
                             Book *b5;
                            b5 = B->searchBook(ss);
                             b5->setTitle(str);
                             b2 = b5 ;
                            }
                            //-------------------
                        break ;
                        case 3 :
                            //--------------------
                            {
                              cout<<"Enter new Category: "<<endl;
                              string str;
                              cin>>str;
                              Book *b4;
                             b4 = B->searchBook(ss);
                              b4->setCategory(str);
                              b2 = b4 ;
                            }
                            //-------------------
                        break ;
                        case 4 :
                            //--------------------
                            {
                              B->deleteBook(b2->getId());
                            }
                            //-------------------
                        break ;
                        case 5 :
                            //--------------------
                            {
                             cout<<"Enter Rating value: "<<endl;
                             double rate_value;
                             cin>> rate_value;
                              Book *b3;
                              b3 = B->searchBook(ss);
                              b3->rateBook(rate_value);
                              b2 = b3 ;
                            }
                            //-------------------
                        break ;
                      case 6 :
                         b9 = false ;
                         break;
                      default :
                          b9 = false ;
                        }
                        }
                        ///////////////////////////////////////////////////////////////////
                       }
                      }
                      break ;
                  case 2 :
                      {
                       int ID ;
                      cout<<"Enter ID : "<<endl;
                      cin >> ID ;
                      Book* b3 ;
                      b3 = B->searchBook(ID);
                    if (b3 == nullptr){
                       cout<<"ID Not Found  " <<endl;
                     }
                    else {
                        cout<<*b3 ;
                       }
                    }
                    break;
                    case 3 :
                      b7 = false ;
                      break;
                  default :
                      b7 = false ;
                 }
              }
              /////////////////////////////////////////////////////////////////////////
          }
          break ;
          case 3 :
           cout<< *B;
            break ;
          case 4 :
              {
                  Book b4;
                 b4 = B->getTheHighestRatedBook();
                  cout<<b4 ;
              }
             break;
          case 5 :
              {
              int ID;
              cout<<"Enter ID"<<endl;
              cin >> ID;
              User *u5 ;
              u5 = U->searchUser(ID);
              ///////////////////////////////////////////////////////////////
              if (u5 == nullptr){
                 cout<<"No Author Found with id = " <<ID <<endl;
               }
               else {
               B->getBooksForUser(*u5);
               }
              ////////////////////////////////////////////////////////////
             }
          break;
           case 6:
           b6 = false ;
           break;
          default :
          b6 = false;
            }
         }
        }
        /////////////////////////////////////////////
        break;
        case 2:
         //////////////////////////
         {
         int NumberOfUsers;
         cout<<"How many users will be added?"<<endl;
         cin >> NumberOfUsers;
         U = new UserList(NumberOfUsers);
         b2 = true ;
         while (b2){
            user_menu();
            cin >> choice2 ;
            switch(choice2){
            case 1:
            {
            User u1 ;
            cin >> u1 ;
            U->addUser(u1);
            }
            break ;
            case 2 :
                /////////////////////////
                b3 = true ;
                while(b3) {
                   search_user_menu();
                   cin >> choice3 ;
                   switch(choice3){
                  case 1 :
                      {
                        string s ;
                        cout<<"Enter Name : "<<endl;
                        cin >> s;
                        User *u2;
                        u2 = U->searchUser(s);
                        if (u2 == nullptr ){
                             cout<<"Name Not Found"<<endl;
                             b3 = false ;
                             b4 = false ;
                        }
                        else {
                        cout<<*u2<<endl;
                        }
                        /////////////////////
                        while (b4){
                          delete_user_menu();
                          cin >> choice4;
                          switch (choice4){
                           case 1 :
                                U->deleteUser(u2->getId());
                                b4 = false ;
                                break;
                           case 2 :
                            b4 = false ;
                            break;
                           default:
                           b4 = false ;
                          }
                        }
                        /////////////////////////
                      }
                        b4 = true ;
                        break ;
                  case 2 :
                      {
                       int id ;
                      cout<<"Enter ID : "<<endl;
                      cin >> id ;
                      User *u3 ;
                      u3 = U->searchUser(id);
                      if (u3 == nullptr){
                           cout<<"ID Not Found"<<endl;
                           b4 = false ;
                           b5 = false ;
                      }
                      else {
                      cout<<*u3 ;
                      }
                      /////////////////////////////////
                       while (b5){
                        delete_user_menu();
                        cin >> choice5;
                        switch (choice5){
                        case 1 :
                         U->deleteUser(u3->getId());
                          b5 = false ;
                         break;
                        case 2 :
                         b5 = false ;
                         break;
                        default:
                         b5 = false ;
                        }
                       }
                      /////////////////////////////////////
                      }
                      b5 = true  ;
                      break ;
                  case 3 :
                      b3 = false ;
                      break;
                  default :
                      b3 = false ;
                   }
                }
                /////////////////////////
            break ;
            case 3 :
            cout<<*U;
            break ;
            case 4 :
            b2 = false ;
            break ;
            default :
            b2 = false ;
            }
         }
         }
         ///////////////////////////
         break;
        case 3 :
        b1 = false ;
        break;
        default :
         b1 = false ;
        }
   }
   return 0 ;
}
