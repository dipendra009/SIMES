# include<iostream.h>
# include<conio.h>
#include<process.h>
# include<stdio.h>
#include<iomanip.h>
# include<fstream.h>
# include<string.h>

ostream & fr(ostream &out )
{
	resetiosflags(ios::left);
	out<<setw(15);
	return out;
}
ostream & nt(ostream &out )
{
	out<<endl<<endl<<"  \t\t";
	return out;
}
ostream & fl(ostream &out)
{
      out<<setw(25);
      out<<setiosflags(ios::left);
      return out;
}
void clear()
{
	clrscr();
	cout<<nt<<"STUDENT'S  INTERNAL MARKS EVALUATION SYSTEM";
	cout<<nt<<"-------------------------------------------";
}
class exam
{
      protected:
		int fullmark;
		int weightage;
		int num;
       public:
		exam()
		{
			fullmark = 0;
			weightage = 0;
			num = 0;
		}
		virtual ~exam()
		{}


};

 class marks : public virtual exam
 {
       public:
		 float *score;
		 float *number;
       public:
		void getmarks(int roll ,int weight, int tot);

		float returnmark(int j) const
		{
		     return number[j];
		}
		void displayscore() const;

		virtual ~marks()
		{
			delete number;
			delete score;
		}


};
void marks ::getmarks(int roll ,int weight, int tot)
		{
		     num=roll;
		     fullmark = tot;
		     weightage=weight;
		     score = new float [roll];
		     number = new float [roll];
		     clear();
		     cout<<nt<<"Enter score rollnumber wise:"<<nt;
		     for(int i=0;i<roll;i++)
		     {
			     cout<<nt<<"Roll No. "<<i+1<<":"<<nt;
			     cin>>score[i];
			     if(score[i]<=fullmark)
			     number[i] = score[i]*weightage/fullmark;
			     else
			     {
				cout<<nt<<"Score cannot exceed fullscore.Please reenter your score:"<<nt;
				i--;
			     }
		     }
		}
void marks :: displayscore() const
		{
		     clear();


		     cout<<nt<<fl<<"Roll Number"<<fr<<"Score"<<fr<<"Marks";
		     cout<<nt<<fl<<"___________"<<fr<<"_____"<<fr<<"_____"<<nt<<nt;
		     int n;
		     for(int i=0;i<num;i++)
		     {
			cout<<nt<<fl<<i+1<<fr<<score[i]<<fr<<number[i];
			if((i+1)%10==0)
			{
			       cout<<nt<<"Press any number to continue:\t"<<nt;
			       cin>>n;
			       clear();

			       cout<<nt<<fl<<"Roll Number"<<fr<<"Score"<<fr<<"Marks";
			       cout<<nt<<fl<<"___________"<<fr<<"_____"<<fr<<"_____"<<nt;

			}
		     }
				cout<<nt<<"Fullscore is:\t"<<fullmark;
				cout<<nt<<"Fullmark is:\t"<<weightage<<nt<<nt;

}
class assessment  : public virtual exam
{
      protected:
		marks *assess;
		float *assmark;
		int  *fullscore;
		int *weightag;
		int ass_num;


       public:
	      void getassess(int roll);
	      int retweightage()
	      {
	      return weightage;
	      }
	      float retassmark(int j)
	      {
		  return assmark[j];
	      }
	      void assessscore(int as_num) const
	      {
		   cout<<"\t\t\tAssessment No.  "<<as_num<<":"<<nt;
		   assess[as_num-1].displayscore();

	      }


};
void assessment :: getassess(int roll)
	      {
			 num = roll;

			 cout<<nt<<"Enter number of assessments:"<<nt;
			 cin>>ass_num;
			 assmark = new float [num];
			 for(int i=0;i<num;i++)
			 assmark[i]=0;
			 weightage=0;
			 fullscore = new int [ass_num];
			 weightag = new int  [ass_num];
			 assess = new marks [ass_num];
			 for(int k=0;k<ass_num;k++)
			 {
				 cout<<nt<<"Assessment No. "<<k+1<<":"<<nt;
				 cout<<nt<<"Enter full score of assessment No. "<<k+1<<":"<<nt;
				 cin>>fullscore[k];
				 cout<<nt<<"Enter weightage:"<<nt;
				 cin>>weightag[k];
				 weightage+=weightag[k];
				 assess[k].getmarks(num,weightag[k],fullscore[k]);
				 for(int j=0;j<roll;j++)
				 assmark[j]+=assess[k].number[j];
			 }

	      }
 class assignment : virtual public marks
{      protected:

