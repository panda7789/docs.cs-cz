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
ms.openlocfilehash: 87faa623f5b145eec8b88e350fce4171125324dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596805"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="4763a-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4763a-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="4763a-103">V následující tabulce jsou jiné než vnitřní matematické funkce, které může být odvozen od vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="4763a-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="4763a-104">Vnitřní matematické funkce dostanete tak, že přidáte `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="4763a-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="4763a-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="4763a-105">Function</span></span>|<span data-ttu-id="4763a-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="4763a-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="4763a-107">Secant – (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-107">Secant (Sec(x))</span></span>|<span data-ttu-id="4763a-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="4763a-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="4763a-109">Cosecant – (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="4763a-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="4763a-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="4763a-111">Kotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="4763a-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="4763a-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="4763a-113">Inverzní sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="4763a-114">Atan (x nebo Sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="4763a-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="4763a-115">Inverzní kosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="4763a-116">Atan (-x nebo Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="4763a-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="4763a-117">Inverzní secant – (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="4763a-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="4763a-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="4763a-119">Inverzní cosecant – (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="4763a-120">Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="4763a-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="4763a-121">Inverzní kotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="4763a-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="4763a-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="4763a-123">Hyperbolický sinus (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="4763a-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="4763a-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="4763a-125">Hyperbolický kosinus (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="4763a-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="4763a-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="4763a-127">Hyperbolický tangens (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="4763a-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="4763a-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="4763a-129">Secant – hyperbolický (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="4763a-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="4763a-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="4763a-131">Cosecant – hyperbolický (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="4763a-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="4763a-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="4763a-133">Hyperbolický kotangens (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="4763a-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="4763a-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="4763a-135">Inverzní hyperbolický sinus (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="4763a-136">Protokol (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="4763a-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="4763a-137">Inverzní hyperbolický kosinus (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="4763a-138">Protokol (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="4763a-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="4763a-139">Inverzní hyperbolický tangens (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="4763a-140">Protokol ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="4763a-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="4763a-141">Inverzní hyperbolický secant – (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="4763a-142">Protokol ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="4763a-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="4763a-143">Inverzní hyperbolický cosecant – (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="4763a-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="4763a-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="4763a-145">Inverzní hyperbolický kotangens (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="4763a-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="4763a-146">Protokol ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="4763a-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4763a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="4763a-147">See Also</span></span>  
 [<span data-ttu-id="4763a-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="4763a-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
