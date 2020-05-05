---
title: nový modifikátor – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795167"
---
# <a name="new-modifier-c-reference"></a>New – modifikátor (Referenční dokumentace jazyka C#)

Při použití jako modifikátoru deklarace `new` klíčová slova explicitně skrývá člen, který je zděděn ze základní třídy. Když skryjete zděděného člena, odvozená verze člena nahradí verzi základní třídy. I když můžete členy skrýt bez použití `new` modifikátoru, zobrazí se upozornění kompilátoru. Pokud použijete `new` příkaz k explicitnímu skrytí člena, potlačí se toto upozornění.

`new` Klíčové slovo lze použít také k [vytvoření instance typu](../operators/new-operator.md) nebo jako [omezení obecného typu](./new-constraint.md).

Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu člena a upravte jej pomocí `new` klíčového slova. Příklad:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

V tomto příkladu `BaseC.Invoke` je skrytý nástrojem `DerivedC.Invoke`. Pole `x` není ovlivněno, protože není skryto podobným názvem.

Název skrývání prostřednictvím dědičnosti má jednu z následujících forem:

- Obecně konstanta, pole, vlastnost nebo typ, který je představen ve třídě nebo struktuře, skrývá všechny členy základní třídy, které sdílejí svůj název. Existují zvláštní případy. Například pokud deklarujete nové pole s názvem `N` , které má typ, který není nevyvolatelný, a základní typ deklaruje `N` jako metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání. Další informace naleznete v oddílu [vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

- Metoda zavedená ve třídě nebo struktuře skrývá vlastnosti, pole a typy, které sdílejí tento název v základní třídě. Také skryje všechny metody základní třídy, které mají stejnou signaturu.

- Indexer zavedený ve třídě nebo struktuře skrývá všechny základní třídy indexerů, které mají stejnou signaturu.

Při použití `new` i [přepsání](override.md) u stejného člena se jedná o chybu, protože dva modifikátory mají vzájemně exkluzivní význam. `new` Modifikátor vytvoří nového člena se stejným názvem a způsobí, že původní člen bude skrytý. `override` Modifikátor rozšiřuje implementaci pro zděděného člena.

Použití `new` modifikátoru v deklaraci, která neskrývá zděděný člen, vygeneruje upozornění.

## <a name="example"></a>Příklad

V tomto příkladu základní třída, `BaseC`a odvozená třída `DerivedC`, používá stejný název `x`pole, který skrývá hodnotu zděděného pole. Příklad demonstruje použití `new` modifikátoru. Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Příklad

V tomto příkladu vnořená Třída skrývá třídu, která má stejný název v základní třídě. Tento příklad ukazuje, jak použít `new` modifikátor k odstranění zprávy upozornění a o tom, jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Pokud tento `new` modifikátor odeberete, program se stále zkompiluje a spustí, ale zobrazí se toto upozornění:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [Správa verzí pomocí klíčových slov override a new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Znalost, kdy použít klíčová slova override a new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
