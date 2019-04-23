---
title: Sémantika s hodnotou null
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: eb1e96ba44c5d64e8366a654c2d06d89c9b46c9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172754"
---
# <a name="null-semantics"></a><span data-ttu-id="5c3d3-102">Sémantika s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="5c3d3-102">Null Semantics</span></span>
<span data-ttu-id="5c3d3-103">Následující tabulka obsahuje odkazy na různé části [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci kde `null` (`Nothing` v jazyce Visual Basic) jsou popsány problémy.</span><span class="sxs-lookup"><span data-stu-id="5c3d3-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="5c3d3-104">Téma</span><span class="sxs-lookup"><span data-stu-id="5c3d3-104">Topic</span></span>|<span data-ttu-id="5c3d3-105">Popis</span><span class="sxs-lookup"><span data-stu-id="5c3d3-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c3d3-106">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="5c3d3-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="5c3d3-107">"Sémantika s hodnotou Null" část tohoto tématu obsahuje informace o třístavové SQL logická porovnání dvou stavů common language runtime (CLR) <xref:System.Boolean>, literál `Nothing` (Visual Basic) a `null` (C#) a další podobné problémy.</span><span class="sxs-lookup"><span data-stu-id="5c3d3-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="5c3d3-108">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="5c3d3-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="5c3d3-109">"Sémantika s hodnotou Null" část tohoto tématu popisuje sémantiku porovnání null v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c3d3-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="5c3d3-110">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="5c3d3-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="5c3d3-111">Část "Rozdíly z .NET" Toto téma popisuje, jak vrátit 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec má hodnotu null nebo je nalezeno umístění 0.</span><span class="sxs-lookup"><span data-stu-id="5c3d3-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="5c3d3-112">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="5c3d3-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="5c3d3-113">Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> vyhodnotí jako operátor `null` (`Nothing` v jazyce Visual Basic) namísto 0 pro sekvenci, která obsahuje pouze hodnoty Null nebo prázdná sekvence.</span><span class="sxs-lookup"><span data-stu-id="5c3d3-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c3d3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c3d3-114">See also</span></span>

- [<span data-ttu-id="5c3d3-115">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="5c3d3-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
