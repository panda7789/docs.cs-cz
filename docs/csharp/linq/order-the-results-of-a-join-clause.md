---
title: Pořadívýsledků join klauzule (LINQ v C#)
description: Přečtěte si, jak objednat výsledky klauzule linq spojení v C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659862"
---
# <a name="order-the-results-of-a-join-clause"></a>Řazení výsledků klauzule join

Tento příklad ukazuje, jak objednat výsledky operace spojení. Všimněte si, že řazení se provádí po spojení. I když můžete `orderby` použít klauzuli s jedním nebo více zdrojových sekvencí před spojením, obecně nedoporučujeme. Někteří zprostředkovatelé LINQ nemusí zachovat toto řazení po spojení.

## <a name="example"></a>Příklad

Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny na základě prvku kategorie, který je stále v oboru. Uvnitř anonymní typ inicializátoru, dílčí dotaz objednávky všechny odpovídající prvky z řady produktů.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
- [orderby – klauzule](../language-reference/keywords/orderby-clause.md)
- [spojit klauzuli](../language-reference/keywords/join-clause.md)
