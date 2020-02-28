---
title: C#Pole – prohlídka C# jazyka
description: Pole jsou nejzákladnější typ kolekce v C# jazyce.
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159192"
---
# <a name="arrays"></a>Pole

***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů. Proměnné obsažené v poli, označované také jako ***prvky*** pole, jsou všechny stejného typu a tento typ se nazývá ***typ elementu*** pole.

Typy polí jsou odkazové typy a deklarace proměnné pole jednoduše nastaví volné místo pro odkaz na instanci pole. Skutečné instance pole jsou vytvářeny dynamicky za běhu pomocí operátoru new. Nová operace určuje ***délku*** nové instance pole, která je poté opravena po dobu života instance. Indexy prvků rozsahu pole od `0` do `Length - 1`. Operátor `new` automaticky inicializuje prvky pole na výchozí hodnotu, což je například nula pro všechny číselné typy a `null` pro všechny typy odkazů.

Následující příklad vytvoří pole `int` prvky, inicializuje pole a vytiskne obsah pole.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Tento příklad vytvoří a pracuje na jednorozměrném ***poli***. C#podporuje rovněž ***multidimenzionální pole***. Počet rozměrů typu pole, označovaný také jako ***rozměr*** typu pole, je jedna plus počet čárek napsaných mezi hranatými závorkami typu pole. Následující příklad přiděluje jednorozměrné, dvojrozměrné a trojrozměrné pole v uvedeném pořadí.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Pole `a1` obsahuje 10 prvků, pole `a2` obsahuje 50 (10 × 5) prvků a pole `a3` obsahuje 100 (10 × 5 × 2) prvků.
Typ elementu pole může být libovolný typ, včetně typu pole. Pole s prvky typu pole se někdy nazývá ***vícenásobné pole*** , protože délky polí elementů nemusí být stejné. Následující příklad přiděluje pole polí `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

První řádek vytvoří pole se třemi prvky, každou typu `int[]` a každý s počáteční hodnotou `null`. Následující řádky poté inicializují tři prvky s odkazy na jednotlivé instance pole s různou délkou.

Operátor New umožňuje zadat počáteční hodnoty prvků pole pomocí ***inicializátoru pole***, což je seznam výrazů zapsaných mezi oddělovači `{` a `}`. Následující příklad přiděluje a inicializuje `int[]` se třemi prvky.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Délka pole je odvozená od počtu výrazů mezi {a}. Deklarace lokální proměnné a pole lze dále zkrátit tak, aby se typ pole nemuselo přestavit.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Oba předchozí příklady jsou ekvivalentní následujícímu kódu:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Předchozí](classes-and-objects.md)
>[Další](interfaces.md)
