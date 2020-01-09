---
title: Výrazy – C# Průvodce programováním
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75699090"
---
# <a name="expressions-c-programming-guide"></a>Výrazy (Průvodce programováním v C#)

*Výraz* je sekvence jednoho nebo více operandů a nula nebo více [operátorů](../../language-reference/operators/index.md) , které lze vyhodnotit na jedinou hodnotu, objekt, metodu nebo obor názvů. Výrazy mohou být tvořeny literálovou hodnotou, voláním metody, operátorem a jeho operandy nebo *jednoduchým názvem*. Jednoduché názvy mohou být název proměnné, typ členu, parametr metody, obor názvů nebo typ.  
  
 Výrazy můžou používat operátory, které zase používají jiné výrazy jako parametry, nebo volání metod, jejichž parametry jsou zase jiné volání metody, takže výrazy můžou být v rozsahu od jednoduchých až po velmi složité. Následují dva příklady výrazů:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Hodnoty výrazů

 Ve většině kontextů, ve kterých jsou výrazy použity, například v příkazech nebo parametrech metody, je očekáván výraz pro vyhodnocení na určitou hodnotu. Jsou-li x a y celá čísla, výraz `x + y` vyhodnotí na číselnou hodnotu. Výraz `new MyClass()` vyhodnocen jako odkaz na novou instanci `MyClass` třídy. Výraz `myClass.ToString()` vyhodnotí jako řetězec, protože to je návratový typ metody. Nicméně i když je název oboru názvů klasifikován jako výraz, nevyhodnotí se na hodnotu, takže nikdy nemůže být konečný výsledek jakéhokoli výrazu. Do parametru metody nelze předat název oboru názvů, nebo jej použít v novém výrazu, nebo jej přiřadit proměnné. Můžete ho použít jenom jako dílčí výraz ve větším výrazu. Totéž platí pro typy (jako oddělené od <xref:System.Type?displayProperty=nameWithType> objektů), názvy skupin metod (jako oddělené od konkrétních metod) a přístup k událostem [Přidat](../../language-reference/keywords/add.md) a [Odebrat](../../language-reference/keywords/remove.md) .  
  
 Každá hodnota má přidružený typ. Například pokud jsou x a y proměnné typu `int`, hodnota `x + y` výrazu je také zadána jako `int`. Pokud je hodnota přiřazena proměnné jiného typu nebo pokud x a y jsou jiné typy, jsou použita pravidla převodu typu. Další informace o tom, jak tyto převody fungují, naleznete v tématu [přetypování a převody typu](../types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Přetečení

 Číselné výrazy mohou způsobit přetečení, pokud je hodnota větší než maximální hodnota typu hodnoty. Další informace najdete v části [zaškrtnuté a nezaškrtnuté](../../language-reference/keywords/checked-and-unchecked.md) a v části [explicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) v tématu [integrovaných číselných převodů](../../language-reference/builtin-types/numeric-conversions.md) .
  
## <a name="operator-precedence-and-associativity"></a>Priorita operátorů a asociativita

 Způsob, jakým je výraz vyhodnocován, se řídí pravidly asociativita a prioritami operátorů. Další informace najdete v tématu [operátory](../../language-reference/operators/index.md).  
  
 Většina výrazů, kromě výrazů přiřazení a výrazů vyvolání metody, musí být vložena do příkazu. Další informace najdete v tématu [příkazy](./statements.md).  
  
## <a name="literals-and-simple-names"></a>Literály a jednoduché názvy

 Dva nejjednodušší typy výrazů jsou literály a jednoduché názvy. Literál je konstantní hodnota, která nemá žádný název. Například v následujícím příkladu kódu jsou `5` i `"Hello World"` hodnoty literálu:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Další informace o literálech naleznete v tématu [Types](/dotnet/csharp/language-reference/keywords).  
  
 V předchozím příkladu jsou `i` i `s` jednoduché názvy, které identifikují místní proměnné. Pokud jsou tyto proměnné použity ve výrazu, název proměnné se vyhodnotí na hodnotu, která je aktuálně uložena v umístění proměnné v paměti. To je ukázáno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Výrazy vyvolání

 V následujícím příkladu kódu je volání `DoWork` výrazem vyvolání.  
  
```csharp
DoWork();  
```  
  
 Volání metody vyžaduje název metody, buď jako název jako v předchozím příkladu, nebo jako výsledek jiného výrazu, následovaný závorkami a parametry metody. Další informace naleznete v tématu [metody](../classes-and-structs/methods.md). Volání delegáta používá název delegáta a parametry metody v závorkách. Další informace najdete v tématu [Delegáti](../delegates/index.md). Volání metod a volání delegáta jsou vyhodnocena jako návratová hodnota metody, pokud metoda vrátí hodnotu. Metody, které vracejí typ void, nelze použít místo hodnoty ve výrazu.  

## <a name="query-expressions"></a>Výrazy dotazů

 Stejná pravidla pro výrazy obecně platí pro výrazy dotazu. Další informace naleznete v tématu [LINQ](../../linq/index.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda

 Lambda výrazy reprezentují "vložené metody", které nemají žádný název, ale mohou mít vstupní parametry a vícenásobné příkazy. Používají se rozsáhle v LINQ k předávání argumentů metodám. Výrazy lambda jsou kompilovány buď delegátům, nebo stromů výrazů v závislosti na kontextu, ve kterém jsou použity. Další informace naleznete v tématu [lambda výrazy](lambda-expressions.md).  
  
## <a name="expression-trees"></a>Stromy výrazů

Stromy výrazů umožňují znázornit výrazy jako datové struktury. Jsou často používány poskytovateli LINQ k překladu výrazů dotazů do kódu, který je smysluplný v nějakém jiném kontextu, jako je třeba databáze SQL. Další informace najdete v tématu [stromy výrazů (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>Definice textu výrazu

C#podporuje *členy Expression-těle*, které umožňují zadání definice textu stručného výrazu pro metody, konstruktory, finalizační metody, vlastnosti a indexery. Další informace naleznete v tématu [Expression-těle Members](expression-bodied-members.md).

## <a name="remarks"></a>Poznámky

 Pokaždé, když je proměnná, vlastnost objektu nebo přístup k indexeru objektů identifikovaná z výrazu, hodnota této položky se používá jako hodnota výrazu. Výraz může být umístěn kdekoli, C# kde je požadována hodnota nebo objekt, pokud se výraz nakonec vyhodnocuje na požadovaný typ.  

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [Expressions](~/_csharplang/spec/expressions.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Operátory](../../language-reference/operators/index.md)
- [Metody](../classes-and-structs/methods.md)
- [Delegáti](../delegates/index.md)
- [Typy](../types/index.md)
- [LINQ](../../linq/index.md)
