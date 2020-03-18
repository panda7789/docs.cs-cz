---
title: nový modifikátor - Odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713334"
---
# <a name="new-modifier-c-reference"></a>nový modifikátor (Odkaz C#

Při použití jako modifikátor deklarace `new` klíčové slovo explicitně skryje člen, který je zděděn ze základní třídy. Když skryjete zděděný člen, odvozená verze člena nahradí verzi základní třídy. I když můžete skrýt `new` členy bez použití modifikátoru, dostanete upozornění kompilátoru. Pokud slouží `new` k explicitnímu skrytí člena, potlačí toto upozornění.

Klíčové slovo můžete také použít k vytvoření instance typu nebo jako [omezení obecného typu](./new-constraint.md). [create an instance of a type](../operators/new-operator.md) `new`

Chcete-li skrýt zděděný člen, deklarujte jej v odvozené `new` třídě pomocí stejného názvu člena a upravte jej pomocí klíčového slova. Například:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

V tomto `BaseC.Invoke` příkladu `DerivedC.Invoke`je skrytý . Pole `x` není ovlivněno, protože není skryto podobným názvem.

Název skrytí prostřednictvím dědičnosti má jednu z následujících forem:

- Obecně konstanta, pole, vlastnost nebo typ, který je zaveden ve třídě nebo struktuře, skryje všechny členy základní třídy, kteří sdílejí jeho název. Existují zvláštní případy. Pokud například deklarujete `N` nové pole s názvem typu, který není neodvolatelný, a základní typ deklaruje `N` jako metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání. Další informace naleznete v části [Vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

- Metoda zavedená ve třídě nebo struktuře skryje vlastnosti, pole a typy, které sdílejí tento název v základní třídě. Také skryje všechny metody základní třídy, které mají stejný podpis.

- Indexer zavedený ve třídě nebo struktuře skryje všechny indexery základní třídy, které mají stejný podpis.

Je chyba použít oba `new` a [přepsat](override.md) na stejný člen, protože dva modifikátory mají vzájemně se vylučující významy. Modifikátor `new` vytvoří nový člen se stejným názvem a způsobí, že původní člen se stane skrytým. Modifikátor `override` rozšiřuje implementaci pro zděděný člen.

Použití `new` modifikátor v deklaraci, která neskrývá zděděný člen generuje upozornění.

## <a name="example"></a>Příklad

V tomto příkladu základní `BaseC`třída , a `DerivedC`odvozené třídy `x`, použijte stejný název pole , který skryje hodnotu zděděného pole. Příklad ukazuje použití modifikátoru. `new` Také ukazuje, jak získat přístup ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Příklad

V tomto příkladu vnořená třída skryje třídu, která má stejný název v základní třídě. Příklad ukazuje, jak pomocí `new` modifikátoru eliminovat varovné zprávy a jak získat přístup ke skrytým členům třídy pomocí jejich plně kvalifikované názvy.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Pokud `new` modifikátor odeberete, program se bude stále zkompilovat a spustit, ale zobrazí se následující upozornění:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v části Nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
- [Správa verzí pomocí klíčových slov override a new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Znalost, kdy použít klíčová slova override a new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
