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
ms.openlocfilehash: 483a97817162140af61df6a58c3e9ab003235c74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="31068-102">Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="31068-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="31068-103">Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodiny technologií a služeb poskytovaných podle [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], můžete opakovaně použít připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="31068-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31068-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="31068-104">Example</span></span>  
 <span data-ttu-id="31068-105">Následující příklad ukazuje, jak znovu použít stejné připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="31068-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="31068-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="31068-106">See Also</span></span>  
 [<span data-ttu-id="31068-107">Základní informace</span><span class="sxs-lookup"><span data-stu-id="31068-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="31068-108">ADO.NET a technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="31068-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [<span data-ttu-id="31068-109">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="31068-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
