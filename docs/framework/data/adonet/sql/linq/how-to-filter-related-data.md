---
title: 'Postupy: filtrování dat v relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: b40de7201610c58b9b8e86045afe5869d958bdf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360832"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="9a4db-102">Postupy: filtrování dat v relaci</span><span class="sxs-lookup"><span data-stu-id="9a4db-102">How to: Filter Related Data</span></span>
<span data-ttu-id="9a4db-103">Použití <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metody určíte, poddotazech, chcete-li omezit množství načíst data.</span><span class="sxs-lookup"><span data-stu-id="9a4db-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4db-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a4db-104">Example</span></span>  
 <span data-ttu-id="9a4db-105">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metoda omezení `Orders` načíst na ty, které nebyly dodány dnes.</span><span class="sxs-lookup"><span data-stu-id="9a4db-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="9a4db-106">Bez tohoto přístupu všechny `Orders` by byly získány, i když se požaduje jenom podmnožina.</span><span class="sxs-lookup"><span data-stu-id="9a4db-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9a4db-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a4db-107">See Also</span></span>  
 [<span data-ttu-id="9a4db-108">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="9a4db-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
