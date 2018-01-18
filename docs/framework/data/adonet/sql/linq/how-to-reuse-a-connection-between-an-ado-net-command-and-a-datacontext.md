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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 196b3c8735168ea935aa1a0d3917dd34b2aa390f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
