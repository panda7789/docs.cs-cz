---
title: Vytvoření vnořené skupiny (LINQ v JAZYKU C#)
description: Informace o vytvoření vnořené skupiny ve výrazu dotazu LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857668"
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
