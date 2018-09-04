---
title: Vytvoření vnořené skupiny (LINQ v JAZYKU C#)
description: Informace o vytvoření vnořené skupiny ve výrazu dotazu LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 82b07c303215200fa974ce614a2d5a77882dcf4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509965"
---
# <a name="create-a-nested-group"></a>Vytvoření vnořené skupiny

Následující příklad ukazuje, jak vytvářet vnořené skupiny ve výrazu dotazu LINQ. Každá skupina, která je vytvořena podle úrovně rok nebo na podnikové úrovni student je pak dále rozdělená do skupin na základě názvů pro osob.

## <a name="example"></a>Příklad

> [!NOTE]
> Obsahuje odkazy na objekty, které jsou definovány ve vzorovém kódu v tomto příkladu [dotazování na kolekci objektů](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Všimněte si, že tři vnořené `foreach` smyčky jsou nutné k iteraci přes vnitřní elementy vnořené skupiny.

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
