---
title: Sémantika s hodnotou null
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792977"
---
# <a name="null-semantics"></a><span data-ttu-id="dc70b-102">Sémantika s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="dc70b-102">Null Semantics</span></span>
<span data-ttu-id="dc70b-103">Následující tabulka obsahuje odkazy na různé části [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace, kde `null` jsou popsány problémy (`Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dc70b-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="dc70b-104">Téma</span><span class="sxs-lookup"><span data-stu-id="dc70b-104">Topic</span></span>|<span data-ttu-id="dc70b-105">Popis</span><span class="sxs-lookup"><span data-stu-id="dc70b-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dc70b-106">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="dc70b-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="dc70b-107">Oddíl "sémantika hodnoty null" v tomto tématu obsahuje diskuzi o třech stavech SQL logických versus dvou stavech modulu CLR (Common Language Runtime <xref:System.Boolean>), literálu `Nothing` (Visual Basic) `null` aC#() a dalších podobných Chyba.</span><span class="sxs-lookup"><span data-stu-id="dc70b-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="dc70b-108">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="dc70b-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="dc70b-109">Oddíl "sémantika hodnoty null" v tomto tématu popisuje sémantiku porovnání s hodnotou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]null v.</span><span class="sxs-lookup"><span data-stu-id="dc70b-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="dc70b-110">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="dc70b-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="dc70b-111">Část rozdíly od .NET tohoto tématu popisuje, jak vrácení 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec je null nebo že nalezená pozice je 0.</span><span class="sxs-lookup"><span data-stu-id="dc70b-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="dc70b-112">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="dc70b-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="dc70b-113">Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> se operátor vyhodnocuje `null` (`Nothing` v Visual Basic) místo 0 pro sekvenci, která obsahuje pouze hodnoty null nebo prázdné sekvence.</span><span class="sxs-lookup"><span data-stu-id="dc70b-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc70b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc70b-114">See also</span></span>

- [<span data-ttu-id="dc70b-115">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="dc70b-115">Data Types and Functions</span></span>](data-types-and-functions.md)
