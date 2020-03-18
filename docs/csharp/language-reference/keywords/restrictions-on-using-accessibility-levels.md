---
title: Omezení používání úrovní usnadnění – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173533"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Omezení používání úrovní usnadnění (odkaz C#

Když zadáte typ v deklaraci, zkontrolujte, zda úroveň usnadnění typu je závislá na úrovni usnadnění přístupu člena nebo jiného typu. Například přímá základní třída musí být alespoň stejně přístupná jako odvozená třída. Následující deklarace způsobit chybu kompilátoru, protože základní třída `BaseClass` je méně přístupné než `MyClass`:

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

Následující tabulka shrnuje omezení deklarovaných úrovní usnadnění.

|Kontext|Poznámky|
|-------------|-------------|
|[Třídy](../../programming-guide/classes-and-structs/classes.md)|Přímá základní třída typu třídy musí být alespoň stejně přístupná jako samotný typ třídy.|
|[Rozhraní](../../programming-guide/interfaces/index.md)|Explicitní základní rozhraní typu rozhraní musí být alespoň stejně přístupné jako samotný typ rozhraní.|
|[Delegáty](../../programming-guide/delegates/index.md)|Návratový typ a typy parametrů typu delegáta musí být alespoň stejně přístupné jako samotný typ delegáta.|
|[Konstanty](../../programming-guide/classes-and-structs/constants.md)|Typ konstanty musí být alespoň stejně přístupný jako konstanta sama.|
|[Pole](../../programming-guide/classes-and-structs/fields.md)|Typ pole musí být alespoň stejně přístupný jako samotné pole.|
|[Metody](../../programming-guide/classes-and-structs/methods.md)|Návratový typ a typy parametrů metody musí být alespoň stejně přístupné jako samotná metoda.|
|[Vlastnosti](../../programming-guide/classes-and-structs/properties.md)|Typ vlastnosti musí být alespoň stejně přístupný jako vlastnost sama.|
|[Akce](../../programming-guide/events/index.md)|Typ události musí být alespoň stejně přístupný jako samotná událost.|
|[Indexery](../../programming-guide/indexers/index.md)|Typy typů a parametrů indexeru musí být alespoň stejně přístupné jako indexer sám.|
|[Operátory](../operators/index.md)|Návratový typ a typy parametrů operátoru musí být alespoň stejně přístupné jako samotný operátor.|
|[Konstruktory](../../programming-guide/classes-and-structs/constructors.md)|Typy parametrů konstruktoru musí být alespoň stejně přístupné jako samotný konstruktor.|

## <a name="example"></a>Příklad

Následující příklad obsahuje chybné deklarace různých typů. Komentář za každou deklarací označuje očekávanou chybu kompilátoru.

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

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](../../language-reference/keywords/index.md)
- [Modifikátory přístupu](../../language-reference/keywords/access-modifiers.md)
- [Doména přístupnosti](../../language-reference/keywords/accessibility-domain.md)
- [Úrovně přístupnosti](../../language-reference/keywords/accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Veřejné](../../language-reference/keywords/public.md)
- [Soukromé](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [Vnitřní](../../language-reference/keywords/internal.md)
