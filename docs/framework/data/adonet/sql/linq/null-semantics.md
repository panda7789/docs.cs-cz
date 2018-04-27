---
title: Sémantika hodnotu Null.
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3c4daa5fd37158f1af31f33ba743a56cf76670d8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="null-semantics"></a><span data-ttu-id="84815-102">Sémantika hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="84815-102">Null Semantics</span></span>
<span data-ttu-id="84815-103">Následující tabulka obsahuje odkazy na různých částí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentace kde `null` (`Nothing` v jazyce Visual Basic) jsou popsány problémy.</span><span class="sxs-lookup"><span data-stu-id="84815-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="84815-104">Téma</span><span class="sxs-lookup"><span data-stu-id="84815-104">Topic</span></span>|<span data-ttu-id="84815-105">Popis</span><span class="sxs-lookup"><span data-stu-id="84815-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="84815-106">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="84815-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="84815-107">V části "Null sémantiku" v tomto tématu zahrnuje diskuzi o třístavové SQL Boolean versus dvou stavů common language runtime (CLR) <xref:System.Boolean>, skutečné `Nothing` (Visual Basic) a `null` (C#) a další podobné potíže.</span><span class="sxs-lookup"><span data-stu-id="84815-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="84815-108">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="84815-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="84815-109">V části "Null sémantiku" v tomto tématu popisuje sémantiku porovnání null v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84815-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="84815-110">Metody System.String</span><span class="sxs-lookup"><span data-stu-id="84815-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="84815-111">V části "Rozdíly z .NET" v tomto tématu popisuje, jak vrátit 0 z <xref:System.String.LastIndexOf%2A> může znamenat, že řetězec má hodnotu null nebo zda je nalezen pozici 0.</span><span class="sxs-lookup"><span data-stu-id="84815-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="84815-112">Nalezení součtu hodnot v číselné posloupnosti</span><span class="sxs-lookup"><span data-stu-id="84815-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="84815-113">Popisuje, jak <xref:System.Linq.Enumerable.Sum%2A> vyhodnocen jako operátor `null` (`Nothing` v jazyce Visual Basic) namísto 0 pro sekvenci, která obsahuje jenom hodnoty Null nebo prázdnou sekvencí.</span><span class="sxs-lookup"><span data-stu-id="84815-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84815-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="84815-114">See Also</span></span>  
 [<span data-ttu-id="84815-115">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="84815-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
