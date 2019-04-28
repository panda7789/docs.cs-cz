---
title: Čistě funkční transformace XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: 48149faba1c41583ab4e50c539d52e4caf90592a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766451"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="0c9ef-102">Čistě funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9ef-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="0c9ef-103">Tato část obsahuje kurz funkční transformace XML.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="0c9ef-104">Jedná se o vysvětlení hlavní koncepty a jazykové konstrukty, musíte porozumět používání funkčním transformacím a příklady použití funkční transformace pro manipulaci s dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="0c9ef-105">I když tento kurz obsahuje LINQ na příklady kódu XML, všechny základní koncepty platí také pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="0c9ef-106">[Kurzu: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz obsahuje řadu příkladů, každý stavíme na předchozí.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="0c9ef-107">Tyto příklady ukazují čistě funkční transformace, jehož přístup k manipulaci s XML.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="0c9ef-108">Tento kurz předpokládá praktické znalosti jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="0c9ef-109">V tomto kurzu se neposkytují podrobné sémantiku jazykovým konstrukcím, ale jsou uvedeny odkazy na dokumentaci jazyka podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="0c9ef-110">Taky se předpokládá praktické znalosti základní počítač vědy koncepty a XML, včetně obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c9ef-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0c9ef-111">In This Section</span></span>  
  
|<span data-ttu-id="0c9ef-112">Téma</span><span class="sxs-lookup"><span data-stu-id="0c9ef-112">Topic</span></span>|<span data-ttu-id="0c9ef-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0c9ef-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0c9ef-114">Úvod k čistě funkčním transformacím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9ef-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="0c9ef-115">Popisuje funkčním transformacím a definuje relevantní terminologie.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="0c9ef-116">Kurz: Odložené provedení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9ef-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="0c9ef-117">Popisuje opožděné vyhodnocení a podrobně odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="0c9ef-118">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9ef-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="0c9ef-119">Kurz demonstrující funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="0c9ef-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c9ef-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c9ef-120">See also</span></span>

- [<span data-ttu-id="0c9ef-121">Dotazování na stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c9ef-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
