---
title: Private protected (referenční dokumentace jazyka C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 4a4ee999fe932674e854b1428ab33b33bc71d2ad
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518448"
---
# <a name="private-protected-c-reference"></a>Private protected (referenční dokumentace jazyka C#)

`private protected` – Kombinace klíčových slov je modifikátor přístupu členu. Privátní chráněný člen je přístupný pro typy odvozené od obsahující třídy, ale pouze v rámci jeho obsahujícího sestavení. Porovnání `private protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).

> [!NOTE]
> `private protected` Modifikátor přístupu je platný v jazyce C# verze 7.2 nebo novější.

## <a name="example"></a>Příklad

Privátní chráněného člena základní třídy je přístupný z odvozených typů v sestavení obsahující pouze v případě, statický typ proměnné je typ odvozené třídy. Představte si třeba následující segment kódu:  

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
        BaseClass baseObject = new BaseClass();

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

Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.
První soubor obsahuje veřejnou základní třídu, `BaseClass`a typ odvozený z ní, `DerivedClass1`. `BaseClass` vlastní privátní chráněný člen `myValue`, což `DerivedClass1` pokusí o přístup k dvěma způsoby. První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě. Nicméně pokus o jeho použití jako zděděného člena v `DerivedClass1` proběhne úspěšně.
V souboru druhý pokus o přístup k `myValue` jako zděděný člen `DerivedClass2` dojde k chybě, protože byl přístupný pouze odvozenými typy v Assembly1.

Členy struktury nemůžou být `private protected` protože struktury nelze dědit.  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))