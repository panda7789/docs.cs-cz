---
title: "Řazení výsledků klauzule join"
description: "Postup řazení výsledků klauzule join."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a>Řazení výsledků klauzule join
Tento příklad ukazuje postup řazení výsledků operace spojení. Všimněte si, že je po spojení provést řazení. Přestože je možné použít `orderby` klauzule s jedním nebo více zdroje pořadí před spojení, obecně nedoporučujeme ji. Někteří poskytovatelé LINQ nemusí zachovat řazení po spojení.  
  
## <a name="example"></a>Příklad  
 Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny založené na kategorii element, který je stále v oboru. Uvnitř inicializátoru anonymního typu poddotazu řadí všechny odpovídající elementy z produktů pořadí.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [OrderBy – klauzule](../language-reference/keywords/orderby-clause.md)  
 [JOIN – klauzule](../language-reference/keywords/join-clause.md) 
