---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 10c74ede8d490bf96a9d0855889669bdc2628b01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785356"
---
# <a name="constant-expressions"></a>Výrazy konstant
Konstantní výraz se skládá z konstantní hodnotu. Konstantní hodnoty jsou přímo převést na strom výrazů konstantní příkazový, bez překladu na straně klienta. To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu. Proto by měl očekávat chování zdroje dat pro všechny výrazy zahrnující konstanty. Výsledkem může být chování, které se liší od chování modulu CLR.  
  
 Následující příklad ukazuje konstantní výraz, který je vyhodnocován na serveru.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] nepodporuje použití třídy uživatelů jako konstanta. Však odkaz na vlastnost ve třídě uživatele je považován za konstantu a bude převeden na příkaz konstantní výraz stromu a ve zdroji dat.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
