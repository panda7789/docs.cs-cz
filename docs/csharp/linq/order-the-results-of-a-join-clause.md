---
title: Řazení výsledků klauzule join (LINQ v JAZYKU C#)
description: Zjistěte, jak řazení výsledků klauzule join LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: e4a12b6f9b4a99decb1f64524ebe67a196084a04
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404733"
---
# <a name="order-the-results-of-a-join-clause"></a>Řazení výsledků klauzule join

Tento příklad ukazuje způsob řazení výsledků operace spojení. Všimněte si, že řazení se provádí po spojení. Přestože lze použít `orderby` klauzule s jedním nebo více zdroji pořadí před spojení, obecně nedoporučujeme to. Někteří poskytovatelé LINQ nemusí zachovávají řazení po spojení.

## <a name="example"></a>Příklad

Tento dotaz vytvoří spojení skupiny a pak seřadí podle kategorie element, který je stále v oboru skupiny. Uvnitř inicializátor anonymního typu orders poddotazu odpovídajících prvků z posloupnosti produktů.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Viz také:

[LINQ (Language Integrated Query)](index.md)  
[orderby – klauzule](../language-reference/keywords/orderby-clause.md)  
[join – klauzule](../language-reference/keywords/join-clause.md)  