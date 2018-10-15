---
title: C# struktury – prohlídka jazyka C#
description: Přečtěte si, že se že se základy C# hodnoty typů nazývaných struktury
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: 2b1870713b488f706f5f3a54413461052173bab6
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49323094"
---
# <a name="structs"></a>Struktury

Třídy, jako jsou ***struktury*** datové struktury, které mohou obsahovat datové členy a funkční členy jsou, ale na rozdíl od tříd, struktur jsou typy hodnot a nevyžadují přidělení haldy. Proměnné typu Struktura přímo ukládá datové struktury, že proměnné typu třída uchovává odkaz na do dynamicky alokovaného objektu. Typy struktury nepodporují dědičnosti zadané uživatelem, a všechny typy struktury implicitně dědí z typu <xref:System.ValueType>, což následně bude implicitně dědí z `object`.

Struktury jsou zvláště užitečná pro malé datové struktury, které mají hodnotu sémantiku. Komplexní čísla, body v souřadnicovém systému nebo páry klíč hodnota do slovníku jsou všechny dobrým příkladem struktury. Použití struktur, místo třídy pro malé datové struktury mohou přinést důležité velký počet přidělení paměti aplikace provádí. Například následující program vytvoří a inicializuje pole 100 bodů. S `Point` implementován jako třída, 101 samostatné objekty jsou vytvořena instance – jednu pro pole a jeden pro 100 elementů.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Alternativou je, aby bod struktury.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Nyní pouze jeden objekt je vytvořena instance – jednu pro pole – a `Point` instance jsou uložené v řádku v poli.

Konstruktory struktury jsou vyvolány pomocí `new` operátoru, podobně jako konstruktor třídy. Ale namísto dynamického přidělování objektu na spravované haldě a vrátí na ni odkaz, konstruktor struktury jednoduše vrací hodnotu – struktura (obvykle do dočasného umístění v zásobníku) a tato hodnota se pak zkopíruje podle potřeby.

Pomocí třídy je možné pro dvě proměnné odkazovat na stejný objekt a proto je možné pro operace v rámci jedné proměnné ovlivňovat objekt odkazovaný jinou proměnnou. Struktury proměnné každý mají své vlastní kopii dat, a není možné pro operace se na nich se má vliv na jinou. Například výstup vytvořený podle následující fragment kódu závisí na tom bod třídy nebo struktury.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Pokud `Point` je třída, výstup je 20, protože a b odkazovat na stejný objekt. Pokud bod je struktura, výstup je 10, protože přiřazení `a` k `b` vytvoří kopii hodnoty, a tuto kopii není ovlivněn následné přiřazení `a.x`.

Předchozí příklad ukazuje dvě omezení struktury. Kopírování celé struktury je poprvé, obvykle méně efektivní než odkaz na objekt, kopírování, předávání přiřazení a hodnota parametru může být dražší s struktury než s typy odkazů. Druhý, s výjimkou `in`, `ref`, a `out` parametry, není možné vytvořit odkazy na struktury, který vylučuje jejich použití v mnoha situacích.

>[!div class="step-by-step"]
[Předchozí](classes-and-objects.md)
[další](arrays.md)
