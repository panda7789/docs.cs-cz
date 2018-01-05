---
title: "Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext"
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
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8cf28a7535cb09946654d4fb43b2f5567fff40c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext
Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodiny technologií a služeb poskytovaných podle [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], můžete opakovaně použít připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak znovu použít stejné připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [ADO.NET a LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
