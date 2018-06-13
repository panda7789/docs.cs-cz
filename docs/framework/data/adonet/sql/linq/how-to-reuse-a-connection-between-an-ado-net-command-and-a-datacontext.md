---
title: 'Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 9618ffd3f6b1a050a4c47d1912b4612ce4031cd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352945"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="49f93-102">Postupy: opakované použití připojení mezi příkaz ADO.NET a DataContext</span><span class="sxs-lookup"><span data-stu-id="49f93-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="49f93-103">Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodiny technologií a služeb poskytovaných podle [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], můžete opakovaně použít připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="49f93-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49f93-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="49f93-104">Example</span></span>  
 <span data-ttu-id="49f93-105">Následující příklad ukazuje, jak znovu použít stejné připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkaz a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="49f93-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="49f93-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="49f93-106">See Also</span></span>  
 [<span data-ttu-id="49f93-107">Základní informace</span><span class="sxs-lookup"><span data-stu-id="49f93-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="49f93-108">ADO.NET a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="49f93-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [<span data-ttu-id="49f93-109">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="49f93-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
