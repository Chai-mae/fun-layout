**<h1 style="color:blue;">Fun with layouts</h1>**


![fun-with-grid-3-wp](https://user-images.githubusercontent.com/93831197/140622923-d26010ba-6c96-4cf7-8c00-d6800f309a56.jpg)


**Introduction**

Qt includes a set of layout management classes that are used to describe how widgets are laid out in an application's user interface. These layouts automatically position and resize widgets when the amount of space available for them changes, ensuring that they are consistently arranged and that the user interface as a whole remains usable.

There is lot of layouts but in our tp we will focus just on :

                               QHBoxLayout:Lines up widgets horizontally
                               QVBoxLayout:Lines up widgets vertically
                               QFormLayout :Manages forms of input widgets and their associated labels
                               QGridLayout:Lays out widgets in a grid
                               
                               
In the **Exo1FunWithLayout.zip** project we have 4 classes.


1)**Experimenting with QHBOXLayout**:

First class is named Dialog1

In this class we  create a label , a Text Edit and a Push button and then we display the in a horizantal layout as follows:

![Screenshot_57](https://user-images.githubusercontent.com/93831197/140621409-18ccddf4-37cb-4fa1-8c3c-c8da32df86da.png)

Here is the code:

                                           Dialog1::Dialog1(QWidget *parent) : QWidget(parent)
                                           
                                           {
                                           
                                           createWidget();
                                           
                                           placeWidget();


                                           }
                                           
                                           void Dialog1::createWidget(){


                                           label = new QLabel("Name:");

                                           
                                           edit = new QLineEdit;
                                           
                                           button= new QPushButton("Search");
                                           
                                           this->setWindowTitle("HBoxLayout test");
                                           
                                           }
                                           
                                           void Dialog1::placeWidget(){
                                           
                                           QHBoxLayout* mainlayout = new QHBoxLayout;
                                           
                                           this->setLayout(mainlayout);
                                           
                                           mainlayout->addWidget(label);
                                           
                                           mainlayout->addWidget(edit);
                                           
                                           mainlayout->addWidget(button);
                                           
                                           }

2)**Nested Layouts**

The second class is named Dialog2

In this class we create a button,a check box in a vertical layout and label ,line edit in a horizontal layout as follows:

![Screenshot_58](https://user-images.githubusercontent.com/93831197/140621311-0bec74b5-d548-42c1-8739-ee9f475351ed.png)
 
We added also a function named makeconnecxion() to exit when we clicked on the button. 

Here is the code:
      
                                       void Dialog2::placeWidgets(){
                                       
                                          auto topleftlayout= new QHBoxLayout;
                                       
                                          auto leftlayout = new QVBoxLayout;
                                       
                                          auto rightlayout = new QVBoxLayout;
                                       
                                          auto mainlayout = new QHBoxLayout;
                                       
                                          this->setLayout(mainlayout);
                                       
                                          topleftlayout->addWidget(l1);
                                       
                                          topleftlayout->addWidget(edit);
                                       
                                          leftlayout->addLayout(topleftlayout);
                                       
                                          leftlayout->addWidget(c1);
                                       
                                          leftlayout->addWidget(c2);
                                       
                                          rightlayout->addWidget(b1);
                                       
                                          rightlayout->addWidget(b2);

                                     
                                          rightlayout->addSpacerItem(new QSpacerItem(10,10, QSizePolicy::Expanding));
                                       
                                          mainlayout->addLayout(leftlayout);
                                       
                                          mainlayout->addLayout(rightlayout);
                                       
                                       }
                                       
                                       void Dialog2::makeconnexion()
                                       
                                       {
                                       
                                          connect(b2, &QPushButton::clicked, this, exit);
                                       
                                       }
                                       
 2)**Bug report Form**  
 
 the third class is called dialog3.
 
 In this class we create a form to report a problem using the form layout as follows :
                                       
                                       
 ![Screenshot_59](https://user-images.githubusercontent.com/93831197/140622591-d532066b-eacb-424d-9a80-2771c94e0328.png)                                
                                       
                                       
                                       
                                       void dialog3::placeWidgets(){
                                       
                                         auto *formlayout =new QFormLayout;
                                         
                                         auto *mainlayout = new QVBoxLayout ;
                                         
                                         repro->addItem(tr("Always"));
                                         
                                         repro->addItem(tr("Sometimes"));
                                         
                                         repro->addItem(tr("Rarely"));
                                         
                                         formlayout->addRow("Name:", name);
                                         
                                         formlayout->addRow("Company:" , company);
                                         
                                         formlayout->addRow("Phone:", phone);
                                         
                                         formlayout->addRow("Email:", email);
                                         
                                         formlayout->addRow("Problem Title:", title);
                                         
                                         formlayout->addRow("Summary Information:", info);
                                         
                                         formlayout->addRow("Reproducibility:", repro);
                                         
                                         buttonbox->addButton(tr("Submit Bug Report"),QDialogButtonBox::AcceptRole);
                                         
                                         buttonbox->addButton(tr("Don't Submit"), QDialogButtonBox::RejectRole);
                                         
                                         buttonbox->addButton(QDialogButtonBox::Reset);


                                         mainlayout->addLayout(formlayout);
                                         
                                         mainlayout->addWidget(buttonbox);
                                         
                                         setLayout(mainlayout);


                                         setWindowTitle("Report Bug");




}

**Grid Layout**

The 4th class  is named dialog4.

In this class we construct a numeric keybord using the grid layout as follows :



![Screenshot_56](https://user-images.githubusercontent.com/93831197/140622819-01bba217-0a4b-4185-8aff-d516b9f776c4.png)




                                         
                                         void dialog4::createWidgets(){
                                         
                                         lcdnumber = new QLCDNumber;
                                         
                                         gridlayout= new QGridLayout;

                                         
                                         //creating the buttons
                                         
                                         for(int i=0; i < 10; i++)
                                         
                                         {
                                         
                                         
                                         numbers.push_back(new QPushButton(QString::number(i)));
                                         
                                         numbers.back()->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Fixed);
                                         
                                         numbers.back()->resize(sizeHint().width(), sizeHint().height());
                                         
                                         }
                                        //enter button
                                         
                                         enterbutton= new QPushButton("Enter",this);
                                         
                                         enterbutton->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Fixed);
                                         
                                         enterbutton->resize(sizeHint().width(), sizeHint().height());


                                         }
                                         
                                         void dialog4::placeWidgets(){
                                         
                                            //adding the lcd display
                                          
                                          gridlayout->addWidget(lcdnumber,0,0,1,3);
                                        
                                           //adding the numbers' buttons
                                          
                                          for(int i=1; i <10; i++)
                                          
                                          gridlayout->addWidget(numbers[i], (i+2)/3, (i+2)%3);
                                          
                                          //adding the button 0
                                          
                                          gridlayout->addWidget(numbers[0], 4, 0);
                                          
                                          //adding the enter button
                                          
                                          gridlayout->addWidget(enterbutton,4,1,1,2);


                                          setLayout(gridlayout);

                                          
                                          setWindowTitle("Numeric KeyPad");
                                          
                                          lcdnumber->setSegmentStyle(QLCDNumber::Filled);
                                          
                                          lcdnumber->setMinimumSize(150, 80);
                                          
                                          }

 



