---
title: "Příklady syntaxe výrazu dotazu: vytváření oddílů"
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
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 858d5c01c36516e3f1a8ca47c4d5500c0f24c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="ff58d-102">Příklady syntaxe výrazu dotazu: vytváření oddílů</span><span class="sxs-lookup"><span data-stu-id="ff58d-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="ff58d-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff58d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="ff58d-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ff58d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ff58d-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="ff58d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="ff58d-106">Skip</span><span class="sxs-lookup"><span data-stu-id="ff58d-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff58d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff58d-107">Example</span></span>  
 <span data-ttu-id="ff58d-108">Následující příklad používá <xref:System.Linq.Enumerable.Skip%2A> metodu za účelem získání všech ale nejprve dvou adres v Praze.</span><span class="sxs-lookup"><span data-stu-id="ff58d-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="ff58d-109">Take</span><span class="sxs-lookup"><span data-stu-id="ff58d-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff58d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff58d-110">Example</span></span>  
 <span data-ttu-id="ff58d-111">Následující příklad používá <xref:System.Linq.Enumerable.Take%2A> metoda získat prvními třemi adresami v Praze.</span><span class="sxs-lookup"><span data-stu-id="ff58d-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="ff58d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff58d-112">See Also</span></span>  
 [<span data-ttu-id="ff58d-113">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ff58d-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