		 float *asgmark;
       public:
	      void getassign(int roll);
	      float retasgmark(int j)
	      {
		  return asgmark[j];
	      }
	      int retweightage()
	      {
	      return weightage;
	      }
	      void assignscore()
	      {
		   cout<<"\t\t\tAssignment Score is:"<<nt;
		   this->displayscore();
	      }
};
void assignment :: getassign(int roll)
	      {
		   num = roll;
		   cout<<nt<<"Enter total number of assignments:"<<nt;
		   cin>>fullmark;
		   cout<<nt<<"Enter weightage in final mark:"<<nt;
		   cin>>weightage;
		   this->getmarks(roll,weightage,fullmark);
		   asgmark = new float [num];
		   for(int i=0;i<num;i++)
		   asgmark[i]=number[i];
	      }
class attendance : public virtual marks
{      protected:

		 float *attmark;
       public:
	      void getattend(int roll);
	      float retattmark(int j)
	      {
		  return attmark[j];
	      }
	      int retweightage()
	      {
	      return weightage;
	      }
	      void attendscore()
	      {
		   cout<<"\t\t\tAttendance is:"<<nt;
		   this->displayscore();
	      }
};
void attendance :: getattend(int roll)
	      {
		   num = roll;
		   cout<<nt<<"Enter total number of attendance:"<<nt;
		   cin>>fullmark;
		   cout<<nt<<"Enter weightage in final mark:"<<nt;
		   cin>>weightage;
		   this->getmarks(roll,weightage,fullmark);
		   attmark = new float [num];
		   for(int i=0;i<num;i++)
		   attmark[i]= number[i];
	      }
 class  student : public assessment, public assignment , public attendance
{
     protected:
	      char *name;
	      int roll;


    public:

	   student()
	   {
		    strcpy(name,"  ");
		    roll=0;


	   }
	   void getdata(int n)
	   {
			cout<<nt<<"Enter name of roll no "<<n<<":"<<nt;
			cin>>name;
			roll = n;




	   }
	   void display()
	   {
		cout<<fl<<name<<fr<<roll;
	   }
};
class subject :  public marks
 {
      protected :
		assessment assess;
		assignment assign;
		attendance attend;

		float *marks;
		int num;
		char *sub;
		student *std;



       public:
	      subject (char *n)
	      {
			   strcpy(sub,n);
			   num = 0;
	      }
	      void secassessscore(int as_num)
	      {
		   assess.assessscore(as_num);
	      }
	      void secattendscore()
	      {
		   attend.attendscore();
	      }
	      void secassignscore()
	      {
		   assign.assignscore();
	      }

	      void getdata();
	      void result();

};
void subject :: getdata()
	      {


		   cout<<nt<<"Enter total number of students:"<<nt;
		   cin>>num;
		   marks = new float [num];
		   std = new student [num];
		   for(int i=0;i<num;i++)
		   marks[i]=0;
		   for(i=0;i<num;i++)
		   {
			   std[i].getdata(i+1);
		   }
		   clear();
		   assess.getassess(num);
		   clear();
		   assign.getassign(num);
		   clear();
		   attend.getattend(num);

		   for(i=0;i<num;i++)
		   {
			   marks[i] = (assess.retassmark(i)+assign.retasgmark(i)+attend.retattmark(i));
		   }
		   fullmark = assign.retweightage()+attend.retweightage()+assess.retweightage();
		   }
void subject :: result()
	      {
		   int n;
		   clear();
		   cout<<nt<<resetiosflags(ios::left)<<setfill('*')<<fr<<setw(34)<<"Final Result"<<setw(22)<<"*"<<setfill(' ')<<nt;
		   cout<<nt<<fl<<"Name"<<fr<<"Roll No."<<fr<<"Marks";
		   cout<<nt<<fl<<"____"<<fr<<"________"<<"_____"<<nt;
		   for(int i=0;i<num;i++)
		   {
		   std[i].display();
		   cout<<fr<<marks[i]<<nt;
		   if((i+1)%10==0)
			{
			       cout<<nt<<"Press any number to continue:\t"<<nt;
			       cin>>n;
			       clear();
			       cout<<nt<<resetiosflags(ios::left)<<setfill('*')<<fr<<setw(34)<<"Final Result"<<setw(22)<<"*"<<setfill(' ')<<nt;
			       cout<<nt<<fl<<"Name"<<fr<<"Roll No."<<fr<<"Marks";
			       cout<<nt<<fl<<"____"<<fr<<"________\t"<<fr<<"_____"<<nt;
			}
		   }
		   cout<<nt<<nt<<"Total Internal mark is:\t"<<fullmark<<nt;
       }


