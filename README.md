# SCL:SL Round Mutators
## ru-RU
### Установка
Для установки откройте релизы и скачайте последнюю версию плагина. Поместите в %appdata%/Qurre/Plugins (~/.config/Qurre/Plugins)
### Как использовать
Мутаторы вызываются в начале раунда. Делается это по чистому рандому и повлиять на это нельзя.
### Разработка
Если вы хотите добавить свои мутаторы, склонируйте репозиторий, создайте новый класс в TFP_RoundMutators.Mutators и унаследуйте интерфейс TFP_RoundMutators.Interfaces.IMutator. Пример кода мутатора:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TFP_RoundMutators.Mutators
{
    internal class test : TFP_RoundMutators.Interfaces.IMutator
    {
        public string Displayname { get; set; } = "<color=white>Тествовый мутатор</color>";
        public string Description { get; set; } = "Это тестовый мутатор";

        public void Disengaged()
        {
            /*
             * Этот код выполняется, когда происходит:
             *  Рестарт раунда
             *  Конец раунда
             *  Ожидание игроков
             */
        }

        public bool DoIWantToEngage()
        {
            /*
             * Здесь можно проверить некоторые условия, при котором мутатор может быть проигнорирован.
             * Например, у нас мутатор меняет фичи у компа, но его может не быть.
             * Вот тут можно проверить условие и вернуть `true`, если вы хотите чтобы мутатор был запущен
             * или `false`, если вы хотите, чтобы мутатор был скипнут
             */
            return true;
        }

        public void Engaged()
        {
            /*
             * Этот код выполняется, когда происходит:
             *  Начало раунда
             */
        }
    }
}
```
## en-US
### Installation
To install the plugin, download latest realease from releases and move it to %appdata%/Qurre/Plugins (~/.config/Qurre/Plugins)
### How to use
Mutators are engaged upon round start. There is no way to influence this, because mutator selection is purely random.
### For developers
If you want to add custom mutators, create a new class in TFP_RoundMutators.Mutators and inherit interface TFP_RoundMutators.Interfaces.IMutator. Example code:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TFP_RoundMutators.Mutators
{
    internal class test : TFP_RoundMutators.Interfaces.IMutator
    {
        public string Displayname { get; set; } = "<color=white>Тествовый мутатор</color>";
        public string Description { get; set; } = "Это тестовый мутатор";

        public void Disengaged()
        {
            /*
             * This method is invoked when:
             *  Round has been restarted
             *  Round has been ended
             *  Players are being awaited
             */
        }

        public bool DoIWantToEngage()
        {
            /*
             * Here you can check for certain conditions, according to which mutator can be skipped.
             * For example, we have a mutator which *buffs* SCP-079
             * Here we can check if SCP-079 is present in the game and return `true`, which means mutator will be engaged
             * or `false` to skip it.
             */
            return true;
        }

        public void Engaged()
        {
            /*
             * This method is executed when:
             *  Round has been started
             */
        }
    }
}
```
