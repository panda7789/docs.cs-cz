---
title: 'Postupy: Zadání kontroly konfliktů souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: 53d3ba6969705940c403795d3764c021f0829c64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098972"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="b565f-102">Postupy: Zadání kontroly konfliktů souběžnosti</span><span class="sxs-lookup"><span data-stu-id="b565f-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="b565f-103">Můžete určit sloupce, které databáze jsou vráceny na konflikty souběžnosti, při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="b565f-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="b565f-104">Další informace najdete v tématu [jak: Zadejte, kteří členové jsou testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="b565f-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b565f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b565f-105">Example</span></span>  
 <span data-ttu-id="b565f-106">Následující kód určuje, že `HomePage` člen by měl být testován nikdy během kontroly aktualizací.</span><span class="sxs-lookup"><span data-stu-id="b565f-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="b565f-107">Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="b565f-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b565f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b565f-108">See also</span></span>

- [<span data-ttu-id="b565f-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b565f-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b565f-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="b565f-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
