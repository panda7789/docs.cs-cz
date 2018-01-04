---
title: "Sémantika hodnotu Null."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6786c7ea4441b1a753d6f0b4213f40fa64dcb4ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="null-semantics"></a><span data-ttu-id="fdd31-102">Sémantika hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="fdd31-102">Null Semantics</span></span>
<span data-ttu-id="fdd31-103">Následující tabulka obsahuje odkazy na různých částí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace kde `null` (`Nothing` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) jsou popsány problémy.</span><span class="sxs-lookup"><span data-stu-id="fdd31-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="fdd31-104">Téma</span><span class="sxs-lookup"><span data-stu-id="fdd31-104">Topic</span></span>|<span data-ttu-id="fdd31-105">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd31-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fdd31-106">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="fdd31-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="fdd31-107">V části "Null sémantiku" v tomto tématu zahrnuje diskuzi o třístavové SQL Boolean versus dvou stavů common language runtime (CLR) <xref:System.Boolean>, skutečné `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) a `null` (C#) a další podobné potíže.</span><span class="sxs-lookup"><span data-stu-id="fdd31-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="fdd31-108">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="fdd31-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="fdd31-109">V části "Null sémantiku" v tomto tématu popisuje sémantiku porovnání null v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fdd31-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="fdd31-110">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="fdd31-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="fdd31-111">V části "Rozdíly z .NET" v tomto tématu popisuje, jak vrátit 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec má hodnotu null nebo zda je nalezen pozici 0.</span><span class="sxs-lookup"><span data-stu-id="fdd31-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="fdd31-112">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="fdd31-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="fdd31-113">Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> vyhodnocen jako operátor `null` (`Nothing` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) namísto 0 pro sekvenci, která obsahuje jenom hodnoty Null nebo prázdnou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="fdd31-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdd31-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdd31-114">See Also</span></span>  
 [<span data-ttu-id="fdd31-115">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="fdd31-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
