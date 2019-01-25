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
ms.openlocfilehash: 1273871faf65afdd1a894c03f13a2c93507c1b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505858"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="ec424-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec424-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="ec424-103">V následující tabulce jsou uvedeny – vnitřní matematické funkce, které může být odvozena z vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="ec424-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="ec424-104">Vnitřní matematické funkce se zpřístupní po přidání `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="ec424-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="ec424-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="ec424-105">Function</span></span>|<span data-ttu-id="ec424-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="ec424-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="ec424-107">Secant – (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-107">Secant (Sec(x))</span></span>|<span data-ttu-id="ec424-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="ec424-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="ec424-109">Cosecant – (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="ec424-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="ec424-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="ec424-111">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="ec424-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="ec424-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="ec424-113">Inverzní sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="ec424-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ec424-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="ec424-115">Inverzní kosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="ec424-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="ec424-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="ec424-117">Inverzní secant – (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="ec424-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ec424-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ec424-119">Inverzní cosecant – (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="ec424-120">Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ec424-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ec424-121">Inverzní kotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="ec424-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="ec424-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="ec424-123">Hyperbolický sinus (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="ec424-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ec424-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ec424-125">Hyperbolický kosinus (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="ec424-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ec424-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ec424-127">Hyperbolický tangens (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="ec424-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ec424-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ec424-129">Hyperbolický secant – (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="ec424-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ec424-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ec424-131">Hyperbolický cosecant – (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="ec424-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ec424-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ec424-133">Hyperbolický kotangens (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="ec424-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ec424-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ec424-135">Inverzní hyperbolický sinus (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="ec424-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ec424-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="ec424-137">Inverzní hyperbolický kosinus (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="ec424-138">Protokol (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ec424-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ec424-139">Inverzní hyperbolický tangens (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="ec424-140">Protokol ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ec424-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="ec424-141">Inverzní hyperbolický secant – (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="ec424-142">Protokol ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ec424-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ec424-143">Inverzní hyperbolický cosecant – (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="ec424-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ec424-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ec424-145">Inverzní hyperbolický kotangens (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="ec424-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="ec424-146">Protokol ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="ec424-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec424-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec424-147">See also</span></span>
- [<span data-ttu-id="ec424-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="ec424-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
