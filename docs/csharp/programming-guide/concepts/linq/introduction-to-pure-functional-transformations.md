---
title: "Úvod do čistého funkční transformace (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 535d022b68fd4d08f04648fb98f5a7a7c53ed6e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="b3609-102">Úvod do čistého funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="b3609-103">Tato část představuje funkční transformací, včetně základní koncepty a podpůrné jazyk vytvoří.</span><span class="sxs-lookup"><span data-stu-id="b3609-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="b3609-104">Výrazně liší od objektově orientované a funkční transformace přístupy k programování, včetně pokynů pro přecházení ty druhé.</span><span class="sxs-lookup"><span data-stu-id="b3609-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="b3609-105">Funkční transformace lze v mnoha scénáře programování, ale transformace XML slouží jako konkrétní příklad sem.</span><span class="sxs-lookup"><span data-stu-id="b3609-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3609-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b3609-106">In This Section</span></span>  
  
|<span data-ttu-id="b3609-107">Téma</span><span class="sxs-lookup"><span data-stu-id="b3609-107">Topic</span></span>|<span data-ttu-id="b3609-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b3609-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b3609-109">Principy a terminologií (funkční transformaci) (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="b3609-110">Představuje koncepty a přehled terminologie čistý funkční transformací.</span><span class="sxs-lookup"><span data-stu-id="b3609-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="b3609-111">Funkční programování vs. Imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="b3609-112">Porovná a výrazně liší od funkční programování do tradičnější imperativní programování (procedurální).</span><span class="sxs-lookup"><span data-stu-id="b3609-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="b3609-113">Refaktoring do čistého funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="b3609-114">Zavádí čistý funkce a jsou uvedeny příklady a čistý a znečištěná funkce.</span><span class="sxs-lookup"><span data-stu-id="b3609-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="b3609-115">Použitelnost funkční transformaci (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="b3609-116">Popisuje typické scénáře funkční transformace.</span><span class="sxs-lookup"><span data-stu-id="b3609-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="b3609-117">Funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3609-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="b3609-118">Popisuje funkční transformace v kontextu transformace stromy XML.</span><span class="sxs-lookup"><span data-stu-id="b3609-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3609-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3609-119">See Also</span></span>  
 [<span data-ttu-id="b3609-120">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b3609-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
