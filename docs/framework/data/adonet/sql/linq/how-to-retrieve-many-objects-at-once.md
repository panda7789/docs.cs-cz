---
title: 'Postupy: Načtení mnoha objektů najednou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: dd53c2fd16a82ce0f69a33e0b7d7ffef7815b91b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220523"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="5c52e-102">Postupy: Načtení mnoha objektů najednou</span><span class="sxs-lookup"><span data-stu-id="5c52e-102">How to: Retrieve Many Objects At Once</span></span>
<span data-ttu-id="5c52e-103">Mnoho objektů v jednom dotazu můžete načíst pomocí <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c52e-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c52e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c52e-104">Example</span></span>  
 <span data-ttu-id="5c52e-105">Následující kód používá <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metody k získání obou `Customer` a `Order` objekty.</span><span class="sxs-lookup"><span data-stu-id="5c52e-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="5c52e-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c52e-106">See also</span></span>

- [<span data-ttu-id="5c52e-107">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="5c52e-107">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
