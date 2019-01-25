---
title: Řazení výsledků klauzule join (LINQ v JAZYKU C#)
description: Zjistěte, jak řazení výsledků klauzule join LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: 7ab9c2ade4029e64d47840ef8dece8e1280d5669
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589292"
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
