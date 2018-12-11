---
title: Omezení používání pro usnadnění úrovně - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: ef1c0a93da2a53f1e199627fb7f83894d01e714a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239326"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Omezení používání úrovní přístupu (referenční dokumentace jazyka C#)

Při zadávání typu v deklaraci, zkontrolujte, zda úroveň přístupnost typu je závislé na úrovni přístupu člena nebo jiného typu. Například přímou základní třídu, musí být přinejmenším stejně dostupná jako odvozené třídy. Následující deklarace způsobí chybu kompilátoru, protože základní třída `BaseClass` je méně dostupný než `MyClass`:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Následující tabulka shrnuje omezení úrovní deklarovaná přístupnost.

|Kontext|Poznámky|
|-------------|-------------|
|[Třídy](../../programming-guide/classes-and-structs/classes.md)|Přímou základní třídu typu třídy musí být přinejmenším stejně dostupná jako typ třídy.|
|[Rozhraní](../../programming-guide/interfaces/index.md)|Explicitní základní rozhraní typu rozhraní musí být přinejmenším stejně dostupná jako samotného typu rozhraní.|
|[Delegáti](../../programming-guide/delegates/index.md)|Návratový typ a typy parametrů typu delegáta musí být přinejmenším stejně dostupná jako samotného typu delegáta.|
|[Konstanty](../../programming-guide/classes-and-structs/constants.md)|Typ konstanty musí být přinejmenším stejně dostupná jako konstanta samotný.|
|[Pole](../../programming-guide/classes-and-structs/fields.md)|Typ pole musí být přinejmenším stejně dostupná jako vlastní pole.|
|[Metody](../../programming-guide/classes-and-structs/methods.md)|Návratový typ a typy parametrů metody musí být přinejmenším stejně dostupná jako metoda sama.|
|[Vlastnosti](../../programming-guide/classes-and-structs/properties.md)|Typ vlastnosti musí být přinejmenším stejně dostupná jako samotné vlastnosti.|
|[Události](../../programming-guide/events/index.md)|Typ události musí být přinejmenším stejně dostupná jako samotné události.|
|[Indexery](../../programming-guide/indexers/index.md)|Typ a parametrem typy indexer musí být přinejmenším stejně dostupná jako samotný indexeru.|
|[Operátory](../../programming-guide/statements-expressions-operators/operators.md)|Návratový typ a typy parametrů operátoru musí být přinejmenším stejně dostupná jako operátor.|
|[Konstruktory](../../programming-guide/classes-and-structs/constructors.md)|Typy parametrů konstruktoru musí být přinejmenším stejně dostupná jako konstruktor samotný.|

## <a name="example"></a>Příklad

Následující příklad obsahuje chybné deklarace různých typů. Komentář po deklaraci označuje chybu kompilátoru očekávané.

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible 
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error: 
    // "The parameter B.MyPrivateMethod is not accessible due to 
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](../../language-reference/keywords/index.md)
- [Modifikátory přístupu](../../language-reference/keywords/access-modifiers.md)
- [Doména přístupnosti](../../language-reference/keywords/accessibility-domain.md)
- [Úrovně přístupnosti](../../language-reference/keywords/accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../language-reference/keywords/public.md)
- [private](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)