---
title: Výrazy – programovací průvodce Jazyka C#
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699090"
---
# <a name="expressions-c-programming-guide"></a>Výrazy (Průvodce programováním v C#)

*Výraz* je posloupnost jednoho nebo více operandů a nula nebo více [operátorů,](../../language-reference/operators/index.md) které lze vyhodnotit na jednu hodnotu, objekt, metodu nebo obor názvů. Výrazy se mohou skládat z literálové hodnoty, vyvolání metody, operátoru a jeho operandů nebo *jednoduchého názvu*. Jednoduché názvy mohou být název proměnné, člena typu, parametru metody, oboru názvů nebo typu.  
  
 Výrazy můžete použít operátory, které zase použít jiné výrazy jako parametry nebo volání metody, jejichž parametry jsou zase volání jiných metod, takže výrazy mohou v rozsahu od jednoduchých až po velmi složité. Následují dva příklady výrazů:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Hodnoty výrazu

 Ve většině kontextů, ve kterých jsou použity výrazy, například v příkazech nebo parametrech metody, se očekává, že výraz vyhodnotí na nějakou hodnotu. Pokud x a y jsou celá `x + y` čísla, výraz vyhodnotí na číselnou hodnotu. Výraz `new MyClass()` vyhodnotí odkaz na novou instanci `MyClass` třídy. Výraz `myClass.ToString()` vyhodnotí řetězec, protože to je návratový typ metody. I když je však název oboru názvů klasifikován jako výraz, nevyhodnocuje se na hodnotu, a proto nikdy nemůže být konečným výsledkem žádného výrazu. Název oboru názvů nelze předat parametru metody ani jej použít v novém výrazu ani přiřadit proměnné. Můžete jej použít pouze jako dílčí výraz ve větším výrazu. Totéž platí pro typy (na rozdíl od <xref:System.Type?displayProperty=nameWithType> objektů), názvy skupin metod [remove](../../language-reference/keywords/remove.md) (na rozdíl od konkrétních metod) a [přistupující](../../language-reference/keywords/add.md) objekty události.  
  
 Každá hodnota má přidružený typ. Například pokud x a y jsou `int`obě proměnné typu `x + y` , hodnota výrazu je také zadán jako `int`. Pokud je hodnota přiřazena proměnné jiného typu nebo pokud x a y jsou různé typy, použijí se pravidla převodu typu. Další informace o tom, jak tyto převody fungují, naleznete v [tématu Casting a Typ převody](../types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Přetečení

 Číselné výrazy mohou způsobit přetečení, pokud je hodnota větší než maximální hodnota typu hodnoty. Další informace naleznete v [tématu Zaškrtnuto a nezaškrtnuté](../../language-reference/keywords/checked-and-unchecked.md) a v části [Explicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) v článku [Předdefinované číselné převody.](../../language-reference/builtin-types/numeric-conversions.md)
  
## <a name="operator-precedence-and-associativity"></a>Priorita operátora a asociativita

 Způsob, jakým je výraz vyhodnocován, se řídí pravidly asociativity a priority operátoru. Další informace naleznete v tématu [Operátoři](../../language-reference/operators/index.md).  
  
 Většina výrazů, s výjimkou výrazů přiřazení a výrazů vyvolání metody, musí být vložena do příkazu. Další informace naleznete v tématu [Statements](./statements.md).  
  
## <a name="literals-and-simple-names"></a>Literály a jednoduché názvy

 Dva nejjednodušší typy výrazů jsou literály a jednoduché názvy. Literál je konstantní hodnota, která nemá žádný název. Například v následujícím příkladu `5` kódu `"Hello World"` jsou hodnoty literálu:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Další informace o literály naleznete v tématu [Typy](/dotnet/csharp/language-reference/keywords).  
  
 V předchozím příkladu `i` jsou `s` oba a jednoduché názvy, které identifikují místní proměnné. Pokud jsou tyto proměnné použity ve výrazu, název proměnné vyhodnotí hodnotu, která je aktuálně uložena v umístění proměnné v paměti. To je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Výrazy vyvolání

 V následujícím příkladu kódu `DoWork` je volání výraz emitování.  
  
```csharp
DoWork();  
```  
  
 Vyvolání metody vyžaduje název metody, buď jako název jako v předchozím příkladu, nebo jako výsledek jiného výrazu, následovaný závorkou a libovolnými parametry metody. Další informace naleznete v [tématu Metody](../classes-and-structs/methods.md). Vyvolání delegáta používá název delegáta a parametry metody v závorce. Další informace naleznete v tématu [Delegáti](../delegates/index.md). Vyvolání metody a vyvolání delegáta vyhodnocují na vrácenou hodnotu metody, pokud metoda vrátí hodnotu. Metody, které vracejí void nelze použít místo hodnoty ve výrazu.  

## <a name="query-expressions"></a>Výrazy dotazu

 Stejná pravidla pro výrazy obecně platí pro výrazy dotazu. Další informace naleznete v tématu [LINQ](../../linq/index.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda

 Lambda výrazy představují "vložené metody", které nemají žádný název, ale mohou mít vstupní parametry a více příkazů. Jsou používány značně v LINQ předat argumenty metody. Lambda výrazy jsou kompilovány delegáty nebo stromy výrazů v závislosti na kontextu, ve kterém jsou používány. Další informace naleznete v tématu [Lambda Expressions](lambda-expressions.md).  
  
## <a name="expression-trees"></a>Stromy výrazů

Stromy výrazů umožňují, aby výrazy byly reprezentovány jako datové struktury. Jsou používány ve velké míře poskytovateli LINQ přeložit výrazy dotazu do kódu, který je smysluplný v jiném kontextu, jako je například databáze SQL. Další informace naleznete v [tématu Expression Trees (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definice těla výrazu

C# podporuje *členy s výrazem*, které umožňují zadat stručnou definici těla výrazu pro metody, konstruktory, finalizační metody, vlastnosti a indexery. Další informace naleznete v [tématu Expression-tělesně členy](expression-bodied-members.md).

## <a name="remarks"></a>Poznámky

 Vždy, když je z výrazu identifikován přístup k proměnné, vlastnosti objektu nebo indexeru objektů, použije se jako hodnota výrazu hodnota této položky. Výraz lze umístit kdekoli v C# kde je požadována hodnota nebo objekt, tak dlouho, dokud výraz nakonec vyhodnotí požadovaný typ.  

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Výrazy](~/_csharplang/spec/expressions.md) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Operátory](../../language-reference/operators/index.md)
- [Metody](../classes-and-structs/methods.md)
- [Delegáty](../delegates/index.md)
- [Typy](../types/index.md)
- [LINQ](../../linq/index.md)
