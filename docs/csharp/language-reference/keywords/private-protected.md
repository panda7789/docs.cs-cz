---
title: soukromý chráněný – C# odkaz
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713206"
---
# <a name="private-protected-c-reference"></a>Private ProtectedC# (Referenční dokumentace)

Kombinací klíčového slova `private protected` je modifikátor přístupu ke členu. Soukromý chráněný člen je přístupný z typů odvozených z obsahující třídy, ale pouze v rámci nadřazeného sestavení. Porovnání `private protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).

> [!NOTE]
> Modifikátor přístupu `private protected` je platný ve C# verzi 7,2 a novější.

## <a name="example"></a>Příklad

Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahujícím sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy. Zvažte například následující segment kódu:  

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

Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.
První soubor obsahuje veřejnou základní třídu, `BaseClass`a typ odvozený z něj, `DerivedClass1`. `BaseClass` vlastní soukromý chráněný člen, `myValue`, který `DerivedClass1` se snaží získat přístup dvěma způsoby. První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` vytvoří chybu. Ale pokus o použití jako zděděného člena v `DerivedClass1` úspěšný bude.
Ve druhém souboru se pokus o přístup k `myValue` jako zděděný člen `DerivedClass2` vytvoří chyba, protože je přístupná pouze pro odvozené typy v Assembly1.

Členy struktury nelze `private protected`, protože strukturu nelze zdědit.  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
