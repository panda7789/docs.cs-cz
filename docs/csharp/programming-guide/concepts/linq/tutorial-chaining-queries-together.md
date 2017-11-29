---
title: "Kurz: Řetězení dotazy společně (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08196f4780e566cc05e36b6cfe78caad3e9c96a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="3a6ce-102">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="3a6ce-103">V tomto kurzu znázorňuje model zpracování, pokud zřetězené dotazy společně.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="3a6ce-104">Řetězení dotazy společně je klíčovou součástí zápisu funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="3a6ce-105">Je důležité si uvědomit, přesně jak zřetězené pracovní dotazy.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="3a6ce-106">Tento postup použijte dotazy, které zpracovávají dokumenty hojně.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a6ce-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3a6ce-107">In This Section</span></span>  
  
|<span data-ttu-id="3a6ce-108">Téma</span><span class="sxs-lookup"><span data-stu-id="3a6ce-108">Topic</span></span>|<span data-ttu-id="3a6ce-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3a6ce-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3a6ce-110">Odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="3a6ce-111">Popisuje koncepce odložené provedení a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="3a6ce-112">Odložené provedení příklad (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="3a6ce-113">Poskytuje příklad odložené provedení.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="3a6ce-114">Řetězení příklad dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="3a6ce-115">Ukazuje, jak odložené provedení funguje, když řetězení dotazy společně.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="3a6ce-116">Zprostředkující Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="3a6ce-117">Identifikuje a ukazuje sémantika zprostředkující materialization.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="3a6ce-118">Řetězení standardní operátory dotazu společně (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="3a6ce-119">Popisuje opožděné sémantika standardní operátory dotazu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a6ce-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6ce-120">See Also</span></span>  
 [<span data-ttu-id="3a6ce-121">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
