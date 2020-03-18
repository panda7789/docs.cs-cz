---
title: Vytvoření vnořené skupiny (LINQ v C#)
description: Zjistěte, jak vytvořit vnořenou skupinu ve výrazu dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688615"
---
# <a name="create-a-nested-group"></a>Vytvoření vnořené skupiny

Následující příklad ukazuje, jak vytvořit vnořené skupiny ve výrazu dotazu LINQ. Každá skupina, která je vytvořena podle studentského roku nebo stupně úrovně je pak dále rozdělena do skupin na základě jmen jednotlivců .

## <a name="example"></a>Příklad

> [!NOTE]
> Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [aplikaci Query a collection of objects](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Všimněte si, `foreach` že tři vnořené smyčky jsou vyžadovány k iteraci přes vnitřní prvky vnořené skupiny.

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
