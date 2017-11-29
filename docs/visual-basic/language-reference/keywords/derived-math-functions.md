---
title: "Derivované matematické funkce (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="6f1dd-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="6f1dd-103">V následující tabulce jsou jiné než vnitřní matematické funkce, které může být odvozen od vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="6f1dd-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="6f1dd-104">Vnitřní matematické funkce dostanete tak, že přidáte `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="6f1dd-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="6f1dd-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="6f1dd-105">Function</span></span>|<span data-ttu-id="6f1dd-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="6f1dd-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="6f1dd-107">Secant – (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-107">Secant (Sec(x))</span></span>|<span data-ttu-id="6f1dd-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="6f1dd-109">Cosecant – (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="6f1dd-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="6f1dd-111">Kotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="6f1dd-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="6f1dd-113">Inverzní sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="6f1dd-114">Atan (x nebo Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="6f1dd-115">Inverzní kosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="6f1dd-116">Atan (-x nebo Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="6f1dd-117">Inverzní secant – (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="6f1dd-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="6f1dd-119">Inverzní cosecant – (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="6f1dd-120">Atan(Sign(x) / Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="6f1dd-121">Inverzní kotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="6f1dd-122">2 * Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="6f1dd-123">Hyperbolický sinus (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="6f1dd-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="6f1dd-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="6f1dd-125">Hyperbolický kosinus (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="6f1dd-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="6f1dd-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="6f1dd-127">Hyperbolický tangens (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="6f1dd-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="6f1dd-129">Secant – hyperbolický (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="6f1dd-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="6f1dd-131">Cosecant – hyperbolický (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="6f1dd-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="6f1dd-133">Hyperbolický kotangens (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="6f1dd-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="6f1dd-135">Inverzní hyperbolický sinus (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="6f1dd-136">Protokol (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="6f1dd-137">Inverzní hyperbolický kosinus (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="6f1dd-138">Protokol (x + Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="6f1dd-139">Inverzní hyperbolický tangens (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="6f1dd-140">Protokol ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="6f1dd-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="6f1dd-141">Inverzní hyperbolický secant – (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="6f1dd-142">Protokol ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="6f1dd-143">Inverzní hyperbolický cosecant – (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="6f1dd-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="6f1dd-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="6f1dd-145">Inverzní hyperbolický kotangens (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="6f1dd-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="6f1dd-146">Protokol ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="6f1dd-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f1dd-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f1dd-147">See Also</span></span>  
 [<span data-ttu-id="6f1dd-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="6f1dd-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
