---
title: Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634687"
---
# <a name="getting-started"></a><span data-ttu-id="9564f-102">Začínáme</span><span class="sxs-lookup"><span data-stu-id="9564f-102">Getting Started</span></span>
<span data-ttu-id="9564f-103">Pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]můžete technologii LINQ použít pro přístup k databázím SQL stejně, jako byste měli přístup ke kolekci v paměti.</span><span class="sxs-lookup"><span data-stu-id="9564f-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="9564f-104">Například objekt `nw` v následujícím kódu je vytvořen tak, aby představoval databázi `Northwind`, cílová tabulka `Customers`, řádky jsou filtrovány pro `Customers` z `London`a řetězec pro `CompanyName` je vybrán pro načtení.</span><span class="sxs-lookup"><span data-stu-id="9564f-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="9564f-105">Po spuštění smyčky se načtou kolekce hodnot `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="9564f-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="9564f-106">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9564f-106">Next Steps</span></span>  
 <span data-ttu-id="9564f-107">Další příklady, včetně vkládání a aktualizace, najdete v tématu [co můžete s LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9564f-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="9564f-108">Dále vyzkoušejte některé návody a kurzy, které vám pomají praktickou zkušenost s používáním [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9564f-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9564f-109">Přečtěte si [návody v tématu učení](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="9564f-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="9564f-110">Nakonec se naučíte, jak začít používat vlastní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projekt, a to čtením [typických kroků pro použití LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9564f-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9564f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9564f-111">See also</span></span>

- [<span data-ttu-id="9564f-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9564f-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="9564f-113">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="9564f-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="9564f-114">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9564f-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="9564f-115">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9564f-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
