---
title: C# Arrays – prohlídka jazyka C#
description: Pole jsou nejzákladnějším typem kolekce v jazyce C#
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159192"
---
# <a name="arrays"></a>Pole

***Pole*** je datová struktura, která obsahuje řadu proměnných, které jsou přístupné prostřednictvím vypočítaných indexů. Proměnné obsažené v poli, nazývané také ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ prvku*** pole.

Typy polí jsou typy odkazů a deklarace proměnné pole jednoduše vyčlení prostor pro odkaz na instanci pole. Skutečné instance pole jsou vytvářeny dynamicky za běhu pomocí nového operátoru. Nová operace určuje ***délku*** nové instance pole, která je pak pevná po dobu životnosti instance. Indexy prvků rozsahu pole od `0` . `Length - 1` Operátor `new` automaticky inicializuje prvky pole na výchozí hodnotu, která je například `null` nulová pro všechny číselné typy a pro všechny typy odkazů.

Následující příklad vytvoří pole `int` prvků, inicializuje pole a vytiskne obsah pole.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Tento příklad vytvoří a pracuje na ***jednorozměrné pole***. C# také podporuje ***vícerozměrná pole***. Počet dimenzí typu pole, označovaný také jako ***pořadí*** typu pole, je jeden plus počet čárek zapsaných mezi hranatými závorkami typu pole. Následující příklad přiděluje jednorozměrné, dvojrozměrné a trojrozměrné pole.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Pole `a1` obsahuje 10 prvků, `a2` pole obsahuje 50 (10 × `a3` 5) prvků a pole obsahuje 100 (10 × 5 × 2) prvků.
Typ prvku pole může být libovolný typ, včetně typu pole. Pole s prvky typu pole se někdy nazývá ***zubaté pole,*** protože délky polí elementu nemusí být všechny stejné. Následující příklad přiděluje pole `int`polí :

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

První řádek vytvoří pole se třemi `int[]` prvky, každý typu `null`a každý s počáteční hodnotou . Následující řádky pak inicializovat tři prvky s odkazy na jednotlivé instance pole různých délek.

Nový operátor umožňuje zadat počáteční hodnoty prvků pole pomocí ***inicializátoru pole***, což je `{` seznam `}`výrazů napsaných mezi oddělovači a . Následující příklad přiděluje `int[]` a inicializuje se třemi prvky.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Délka pole je odvozena z počtu výrazů mezi { a }. Místní proměnné a pole deklarace lze zkrátit dále tak, aby typ pole není třeba přeformulovat.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Oba předchozí příklady jsou ekvivalentní následující kód:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Předchozí](classes-and-objects.md)
>[další](interfaces.md)
