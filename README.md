# utl-create-a-datastep-array-of-variables-with-an-arbitrary-common-suffix
Create a datastep array of variables with an arbitrary common suffix 
    Create a datastep array of variables with an arbitrary common suffix                                                                
                                                                                                                                        
      Problem: Compute row sums for variables ending in '20'                                                                            
                                                                                                                                        
          JAN_20 FEB_20 MAR_20 APR_20 MAY_20 JUN_20 JUL_20 AUG_20 SEP_20 OCT_20_20 NOV DEC_20                                           
                                                                                                                                        
          I realize that you can use the SAS range JAN_20--DEC20 statement, however this solution                                       
          does not require that the variables be consecutive.                                                                           
                                                                                                                                        
    https://cutt.ly/HgDzXo5                                                                                                             
    https://github.com/rogerjdeangelis/utl-create-a-datastep-array-of-variables-with-an-arbitrary-common-suffix                         
                                                                                                                                        
    StackOverflow                                                                                                                       
    https://cutt.ly/IgDzpQU                                                                                                             
    https://stackoverflow.com/questions/64655449/how-to-use-sas-array-wildcards-to-create-an-array-of-variables-that-have-names-e       
                                                                                                                                        
    macros                                                                                                                              
    https://tinyurl.com/y9nfugth                                                                                                        
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                          
                                                                                                                                        
    *                                                                                                                                   
    #####  #   #  ####   #   #  #####                                                                                                   
      #    ##  #  #   #  #   #    #                                                                                                     
      #    # # #  #   #  #   #    #                                                                                                     
      #    #  ##  ####   #   #    #                                                                                                     
      #    #   #  #      #   #    #                                                                                                     
      #    #   #  #      #   #    #                                                                                                     
    #####  #   #  #       ###     #                                                                                                     
                                                                                                                                        
    #! INPUT ;                                                                                                                          
                                                                                                                                        
    data have;                                                                                                                          
      retain rec;                                                                                                                       
      array mths JAN20 FEB20 MAR20 APR20 MAY20 JUN20 JUL20 AUG20 SEP20 OCT20 NOV20 DEC20;                                               
      do rec=1 to 5;                                                                                                                    
         do over mths;                                                                                                                  
             mths=rec*10000;                                                                                                            
          end;                                                                                                                          
          output;                                                                                                                       
      end;                                                                                                                              
      stop;                                                                                                                             
    run;quit;                                                                                                                           
                                                                                                                                        
    WORK.HAVE total obs=5                                                         |  RULES (SUM VARIABLES ENDING ON '20'                
                                                                                  |                                                     
     REC JAN20 FEB20 MAR20 APR20 MAY20 JUN20 JUL20 AUG20 SEP20 OCT20 NOV20 DEC20  |   ROWSUM                                            
                                                                                  |                                                     
      1  10000 10000 10000 10000 10000 10000 10000 10000 10000 10000 10000 10000  |   120000                                            
      2  20000 20000 20000 20000 20000 20000 20000 20000 20000 20000 20000 20000  |   240000                                            
      3  30000 30000 30000 30000 30000 30000 30000 30000 30000 30000 30000 30000  |   360000                                            
      4  40000 40000 40000 40000 40000 40000 40000 40000 40000 40000 40000 40000  |   480000                                            
      5  50000 50000 50000 50000 50000 50000 50000 50000 50000 50000 50000 50000  |   600000                                            
                                                                                  |                                                     
    *                                                                                                                                   
     ###   #   #  #####  ####   #   #  #####                                                                                            
    #   #  #   #    #    #   #  #   #    #                                                                                              
    #   #  #   #    #    #   #  #   #    #                                                                                              
    #   #  #   #    #    ####   #   #    #                                                                                              
    #   #  #   #    #    #      #   #    #                                                                                              
    #   #  #   #    #    #      #   #    #                                                                                              
     ###    ###     #    #       ###     #                                                                                              
                                                                                                                                        
    #! OUTPUT                                                                                                                           
                                                                                                                                        
    WORK.WANT total obs=5                                                                                                               
                                                                                                                                        
     REC JAN20 FEB20 MAR20 APR20 MAY20 JUN20 JUL20 AUG20 SEP20 OCT20 NOV20 DEC20  ROWSUM                                                
                                                                                                                                        
      1  10000 10000 10000 10000 10000 10000 10000 10000 10000 10000 10000 10000  120000                                                
      2  20000 20000 20000 20000 20000 20000 20000 20000 20000 20000 20000 20000  240000                                                
      3  30000 30000 30000 30000 30000 30000 30000 30000 30000 30000 30000 30000  360000                                                
      4  40000 40000 40000 40000 40000 40000 40000 40000 40000 40000 40000 40000  480000                                                
      5  50000 50000 50000 50000 50000 50000 50000 50000 50000 50000 50000 50000  600000                                                
                                                                                                                                        
    *                                                                                                                                   
    ####   ####    ###    ###   #####   ###    ###                                                                                      
    #   #  #   #  #   #  #   #  #      #   #  #   #                                                                                     
    #   #  #   #  #   #  #      #       #      #                                                                                        
    ####   ####   #   #  #      ####     #      #                                                                                       
    #      # #    #   #  #      #         #      #                                                                                      
    #      #  #   #   #  #   #  #      #   #  #   #                                                                                     
    #      #   #   ###    ###   #####   ###    ###                                                                                      
                                                                                                                                        
    #! PROCESS ;                                                                                                                        
                                                                                                                                        
    data want;                                                                                                                          
      set have;                                                                                                                         
      array mths %varlist(have,prx=/20$/);                                                                                              
      rowsum= sum(of mths[*]);                                                                                                          
    run;quit;                                                                                                                           
                                                                                                                                        
                                                                                                                                        
