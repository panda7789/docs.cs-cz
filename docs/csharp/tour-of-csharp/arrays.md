---
title: C# pole - přehled používání jazyka C#
description: Pole jsou nejzákladnější typ kolekce v jazyce C#
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: c0fe65348ab2d41852ed9150571dcb0e5b8553f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351002"
---
# <a name="arrays"></a>Pole

***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou přístupné prostřednictvím počítaný indexy. Proměnné, které jsou obsaženy v poli, označované taky jako ***elementy*** pole, jsou všechny stejného typu a se nazývá tento typ ***typ elementu*** pole.

Typy polí jsou odkazové typy a deklarace proměnné pole jednoduše vyčleňuje místa pro odkaz na pole instance. Skutečné pole vytváření instancí dynamicky za běhu pomocí nové operátoru. Určuje operaci nového ***délka*** nové pole instance, kterou pak vyřešen po dobu jeho existence instance. Indexy elementů rozsah pole z `0` k `Length - 1`. `new` Operátor automaticky inicializuje prvků pole na jejich výchozí hodnoty, které je třeba nulu pro všechny číselnými typy a `null` pro všechny typy odkazů.

Následující příklad vytvoří pole `int` elementy, inicializuje pole a vytiskne obsah pole.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Tento příklad vytvoří a bude pracovat ***jednorozměrná pole***. C# také podporuje ***vícerozměrných polí***. Zadejte počet rozměrů pole, také známé jako ***pořadí*** typ pole, je jedna plus počet čárkami zapsána mezi hranaté závorky typu pole. Následující příklad přiděluje jednorozměrná, dvourozměrná a trojrozměrné, v uvedeném pořadí.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Pole obsahuje prvky, 10, `a2` pole obsahuje 50 (10 × 5) elementů a `a3` 100 (10 × 5 × 2) obsahuje pole elementy.
Typ elementu typu pole mohou být jakéhokoli typu, včetně typu pole. Pole s prvky typu pole se někdy nazývá ***Vícenásobná pole*** protože ne všechny délek element pole mají být stejné. Následující příklad přiděluje pole pole `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

První řádek vytvoří pole u elementů na tři, každý typ `int[]` a každý s počáteční hodnotou `null`. Další řádek potom inicializujte tři prvky s odkazy na pole jednotlivých instancí různých délek.

Operátor new umožňuje počáteční hodnoty prvků pole, které mají být zadán pomocí ***inicializátor pole***, což je seznam výrazů zapsána mezi oddělovače `{` a `}`. V následujícím příkladu přiděluje a inicializuje `int[]` s tři prvky.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Všimněte si, že je délka pole odvodit z počet výrazů mezi {a}. Místní proměnné a deklarace pole lze zkrátit další tak, aby typ pole není nutné nutno revidovat.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Obě v předchozích příkladech jsou ekvivalentní takto:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
[Předchozí](structs.md)
[další](interfaces.md)
