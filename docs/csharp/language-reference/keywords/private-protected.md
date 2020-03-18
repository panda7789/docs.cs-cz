---
title: privátní chráněné - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713206"
---
# <a name="private-protected-c-reference"></a>privátní chráněné (C# Reference)

Kombinace `private protected` klíčových slov je modifikátor přístupu členů. Soukromý chráněný člen je přístupný typy odvozené z obsahující třídy, ale pouze v rámci jeho obsahující sestavení. Porovnání `private protected` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).

> [!NOTE]
> Modifikátor `private protected` přístupu je platný v c# verze 7.2 a novější.

## <a name="example"></a>Příklad

Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahující sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy. Zvažte například následující segment kódu:  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;  

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

Tento příklad obsahuje `Assembly1.cs` dva `Assembly2.cs`soubory a .
První soubor obsahuje třídu `BaseClass`public base a typ z `DerivedClass1`něj odvozený . `BaseClass`vlastní soukromý chráněný člen `myValue`, `DerivedClass1` který se pokusí o přístup dvěma způsoby. První pokus o `myValue` přístup prostřednictvím instance `BaseClass` způsobí chybu. Pokus o jeho použití jako zděděného člena v aplikaci však `DerivedClass1` bude úspěšný.
V druhém souboru pokus `myValue` o přístup jako `DerivedClass2` zděděný člen způsobí chybu, protože je přístupný pouze odvozené typy v Assembly1.

Členy struktury nelze `private protected` zdědit, protože strukturu nelze zdědit.  

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
