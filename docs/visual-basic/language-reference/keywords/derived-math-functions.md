---
title: Derivované matematické funkce (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836581"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="52bd5-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52bd5-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="52bd5-103">V následující tabulce jsou uvedeny – vnitřní matematické funkce, které může být odvozena z vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="52bd5-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="52bd5-104">Vnitřní matematické funkce se zpřístupní po přidání `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="52bd5-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="52bd5-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="52bd5-105">Function</span></span>|<span data-ttu-id="52bd5-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="52bd5-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="52bd5-107">Secant – (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-107">Secant (Sec(x))</span></span>|<span data-ttu-id="52bd5-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="52bd5-109">Cosecant – (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="52bd5-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="52bd5-111">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="52bd5-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="52bd5-113">Inverzní sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="52bd5-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="52bd5-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="52bd5-115">Inverzní kosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="52bd5-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="52bd5-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="52bd5-117">Inverzní secant – (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="52bd5-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="52bd5-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="52bd5-119">Inverzní cosecant – (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="52bd5-120">Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="52bd5-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="52bd5-121">Inverzní kotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="52bd5-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="52bd5-123">Hyperbolický sinus (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="52bd5-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="52bd5-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="52bd5-125">Hyperbolický kosinus (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="52bd5-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="52bd5-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="52bd5-127">Hyperbolický tangens (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="52bd5-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="52bd5-129">Hyperbolický secant – (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="52bd5-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="52bd5-131">Hyperbolický cosecant – (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="52bd5-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="52bd5-133">Hyperbolický kotangens (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="52bd5-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="52bd5-135">Inverzní hyperbolický sinus (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="52bd5-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="52bd5-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="52bd5-137">Inverzní hyperbolický kosinus (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="52bd5-138">Protokol (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="52bd5-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="52bd5-139">Inverzní hyperbolický tangens (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="52bd5-140">Protokol ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="52bd5-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="52bd5-141">Inverzní hyperbolický secant – (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="52bd5-142">Protokol ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="52bd5-143">Inverzní hyperbolický cosecant – (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="52bd5-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="52bd5-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="52bd5-145">Inverzní hyperbolický kotangens (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="52bd5-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="52bd5-146">Protokol ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="52bd5-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52bd5-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52bd5-147">See also</span></span>

- [<span data-ttu-id="52bd5-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="52bd5-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
