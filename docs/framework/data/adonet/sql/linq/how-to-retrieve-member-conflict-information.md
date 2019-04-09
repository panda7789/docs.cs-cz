---
title: 'Postupy: Načtení informací o konfliktech členů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: fae1513e7a7ead98318d907b220b7510758c9ffe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115086"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="9bf5a-102">Postupy: Načtení informací o konfliktech členů</span><span class="sxs-lookup"><span data-stu-id="9bf5a-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="9bf5a-103">Můžete použít <xref:System.Data.Linq.MemberChangeConflict> třídy k načtení informací o jednotlivých členů v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="9bf5a-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="9bf5a-104">V tomto kontextu stejné můžete zadat vlastní zpracování konflikt pro žádného člena.</span><span class="sxs-lookup"><span data-stu-id="9bf5a-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="9bf5a-105">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9bf5a-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf5a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bf5a-106">Example</span></span>  
 <span data-ttu-id="9bf5a-107">Následující kód prochází <xref:System.Data.Linq.ObjectChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="9bf5a-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="9bf5a-108">Pro každý objekt, pak prochází <xref:System.Data.Linq.MemberChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="9bf5a-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bf5a-109">Zahrnout <xref:System.Reflection> negace <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informace.</span><span class="sxs-lookup"><span data-stu-id="9bf5a-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9bf5a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bf5a-110">See also</span></span>

- [<span data-ttu-id="9bf5a-111">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="9bf5a-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
