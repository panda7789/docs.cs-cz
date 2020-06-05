---
title: Derivované matematické funkce
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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373879"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="f4b2b-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="f4b2b-103">V následující tabulce jsou uvedeny nevnitřní matematické funkce, které lze odvodit z vnitřních matematických funkcí <xref:System.Math?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="f4b2b-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="f4b2b-104">K vnitřním matematickým funkcím můžete přistupovat přidáním `Imports System.Math` do souboru nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="f4b2b-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="f4b2b-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="f4b2b-105">Function</span></span>|<span data-ttu-id="f4b2b-106">Odvozené ekvivalenty</span><span class="sxs-lookup"><span data-stu-id="f4b2b-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="f4b2b-107">Sekans (SEC (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-107">Secant (Sec(x))</span></span>|<span data-ttu-id="f4b2b-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="f4b2b-109">Kosekans (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="f4b2b-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="f4b2b-111">Kotangens (CTAN (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="f4b2b-112">1/Tan (x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="f4b2b-113">Inverzní sinus (ASIN (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="f4b2b-114">Atan (x/SQRT (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="f4b2b-115">Inverzní kosinus (acos (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="f4b2b-116">Atan (-x/SQRT (-x \* x + 1)) + 2 \* Atan (1)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="f4b2b-117">Inverzní funkce sekans (asec (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="f4b2b-118">2 \* Atan (1) – Atan (podpis (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f4b2b-119">Inverzní kosekans (acsc (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="f4b2b-120">Atan (Sign (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f4b2b-121">Inverzní kotangens (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="f4b2b-122">2 \* Atan (1) – Atan (x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="f4b2b-123">Hyperbolický sinus (sinh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="f4b2b-124">(EXP (x) – EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="f4b2b-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="f4b2b-125">Hyperbolický kosinus (cosh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="f4b2b-126">(EXP (x) + EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="f4b2b-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="f4b2b-127">Hyperbolický tangens (tanh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="f4b2b-128">(EXP (x) – EXP (-x))/(EXP (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="f4b2b-129">Hyperbolický sekans (sech (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="f4b2b-130">2/(EXP (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="f4b2b-131">Hyperbolický kosekans (csch (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="f4b2b-132">2/(EXP (x) – EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="f4b2b-133">Hyperbolický kotangens (coth (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="f4b2b-134">(EXP (x) + EXP (-x))/(EXP (x) – EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="f4b2b-135">Inverzní hyperbolický sinus (asinh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="f4b2b-136">Protokol (x + SQRT (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="f4b2b-137">Inverzní hyperbolický kosinus (acosh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="f4b2b-138">Protokol (x + SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f4b2b-139">Inverzní hyperbolický tangens (atanh – (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="f4b2b-140">Protokol ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="f4b2b-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="f4b2b-141">Inverzní hyperbolický sekans (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="f4b2b-142">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="f4b2b-143">Inverzní hyperbolický kosekans (acsch (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="f4b2b-144">Log (znaménko (x) \* SQRT (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="f4b2b-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="f4b2b-145">Inverzní hyperbolický kotangens (acoth (x))</span><span class="sxs-lookup"><span data-stu-id="f4b2b-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="f4b2b-146">Protokol ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="f4b2b-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4b2b-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4b2b-147">See also</span></span>

- [<span data-ttu-id="f4b2b-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="f4b2b-148">Math Functions</span></span>](../functions/math-functions.md)
