---
title: chráněné vnitřní - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713193"
---
# <a name="protected-internal-c-reference"></a>chráněné interní (C# Reference)

Kombinace `protected internal` klíčových slov je modifikátor přístupu členů. Chráněný interní člen je přístupný z aktuálního sestavení nebo z typů, které jsou odvozeny z obsahující třídy. Porovnání `protected internal` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný vnitřní člen základní třídy je přístupný z libovolného typu v rámci jeho obsahující sestavení. Je také přístupný v odvozené třídě umístěné v jiném sestavení pouze v případě, že přístup probíhá prostřednictvím proměnné odvozeného typu třídy. Zvažte například následující segment kódu:

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

Tento příklad obsahuje `Assembly1.cs` dva `Assembly2.cs`soubory a .
První soubor obsahuje třídu `BaseClass`public base a `TestAccess`jinou třídu . `BaseClass`vlastní chráněný interní člen `myValue`, ke kterému `TestAccess` má typ přístup.
V druhém souboru pokus `myValue` o přístup `BaseClass` prostřednictvím instance způsobí chybu, zatímco přístup k tomuto členu prostřednictvím instance odvozené třídy, `DerivedClass` bude úspěšné.

Členy struktury nelze `protected internal` zdědit, protože strukturu nelze zdědit.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [Veřejné](public.md)
- [Soukromé](private.md)
- [Vnitřní](internal.md)
- [Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
