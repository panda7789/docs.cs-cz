---
title: 'Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 079b4b28a613ce6a9ae525514b89ea9e316a7c66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613672"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="eb907-102">Postupy: Opakované použití připojení mezi příkazem ADO.NET a položkou DataContext</span><span class="sxs-lookup"><span data-stu-id="eb907-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="eb907-103">Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řady technologií a je založena na služby poskytované [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], můžete znovu použít pro připojení [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkazu a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="eb907-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb907-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb907-104">Example</span></span>  
 <span data-ttu-id="eb907-105">Následující příklad ukazuje, jak znovu použít stejné připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkazu a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="eb907-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="eb907-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb907-106">See also</span></span>
- [<span data-ttu-id="eb907-107">Základní informace</span><span class="sxs-lookup"><span data-stu-id="eb907-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="eb907-108">ADO.NET a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="eb907-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="eb907-109">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="eb907-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
