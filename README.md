#include <iostream>
#include <fstream>
#include <sstream>
using namespace std;

bool evaluateComb(int comb)
{
    int ucif=comb%10;
    comb/=10;
    bool ok=true;
    while(comb>0&&ok)
    {

            int cif = comb%10;

            bool okRow = ucif-1==cif || ucif+1==cif;
            bool okCol = ucif-3==cif || ucif+3==cif;
            bool okDiag = ucif-4==cif || ucif+4==cif || ucif-2==cif || ucif+2==cif;
            //cout<<okRow<<" "<<okCol<<" "<<okDiag<<endl;
            ok = okRow||okCol;
            //cout<<ok<<" "<<cif<<" "<<ucif<<endl;

        ucif=comb%10;
        //cout<<ucif<<endl;
        comb/=10;
    }
    cout<<ok<<endl;
    return ok;
}

int main()
{
    stringstream ss;
    ifstream fin("smartphone1.in");
    string _n, _line;
    getline(fin,_n);
    ss<<_n;
    int n;
    ss>>n;
    //cout<<n;
    int combinatii[n];
    getline(fin,_line);
    fin.close();
    //cout<<_line<<endl;
    stringstream nr;
    nr<<_line;
    for(int i=0;i<n;i++)
    {
        string s;
        nr>>s;
        //cout<<s<<endl;
        stringstream _ss(s);
        int comb;
        _ss>>comb;
        combinatii[i]=comb;
        //cout<<comb<<endl;
    }
    int ok = 0;
    for(int i=0; i<n;i++)
        if(evaluateComb(combinatii[i]))
            ok++;
    cout<<ok;
    return 0;
}
