---
title: Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)
Když zadáte v deklaraci typu, zkontrolujte, zda usnadnění úroveň tohoto typu je závislé na úrovni přístupu člena nebo jiného typu. Například přímé základní třídu, musí být dostupné jako odvozené třídy. Následující deklarace způsobit chyby kompilátoru, protože základní třída `BaseClass` je méně přístupný než `MyClass`:  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 Následující tabulka shrnuje omezení na úrovní deklarované přístupu.  
  
|Kontext|Poznámky|  
|-------------|-------------|  
|[Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)|Základní třídy přímé typu třídy musí být dostupné jako typ třídy.|  
|[Rozhraní](../../../csharp/programming-guide/interfaces/index.md)|Rozhraní explicitní základní typ rozhraní musí být dostupné jako vlastní typ rozhraní.|  
|[Delegáti](../../../csharp/programming-guide/delegates/index.md)|Návratový typ a typy parametrů typu delegáta musí být dostupné jako vlastní typ delegáta.|  
|[Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)|Typ konstanty musí být dostupné jako konstanta sám sebe.|  
|[Pole](../../../csharp/programming-guide/classes-and-structs/fields.md)|Typ pole musí být dostupné jako vlastní pole.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Návratový typ a typy parametrů metody musí být přístupné metoda sama.|  
|[Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)|Typ vlastnosti musí být dostupné jako samotné vlastnosti.|  
|[Události](../../../csharp/programming-guide/events/index.md)|Typ události musí být dostupné jako samotné události.|  
|[Indexery](../../../csharp/programming-guide/indexers/index.md)|Typ a parametr typy indexer musí být dostupné jako indexeru sám sebe.|  
|[Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Návratový typ a typy parametrů operátoru musí být dostupné jako operátor.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Typy parametrů konstruktor musí být dostupné jako konstruktoru sám sebe.|  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje chybné deklarace různých typů. Komentář následující každá deklarace značí chybu očekávané kompilátoru.  
  
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
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
