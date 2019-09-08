---
title: Nalezení maximální hodnoty v číselné posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ebef8cb373da4021fd68fd7ce38de8cb06eb81ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782181"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="610fe-102">Nalezení maximální hodnoty v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="610fe-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="610fe-103"><xref:System.Linq.Enumerable.Max%2A> Použijte operátor k vyhledání nejvyšší hodnoty v posloupnosti číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="610fe-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="610fe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="610fe-104">Example</span></span>  
 <span data-ttu-id="610fe-105">Následující příklad najde poslední datum zařazení pro každého zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="610fe-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="610fe-106">Pokud spustíte tento dotaz proti ukázkové databázi Northwind, výstup je: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="610fe-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="610fe-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="610fe-107">Example</span></span>  
 <span data-ttu-id="610fe-108">Následující příklad najde nejvíc jednotek na skladě pro libovolný produkt.</span><span class="sxs-lookup"><span data-stu-id="610fe-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="610fe-109">Pokud tento příklad spustíte s ukázkovou databází Northwind, výstup je: `125`.</span><span class="sxs-lookup"><span data-stu-id="610fe-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="610fe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="610fe-110">Example</span></span>  
 <span data-ttu-id="610fe-111">Následující příklad používá Max k nalezení `Products` nejvyšší jednotkové ceny v každé kategorii.</span><span class="sxs-lookup"><span data-stu-id="610fe-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="610fe-112">Výstup pak zobrazí výsledky podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="610fe-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="610fe-113">Pokud spustíte předchozí dotaz na ukázkovou databázi Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="610fe-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="610fe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="610fe-114">See also</span></span>

- [<span data-ttu-id="610fe-115">Agregační dotazy</span><span class="sxs-lookup"><span data-stu-id="610fe-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="610fe-116">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="610fe-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
