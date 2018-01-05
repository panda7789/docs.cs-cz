---
title: "Výpočetní součet hodnot v číselného pořadí"
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
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6b28c6f9626919ee52be2a42eb2f68aecc9acbf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="555ac-102">Výpočetní součet hodnot v číselného pořadí</span><span class="sxs-lookup"><span data-stu-id="555ac-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="555ac-103">Použití <xref:System.Linq.Enumerable.Sum%2A> operátor vypočítat součet číselných hodnot v pořadí.</span><span class="sxs-lookup"><span data-stu-id="555ac-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="555ac-104">Všimněte si těchto vlastností `Sum` operátor v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="555ac-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="555ac-105">Agregační operátor standardní – operátor dotazu `Sum` vyhodnotí na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="555ac-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="555ac-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechána beze změny.</span><span class="sxs-lookup"><span data-stu-id="555ac-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="555ac-107">Z tohoto důvodu `Sum` vyhodnocen jako null místo na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="555ac-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
-   <span data-ttu-id="555ac-108">Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="555ac-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="555ac-109">Součet počty 32bitové celé číslo není počítaný pomocí 64-bit výsledky a pro může dojít k přetečení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad `Sum`.</span><span class="sxs-lookup"><span data-stu-id="555ac-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="555ac-110">Tato možnost existuje i v případě implementace standardní – operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.</span><span class="sxs-lookup"><span data-stu-id="555ac-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="555ac-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="555ac-111">Example</span></span>  
 <span data-ttu-id="555ac-112">Vyhledá celkový nákladní všech objednávek v následujícím příkladu `Order` tabulky.</span><span class="sxs-lookup"><span data-stu-id="555ac-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="555ac-113">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="555ac-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="555ac-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="555ac-114">Example</span></span>  
 <span data-ttu-id="555ac-115">Následující příklad vyhledá celkový počet jednotek v pořadí pro všechny produkty.</span><span class="sxs-lookup"><span data-stu-id="555ac-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="555ac-116">Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `780`.</span><span class="sxs-lookup"><span data-stu-id="555ac-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="555ac-117">Všimněte si, že musíte vysílat `short` typy (například `UnitsOnOrder`) protože `Sum` nemá žádné přetížení pro krátké typy.</span><span class="sxs-lookup"><span data-stu-id="555ac-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="555ac-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="555ac-118">See Also</span></span>  
 [<span data-ttu-id="555ac-119">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="555ac-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="555ac-120">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="555ac-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
