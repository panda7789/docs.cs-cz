---
title: 'Kurz: Zřetězení dotazů společně (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: cab012a6ae618bd731c26bc1a002c144b84d2169
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513529"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="a0faa-102">Kurz: Zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="a0faa-103">Tento kurz ukazuje zpracování modelu při řetězení dotazů společně.</span><span class="sxs-lookup"><span data-stu-id="a0faa-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="a0faa-104">Zřetězení dotazů je klíčovou součástí vytváření funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="a0faa-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="a0faa-105">Je důležité pochopit, přesně jak zřetězených dotazů práce.</span><span class="sxs-lookup"><span data-stu-id="a0faa-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="a0faa-106">Tento postup použít dotazy, které zpracovávají dokumenty Office Open XML neúmyslné.</span><span class="sxs-lookup"><span data-stu-id="a0faa-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0faa-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a0faa-107">In This Section</span></span>  
  
|<span data-ttu-id="a0faa-108">Téma</span><span class="sxs-lookup"><span data-stu-id="a0faa-108">Topic</span></span>|<span data-ttu-id="a0faa-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a0faa-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a0faa-110">Odložené provedení a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="a0faa-111">Popisuje koncepty odložené provedení a opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="a0faa-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="a0faa-112">Příklad odloženého provedení (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="a0faa-113">Poskytuje příklad odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="a0faa-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="a0faa-114">Příklad řetězení dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="a0faa-115">Ukazuje, jak odložené provedení funguje při zřetězení dotazů.</span><span class="sxs-lookup"><span data-stu-id="a0faa-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="a0faa-116">Přechodná Materializace (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="a0faa-117">Identifikuje a ilustruje sémantiku přechodná materializace.</span><span class="sxs-lookup"><span data-stu-id="a0faa-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="a0faa-118">Zřetězení standardních dotazovacích operátorů pohromadě (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="a0faa-119">Popisuje opožděné sémantiku standardních operátorů pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="a0faa-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0faa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0faa-120">See Also</span></span>

- [<span data-ttu-id="a0faa-121">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a0faa-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
