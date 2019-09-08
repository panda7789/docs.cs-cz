---
title: Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793911"
---
# <a name="getting-started"></a><span data-ttu-id="04760-102">Začínáme</span><span class="sxs-lookup"><span data-stu-id="04760-102">Getting Started</span></span>
<span data-ttu-id="04760-103">Pomocí nástroje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]můžete [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] využívat technologii pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="04760-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="04760-104">`nw` Například objekt v následujícím kódu je vytvořen pro `Customers` `Northwind` reprezentaci databáze, na `Customers` cílovou tabulku, řádky jsou filtrovány z `London`a je vybrán řetězec pro `CompanyName` . pro načtení.</span><span class="sxs-lookup"><span data-stu-id="04760-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="04760-105">Po spuštění smyčky se načte kolekce `CompanyName` hodnot.</span><span class="sxs-lookup"><span data-stu-id="04760-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="04760-106">Další kroky</span><span class="sxs-lookup"><span data-stu-id="04760-106">Next Steps</span></span>  
 <span data-ttu-id="04760-107">Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="04760-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="04760-108">Dále vyzkoušejte některé návody a kurzy, které vám pomají praktické zkušenosti s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04760-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="04760-109">Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="04760-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="04760-110">Nakonec se naučíte, jak začít pracovat na vlastním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu načtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="04760-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04760-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04760-111">See also</span></span>

- [<span data-ttu-id="04760-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="04760-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="04760-113">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="04760-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="04760-114">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04760-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="04760-115">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="04760-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
