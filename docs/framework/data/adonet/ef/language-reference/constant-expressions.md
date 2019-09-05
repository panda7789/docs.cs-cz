---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: b31cd881f1307ec734c026d3c873d7a650e19a20
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251135"
---
# <a name="constant-expressions"></a>Výrazy konstant
Konstantní výraz se skládá z konstantní hodnoty. Konstantní hodnoty jsou přímo převedeny na konstantní výrazy stromu příkazů bez jakéhokoli překladu na klienta. To zahrnuje výrazy, které mají za následek konstantní hodnotu. Proto by mělo být očekávané chování zdroje dat pro všechny výrazy, které obsahují konstanty. To může mít za následek chování, které se liší od chování CLR.  
  
 Následující příklad ukazuje konstantní výraz, který je vyhodnocen na serveru.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities nepodporuje použití třídy uživatele jako konstanty. Odkaz na vlastnost třídy uživatele se však považuje za konstantu a bude převeden na výraz konstantního stromu příkazů a proveden ve zdroji dat.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy v dotazech LINQ to Entities](expressions-in-linq-to-entities-queries.md)
