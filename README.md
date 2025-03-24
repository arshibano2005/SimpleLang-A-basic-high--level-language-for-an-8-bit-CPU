# SimpleLang-A-basic-high--level-language-for-an-8-bit-CPU

#include<iostream>
#include<sstream>
#include<unordered_map>
#include<cctype>

enum TokenCategory{Type,IDENTIFIER,VALUE,EQUAL,PLUS,MINUS,CONDITION,COMPARE,OPEN_BLOCK,CLOSE_BLOCK,END_STATEMENT,STOP};

struct Lexeme{
    TokenCategory category;
    string content;
};

vector<Lexeme>analyzeCode(conststring&sourceCode){
        vector<Lexeme>tokenList;
        istringstream input9sourceCode);
        string term;
        while(input>>term){
            if(term=="int"){
                tokenList.push_back({TYPE,term});
            }
            else if(term=="if"){
                 tokenList.push_back({condition,term});
              }
              else if(term=="="){
                      tokenList.push_back({EQUAL,term});
              }
              else if(term=="+"){
                     tokenList.push_back({PLUS,term});
              }
              else if(term=="-"){
                     tokenList.push_back({MINUS,term});
              }
              else if(term=="=="){
                      tokenList.push_back({COMPARE,term});
              }
              else if(term=="{"){
                      tokenList.push_back({OPEN_BLOCK,term});
              }
              else if(term=="}"){
                      tokenList.push_back({CLOSE_BLOCK,term});
              }
              else if(term==";"){
                     tokenList.push_back({END_STATEMENT,term});

              }
              else if(isdigit(term[0])){
                    tokenList.push_back({VALUE,term});
              }
              else{
                    tokenList.push_back({IDENTIFIER,term});
              }
          }
          tokenList.push_back({STOP,""});

          return tokenList;
}

unordered_map<string,int>memoryTable;

void translateToAssembly(constvector<LExeme>&tokenList){
       cout<<"Generate Assembly Code:\n";
        for(size_t i=0;i<tokenList.size();i++){
                  if(tokenList.[i].category==IDENTIFIER && i+2<tokenList.size() && tokenList[i+1].category==EQUAL){
                         cout<<" MOV"<< tokenList[i].content<<","<<tokenlist[i+2].content<<"\n";
                         memoryTable[tokenList[i].content]=stoi(tokenList[i+2].content);
                         i+=3;
                    }
                     else if(tokenList[i].category==IDENTIFIER && i+4<tokenList.size() && tokenLIst[i+1].category==EQUAL && tokenList[i+3].category==PLUS){
                          int result=memoryTable[tokenList[i+2].content]+stoi(tokenList[i+4].content);
                          cout<<"ADD"<<tokenList[i+2].content<<","<<tokenList[i+4].content<<"\n";
                          cout<<"MOV"<<tokenList[i].content<<","<<result<<"\n;
                          memoryTable[tokenList[i].content]=resilt;
                          i+=5;

                      }
                      else if(tokenList[i].category==CONDITION){
                             cout<<"CPM"<<tokenList[i+1].content<<","<<tokenList[i+3].content<<',";
                             cout<<"JNE EXIT_BLOCK\N";
                             i+=4;
                      }
                      else if(tokenList[i].category==IDENTIFIER && i+4<tokenList.size() && tokenList[i+3].category==MINUS){
                            int result=memoryTable[tokenList[i+2].content]-stoi(tokenList[i+4].content);
                            cout<<"SUB"<<tokenList[i+2].content<<"\n"<<tokenList[i+4].content<<"\n";
                            cout<<"mov"<<tokenList[i].content<<","<<result<<"\n";
                            memoryTable[tokenList[i].content]=result;
                            i+=5;
                      }
              }
               cout<<"EXIT_BLOCK:\n";
}

int main(){
    string sampleCode=int x;int y;x=10;y=x+2;
    if(y==12){
       y=y-1;
    }

    vector<Lexeme>tokenSequence=analyzeCode(SampleCode);

    translateToAssembly(tokenSequence);

    return 0;
}
    
       

    
              
            
                
                 
