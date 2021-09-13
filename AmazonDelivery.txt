/*START OF PROGRAM*/
    #include<stdio.h>
    #include<string.h>
    #include<stdlib.h>
    #include<time.h>
    //customer details structure start
    struct cust
    {
        int id;
	//nested structure for customer personal information
        struct custpers{
            char phone[12];
            char name[20];
            char usname[20];
            char pass[11];
        }custp;
	//inner structure end
    }cust[20];
    //customer structure details end
    //structure for delivery individuals
    struct dperson{
        char dname[20];
        char dphone[12];
    }dpers[10];
    //structure for delivery individuals
    //structure for items
    struct item{
        char iname[15];
        int iprice;
    }itemo[20];
    //structure for items end
    /*control variables start*/
    int pot;int ctr = 12;
    int ictr = 12;int actr = 10;
    int octr = 0;
    int tre = 0;
    int bt = -1;
    int globindex;
    /*control variables end*/
    //temporary storage structure start
    struct orders{
        char odname[20];
        float pri;
        char odphone[20];
	int oide;
	char cname[20];
    }ord[10];
    //temporary storage structure end
    //structure for storing order details start
    struct orderitems{char orname[15];int qtyy;float totalc;char dename[20];char deph[12];}red[10];
    //structure for storing order details end
    //initialisation method start
    void init()
    {
        cust[1].id = 10984;
        strcpy(cust[1].custp.phone,"9665456342");
        strcpy(cust[1].custp.name,"rajesh kumar");
        strcpy(cust[1].custp.usname,"rajesh_kumar");
        strcpy(cust[1].custp.pass,"raj123");
        cust[2].id = 20984;
        strcpy(cust[2].custp.phone,"9665456352");
        strcpy(cust[2].custp.name,"prathmesh_kaur");
        strcpy(cust[2].custp.usname,"prathmesh_kaur");
        strcpy(cust[2].custp.pass,"pra123");
        cust[3].id = 30984;
        strcpy(cust[3].custp.phone,"9640456343");
        strcpy(cust[3].custp.name,"abhishek_pranj");
        strcpy(cust[3].custp.usname,"abhishek_pranj");
        strcpy(cust[3].custp.pass,"abhi123");
	cust[4].id = 14986;
        strcpy(cust[4].custp.phone,"9934563640");
        strcpy(cust[4].custp.name,"karamjeet sheik");
        strcpy(cust[4].custp.usname,"karamjeet_sheik");
        strcpy(cust[4].custp.pass,"kar123");
        cust[5].id = 15745;
        strcpy(cust[5].custp.phone,"7386531245");
        strcpy(cust[5].custp.name,"siddarth desai");
        strcpy(cust[5].custp.usname,"siddarth_desai");
        strcpy(cust[5].custp.pass,"sid123");
        cust[6].id = 12343;
        strcpy(cust[6].custp.phone,"6555674654");
        strcpy(cust[6].custp.name,"abhinith bakshi");
        strcpy(cust[6].custp.usname,"abhinith_bakshi");
        strcpy(cust[6].custp.pass,"abh123");
        cust[7].id = 23123;
        strcpy(cust[7].custp.phone,"7666541234");
        strcpy(cust[7].custp.name,"prajin kapoor");
        strcpy(cust[7].custp.usname,"prajin_kapoor");
        strcpy(cust[7].custp.pass,"praj123");
        cust[8].id = 24569;
        strcpy(cust[8].custp.phone,"8747432678");
        strcpy(cust[8].custp.name,"akash vora");
        strcpy(cust[8].custp.usname,"akash_vora");
        strcpy(cust[8].custp.pass,"aka123");
        cust[9].id = 19670;
        strcpy(cust[9].custp.phone,"6553465944");
        strcpy(cust[9].custp.name,"aditya monu");
        strcpy(cust[9].custp.usname,"aditya_monu");
        strcpy(cust[9].custp.pass,"adi123");
        strcpy(dpers[1].dname,"rakesh junap");
        strcpy(dpers[1].dphone,"944068439");
        strcpy(dpers[2].dname,"karthin kinfu");
        strcpy(dpers[2].dphone,"9883832156");
        strcpy(dpers[3].dname,"karanjit paddu");
        strcpy(dpers[3].dphone,"9776434210");
        strcpy(dpers[4].dname,"fadnacik fini");
	strcpy(dpers[4].dphone,"8223415612");
	strcpy(dpers[5].dname,"dockwitch bora");
	strcpy(dpers[5].dphone,"8666747354");
        strcpy(dpers[6].dname,"larymon darn");
	strcpy(dpers[6].dphone,"9776384519");
	strcpy(dpers[7].dname,"staney khaja");
	strcpy(dpers[7].dphone,"7445372398");
	strcpy(dpers[8].dname,"garlay jordan");
	strcpy(dpers[8].dphone,"7488893341");
        strcpy(dpers[9].dname,"vardon cardey");
	strcpy(dpers[9].dphone,"6888909785");
	strcpy(itemo[0].iname,"pencil");
        itemo[0].iprice = 8;
        strcpy(itemo[1].iname,"pen");
        itemo[1].iprice = 10;
        strcpy(itemo[2].iname,"ipad");
        itemo[2].iprice = 32956;
        strcpy(itemo[3].iname,"rpi");
        itemo[3].iprice = 2198;
        strcpy(itemo[4].iname,"iphone");
        itemo[4].iprice = 56748;
        strcpy(itemo[5].iname,"samsung");
        itemo[5].iprice = 28999;
	strcpy(itemo[6].iname,"earphones");
        itemo[6].iprice = 1100;
	strcpy(itemo[7].iname,"deodrant");
        itemo[7].iprice = 800;
	strcpy(itemo[8].iname,"oneplus");
        itemo[8].iprice = 39999;
	strcpy(itemo[9].iname,"comic");
        itemo[9].iprice = 340;
        strcpy(itemo[10].iname,"bose");
        itemo[10].iprice = 15000;
	strcpy(itemo[11].iname,"dell");
        itemo[11].iprice = 65757;
    }//initialisation method end
    /*function declations start*/
    void login();
    void trackorder();
    void addacc();
    void additem();
    void order();
    /*function declations end*/
    //main method start
    int main()
    {
        init();int lko = 1;int pyi;
        printf("***********WELCOME TO AMAZON DELIVERY**********\n\n\n");//welcome message
        printf("Do you wish to login?\t y/n\n");//login confirmation
        char yn;
        scanf(" %c",&yn);
        if(yn == 'y')
        {
            login();
        }
           if(pot == 4||yn!= 'y')
               printf("*****You are now using our service as a guest*****\n\n");
            do
            {
		/*MENU*/
                printf("\tENTER YOUR SERVICE\n");
                printf("\t1.PLACE AN ORDER\n");
                printf("\t2.ADD AN ITEM TO THE LIST\n");
                printf("\t3.TRACK AN ORDER\n");
                printf("\t4.EXIT\n");
		//menu end
                scanf("%d",&pyi);
                switch(pyi)
                {
                    case 1:
                    order();
                    break;
                    case 2:
                    additem();
                    break;
                    case 3:
                    trackorder();
                    break;
                    case 4:
                    printf("\tdo you really want to exit? \ty/n\n");
                    char con;
                    scanf(" %c",&con);
                    if(con=='y')
                    {
                        printf("THANK YOU\n");
                        lko = 0;
                    }
                    else
                    {
                        lko = 1;
                    }
                    break;
                    default:
                    printf("no such operation\n");
                    break;
                      
                    
                }
                 
            }while(lko>0);
        
	
    }//end of main block
    //login method starts
    void login()
    {
        char getn[20],getp[15];
        printf("enter your username\n");//getusername
        scanf(" %s",getn);
        int i,index=100;
	for(i = 1;i<20;i++)
	{
            if(strcmp(getn,cust[i].custp.usname)==0)
            {
                index = i;globindex = i;
		break;
            }
	}
        if(index == 100)
        {
		char na;char fg;
            printf("no such account found\n");
	    printf("would you like to try again?y/n\n");
	    scanf("%c\n",&fg);
	    if(fg =='y')
		    login();
	    else
	    {
            printf("DO YOU WANT TO CREATE A NEW ACCOUNT?y/n\n");//add new account
            scanf("%c\n",&na);
            if(na == 'y')
            {
                addacc();
                //return;
            }
	    else
		    return;
	    }
        }
        else
        {
	         printf("ENTER YOUR PASSWORD\n");//get password
                 scanf("%s",getp);
                 if((strcmp(getp,cust[index].custp.pass))==0)
                 {
                     printf("****LOGIN SUCCESSFUL*****\n");
                     return;
                 }
                 else
                 {
                     printf("wrong password\n");char dc;
                     printf("do you wish to try again?\ty/n\n");
                     scanf(" %c",&dc);
                     if(dc=='y')
                        login();
                     else
                     {
                        pot = 4;
                         
                     }
                
                 }
        }return;
    }//end of login method
    //add account method starts
    void addacc()
    {
        printf("enter your id no\n");
        scanf("%d",&cust[(actr)].id);
        printf("enter your name\n");
        scanf("%s",cust[(actr)].custp.name);
        printf("enter your phone number\n");
        scanf("%s",&cust[(actr)].custp.phone);
        printf("enter your username\n");
        scanf("%s",cust[actr].custp.usname);
        printf("enter your password\n");
        scanf("%s",cust[actr].custp.pass);
        printf("congratulations your account has been created successfully!!\n\n");
        actr++;
	printf("provide login details\n");
	login();
    }//add account method ends
    //order method start
    void order()
    {
	printf("enter you user name:\n");char na[20];bt++;
	scanf("%s",na);strcpy(ord[bt].cname,na);
	tre = 0;
        srand(time(0));int t;
        printf("you chose to order\n");tre = 0;
	for(t = 0;t<9;t++)
	{
        printf("enter the name of the item you want to order\n");char getna[15];tre++;
        //char getna[15];
        scanf("%s",getna);
        int index=100;int i;
        for(i = 0;i<20;i++)
        {
            if(strcmp(getna,itemo[i].iname)==0)
            {
                index = i;
                break;
            }
	}
        if(index != 100)
        {
		/*billing algorithm*/
		strcpy(red[tre].orname,getna);
		printf("the price of each item : %d\n",itemo[index].iprice);
		printf("enter the quantity for item : %s\n",getna);
		int qty;
		scanf("%d",&qty);
           	int totprice = ((itemo[index].iprice)*qty);
                int disc = (rand() %(25 - 5 + 1)) + 5;
           	float totali = totprice- totprice*(disc/100);
           	float taxo = (rand() %(14 - 5 + 1)) + 5;
               	float total = totali + ((totali*(taxo/100)));
        	int ind = (rand() %(9 - 1 + 1)) + 1;
	  	int gh = (rand() % (35000 - 11000 + 1))+11000;
	  	red[tre].totalc = total + 35.6;red[tre].qtyy = qty;
	 	strcpy(red[tre].dename,dpers[ind].dname);
	 	strcpy(red[tre].deph,dpers[ind].dphone);

           
		printf("do you want to order more items?\t y/n\n");char ci;
		scanf(" %c",&ci);
		if(ci=='y')
		{
			continue;
		}
		else
		{
			/*printing of the bill*/
			printf("\t\tORDER ID : %d\t\n ",gh);
			ord[bt].oide = gh;
			printf("\t\tCUSTOMER NAME : %s\t\n ",ord[bt].cname);
			printf("\t\tNAME    \t\t| QUANTITY\t\t |PRICE\t\t\t\n");
			float grand = 0.0;
			strcpy(ord[bt].odname,red[tre].dename);
			strcpy(ord[bt].odphone,red[tre].deph);int po;
			for(po = 0;po<=tre;po++)
			{
			printf("\t\t %s\t\t\t\ | %d\t\t\t | %f\t\t\n",red[po].orname,red[po].qtyy,red[po].totalc);
			grand = grand + red[po].totalc;
			}
			printf("\n\n\t\tGRAND TOTAL : %f\n",grand);
			printf("\t\tDELIVERY PERSON : %s\n",dpers[ind].dname);
			printf("\t\tCONTACT : %s\n   ",dpers[ind].dphone);
			printf("\t\tEXPECTED TIME OF DELIVERY :%d DAYS\n ",ind);
			ord[bt].pri = grand;
			break;
			/*bill print algorithm ended*/
		}
	}
        else
        {
            printf("no such item found \n");
            printf("do you want to add an item?y/n\n");
            char cx;
            scanf(" %c",&cx);
            if(cx== 'y')
            {
                additem();tre--;continue;
		
            }
           
        }
	}
	
    }
    //start method add item
    void additem()
    {
        printf("enter the name of the item \n");
        scanf("%s",itemo[ictr].iname);
        printf("enter the price for each item\n");
        scanf("%d",&itemo[ictr].iprice);
	printf("item added successfully!!\n");
        ictr++;
    }
    //add item method end
    //trackorder method start
    void trackorder()
    {
        printf("enter the order number\n");
        int fv;
        scanf("%d",&fv);
        int i;int inde = 100;
        for(i = 0;i<10;i++)
        {
            if(ord[i].oide == fv)
            {
                inde = i;
                break;
            }
        }
        if(inde == 100)
        {
            printf("no such order found\n");
            printf("do you wish to try again?\ty/n\n");
            char ex;
            scanf(" %c",&ex);
            if(ex == 'y')
                trackorder();
            else
                return;
        }
        else
        {
            printf("order found\n");
            printf("NAME : %s\n",ord[inde].cname);
            printf("PRICE : %f\n",ord[inde].pri);
            printf("DELIVERY PERSON : %s\n",ord[inde].odname);
	    printf("contact :%s\n",ord[inde].odphone);
            printf("thank you\n");
            return;
        }
    }
    //track order method end
/* END OF PROGRAM*/
