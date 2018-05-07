---
title: Řazení výsledků klauzule join
description: Postup řazení výsledků klauzule join.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="order-the-results-of-a-join-clause"></a>Řazení výsledků klauzule join
Tento příklad ukazuje postup řazení výsledků operace spojení. Všimněte si, že je po spojení provést řazení. Přestože je možné použít `orderby` klauzule s jedním nebo více zdroje pořadí před spojení, obecně nedoporučujeme ji. Někteří poskytovatelé LINQ nemusí zachovat řazení po spojení.  
  
## <a name="example"></a>Příklad  
 Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny založené na kategorii element, který je stále v oboru. Uvnitř inicializátoru anonymního typu poddotazu řadí všechny odpovídající elementy z produktů pořadí.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [orderby – klauzule](../language-reference/keywords/orderby-clause.md)  
 [join – klauzule](../language-reference/keywords/join-clause.md) 
