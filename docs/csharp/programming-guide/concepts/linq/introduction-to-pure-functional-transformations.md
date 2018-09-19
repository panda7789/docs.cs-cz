---
title: Úvod k čistě funkčním transformacím (C#)
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: f04189c5ae6fc8f6c827f983357ab0126b2c086d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998575"
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="e7ba1-102">Úvod k čistě funkčním transformacím (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="e7ba1-103">Tato část představuje funkčním transformacím, včetně základní koncepty a podpůrné jazykové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="e7ba1-104">To se liší od objektově orientované a funkční transformace přístupy k programování, včetně Rady o tom, jak přechod na ten.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="e7ba1-105">Přestože funkční transformace lze použít v mnoha programovacích scénářů, je použita transformace XML jako konkrétní příklad zde.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7ba1-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e7ba1-106">In This Section</span></span>  
  
|<span data-ttu-id="e7ba1-107">Téma</span><span class="sxs-lookup"><span data-stu-id="e7ba1-107">Topic</span></span>|<span data-ttu-id="e7ba1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e7ba1-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e7ba1-109">Koncepty a terminologie (funkční transformace) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="e7ba1-110">Představuje koncepty a terminologie čistě funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="e7ba1-111">Funkční programování vs. Imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="e7ba1-112">Porovná a výrazně liší od tradičnější imperativního (procesního) programování funkční programování.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="e7ba1-113">Refaktoring do čistých funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="e7ba1-114">Představuje čistě funkce a jsou uvedeny příklady a čistě a znečištěná funkce.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="e7ba1-115">Použitelnost funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="e7ba1-116">Popisuje některé typické scénáře pro funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="e7ba1-117">Funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="e7ba1-118">Popisuje funkční transformace v rámci transformace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="e7ba1-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7ba1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7ba1-119">See Also</span></span>

- [<span data-ttu-id="e7ba1-120">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e7ba1-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
