---
title: 'Postupy: Načtení informací o konfliktech členů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793302"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="4e86b-102">Postupy: Načtení informací o konfliktech členů</span><span class="sxs-lookup"><span data-stu-id="4e86b-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="4e86b-103"><xref:System.Data.Linq.MemberChangeConflict> Třídu můžete použít k načtení informací o jednotlivých členech v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="4e86b-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="4e86b-104">V tomto stejném kontextu můžete poskytnout vlastní zpracování konfliktu pro libovolného člena.</span><span class="sxs-lookup"><span data-stu-id="4e86b-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="4e86b-105">Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e86b-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e86b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e86b-106">Example</span></span>  
 <span data-ttu-id="4e86b-107">Následující kód prochází <xref:System.Data.Linq.ObjectChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="4e86b-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="4e86b-108">Pro každý objekt pak prochází <xref:System.Data.Linq.MemberChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="4e86b-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e86b-109">Zahrňte <xref:System.Reflection> do poskytování <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informací.</span><span class="sxs-lookup"><span data-stu-id="4e86b-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4e86b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e86b-110">See also</span></span>

- [<span data-ttu-id="4e86b-111">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="4e86b-111">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
