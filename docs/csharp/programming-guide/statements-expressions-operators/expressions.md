---
title: Výrazy (Průvodce programováním v C#)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 830c68e6857e72fe19099753ba57a7e22491af2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expressions-c-programming-guide"></a>Výrazy (Průvodce programováním v C#)
*Výraz* je posloupnost nula nebo více operátory, které lze vyhodnotit na hodnotu typu single, objekt, metodu nebo obor názvů a jeden nebo více operandy. Výrazy se může skládat z literálovou hodnotou, volání metody, operátor a jejími operandy, nebo *jednoduchý název*. Název proměnné, typ, parametru metody, obor názvů nebo člena typu může být jednoduché názvy.  
  
 Výrazy můžete použít operátory, které pak použít jako parametry nebo volání metod, jejíž parametry jsou naopak další volání metod, takže výrazy může být v rozsahu od jednoduchého do velmi složité jiné výrazy. Následují dva příklady výrazů:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Výraz hodnoty  
 Ve většině kontextů, ve kterých se používají výrazy, například příkazy nebo parametry metody očekává se výraz k vyhodnocení na určitou hodnotu. Pokud x a y jsou celá čísla, výraz `x + y` jehož výsledkem je číselná hodnota. Výraz `new MyClass()` vyhodnocen jako odkaz na novou instanci třídy `MyClass` objektu. Výraz `myClass.ToString()` vyhodnotí jako řetězec, protože se jedná o návratový typ metody. Ale, i když název oboru názvů klasifikovaný jako výraz, ho nelze vyhodnotit na hodnotu a proto nemůže být nikdy konečný výsledek jakýkoli výraz. Nelze předat název oboru názvů parametru metody, nebo ho použít nový výraz nebo přiřadit k proměnné. Pouze ho můžete použít jako výraz dílčí větší výrazu. Totéž platí pro typy (formou <xref:System.Type?displayProperty=nameWithType> objekty), názvy skupin – metoda (na rozdíl od konkrétní metody) a událostí [přidat](../../../csharp/language-reference/keywords/add.md) a [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupující objekty.  
  
 Každá hodnota má typ přidružené. Například pokud x a y jsou obě proměnné typu `int`, hodnotu výrazu `x + y` rovněž je zadán jako `int`. Pokud hodnota je přiřazený k proměnné jiného typu, nebo pokud x a y jsou různé typy, platí pravidla převod typů. Další informace o fungování takové převody najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Přetečení  
 Numerické výrazy může způsobit některé, pokud je hodnota větší než maximální hodnota hodnota typu. Další informace najdete v tématu [zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md) a [explicitní číselné převody tabulky](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Priorita operátorů a asociativnost  
 Způsobem, ve které je výraz vyhodnocen se řídí pravidly asociativnost a operátor priorit. Další informace najdete v tématu [operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Většina výrazy, s výjimkou přiřazení výrazy a výrazy volání metody, musí být vložený v příkazu. Další informace najdete v tématu [příkazy](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Literály a jednoduché názvy  
 Nejjednodušší dva druhy výrazy jsou literály a jednoduché názvy. Literál je konstantní hodnota, která nemá žádný název. Například v následujícím příkladu kódu obě `5` a `"Hello World"` jsou literálových hodnot:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Další informace o literály, najdete v části [typy](../../../csharp/language-reference/keywords/types.md).  
  
 V předchozím příkladu obě `i` a `s` jsou jednoduché názvy, které identifikují lokální proměnné. Pokud tyto proměnné se používají ve výrazu, název proměnné se vyhodnotí na hodnotu, která je aktuálně uložené v proměnné umístění v paměti. To je ukázáno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Vyvolání výrazy  
 V následujícím příkladu kódu volání `DoWork` je výraz volání.  
  
```csharp
DoWork();  
```  
  
 Volání metody vyžaduje název metody, jako název jako v předchozím příkladu nebo v důsledku jiného výrazu, následovaný závorky a všechny parametry metody. Další informace najdete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Delegát volání používá název delegáta a metoda parametrů do závorek. Další informace najdete v tématu [delegáti](../../../csharp/programming-guide/delegates/index.md). Volání metod a volání delegáta vyhodnotit návratovou hodnotu metody, pokud metoda vrátí hodnotu. Metody, které vracet typ void nelze použít namísto hodnotu ve výrazu.  

## <a name="query-expressions"></a>Výrazy dotazů  
 Stejná pravidla pro výrazy obecně použít na výrazy dotazu. Další informace najdete v tématu [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Lambda – výrazy  
 Lambda – výrazy představují "vložené metody", které mají žádný název, ale může mít vstupní parametry a více příkazů. Používají se hojně v technologii LINQ předání argumentů do metody. Lambda – výrazy kompilovány delegáti nebo stromů výrazů v závislosti na kontextu, ve kterém se používají. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Stromy výrazů  
 Stromy výrazů povolit výrazy a být reprezentován jako datové struktury. Používají se hojně poskytovateli LINQ přeložit výrazy dotazů do kódu, který má smysl v jiných kontextu, například do databáze SQL. Další informace najdete v tématu [stromů výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
## <a name="expression-body-definitions"></a>Výraz definice textu

C# podporuje *výraz vozidlo členy*, které vám umožňují zadat definici stručného výrazu těla metody, konstruktory, finalizační metody, vlastnosti a indexery. Další informace najdete v tématu [výraz vozidlo členy](expression-bodied-members.md).

## <a name="remarks"></a>Poznámky  
 Vždy, když je proměnná, vlastnost objektu nebo přístupu k objektům indexer identifikuje z výrazu, hodnota této položky se používá jako hodnotu výrazu. Výraz mohou být umístěny kdekoli v jazyce C# kdy je potřeba, hodnota nebo objekt tak dlouho, dokud nakonec vyhodnocen jako požadovaný typ.  

## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
