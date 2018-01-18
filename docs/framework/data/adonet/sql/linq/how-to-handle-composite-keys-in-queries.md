---
title: "Postupy: zpracování složené klíče v dotazech."
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
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0267cba0d20ac77a938c64cfa87e750f690471f8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Postupy: zpracování složené klíče v dotazech.
Některé operátory může trvat jenom jeden argument. Pokud váš argument musí obsahovat více než jeden sloupec z databáze, musíte vytvořit anonymní typ představují kombinaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz, který volá `GroupBy` operátor, který můžete provést pouze jednu `key` argument.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Stejná situace se vztahují na spojení, jako v následujícím příkladu:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
