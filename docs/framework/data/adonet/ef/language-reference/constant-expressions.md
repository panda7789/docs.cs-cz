---
title: "Výrazy konstant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ccc54df7a69db8186c653afb415a5679b65ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="constant-expressions"></a>Výrazy konstant
Konstantní výraz se skládá z konstantní hodnotu. Konstantní hodnoty jsou přímo převést na příkaz konstantní výrazy stromu, bez překladu na straně klienta. To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu. Chování zdroje dat by měl být tedy, že pro všechny výrazy zahrnující konstanty. To může mít za následek chování, které se liší od chování CLR.  
  
 Následující příklad ukazuje konstantní výraz, který se vyhodnotí na serveru.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]nepodporuje použití třídy uživatele jako konstanta. Však odkaz na vlastnost třídy uživatel se považuje za konstantu a budou převést na strom příkaz konstantní výraz a ve zdroji dat.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
