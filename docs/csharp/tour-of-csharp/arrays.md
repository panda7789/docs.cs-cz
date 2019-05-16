---
title: C#Pole – připravuje C# jazyka
description: Pole jsou v základním typem kolekce C# jazyka
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 56a053ac8525d4c6c34592d6092f3f162cb04247
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634608"
---
# <a name="arrays"></a>Pole

***Pole*** je datová struktura, která obsahuje několik proměnných, které jsou přístupné prostřednictvím vypočítané indexy. Proměnné, které jsou obsaženy v poli, tzv. ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ elementu*** pole.

Typy pole jsou typy odkazů a deklarace proměnné pole jednoduše vyčleňuje místo odkazu na pole instance. Dynamicky se vytvářejí instance skutečné pole za běhu pomocí operátoru new. Určuje novou operaci ***délka*** nové instance pole, které se potom jsme opravili po dobu životnosti instance. Indexy prvků v rozsahu pole z `0` k `Length - 1`. `new` Operátor automaticky inicializuje prvků pole na výchozí hodnoty, které je třeba nulu pro všechny číselné typy a `null` pro všechny typy odkazů.

Následující příklad vytvoří pole `int` prvky, inicializuje pole a vytiskne obsah pole.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Tento příklad vytvoří a pracuje ***jednorozměrné pole***. C# rovněž podporuje ***vícerozměrných polí***. Zadejte počet rozměrů pole, označované také jako ***pořadí*** typ pole je jednu plus počet čárek mezi hranaté závorky pole zapsána. Následující příklad přiděluje jednorozměrná dvourozměrném a trojrozměrného pole.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Pole obsahuje 10 prvků `a2` pole obsahuje 50 (10 × 5) elementy a `a3` 100 (10 × 5 × 2) obsahuje pole prvků.
Typ elementu pole může být libovolného typu, včetně typu pole. Někdy se označuje jako pole s prvky typu pole ***vícenásobného pole*** protože ne všechny délky pole elementu mají být stejné. V následujícím příkladu se přiděluje pole polí `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

První řádek vytvoří pole se třemi prvky, každý typ `int[]` a každý s počáteční hodnotou `null`. Následující řádky následně inicializujete tři prvky s odkazy na jednotlivá pole instancí z různých délek.

Operátor new povoluje počáteční hodnoty prvků pole zadat pomocí ***inicializátor pole***, což je seznamem výrazů napsané mezi oddělovači `{` a `}`. V následujícím příkladu se přiděluje a inicializuje `int[]` s tři elementy.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Všimněte si, že délka pole je odvozen z počet výrazů mezi {a}. Lokální proměnná a pole deklarace lze zkrátit další tak, aby typ pole nemusí být revidovat.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Obě předchozí příklady jsou ekvivalentní následujícímu zápisu:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Předchozí](structs.md)
>[další](interfaces.md)
