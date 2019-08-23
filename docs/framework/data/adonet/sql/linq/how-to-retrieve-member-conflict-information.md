---
title: 'Postupy: Načtení informací o konfliktech členů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928636"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="a0c26-102">Postupy: Načtení informací o konfliktech členů</span><span class="sxs-lookup"><span data-stu-id="a0c26-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="a0c26-103"><xref:System.Data.Linq.MemberChangeConflict> Třídu můžete použít k načtení informací o jednotlivých členech v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="a0c26-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="a0c26-104">V tomto stejném kontextu můžete poskytnout vlastní zpracování konfliktu pro libovolného člena.</span><span class="sxs-lookup"><span data-stu-id="a0c26-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="a0c26-105">Další informace najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a0c26-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c26-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c26-106">Example</span></span>  
 <span data-ttu-id="a0c26-107">Následující kód prochází <xref:System.Data.Linq.ObjectChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="a0c26-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="a0c26-108">Pro každý objekt pak prochází <xref:System.Data.Linq.MemberChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="a0c26-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0c26-109">Zahrňte <xref:System.Reflection> do poskytování <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informací.</span><span class="sxs-lookup"><span data-stu-id="a0c26-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a0c26-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0c26-110">See also</span></span>

- [<span data-ttu-id="a0c26-111">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="a0c26-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
