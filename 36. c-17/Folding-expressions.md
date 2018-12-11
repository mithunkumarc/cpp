A fold expression performs a fold of a template parameter pack over a binary operator.

    An expression of the form (... operator e) or (e operator ...), where op is a fold-operator and e is an unexpanded parameter pack, 
    are called unary folds.

    An expression of the form (e1 op ... op e2), where op are fold-operators, is called a binary fold. 
    Either e1 or e2 are unexpanded parameter packs, but not both.


#example 1;

        #include <iostream>

        template<typename... Args>
        bool logicalAnd(Args... args){
          //binary folding
          return (true && ... && args);
        }
        int main(){
          bool b = true;
          bool& b2 = b;
          std::cout << logicalAnd(b,b2,true) << std::endl;  
        return 0;
        }
      
        compiling command : g++ -std=c++17 programName.cpp
        output :          
        true/1
        
        
#example 2

          #include <iostream>

          template<typename... Args>
          auto sum(Args... args){
            //uniary folding
            return (... + args);
          }
          int main(){
            bool b = true;
            bool& b2 = b;
            std::cout << sum(1,3.4,7) << std::endl;  
          return 0;
          }


          ouput : 
          11.4

