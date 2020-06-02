---
title: začínáme
description: Pomocí tohoto ukázkového LINQ to SQL kódu můžete začít používat technologii LINQ pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286414"
---
# <a name="getting-started"></a><span data-ttu-id="2c5bd-103">začínáme</span><span class="sxs-lookup"><span data-stu-id="2c5bd-103">Getting Started</span></span>
<span data-ttu-id="2c5bd-104">Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete technologii LINQ použít pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="2c5bd-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="2c5bd-105">Například `nw` objekt v následujícím kódu je vytvořen pro reprezentaci `Northwind` databáze, na `Customers` cílovou tabulku, řádky jsou filtrovány `Customers` z `London` a `CompanyName` je vybrán řetězec pro načtení.</span><span class="sxs-lookup"><span data-stu-id="2c5bd-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="2c5bd-106">Po spuštění smyčky se `CompanyName` načte kolekce hodnot.</span><span class="sxs-lookup"><span data-stu-id="2c5bd-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="2c5bd-107">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2c5bd-107">Next Steps</span></span>  
 <span data-ttu-id="2c5bd-108">Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2c5bd-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="2c5bd-109">Dále vyzkoušejte některé návody a kurzy, které vám pomají praktické zkušenosti s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c5bd-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2c5bd-110">Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="2c5bd-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="2c5bd-111">Nakonec se naučíte, jak začít pracovat na vlastním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu načtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2c5bd-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5bd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c5bd-112">See also</span></span>

- [<span data-ttu-id="2c5bd-113">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2c5bd-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="2c5bd-114">Úvod do jazyka LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5bd-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="2c5bd-115">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c5bd-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="2c5bd-116">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2c5bd-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
