---
title: Nalezení minimální hodnoty v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793830"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="45175-102">Nalezení minimální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="45175-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="45175-103"><xref:System.Linq.Enumerable.Min%2A> Použijte operátor k vrácení minimální hodnoty z sekvence číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="45175-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45175-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="45175-104">Example</span></span>  
 <span data-ttu-id="45175-105">Následující příklad najde nejnižší jednotkovou cenu každého produktu.</span><span class="sxs-lookup"><span data-stu-id="45175-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="45175-106">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="45175-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="45175-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="45175-107">Example</span></span>  
 <span data-ttu-id="45175-108">Následující příklad najde nejnižší částku dopravného pro jakékoli pořadí.</span><span class="sxs-lookup"><span data-stu-id="45175-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="45175-109">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="45175-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="45175-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="45175-110">Example</span></span>  
 <span data-ttu-id="45175-111">Následující příklad používá minimum k nalezení `Products` nejnižší jednotkové ceny v každé kategorii.</span><span class="sxs-lookup"><span data-stu-id="45175-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="45175-112">Výstup je uspořádán podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="45175-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="45175-113">Pokud spustíte předchozí dotaz na ukázkovou databázi Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="45175-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="45175-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45175-114">See also</span></span>

- [<span data-ttu-id="45175-115">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="45175-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="45175-116">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="45175-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
