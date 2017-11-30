---
title: "Čistý funkční transformace XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01ad228d91037de1585d1e66292fddb80c785ada
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="7aafd-102">Čistý funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aafd-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="7aafd-103">Tato část obsahuje návod funkční transformace pro formát XML.</span><span class="sxs-lookup"><span data-stu-id="7aafd-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="7aafd-104">To zahrnuje vysvětlení hlavní koncepty a jazyk vytvoří, musíte pochopit použít funkční transformace a příklady použití funkční transformace k manipulaci s dokument XML.</span><span class="sxs-lookup"><span data-stu-id="7aafd-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="7aafd-105">I když v tomto kurzu poskytuje LINQ příklady kódu XML, všechny základní koncepty platí také pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="7aafd-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="7aafd-106">[Kurz: manipulace s obsahu v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurzu poskytuje řadu příklady, každá je postavena na předchozí.</span><span class="sxs-lookup"><span data-stu-id="7aafd-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="7aafd-107">Tyto příklady ukazují funkční způsob čistý transformational manipulace s kódem XML.</span><span class="sxs-lookup"><span data-stu-id="7aafd-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="7aafd-108">Tento kurz předpokládá praktické znalosti jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7aafd-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="7aafd-109">Podrobné sémantiku jazykové konstrukty nejsou k dispozici v tomto kurzu, ale jsou uvedeny odkazy na dokumentaci jazyk podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="7aafd-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="7aafd-110">Taky se předpokládá praktické znalosti základní počítač vědecké účely koncepty a XML, včetně obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="7aafd-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7aafd-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7aafd-111">In This Section</span></span>  
  
|<span data-ttu-id="7aafd-112">Téma</span><span class="sxs-lookup"><span data-stu-id="7aafd-112">Topic</span></span>|<span data-ttu-id="7aafd-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7aafd-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7aafd-114">Úvod do čistého funkční transformace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aafd-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="7aafd-115">Popisuje funkční transformace a definuje relevantní technologiím.</span><span class="sxs-lookup"><span data-stu-id="7aafd-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="7aafd-116">Kurz: Odložený provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aafd-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="7aafd-117">Popisuje opožděné vyhodnocení a odložené provedení podrobně.</span><span class="sxs-lookup"><span data-stu-id="7aafd-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="7aafd-118">Kurz: Manipulace se obsah v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aafd-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="7aafd-119">Kurz, který ukazuje funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="7aafd-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7aafd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aafd-120">See Also</span></span>  
 [<span data-ttu-id="7aafd-121">Dotazování stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aafd-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
