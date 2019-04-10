---
title: 'Postupy: Filtrování souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218222"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="93dc7-102">Postupy: Filtrování souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="93dc7-102">How to: Filter Related Data</span></span>
<span data-ttu-id="93dc7-103">Použití <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metody určíte, poddotazech, chcete-li omezit množství načtena data.</span><span class="sxs-lookup"><span data-stu-id="93dc7-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93dc7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="93dc7-104">Example</span></span>  
 <span data-ttu-id="93dc7-105">V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metoda omezení `Orders` načíst na ty, které nebyly dodány ještě dnes.</span><span class="sxs-lookup"><span data-stu-id="93dc7-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="93dc7-106">Bez tohoto přístupu všechny `Orders` by byly načteny, i když je požadován pouze podmnožinu.</span><span class="sxs-lookup"><span data-stu-id="93dc7-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="93dc7-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93dc7-107">See also</span></span>

- [<span data-ttu-id="93dc7-108">Dotazy do databáze</span><span class="sxs-lookup"><span data-stu-id="93dc7-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
