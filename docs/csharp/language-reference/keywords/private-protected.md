---
title: Private Protected – reference jazyka C#
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301798"
---
# <a name="private-protected-c-reference"></a>Private Protected (Referenční dokumentace jazyka C#)

`private protected`Kombinace klíčového slova je modifikátor přístupu ke členu. Soukromý chráněný člen je přístupný z typů odvozených z obsahující třídy, ale pouze v rámci nadřazeného sestavení. Porovnání `private protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).

> [!NOTE]
> `private protected`Modifikátor přístupu je platný v jazyce C# verze 7,2 a novějším.

## <a name="example"></a>Příklad

Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahujícím sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy. Zvažte například následující segment kódu:

```csharp
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

Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs` .
První soubor obsahuje veřejnou základní třídu, `BaseClass` a typ, který je z něj odvozený `DerivedClass1` . `BaseClass`vlastní soukromý chráněný člen, `myValue` , který se `DerivedClass1` snaží získat přístup dvěma způsoby. Při prvním pokusu o přístup `myValue` prostřednictvím instance `BaseClass` se vytvoří chyba. Pokus o jeho použití jako zděděný člen v nástroji bude ale `DerivedClass1` úspěšný.

Ve druhém souboru dojde k chybě pokusu o přístup `myValue` jako zděděný člen `DerivedClass2` , protože je přístupný pouze pro odvozené typy v Assembly1.

Pokud `Assembly1.cs` obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> název `Assembly2` , odvozená třída `DerivedClass1` bude mít přístup ke `private protected` členům deklarovaným v `BaseClass` . `InternalsVisibleTo`zpřístupňuje `private protected` členy na odvozených třídách v jiných sestaveních.

Členy struktury nemůžou být `private protected` zděděné, protože strukturu nejde zdědit.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [public](public.md)
- [hlášen](private.md)
- [internal](internal.md)
- [Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
