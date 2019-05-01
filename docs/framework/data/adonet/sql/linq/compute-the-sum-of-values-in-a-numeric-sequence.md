---
title: Určení součtu hodnot v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 2f66b996a0e688205d61f5fca476c0335616ee38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032939"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="79377-102">Určení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="79377-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="79377-103">Použití <xref:System.Linq.Enumerable.Sum%2A> operátor pro výpočet součtu číselných hodnot v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="79377-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="79377-104">Mějte na paměti následující charakteristiky `Sum` operátor v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="79377-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="79377-105">Standardní operátor dotazu agregační operátor `Sum` vyhodnocen jako nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="79377-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="79377-106">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechány beze změny.</span><span class="sxs-lookup"><span data-stu-id="79377-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="79377-107">Z tohoto důvodu `Sum` vyhodnotí na hodnotu null namísto na nulu pro prázdnou sekvencí nebo pro sekvenci, která obsahuje pouze hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="79377-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="79377-108">Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79377-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="79377-109">Součet počty 32bitové celé číslo není počítaný pomocí 64-bit výsledky a přetečení se může stát [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad `Sum`.</span><span class="sxs-lookup"><span data-stu-id="79377-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="79377-110">Tato možnost existuje i v případě, že implementace standardní operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.</span><span class="sxs-lookup"><span data-stu-id="79377-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79377-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="79377-111">Example</span></span>  
 <span data-ttu-id="79377-112">Následující příklad vyhledá Dopravné celkem všech objednávek v `Order` tabulky.</span><span class="sxs-lookup"><span data-stu-id="79377-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="79377-113">Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, je výstup: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="79377-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="79377-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="79377-114">Example</span></span>  
 <span data-ttu-id="79377-115">Následující příklad vyhledá celkový počet jednotek v pořadí pro všechny produkty.</span><span class="sxs-lookup"><span data-stu-id="79377-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="79377-116">Pokud spouštíte skript v ukázkové databázi Northwind tento dotaz, je výstup: `780`.</span><span class="sxs-lookup"><span data-stu-id="79377-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="79377-117">Všimněte si, že musíte přetypovat `short` typů (například `UnitsOnOrder`) protože `Sum` nemá žádné přetížení pro krátké typy.</span><span class="sxs-lookup"><span data-stu-id="79377-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="79377-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79377-118">See also</span></span>

- [<span data-ttu-id="79377-119">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="79377-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="79377-120">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="79377-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
