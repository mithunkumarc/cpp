Constant expressions are expressions evaluated by the compiler at compile-time. Only non-complex computations can be carried out in a constant expression. Use the constexpr specifier to indicate the variable, function, etc. is a constant expression.

        constexpr int square(int x) {
          return x * x;
        }

        int square2(int x) {
          return x * x;
        }

        int a = square(2);  // mov DWORD PTR [rbp-4], 4

        int b = square2(2); // mov edi, 2
                            // call square2(int)
                            // mov DWORD PTR [rbp-8], eax

constexpr values are those that the compiler can evaluate at compile-time:

        const int x = 123;
        constexpr const int& y = x; // error -- constexpr variable `y` must be initialized by a constant expression

Constant expressions with classes:

        struct Complex {
          constexpr Complex(double r, double i) : re(r), im(i) { }
          constexpr double real() { return re; }
          constexpr double imag() { return im; }

        private:
          double re;
          double im;
        };

        constexpr Complex I(0, 1);
