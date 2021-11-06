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

In this class we create a button and a check box in a vertical layout and label ,line edit in a horizontal layout as follows:



