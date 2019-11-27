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
# <a name="derived-math-functions-visual-basic"></a>Derivované matematické funkce (Visual Basic)
V následující tabulce jsou uvedeny nevnitřní matematické funkce, které lze odvodit z vnitřních matematických funkcí objektu <xref:System.Math?displayProperty=nameWithType>. K vnitřním funkcím matematiky můžete přistupovat přidáním `Imports System.Math` do souboru nebo projektu.  
  
|Funkce|Odvozené ekvivalenty|  
|--------------|-------------------------|  
|Sekans (SEC (x))|1 / Cos(x)|  
|Kosekans (CSC (x))|1 / Sin(x)|  
|Kotangens (CTAN (x))|1/Tan (x)|  
|Inverzní sinus (ASIN (x))|Atan (x/SQRT (-x * x + 1))|  
|Inverzní kosinus (acos (x))|Atan (-x/SQRT (-x * x + 1)) + 2 \* Atan (1)|  
|Inverzní funkce sekans (asec (x))|2 * Atan (1) – Atan (podpis (x)/SQRT (x \* x – 1))|  
|Inverzní kosekans (acsc (x))|Atan (Sign (x)/SQRT (x * x – 1))|  
|Inverzní kotangens (ACOT (x))|2 * Atan (1) – Atan (x)|  
|Hyperbolický sinus (sinh – (x))|(Exp(x) – Exp(-x)) / 2|  
|Hyperbolický kosinus (cosh – (x))|(Exp(x) + Exp(-x)) / 2|  
|Hyperbolický tangens (tanh – (x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Hyperbolický sekans (sech (x))|2 / (Exp(x) + Exp(-x))|  
|Hyperbolický kosekans (csch (x))|2 / (Exp(x) – Exp(-x))|  
|Hyperbolický kotangens (coth (x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Inverzní hyperbolický sinus (asinh – (x))|Protokol (x + SQRT (x * x + 1))|  
|Inverzní hyperbolický kosinus (acosh – (x))|Protokol (x + SQRT (x * x – 1))|  
|Inverzní hyperbolický tangens (atanh – (x))|Protokol ((1 + x)/(1 – x))/2|  
|Inverzní hyperbolický sekans (AsecH (x))|Log ((sqrt (-x * x + 1) + 1)/x)|  
|Inverzní hyperbolický kosekans (acsch (x))|Log (znaménko (x) * SQRT (x \* x + 1) + 1)/x)|  
|Inverzní hyperbolický kotangens (acoth (x))|Protokol ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Viz také:

- [Matematické funkce](../../../visual-basic/language-reference/functions/math-functions.md)
