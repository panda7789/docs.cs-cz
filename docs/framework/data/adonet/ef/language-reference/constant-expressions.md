---
title: Výrazy konstant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: cc3a214a2faa06c79ee0794b0158381bff0c4b0b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539887"
---
# <a name="constant-expressions"></a>Výrazy konstant
Konstantní výraz se skládá z konstantní hodnotu. Konstantní hodnoty jsou přímo převést na strom výrazů konstantní příkazový, bez překladu na straně klienta. To zahrnuje výrazy, jejichž výsledkem konstantní hodnotu. Proto by měl očekávat chování zdroje dat pro všechny výrazy zahrnující konstanty. Výsledkem může být chování, které se liší od chování modulu CLR.  
  
 Následující příklad ukazuje konstantní výraz, který je vyhodnocován na serveru.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 Technologie LINQ to Entities nepodporuje použití třídy uživatelů jako konstanta. Však odkaz na vlastnost ve třídě uživatele je považován za konstantu a bude převeden na příkaz konstantní výraz stromu a ve zdroji dat.  
  
## <a name="see-also"></a>Viz také:

- [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
