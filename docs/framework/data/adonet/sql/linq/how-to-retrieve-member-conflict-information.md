---
title: "Postupy: načtení informací o konflikt člena"
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
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a6766e40b842675cbe37ba1ebeb1a956c19e6318
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="4364c-102">Postupy: načtení informací o konflikt člena</span><span class="sxs-lookup"><span data-stu-id="4364c-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="4364c-103">Můžete použít <xref:System.Data.Linq.MemberChangeConflict> třídy k načtení informací o jednotlivé členy v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="4364c-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="4364c-104">V tomto kontextu stejné můžete zadat vlastní zpracování chyb jsou v konfliktu u člena.</span><span class="sxs-lookup"><span data-stu-id="4364c-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="4364c-105">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4364c-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4364c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4364c-106">Example</span></span>  
 <span data-ttu-id="4364c-107">Následující kód iteruje <xref:System.Data.Linq.ObjectChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="4364c-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="4364c-108">Pro každý objekt, se pak provádí iteraci <xref:System.Data.Linq.MemberChangeConflict> objekty.</span><span class="sxs-lookup"><span data-stu-id="4364c-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4364c-109">Zahrnout <xref:System.Reflection> Chcete-li poskytovat <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informace.</span><span class="sxs-lookup"><span data-stu-id="4364c-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4364c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4364c-110">See Also</span></span>  
 [<span data-ttu-id="4364c-111">Postupy: Správa je v konfliktu změn</span><span class="sxs-lookup"><span data-stu-id="4364c-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
