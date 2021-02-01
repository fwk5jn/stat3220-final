# stat3220-final
SAS project uses two factor factorial analysis to examine relationship between violent lyrics and student agression
 
      '''
      
      data lyrics;
      infile 'C:\Users\firem\Desktop\University of Virginia\STAT 3220\final project\lyrics.txt'
      dlm='09'X firstobs=2;
      input subject song $ pool $ score;
      run;

      proc print data=lyrics;
      run;

      proc sgplot data=lyrics;
      title 'Song vs. Score';
      scatter x=song y=score/group=pool;
      run;
      proc sgplot data=lyrics;
      title 'Pool vs. Score';
      scatter x=pool y=score/group=song;
      run;
      proc sgplot data=lyrics;
      vbox score/ category=pool;
      run;
      proc ANOVA data=lyrics;
      class pool;
      model score=pool;
      means pool/ hovtest=levene(type =pool);
      run;

      proc anova data=lyrics;
      class pool;
      model score=pool;
      means pool/ hovtest=bartlett;
      run;

      
      '''
