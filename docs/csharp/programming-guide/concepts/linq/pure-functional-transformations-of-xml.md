---
title: Čistý funkční transformace XML (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: 7bbe5735541432108794959a7889976d4951fffd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336707"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="27780-102">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="27780-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="27780-103">Tato část obsahuje návod funkční transformace pro formát XML.</span><span class="sxs-lookup"><span data-stu-id="27780-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="27780-104">To zahrnuje vysvětlení hlavní koncepty a jazyk vytvoří, musíte pochopit použít funkční transformace a příklady použití funkční transformace k manipulaci s dokument XML.</span><span class="sxs-lookup"><span data-stu-id="27780-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="27780-105">I když v tomto kurzu poskytuje LINQ příklady kódu XML, všechny základní koncepty platí také pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="27780-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="27780-106">[Kurz: manipulace s obsahu v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu poskytuje řadu příklady, každá je postavena na předchozí.</span><span class="sxs-lookup"><span data-stu-id="27780-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="27780-107">Tyto příklady ukazují funkční způsob čistý transformational manipulace s kódem XML.</span><span class="sxs-lookup"><span data-stu-id="27780-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="27780-108">Tento kurz předpokládá praktické znalosti jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="27780-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="27780-109">Podrobné sémantiku jazykové konstrukty nejsou k dispozici v tomto kurzu, ale jsou uvedeny odkazy na dokumentaci jazyk podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="27780-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="27780-110">Taky se předpokládá praktické znalosti základní počítač vědecké účely koncepty a XML, včetně obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="27780-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27780-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27780-111">In This Section</span></span>  
  
|<span data-ttu-id="27780-112">Téma</span><span class="sxs-lookup"><span data-stu-id="27780-112">Topic</span></span>|<span data-ttu-id="27780-113">Popis</span><span class="sxs-lookup"><span data-stu-id="27780-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="27780-114">Úvod do čistého funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="27780-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="27780-115">Popisuje funkční transformace a definuje relevantní technologiím.</span><span class="sxs-lookup"><span data-stu-id="27780-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="27780-116">Kurz: Řetězení dotazy společně (C#)</span><span class="sxs-lookup"><span data-stu-id="27780-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="27780-117">Popisuje opožděné vyhodnocení a odložené provedení podrobně.</span><span class="sxs-lookup"><span data-stu-id="27780-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="27780-118">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="27780-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="27780-119">Kurz, který ukazuje funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="27780-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27780-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="27780-120">See Also</span></span>  
 [<span data-ttu-id="27780-121">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="27780-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
