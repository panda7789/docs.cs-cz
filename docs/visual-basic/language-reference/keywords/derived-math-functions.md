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
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349851"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="cacdb-102">Derivované matematické funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cacdb-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="cacdb-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span><span class="sxs-lookup"><span data-stu-id="cacdb-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="cacdb-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span><span class="sxs-lookup"><span data-stu-id="cacdb-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="cacdb-105">Funkce</span><span class="sxs-lookup"><span data-stu-id="cacdb-105">Function</span></span>|<span data-ttu-id="cacdb-106">Derived equivalents</span><span class="sxs-lookup"><span data-stu-id="cacdb-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="cacdb-107">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-107">Secant (Sec(x))</span></span>|<span data-ttu-id="cacdb-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="cacdb-109">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="cacdb-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="cacdb-111">Cotangent (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="cacdb-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="cacdb-113">Inverse sine (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="cacdb-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="cacdb-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="cacdb-115">Inverse cosine (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="cacdb-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="cacdb-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="cacdb-117">Inverse secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="cacdb-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cacdb-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cacdb-119">Inverse cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="cacdb-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cacdb-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cacdb-121">Inverse cotangent (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="cacdb-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="cacdb-123">Hyperbolic sine (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="cacdb-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cacdb-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="cacdb-125">Hyperbolic cosine (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="cacdb-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cacdb-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="cacdb-127">Hyperbolic tangent (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="cacdb-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="cacdb-129">Hyperbolic secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="cacdb-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="cacdb-131">Hyperbolic cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="cacdb-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="cacdb-133">Hyperbolic cotangent (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="cacdb-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="cacdb-135">Inverse hyperbolic sine (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="cacdb-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="cacdb-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="cacdb-137">Inverse hyperbolic cosine (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="cacdb-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cacdb-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cacdb-139">Inverse hyperbolic tangent (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="cacdb-140">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cacdb-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="cacdb-141">Inverse hyperbolic secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="cacdb-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="cacdb-143">Inverse hyperbolic cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="cacdb-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="cacdb-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="cacdb-145">Inverse hyperbolic cotangent (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="cacdb-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="cacdb-146">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="cacdb-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cacdb-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cacdb-147">See also</span></span>

- [<span data-ttu-id="cacdb-148">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="cacdb-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
