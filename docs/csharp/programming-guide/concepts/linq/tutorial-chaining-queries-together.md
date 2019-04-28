---
title: 'Kurz: Zřetězení dotazů (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: 3beed32aa276f218a80267748e74707941957e53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711990"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="89502-102">Kurz: Zřetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="89502-103">Tento kurz ukazuje zpracování modelu při řetězení dotazů společně.</span><span class="sxs-lookup"><span data-stu-id="89502-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="89502-104">Zřetězení dotazů je klíčovou součástí vytváření funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="89502-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="89502-105">Je důležité pochopit, přesně jak zřetězených dotazů práce.</span><span class="sxs-lookup"><span data-stu-id="89502-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="89502-106">Tento postup použít dotazy, které zpracovávají dokumenty Office Open XML neúmyslné.</span><span class="sxs-lookup"><span data-stu-id="89502-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89502-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="89502-107">In This Section</span></span>  
  
|<span data-ttu-id="89502-108">Téma</span><span class="sxs-lookup"><span data-stu-id="89502-108">Topic</span></span>|<span data-ttu-id="89502-109">Popis</span><span class="sxs-lookup"><span data-stu-id="89502-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="89502-110">Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="89502-111">Popisuje koncepty odložené provedení a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="89502-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="89502-112">Příklad odloženého provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="89502-113">Poskytuje příklad odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="89502-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="89502-114">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="89502-115">Ukazuje, jak odložené provedení funguje při zřetězení dotazů.</span><span class="sxs-lookup"><span data-stu-id="89502-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="89502-116">Přechodná Materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="89502-117">Identifikuje a ilustruje sémantiku přechodná materializace.</span><span class="sxs-lookup"><span data-stu-id="89502-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="89502-118">Zřetězení standardních dotazovacích operátorů pohromadě (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="89502-119">Popisuje opožděné sémantiku standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="89502-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89502-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89502-120">See also</span></span>

- [<span data-ttu-id="89502-121">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="89502-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
