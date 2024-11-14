## Mac

Check if homebrew is installed
```brew --version```

If you do not get a version number you will need to install homebrew
```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"```

If you are a mac with Apple Silicon (M1, M2...) run this
```echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile```

Use homebrew to install `sfml` and `neovim`
```brew install sfml```
```brew install neovim```

Create then edit `main.cpp`
```nvim main.cpp```

In nvim type `i` then paste the following code

```cpp
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

To compile run
```g++ main.cpp -I/opt/homebrew/Cellar/sfml/2.6.1/include -o app -L/opt/homebrew/Cellar/sfml/2.6.1/lib -lsfml-graphics -lsfml-window -lsfml-system```

To run the app
```./app```

