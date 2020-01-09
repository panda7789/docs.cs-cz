---
title: Omezení používání úrovní dostupnosti – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 90c76e68ca526106f3a8be6e3db2640edbb2bc80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715160"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Omezení používání úrovní přístupnostiC# (Referenční dokumentace)

Při zadání typu v deklaraci ověřte, zda je úroveň přístupnosti typu závislá na úrovni přístupnosti člena nebo jiného typu. Například Přímá základní třída musí být alespoň tak přístupná jako odvozená třída. Následující deklarace způsobí chybu kompilátoru, protože základní třída `BaseClass` je méně dostupná než `MyClass`:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Následující tabulka shrnuje omezení deklarované úrovně přístupnosti.

|Kontext|Poznámky|
|-------------|-------------|
|[Třídy](../../programming-guide/classes-and-structs/classes.md)|Přímá základní třída typu třídy musí být alespoň tak přístupná jako typ třídy samotné.|
|[Rozhraní](../../programming-guide/interfaces/index.md)|Explicitní základní rozhraní typu rozhraní musí být alespoň tak přístupná jako typ rozhraní.|
|[Delegáti](../../programming-guide/delegates/index.md)|Návratový typ a typy parametrů typu delegáta musí být k dispozici alespoň jako typ delegáta.|
|[Konstanty](../../programming-guide/classes-and-structs/constants.md)|Typ konstanty musí být alespoň tak přístupný jako konstanta sama.|
|[Pole](../../programming-guide/classes-and-structs/fields.md)|Typ pole musí být alespoň tak přístupný jako pole samotné.|
|[Metody](../../programming-guide/classes-and-structs/methods.md)|Návratový typ a typy parametrů metody musí být k dispozici alespoň jako metoda samotná.|
|[Vlastnosti](../../programming-guide/classes-and-structs/properties.md)|Typ vlastnosti musí být alespoň tak přístupný jako vlastnost sama.|
|[Události](../../programming-guide/events/index.md)|Typ události musí být alespoň tak přístupný jako událost samotná.|
|[Indexery](../../programming-guide/indexers/index.md)|Typy a parametry indexeru musí být alespoň tak přístupné jako indexer samotný.|
|[Operátory](../operators/index.md)|Návratový typ a typy parametrů operátoru musí být k dispozici alespoň jako samotný operátor.|
|[Konstruktory](../../programming-guide/classes-and-structs/constructors.md)|Typy parametrů konstruktoru musí být alespoň tak přístupné jako samotný konstruktor.|

## <a name="example"></a>Příklad

Následující příklad obsahuje chybné deklarace různých typů. Komentář, který následuje za každou deklarací, indikuje očekávanou chybu kompilátoru.

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

- [C#Odkaz](../../language-reference/index.md)
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
