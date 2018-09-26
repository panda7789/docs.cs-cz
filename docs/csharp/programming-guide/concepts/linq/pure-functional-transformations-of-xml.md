---
title: Čistě funkční transformace XML (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: e05c6167973b2342aafd51aad7d9102db9e94ae0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079977"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="c3e7d-102">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c3e7d-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="c3e7d-103">Tato část obsahuje kurz funkční transformace XML.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="c3e7d-104">Jedná se o vysvětlení hlavní koncepty a jazykové konstrukty, musíte porozumět používání funkčním transformacím a příklady použití funkční transformace pro manipulaci s dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="c3e7d-105">I když tento kurz obsahuje LINQ na příklady kódu XML, všechny základní koncepty platí také pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="c3e7d-106">[Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz obsahuje řadu příkladů, každý stavíme na předchozí.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="c3e7d-107">Tyto příklady ukazují čistě funkční transformace, jehož přístup k manipulaci s XML.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="c3e7d-108">Tento kurz předpokládá praktické znalosti jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="c3e7d-109">V tomto kurzu se neposkytují podrobné sémantiku jazykovým konstrukcím, ale jsou uvedeny odkazy na dokumentaci jazyka podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="c3e7d-110">Taky se předpokládá praktické znalosti základní počítač vědy koncepty a XML, včetně obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3e7d-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c3e7d-111">In This Section</span></span>  
  
|<span data-ttu-id="c3e7d-112">Téma</span><span class="sxs-lookup"><span data-stu-id="c3e7d-112">Topic</span></span>|<span data-ttu-id="c3e7d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c3e7d-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c3e7d-114">Úvod k čistě funkčním transformacím (C#)</span><span class="sxs-lookup"><span data-stu-id="c3e7d-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="c3e7d-115">Popisuje funkčním transformacím a definuje relevantní terminologie.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="c3e7d-116">Kurz: Zřetězení dotazů společně (C#)</span><span class="sxs-lookup"><span data-stu-id="c3e7d-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="c3e7d-117">Popisuje opožděné vyhodnocení a podrobně odloženého provedení.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="c3e7d-118">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="c3e7d-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="c3e7d-119">Kurz demonstrující funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="c3e7d-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3e7d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3e7d-120">See Also</span></span>

- [<span data-ttu-id="c3e7d-121">Dotazování na stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c3e7d-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
