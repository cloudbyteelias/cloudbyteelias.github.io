---
title: first-post
date: 2021-02-05 20:55:05
tags:
---
``` c++
//teste ss


#include <iostream>
#include <iomanip>
#include <cmath>



using namespace std;

int main(int argc, char const *argv[]){
    
    size_t max{};

    cout << "Numero de primos a serem calculados?" ;
    cout << endl;
    cin >> max;

    if (max == 0){
        cout << "Error";
        return EXIT_FAILURE;
    }

    auto* primes {new unsigned [max]};

    size_t count {1};
    primes[0] = 2;

    unsigned trial {3};

    while(count < max){

        bool isprime{true};

        const auto limit = static_cast<unsigned>(sqrt(trial));

        for(size_t i{}; primes[i] <= limit && isprime; ++i){

                isprime = trial % primes[i] > 0;

        }

        if(isprime){
            primes[count ++] = trial;
            trial += 2;
        }

        //output

        for(size_t i {}; i < max; i++){

            cout << setw(10) << primes[i];

            if((i+1) % 10 == 0){
                cout << endl;
            }
        }

        //cout << endl;
        delete[] primes; // free memory array
        //primes = nullptr; // reset no ponteiro
    
    }

    return EXIT_SUCCESS;
}
```