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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801891"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="0d2e4-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="0d2e4-103">V následující tabulce jsou uvedeny – vnitřní matematické funkce, které může být odvozena z vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="0d2e4-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="0d2e4-104">Vnitřní matematické funkce se zpřístupní po přidání `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="0d2e4-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="0d2e4-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="0d2e4-105">Function</span></span>|<span data-ttu-id="0d2e4-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="0d2e4-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="0d2e4-107">Secant – (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-107">Secant (Sec(x))</span></span>|<span data-ttu-id="0d2e4-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="0d2e4-109">Cosecant – (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="0d2e4-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="0d2e4-111">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="0d2e4-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="0d2e4-113">Inverzní sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="0d2e4-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="0d2e4-115">Inverzní kosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="0d2e4-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="0d2e4-117">Inverzní secant – (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="0d2e4-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0d2e4-119">Inverzní cosecant – (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="0d2e4-120">Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0d2e4-121">Inverzní kotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="0d2e4-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="0d2e4-123">Hyperbolický sinus (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="0d2e4-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="0d2e4-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="0d2e4-125">Hyperbolický kosinus (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="0d2e4-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="0d2e4-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="0d2e4-127">Hyperbolický tangens (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="0d2e4-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="0d2e4-129">Hyperbolický secant – (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="0d2e4-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="0d2e4-131">Hyperbolický cosecant – (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="0d2e4-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="0d2e4-133">Hyperbolický kotangens (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="0d2e4-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="0d2e4-135">Inverzní hyperbolický sinus (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="0d2e4-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="0d2e4-137">Inverzní hyperbolický kosinus (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="0d2e4-138">Protokol (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0d2e4-139">Inverzní hyperbolický tangens (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="0d2e4-140">Protokol ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="0d2e4-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="0d2e4-141">Inverzní hyperbolický secant – (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="0d2e4-142">Protokol ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="0d2e4-143">Inverzní hyperbolický cosecant – (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="0d2e4-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="0d2e4-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="0d2e4-145">Inverzní hyperbolický kotangens (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="0d2e4-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="0d2e4-146">Protokol ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="0d2e4-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d2e4-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d2e4-147">See also</span></span>

- [<span data-ttu-id="0d2e4-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="0d2e4-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
