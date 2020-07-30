---
title: Protected Internal-C# – referenční informace
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: 4067da93bcceba0fa3e4a14aa58b4cde812412f3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301785"
---
# <a name="protected-internal-c-reference"></a>Protected Internal (Referenční dokumentace jazyka C#)

`protected internal`Kombinace klíčového slova je modifikátor přístupu ke členu. Chráněný interní člen je přístupný z aktuálního sestavení nebo z typů, které jsou odvozeny z nadřazené třídy. Porovnání `protected internal` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný interní člen základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení. Je také přístupný v odvozené třídě nacházející se v jiném sestavení pouze v případě, že k přístupu dojde prostřednictvím proměnné odvozeného typu třídy. Zvažte například následující segment kódu:

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

Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs` .
První soubor obsahuje veřejnou základní třídu, `BaseClass` a další třídu, `TestAccess` . `BaseClass`vlastní chráněný interní člen, `myValue` , který je k dispozici pro daný `TestAccess` typ.
Ve druhém souboru dojde k pokusu o přístup `myValue` prostřednictvím instance aplikace k `BaseClass` chybě, zatímco přístup k tomuto členu prostřednictvím instance odvozené třídy `DerivedClass` bude úspěšný.

Členy struktury nemůžou být `protected internal` zděděné, protože strukturu nejde zdědit.

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
