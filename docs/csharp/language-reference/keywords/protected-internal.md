---
title: interní - chráněné C# odkaz
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: ddfefa2a0bb145aa49a60f06a40725d2706cecb5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661658"
---
# <a name="protected-internal-c-reference"></a>chráněné vnitřní (C# Reference)

`protected internal` – Kombinace klíčových slov je modifikátor přístupu členu. Chráněné vnitřní člen je přístupný z aktuálního sestavení nebo typy, které jsou odvozeny ze třídy obsahující. Porovnání `protected internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněné vnitřní člena základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení. Je také dostupná v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístup prostřednictvím proměnné typu odvozené třídy. Představte si třeba následující segment kódu:

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

Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.
První soubor obsahuje veřejnou základní třídu, `BaseClass`a jiné třídy `TestAccess`. `BaseClass` vlastní chráněný interní člen `myValue`, který přistupuje `TestAccess` typu.
V souboru druhý pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě při přístupu do tohoto člena prostřednictvím instance třídy odvozená `DerivedClass` proběhne úspěšně.

Členy struktury nemůžou být `protected internal` protože struktury nelze dědit.

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
