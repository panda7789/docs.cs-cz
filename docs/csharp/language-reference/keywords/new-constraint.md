---
title: New – omezení - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401485"
---
# <a name="new-constraint-c-reference"></a>New – omezení (referenční dokumentace jazyka C#)

`new` Omezení určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů. Použít `new` omezení, typ nemůže být abstraktní.

Použít `new` omezení parametru typu, když obecné třídy vytvoří nové instance daného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Při použití `new()` omezení s jinými omezeními, musí se zadat poslední:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Další informace najdete v tématu [omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md).

Můžete také použít `new` – klíčové slovo do [vytvořit instanci typu](../operators/new-operator.md) nebo stejně jako [modifikátoru deklarace člena](new-modifier.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [omezení parametru typu](~/_csharplang/spec/classes.md#type-parameter-constraints) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Obecné typy](../../programming-guide/generics/index.md)
