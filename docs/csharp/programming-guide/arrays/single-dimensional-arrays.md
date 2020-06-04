---
title: Jednorozměrná pole – Průvodce programováním v C#
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410241"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Jednorozměrná pole (Průvodce programováním v C#)

Vytvoříte jednorozměrné pole pomocí operátoru [New](../../language-reference/operators/new-operator.md) , který určuje typ prvku pole a počet prvků. Následující příklad deklaruje pole pěti celých čísel:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

Toto pole obsahuje prvky z `array[0]` do `array[4]` . Prvky pole jsou inicializovány na výchozí hodnotu typu prvku `0` pro celá čísla.

Pole mohou ukládat jakýkoli typ prvku, který zadáte, například následující příklad, který deklaruje pole řetězců:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a>Inicializace pole

Při deklaraci pole můžete inicializovat prvky pole. Specifikátor délky není potřebný, protože je odvozený podle počtu prvků v inicializačním seznamu. Příklad:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

Následující kód ukazuje deklaraci pole řetězců, kde je každý element pole inicializován pomocí názvu dne:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
Můžete se vyhnout `new` výrazu a typu pole při inicializaci pole při deklaraci, jak je znázorněno v následujícím kódu. Toto se nazývá [implicitně typované pole](implicitly-typed-arrays.md):

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

Můžete deklarovat proměnnou pole bez jejího vytvoření, ale je nutné použít `new` operátor, pokud k této proměnné přiřadíte nové pole. Příklad:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a>Pole Typ hodnoty a odkazové typy

Zvažte následující deklaraci pole:  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

Výsledek tohoto příkazu závisí na tom, zda `SomeType` je typ hodnoty nebo typ odkazu. Pokud se jedná o typ hodnoty, příkaz vytvoří pole 10 prvků, z nichž každý má typ `SomeType` . Pokud `SomeType` je odkazový typ, příkaz vytvoří pole 10 prvků, z nichž každá je inicializována na odkaz s hodnotou null. V obou instancích jsou prvky inicializovány na výchozí hodnotu pro typ prvku. Další informace o typech hodnot a odkazových typech naleznete v tématu [typy hodnot](../../language-reference/builtin-types/value-types.md) a [odkazové typy](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Pole](./index.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
