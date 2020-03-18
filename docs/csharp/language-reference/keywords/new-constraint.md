---
title: nové omezení – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713358"
---
# <a name="new-constraint-c-reference"></a>nové omezení (odkaz Jazyka C#)

Omezení `new` určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů. Chcete-li `new` použít omezení, typ nemůže být abstraktní.

Použijte `new` omezení na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Při použití `new()` omezení s jinými omezeními musí být zadáno jako poslední:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Další informace naleznete [v tématu Omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Klíčové slovo můžete také použít k [vytvoření instance typu](../operators/new-operator.md) nebo jako [modifikátor deklarace člena](new-modifier.md). `new`

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Obecné typy](../../programming-guide/generics/index.md)
