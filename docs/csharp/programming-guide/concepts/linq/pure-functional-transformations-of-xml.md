---
title: "Čistý funkční transformace XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32259e0b75d8c098663b589f33e2f36344fb15cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="5360c-102">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5360c-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="5360c-103">Tato část obsahuje návod funkční transformace pro formát XML.</span><span class="sxs-lookup"><span data-stu-id="5360c-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="5360c-104">To zahrnuje vysvětlení hlavní koncepty a jazyk vytvoří, musíte pochopit použít funkční transformace a příklady použití funkční transformace k manipulaci s dokument XML.</span><span class="sxs-lookup"><span data-stu-id="5360c-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="5360c-105">I když v tomto kurzu poskytuje LINQ příklady kódu XML, všechny základní koncepty platí také pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="5360c-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="5360c-106">[Kurz: manipulace s obsahu v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu poskytuje řadu příklady, každá je postavena na předchozí.</span><span class="sxs-lookup"><span data-stu-id="5360c-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="5360c-107">Tyto příklady ukazují funkční způsob čistý transformational manipulace s kódem XML.</span><span class="sxs-lookup"><span data-stu-id="5360c-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="5360c-108">Tento kurz předpokládá praktické znalosti jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5360c-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="5360c-109">Podrobné sémantiku jazykové konstrukty nejsou k dispozici v tomto kurzu, ale jsou uvedeny odkazy na dokumentaci jazyk podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="5360c-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="5360c-110">Taky se předpokládá praktické znalosti základní počítač vědecké účely koncepty a XML, včetně obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="5360c-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5360c-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5360c-111">In This Section</span></span>  
  
|<span data-ttu-id="5360c-112">Téma</span><span class="sxs-lookup"><span data-stu-id="5360c-112">Topic</span></span>|<span data-ttu-id="5360c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5360c-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5360c-114">Úvod do čistého funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="5360c-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="5360c-115">Popisuje funkční transformace a definuje relevantní technologiím.</span><span class="sxs-lookup"><span data-stu-id="5360c-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="5360c-116">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="5360c-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="5360c-117">Popisuje opožděné vyhodnocení a odložené provedení podrobně.</span><span class="sxs-lookup"><span data-stu-id="5360c-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="5360c-118">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="5360c-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="5360c-119">Kurz, který ukazuje funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="5360c-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5360c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5360c-120">See Also</span></span>  
 [<span data-ttu-id="5360c-121">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5360c-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