int main()
{
    clear();

    cout<<setprecision(2);
    int choice;
    do
    {
    cout<<nt<<"1:"<<fl<<"To calculate internal marks."<<nt;
    cout<<nt<<"2:"<<fl<<"To display previos result."<<nt;
    cout<<nt<<"3:"<<fl<<"Exit."<<nt;
    cout<<nt<<"Enter your choice:"<<nt;

    cin>>choice;
    clear();
    switch(choice)
    {
		  case 1:
		       {
			      cout<<nt<<"Enter name of subject:"<<nt;
			      char *name;
			      cin>>name;
			      subject sect(name);

			      fstream file;
			      cout<<nt<<"Enter name for the file"<<nt;
			      char *f;
			      cin>>f;
			      file.open(f,ios::out|ios::trunc|ios::binary);

			      if(!file.good())
			      {
				cout<<nt<<"Error in opening file"<<nt
				<<"Sorry, data can not be recorded."<<nt;
				//exit(0);
			      }
			      sect.getdata();
			      file.seekp(0,ios::beg);
			      file.write((char*)(&sect),sizeof(sect));
			      file.close();
			      clear();

			      do
			      {
			      cout<<nt<<"What do you want to know?"<<nt;
			      cout<<nt<<"1: Result of an assessment."<<nt;
			      cout<<nt<<"2: Result of assignments."<<nt;
			      cout<<nt<<"3: Result of attendance."<<nt;
			      cout<<nt<<"4: Final Result."<<nt;
			      cout<<nt<<"5: Exit."<<nt;
			      cout<<nt<<"Enter your choice :  ";
			      int choice1;
			      cin>>choice1;
			      clear();

			      switch(choice1)
			      {
					     case 1:
						  {
						       cout<<nt<<"Enter assessment no.:"<<nt;
						       int num;
						       cin>>num;
						       clear();

						       sect.secassessscore(num);
						       break;
						  }
					     case 2:
						  {
						       clear();

						       sect.secassignscore();
						       break;
						  }
					     case 3:
						  {
						       clear();

						       sect.secattendscore();
						       break;
						  }
					     case 4:
						  {
						       clear();

						       sect.result();
						       break;
						  }
			      default:
						  {
							  cout<<"Wrong choice"<<nt;
							  exit(0);
						  }
			      }
			      }
			      while(choice);
		       break;

		       }
		  case 2:
		       {
			      cout<<nt<<"Enter name of the subject:"<<nt;
			      char *name;
			      cin>>name;
			      subject sect(name);
			      fstream file;
			      cout<<nt<<"Enter name for the file"<<nt;
			      char *f;
			      cin>>f;
			      file.open(f,ios::out|ios::nocreate|ios::binary);
			      if(!file.good())
			      {
				  cout<<nt<<"Error in opening file";
				  cout<<nt<<"Sorry ,data can not be readen from given file.";
				  exit(0);
			      }
			      file.seekg(0,ios::beg);
			      file.read((char*)(&sect),sizeof(sect));
			      file.close();
			      cout<<nt<<"What do you want to know?"<<nt;
			      cout<<nt<<"1: Result of an assessment."<<nt;
			      cout<<nt<<"2: Result of assignments."<<nt;
			      cout<<nt<<"3: Result of attendance."<<nt;
			      cout<<nt<<"4: Final Result."<<nt;
			      cout<<nt<<"Enter your choice :  ";
			      int choice1;
			      cin>>choice1;
			      clear();

			      switch(choice1)
			      {
					     case 1:
						  {
						       cout<<nt<<"Enter assessment no.:"<<nt;
						       int num;
						       cin>>num;
						       clear();

						       sect.secassessscore(num);
						       break;
						  }
					     case 2:
						  {
						       clear();

						       sect.secassignscore();
						       break;
						  }
					     case 3:
						  {
						       clear();
						       sect.secattendscore();
						       break;
						  }
					     case 4:
						  {
						   clear();
						   sect.result();
						       break;
						  }
			      default:
						  {
							  cout<<"Wrong choice"<<nt;
							  exit(0);
						  }
			      }
		       break;
		       }
		    case 3:
			 {

			      exit (0);
			      break;
			 }
		  default:
			  {
			      cout<<"Wrong choice";
			      break;
			  }
    }
   }

    while(choice);
    getch();
    return 0;
}



