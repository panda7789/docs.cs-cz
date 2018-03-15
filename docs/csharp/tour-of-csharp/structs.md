---
title: "C# struktury - přehled používání jazyka C#"
description: "Informace, že typů, názvem struktury hodnot Základy C#"
keywords: "Rozhraní .NET, C#, struktura, typu hodnoty"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: fa840d80bba98889f75863db2612f196d78bd3c5
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="structs"></a>Struktury

Jako jsou třídy, ***struktury*** jsou datové struktury, které mohou obsahovat členy data a funkce členy, ale na rozdíl od třídy, struktury, jsou typy hodnot a nevyžadují přidělení haldy. Proměnné typu Struktura přímo ukládá data struktura, zatímco proměnná typu třídy ukládá odkaz na objekt dynamicky přidělené. Struktura typy nepodporují dědičnosti definované uživatelem, a všechny typy struktura implicitně dědí od typu <xref:System.ValueType>, který v zapnout implicitně dědí z `object`.

Struktury jsou obzvláště užitečná pro malé datové struktury, které mají hodnotu sémantiku. Komplexní čísla, body v souřadnicový systém nebo páry klíč hodnota ve slovníku jsou všechny dobrými příklady struktury. Použití struktur místo třídy pro malé datové struktury provádět velký rozdíl v počtu přidělení paměti aplikace provede. Například následující program vytvoří a inicializuje pole 100 bodů. S `Point` implementována jako třída, 101 samostatných objektech instance – jednu pro pole a jeden pro 100 elementy.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Alternativou je aby bod struktury.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Nyní pouze jeden objekt je vytvořena instance – jednu pro pole – a `Point` instance jsou uložené v řádku v poli.

Konstruktory struktury jsou spuštěny se operátor new, ale neznamená, že paměť je právě přiděleny. Místo dynamické přidělování objektu a vrátí odkaz na jeho struktura konstruktor jednoduše vrátí hodnotu – struktura (obvykle do dočasného umístění v zásobníku) a tato hodnota je pak zkopíruje podle potřeby.

Pomocí třídy je možné pro dvě proměnné tak, aby odkazovaly na stejný objekt a proto možná pro operace na jednu proměnnou ovlivnit objekt odkazují jiné proměnné. S struktury proměnné každý mají své vlastní kopii dat a není možné pro operace na jeden, který bude mít vliv na druhý. Například výstup vytvořený podle následující fragment kódu závisí na tom bodu třídu nebo struktury.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Pokud `Point` je třída, výstup je 20, protože a b odkazují na stejný objekt. Pokud je bod struktury, výstup je 10, protože přiřazení `a` k `b` vytvoří kopii hodnoty, a tato kopie není ovlivněna následné přiřazení `a.x`.

Předchozí příklad označuje dvě omezení struktury. Nejprve kopírování celá struktura je obvykle míň efektivní než kopírování odkaz na objekt, takže předávání přiřazení a hodnota parametru může být nákladnější s struktury než s odkazové typy. Druhý, s výjimkou `in`, `ref`, a `out` parametry, není možné vytvořit odkazy na struktury, která pravidla se jejich využití v mnoha situacích.

>[!div class="step-by-step"]
[Předchozí](classes-and-objects.md)
[další](arrays.md)
