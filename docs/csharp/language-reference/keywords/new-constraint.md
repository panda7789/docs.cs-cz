---
title: nové omezení – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713358"
---
# <a name="new-constraint-c-reference"></a>New – omezeníC# (Referenční dokumentace)

Omezení `new` určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů. Chcete-li použít omezení `new`, typ nemůže být abstraktní.

Použijte omezení `new` na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Použijete-li omezení `new()` s jinými omezeními, je nutné ji zadat jako poslední:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Další informace najdete v tématu [omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Pomocí klíčového slova `new` lze také [vytvořit instanci typu](../operators/new-operator.md) nebo jako [Modifikátor deklarace členů](new-modifier.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Obecné typy](../../programming-guide/generics/index.md)
