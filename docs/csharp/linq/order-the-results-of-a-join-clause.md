---
title: Řazení výsledků klauzule join (LINQ v JAZYKU C#)
description: Zjistěte, jak řazení výsledků klauzule join LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659862"
---
# <a name="order-the-results-of-a-join-clause"></a>Řazení výsledků klauzule join

Tento příklad ukazuje způsob řazení výsledků operace spojení. Všimněte si, že řazení se provádí po spojení. Přestože lze použít `orderby` klauzule s jedním nebo více zdroji pořadí před spojení, obecně nedoporučujeme to. Někteří poskytovatelé LINQ nemusí zachovávají řazení po spojení.

## <a name="example"></a>Příklad

Tento dotaz vytvoří spojení skupiny a pak seřadí podle kategorie element, který je stále v oboru skupiny. Uvnitř inicializátor anonymního typu orders poddotazu odpovídajících prvků z posloupnosti produktů.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
- [orderby – klauzule](../language-reference/keywords/orderby-clause.md)
- [join – klauzule](../language-reference/keywords/join-clause.md)
