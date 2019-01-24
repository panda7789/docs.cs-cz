---
title: Výrazy - C# Průvodce programováním
ms.custom: seodec18
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4fc6485b8ca1c2613df586a56c0c974e9e721380
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600489"
---
# <a name="expressions-c-programming-guide"></a>Výrazy (Průvodce programováním v C#)
*Výraz* je posloupnost nula nebo více operátory, které lze vyhodnotit na jednu hodnotu, objekt, metodu nebo obor názvů a jednu nebo více operandů. Výrazy se může skládat z literálovou hodnotou, volání metody, operátor a jeho operandy nebo *jednoduchý název*. Název proměnné, člen typu, parametr metody, obor názvů nebo typ může být jednoduché názvy.  
  
 Výrazy můžete použít operátory, které pak použít jako parametry nebo volání metody, jejíž parametry jsou zase další volání metody, takže výrazů může být v rozsahu od jednoduché velmi složité jiných výrazech. Následují dva příklady výrazů:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Výraz hodnoty  
 Ve většině kontextech, ve kterých se používají výrazy, například v příkazech nebo parametry metody výrazu by měl vyhodnotit na nějakou hodnotu. Pokud x a y jsou celá čísla, výraz `x + y` vyhodnotí na číselnou hodnotu. Výraz `new MyClass()` vyhodnocen jako odkaz na novou instanci třídy `MyClass` třídy. Výraz `myClass.ToString()` vyhodnotí jako řetězec, protože to je návratový typ metody. Ale i když název oboru názvů klasifikovaný jako výraz, to není vyhodnocen na hodnotu a proto nemůže být nikdy konečný výsledek libovolný výraz. Nelze předat název oboru názvů parametru metody, nebo použít ve výrazu nový nebo ji přiřadit k proměnné. Můžete ho používáte jenom jako dílčí výraz do větších výrazů. Totéž platí pro typy (formou <xref:System.Type?displayProperty=nameWithType> objekty), názvy skupin – metoda (odlišuje specifických metod) a události [přidat](../../../csharp/language-reference/keywords/add.md) a [odebrat](../../../csharp/language-reference/keywords/remove.md) přistupující objekty.  
  
 Každá hodnota má přidruženého typu. Například pokud x a y jsou obě proměnné typu `int`, hodnotu výrazu `x + y` je také zadán jako `int`. Pokud je hodnota přiřazena proměnné jiného typu, nebo pokud x a y jsou různé typy, jsou použita pravidla převodu typu. Další informace o tom, jak tyto převody fungují, najdete v části [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Přetečení  
 Numerických výrazů může způsobit přetečení, pokud je hodnota větší než maximální hodnota typu hodnoty. Další informace najdete v tématu [zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md) a [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Priorita a asociativita operátora  
 Způsob, ve kterém je výraz vyhodnocen se řídí pravidly priority operátoru a asociativity. Další informace najdete v tématu [operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Většina výrazy, s výjimkou přiřazení výrazy a výrazy typu invocation metodu, musí být vložený v příkazu. Další informace najdete v tématu [příkazy](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Literály a jednoduché názvy  
 Nejjednodušší dva typy výrazů jsou literály a jednoduché názvy. Literál je konstantní hodnota, která nemá žádný název. Například v následujícím příkladu kódu i `5` a `"Hello World"` jsou hodnoty literálu:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Další informace o literály, naleznete v tématu [typy](../../../csharp/language-reference/keywords/types.md).  
  
 V předchozím příkladu obě `i` a `s` jsou jednoduché názvy, které identifikují lokální proměnné. Když tyto proměnné se používají ve výrazu, název proměnné vyhodnocen na hodnotu, která je aktuálně uloženo v proměnné umístění v paměti. To je ukázáno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Výrazy typu Invocation  
 V následujícím příkladu kódu volání `DoWork` je výraz volání.  
  
```csharp
DoWork();  
```  
  
 Volání metody vyžaduje název metody, jako název jako v předchozím příkladu, nebo v důsledku jiného výrazu, za nímž následuje (otevírací) a parametry metody. Další informace najdete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Volání delegáta používá název delegáta a metoda parametrů v závorkách. Další informace najdete v tématu [delegáti](../../../csharp/programming-guide/delegates/index.md). Vyvolání metod a vyvolání delegáta vyhodnotit návratovou hodnotu metody, pokud metoda vrátí hodnotu. Metody, které vracejí void nelze použít namísto hodnotu ve výrazu.  

## <a name="query-expressions"></a>Výrazy dotazů  
 Stejná pravidla pro výrazy platí obecně pro výrazy dotazu. Další informace najdete v tématu [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 Výrazy lambda představují "inline metod", které žádný název, ale může mít vstupní parametry a více příkazů. Používají se často v technologii LINQ předání argumentů metody. Výrazy lambda jsou kompilovány do delegátů nebo stromů výrazů v závislosti na kontextu, ve kterém jsou použity. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Stromy výrazů

Stromů výrazů povolit výrazů, aby se dala vyjádřit jako datové struktury. Používají se hojně poskytovateli LINQ pro převod do kódu, který má smysl v jiných kontextu, jako je SQL database – výrazy dotazů. Další informace najdete v tématu [stromů výrazů (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definice textu výrazu

C# podporuje *členové tvoření*, které umožňují zadat definici stručné výraz těla metody, konstruktory, finalizační metody, vlastnostmi a indexery. Další informace najdete v tématu [členové tvoření](expression-bodied-members.md).

## <a name="remarks"></a>Poznámky  
 Pokaždé, když se proměnná, vlastnost objektu nebo objekt přístup indexeru je identifikován z výrazu, hodnota této položky se používá jako hodnotu výrazu. Výraz může být umístěna kdekoli v jazyce C# ve kterém jsou vyžadována, hodnotu nebo objekt za předpokladu, takže v konečném důsledku je vyhodnocen požadovaného typu.  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)
- [Typy](../../../csharp/programming-guide/types/index.md)
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
