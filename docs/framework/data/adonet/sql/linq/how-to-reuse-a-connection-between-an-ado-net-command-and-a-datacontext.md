---
title: 'Postupy: Opakované použití propojení mezi příkazem ADO.NET a položkou DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033693"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="bda25-102">Postupy: Opakované použití propojení mezi příkazem ADO.NET a položkou DataContext</span><span class="sxs-lookup"><span data-stu-id="bda25-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="bda25-103">Protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je součástí [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] řady technologií a je založena na služby poskytované [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], můžete znovu použít pro připojení [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkazu a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="bda25-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bda25-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bda25-104">Example</span></span>  
 <span data-ttu-id="bda25-105">Následující příklad ukazuje, jak znovu použít stejné připojení mezi [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] příkazu a <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="bda25-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bda25-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bda25-106">See also</span></span>

- [<span data-ttu-id="bda25-107">Základní informace</span><span class="sxs-lookup"><span data-stu-id="bda25-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="bda25-108">ADO.NET a LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bda25-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="bda25-109">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="bda25-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
