---
title: Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 506257c13bbaada98dffa9d3a15c834037c1d971
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038555"
---
# <a name="getting-started"></a><span data-ttu-id="78b97-102">Začínáme</span><span class="sxs-lookup"><span data-stu-id="78b97-102">Getting Started</span></span>
<span data-ttu-id="78b97-103">S použitím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro přístup k SQL databáze, stejně jako by přístup ke kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="78b97-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="78b97-104">Například `nw` je vytvořen objekt v následujícím kódu představují `Northwind` databáze, `Customers` cílové tabulky, řádky se filtrují pro `Customers` z `London`a řetězec pro `CompanyName` zaškrtnuto pro načtení.</span><span class="sxs-lookup"><span data-stu-id="78b97-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="78b97-105">Při provádění smyčky, kolekce `CompanyName` hodnoty načteny.</span><span class="sxs-lookup"><span data-stu-id="78b97-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="78b97-106">Další kroky</span><span class="sxs-lookup"><span data-stu-id="78b97-106">Next Steps</span></span>  
 <span data-ttu-id="78b97-107">Mezi další příklady, včetně vkládání a aktualizacích, naleznete v části [co jste můžete dělat s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="78b97-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="78b97-108">Dále vyzkoušejte některé názorné postupy a kurzy, které mají praktické zkušenosti pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="78b97-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="78b97-109">Zobrazit [učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="78b97-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="78b97-110">A konečně, přečtěte si, jak začít pracovat na vlastním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu načtením [typické postupy použití LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="78b97-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b97-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78b97-111">See also</span></span>

- [<span data-ttu-id="78b97-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="78b97-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="78b97-113">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="78b97-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="78b97-114">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78b97-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="78b97-115">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="78b97-115">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
