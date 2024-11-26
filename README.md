## Links

[Reference for mac](https://stackoverflow.com/questions/69720807/how-do-i-use-sfml-on-apple-m1-mac)

[Guide for linux/wsl](https://www.sfml-dev.org/tutorials/2.6/start-linux.php)

## Mac

Check if homebrew is installed
```
brew --version
```

If you do not get a version number you will need to install homebrew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

If you are a mac with Apple Silicon (M1, M2...) run this
```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

Use homebrew to install `sfml` and `neovim`
```
brew install sfml
```

```
brew install neovim
```

Create then edit `main.cpp`
```
nvim main.cpp
```

In nvim type `i` then paste the following code
```cpp
// test file from SFML: https://www.sfml-dev.org/tutorials/2.6/start-linux.php
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```

To save the file press the escape key then enter `:wq`

To compile
```
g++ main.cpp -I/opt/homebrew/Cellar/sfml/2.6.1/include -o app -L/opt/homebrew/Cellar/sfml/2.6.1/lib -lsfml-graphics -lsfml-window -lsfml-system
```

If this fails use `brew info sfml` to get the version number.
Change the version number in the command above to match.

To run the app
```
./app
```

<br>

## WSL on Windows

Install WSL
```
wsl --install
```

Reboot your computer

Install Ubuntu
```
wsl -- install Ubuntu
```

Enter WSL
```
wsl
```

Update apt
```
sudo apt update
```

Install `sfml` and `neovim`
```
sudo apt install libsfml-dev
```
```
sudo apt install neovim
```

Create then edit `main.cpp`
```
nvim main.cpp
```

In nvim type `i` then paste the following code
```cpp
// test file from SFML: https://www.sfml-dev.org/tutorials/2.6/start-linux.php
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```

To save the file press the escape key then enter `:wq`

To compile
```
g++ -c main.cpp
```
```
g++ main.o -o sfml-app -lsfml-graphics -lsfml-window -lsfml-system
```

Run the executable
```
./sfml-app
```
