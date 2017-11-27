---
title: "Začínáme"
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
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c6db401f710c470ea890a7a7ac090fabef5d64c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started"></a><span data-ttu-id="478ff-102">Začínáme</span><span class="sxs-lookup"><span data-stu-id="478ff-102">Getting Started</span></span>
<span data-ttu-id="478ff-103">Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie pro přístup k SQL databáze stejně, jako by přístup kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="478ff-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="478ff-104">Například `nw` je vytvořen objekt v následujícím kódu pro představují `Northwind` databáze, `Customers` je cílová tabulka, řádky jsou filtrovány pro `Customers` z `London`a řetězec pro `CompanyName` je vybrána pro načtení.</span><span class="sxs-lookup"><span data-stu-id="478ff-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="478ff-105">Když se spustí smyčky, kolekce `CompanyName` je načíst hodnoty.</span><span class="sxs-lookup"><span data-stu-id="478ff-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="478ff-106">Další kroky</span><span class="sxs-lookup"><span data-stu-id="478ff-106">Next Steps</span></span>  
 <span data-ttu-id="478ff-107">Mezi další příklady, včetně vložení a aktualizace, najdete v tématu [co jste můžete provést pomocí technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="478ff-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="478ff-108">Zkuste některé kurzy tak, aby měl praktických zkušeností, použití a návody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="478ff-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="478ff-109">V tématu [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="478ff-109">See [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="478ff-110">Nakonec, zjistěte, jak začít pracovat na vlastních [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu čtení [obvyklé kroky pro použití technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="478ff-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478ff-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="478ff-111">See Also</span></span>  
 [<span data-ttu-id="478ff-112">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="478ff-112">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="478ff-113">Úvod do LINQ</span><span class="sxs-lookup"><span data-stu-id="478ff-113">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 [<span data-ttu-id="478ff-114">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="478ff-114">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
