---
title: "Příklady syntaxe dotazů metoda: seskupování"
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
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b2001c76cac2c09159508d2d13da451c81b4cf1a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="c3eda-102">Příklady syntaxe dotazů metoda: seskupování</span><span class="sxs-lookup"><span data-stu-id="c3eda-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="c3eda-103">V příkladech v tomto tématu ukazují, jak používat `GroupBy` metodu pro dotaz [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="c3eda-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="c3eda-104">Model prodeje společnosti AdventureWorks, který se používá v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c3eda-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c3eda-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="c3eda-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="c3eda-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3eda-106">Example</span></span>  
 <span data-ttu-id="c3eda-107">Následující příklad používá `GroupBy` metoda vrátí `Address` objekty, které jsou seskupené podle PSČ.</span><span class="sxs-lookup"><span data-stu-id="c3eda-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="c3eda-108">Výsledky se promítá do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="c3eda-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="c3eda-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3eda-109">Example</span></span>  
 <span data-ttu-id="c3eda-110">Následující příklad používá `GroupBy` metoda vrátí `Contact` objekty, které jsou seskupené podle první písmeno poslední jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="c3eda-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="c3eda-111">Výsledky jsou také seřazené podle první písmeno příjmení a promítnout do anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="c3eda-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="c3eda-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3eda-112">Example</span></span>  
 <span data-ttu-id="c3eda-113">Následující příklad používá `GroupBy` metoda vrátí `SalesOrderHeader` objekty, které jsou seskupené podle ID zákazníka.</span><span class="sxs-lookup"><span data-stu-id="c3eda-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="c3eda-114">Vrátí počet prodeje pro každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="c3eda-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c3eda-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3eda-115">See Also</span></span>  
 [<span data-ttu-id="c3eda-116">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c3eda-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
