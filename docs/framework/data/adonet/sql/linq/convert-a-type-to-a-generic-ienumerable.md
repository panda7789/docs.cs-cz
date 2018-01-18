---
title: "Převést typ na obecný IEnumerable"
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
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa15e1336c31aec47fb2255f224146b9ac7e429d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Převést typ na obecný IEnumerable
Použití <xref:System.Linq.Enumerable.AsEnumerable%2A> vrátit argument zadán jako obecný `IEnumerable`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (použití výchozí Obecné `Query`) se pokusit o převést dotaz SQL a spustit na serveru. Ale `where` klauzule odkazuje uživatelem definované metody na straně klienta (`isValidProduct`), který nelze převést na SQL.  
  
 Řešení je k určení obecného klienta <xref:System.Collections.Generic.IEnumerable%601> implementace `where` nahradit Obecné <xref:System.Linq.IQueryable%601>. To se provádí volání <xref:System.Linq.Enumerable.AsEnumerable%2A> operátor.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
