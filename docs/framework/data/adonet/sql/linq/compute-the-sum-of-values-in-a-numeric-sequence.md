---
title: Určení součtu hodnot v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247917"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="10c61-102">Určení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="10c61-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="10c61-103"><xref:System.Linq.Enumerable.Sum%2A> Použijte operátor k výpočtu součtu číselných hodnot v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="10c61-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="10c61-104">Všimněte si následujících vlastností `Sum` operátoru v: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10c61-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="10c61-105">Agregační operátor `Sum` standardního operátoru dotazu vyhodnocuje nulu pro prázdnou sekvenci nebo sekvenci, která obsahuje pouze hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="10c61-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="10c61-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému jsou sémantika jazyka SQL ponechána beze změny.</span><span class="sxs-lookup"><span data-stu-id="10c61-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="10c61-107">Z tohoto důvodu je `Sum` vyhodnocena na hodnotu null namísto na nulu pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="10c61-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="10c61-108">Omezení SQL pro mezilehlé výsledky se vztahují na agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10c61-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="10c61-109">Součet 32 celočíselných celočíselných hodnot není počítán pomocí 64 bitových výsledků a přetečení může nastat pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Sum`překlad.</span><span class="sxs-lookup"><span data-stu-id="10c61-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="10c61-110">Tato možnost existuje i v případě, že standardní implementace operátoru dotazu nezpůsobí přetečení odpovídající posloupnosti v paměti.</span><span class="sxs-lookup"><span data-stu-id="10c61-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10c61-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="10c61-111">Example</span></span>  
 <span data-ttu-id="10c61-112">Následující příklad najde celkové přepravení všech objednávek v `Order` tabulce.</span><span class="sxs-lookup"><span data-stu-id="10c61-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="10c61-113">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="10c61-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="10c61-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="10c61-114">Example</span></span>  
 <span data-ttu-id="10c61-115">Následující příklad najde celkový počet jednotek v pořadí pro všechny produkty.</span><span class="sxs-lookup"><span data-stu-id="10c61-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="10c61-116">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `780`.</span><span class="sxs-lookup"><span data-stu-id="10c61-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="10c61-117">Všimněte si, že je `short` nutné přetypovat typy ( `UnitsOnOrder`například), `Sum` protože nemá žádné přetížení pro krátké typy.</span><span class="sxs-lookup"><span data-stu-id="10c61-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="10c61-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10c61-118">See also</span></span>

- [<span data-ttu-id="10c61-119">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="10c61-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="10c61-120">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="10c61-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
