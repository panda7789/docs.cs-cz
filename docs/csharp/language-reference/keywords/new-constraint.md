---
title: New – omezení - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 2aa68bec13322e332bfe3841bc99403f72301183
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421797"
---
# <a name="new-constraint-c-reference"></a>New – omezení (referenční dokumentace jazyka C#)

`new` Omezení určuje, že každý argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů. Typ omezení new použít, nemůže být abstraktní.

## <a name="example"></a>Příklad

Použít `new` omezení parametru typu, když obecné třídy vytvoří nové instance daného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a>Příklad

Při použití `new()` omezení s jinými omezeními, musí se zadat poslední:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Další informace najdete v tématu [omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Obecné typy](../../programming-guide/generics/index.md)
