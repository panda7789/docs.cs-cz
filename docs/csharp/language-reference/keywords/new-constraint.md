---
description: New – Referenční dokumentace jazyka C#
title: New – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: f7b097729fe973aba7b85c48e1b1033aade83080
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139447"
---
# <a name="new-constraint-c-reference"></a>New – omezení (Referenční dokumentace jazyka C#)

`new`Omezení určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů. Chcete-li použít `new` omezení, typ nemůže být abstraktní.

Použijte `new` omezení na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Použijete-li `new()` omezení s jinými omezeními, musí být zadána jako poslední:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Další informace najdete v tématu [omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Klíčové slovo lze použít také `new` k [vytvoření instance typu](../operators/new-operator.md) nebo jako [Modifikátor deklarace člena](new-modifier.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Obecné typy](../../programming-guide/generics/index.md)
