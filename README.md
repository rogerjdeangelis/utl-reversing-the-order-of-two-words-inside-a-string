# utl-reversing-the-order-of-two-words-inside-a-string
Reverse the order [any word] Doctor =>  Doctor [any word]     

    SAS Forum: Reversing the order of two words inside a string                                 
                                                                                                
    Reverse the order [any word] Doctor =>  Doctor [any word]                                   
                                                                                                
     Example:                                                                                   
          CUSTOMER DOB Who Doctor  should be CUSTOMER DOB Doctor Who                            
                                                                                                
    SAS Forum                                                                                   
    https://tinyurl.com/y4no7ob8                                                                
    https://communities.sas.com/t5/SAS-Programming/Swapping-the-WORD-in-String/m-p/592669       
                                                                                                
    github                                                                                      
    https://tinyurl.com/yxqmaphy                                                                
    https://github.com/rogerjdeangelis/utl-reversing-the-order-of-two-words-inside-a-string     
                                                                                                
    *_                   _                                                                      
    (_)_ __  _ __  _   _| |_                                                                    
    | | '_ \| '_ \| | | | __|                                                                   
    | | | | | |_) | |_| | |_                                                                    
    |_|_| |_| .__/ \__,_|\__|                                                                   
            |_|                                                                                 
    ;                                                                                           
                                                                                                
     cards4;                                                                                    
     CUSTOMER Who Doctor                                                                        
     CUSTOMER TV Who Doctor                                                                     
     CUSTOMER Dugi Doctor Houser                                                                
     CUSTOMER John Smith                                                                        
     CUSTOMER Doctor                                                                            
                                                                                                
    *            _               _                                                              
      ___  _   _| |_ _ __  _   _| |_                                                            
     / _ \| | | | __| '_ \| | | | __|                                                           
    | (_) | |_| | |_| |_) | |_| | |_                                                            
     \___/ \__,_|\__| .__/ \__,_|\__|                                                           
                    |_|                                                                         
    ;                                                                                           
                                                                                                
    CUSTOMER Doctor Who                                                                         
    CUSTOMER TV Doctor Who                                                                      
    CUSTOMER Doctor Dugi Houser                                                                 
    CUSTOMER John Smith                                                                         
    CUSTOMER Doctor                                                                             
                                                                                                
    *                                                                                           
     _ __  _ __ ___   ___ ___  ___ ___                                                          
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                         
    | |_) | | | (_) | (_|  __/\__ \__ \                                                         
    | .__/|_|  \___/ \___\___||___/___/                                                         
    |_|                                                                                         
    ;                                                                                           
                                                                                                
    data _null_;                                                                                
                                                                                                
       length wrd $64;                                                                          
                                                                                                
       informat cust $12. therest $64.;                                                         
       input cust therest &;                                                                    
                                                                                                
       * position of word before descending;                                                    
       rx=prxmatch("/(\w+)\s+Doctor/",therest);                                                 
                                                                                                
       if rx ne 0 then do;                                                                      
          wrd=scan(substr(therest,rx),1);                                                       
          wrdlen=length(wrd)+7;                                                                 
          substr(therest,rx,wrdlen)=catx(" ","Doctor",wrd);                                     
          _infile_=catx(" ",cust,therest);                                                      
          put _infile_;                                                                         
       end;                                                                                     
       else put _infile_;                                                                       
                                                                                                
    cards4;                                                                                     
    CUSTOMER Who Doctor                                                                         
    CUSTOMER TV Who Doctor                                                                      
    CUSTOMER Dugi Doctor Houser                                                                 
    CUSTOMER John Smith                                                                         
    CUSTOMER Doctor                                                                             
    ;;;;                                                                                        
    run;quit;                                                                                   
                                                                                                
