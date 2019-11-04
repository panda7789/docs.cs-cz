---
title: nový modifikátor – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 082cd37eca6b5de1251d73a5483665f8a98b0132
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422671"
---
# <a name="new-modifier-c-reference"></a>New – modifikátorC# (Referenční dokumentace)

Při použití jako modifikátor deklarace klíčová slova `new` explicitně skrývá člen, který je zděděn ze základní třídy. Když skryjete zděděného člena, odvozená verze člena nahradí verzi základní třídy. I když můžete členy skrýt bez použití modifikátoru `new`, zobrazí se upozornění kompilátoru. Použijete-li `new` k explicitnímu skrytí člena, potlačí toto upozornění.

Můžete také použít klíčové slovo `new` pro [vytvoření instance typu](../operators/new-operator.md) nebo jako [omezení obecného typu](./new-constraint.md).

Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu člena a upravte jej pomocí klíčového slova `new`. Příklad:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

V tomto příkladu je `BaseC.Invoke` skrytý pomocí `DerivedC.Invoke`. Pole `x` není ovlivněno, protože není skryté podobným názvem.

Název skrývání prostřednictvím dědičnosti má jednu z následujících forem:

- Obecně konstanta, pole, vlastnost nebo typ, který je představen ve třídě nebo struktuře, skrývá všechny členy základní třídy, které sdílejí svůj název. Existují zvláštní případy. Například pokud deklarujete nové pole s názvem `N`, že má typ, který není nevyvolatelný, a základní typ deklaruje `N` jako metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání. Další informace naleznete v oddílu [vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

- Metoda zavedená ve třídě nebo struktuře skrývá vlastnosti, pole a typy, které sdílejí tento název v základní třídě. Také skryje všechny metody základní třídy, které mají stejnou signaturu.

- Indexer zavedený ve třídě nebo struktuře skrývá všechny základní třídy indexerů, které mají stejnou signaturu.

Použití `new` i [přepsání](override.md) u stejného člena je chybné, protože dva modifikátory mají vzájemně se vylučující významy. Modifikátor `new` vytvoří nového člena se stejným názvem a způsobí, že původní člen bude skrytý. Modifikátor `override` rozšiřuje implementaci zděděného člena.

Použití modifikátoru `new` v deklaraci, která neskrývá zděděný člen, vygeneruje upozornění.

## <a name="example"></a>Příklad

V tomto příkladu základní třída, `BaseC`a odvozená třída `DerivedC`, používají stejný název pole `x`, který skrývá hodnotu zděděného pole. Příklad ukazuje použití modifikátoru `new`. Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Příklad

V tomto příkladu vnořená Třída skrývá třídu, která má stejný název v základní třídě. Příklad ukazuje, jak použít modifikátor `new` k eliminaci zprávy upozornění a o tom, jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Pokud odeberete modifikátor `new`, program se stále zkompiluje a spustí, ale zobrazí se toto upozornění:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [Správa verzí pomocí klíčových slov override a new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Znalost, kdy použít klíčová slova override a new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
