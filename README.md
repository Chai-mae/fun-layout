**Introduction**

Qt includes a set of layout management classes that are used to describe how widgets are laid out in an application's user interface. These layouts automatically position and resize widgets when the amount of space available for them changes, ensuring that they are consistently arranged and that the user interface as a whole remains usable.

There is lot of layouts but in our tp we will focus just on :

                               QHBoxLayout:Lines up widgets horizontally
                               QVBoxLayout:Lines up widgets vertically
                               QFormLayout :Manages forms of input widgets and their associated labels
                               QGridLayout:Lays out widgets in a grid
                               
                               
In the **Exo1FunWithLayout.zip** project we have 4 classes.


1)**Experimenting with QHBOXLayout**:

First class named Dialog1

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

The second class named Dialog2

In this class we create a button,a check box in a vertical layout and label ,line edit in a horizontal layout as follows:

![Screenshot_58](https://user-images.githubusercontent.com/93831197/140621311-0bec74b5-d548-42c1-8739-ee9f475351ed.png)
 
We added also a function named makeconnecxions() to exit when we clicked on the button. 

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
 



