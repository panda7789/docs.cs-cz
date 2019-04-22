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
# <a name="derived-math-functions-visual-basic"></a>Derivované matematické funkce (Visual Basic)
V následující tabulce jsou uvedeny – vnitřní matematické funkce, které může být odvozena z vnitřní matematické funkce <xref:System.Math?displayProperty=nameWithType> objektu. Vnitřní matematické funkce se zpřístupní po přidání `Imports System.Math` do souboru nebo projektu.  
  
|Funkce|Odvozené ekvivalenty|  
|--------------|-------------------------|  
|Secant – (Sec(x))|1 / Cos(x)|  
|Cosecant – (Csc(x))|1 / Sin(x)|  
|Cotangent (Ctan(x))|1 / Tan(x)|  
|Inverzní sinus (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|Inverzní kosinus (Acos(x))|Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)|  
|Inverzní secant – (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))|  
|Inverzní cosecant – (Acsc(x))|Atan(Sign(x) / Sqrt (x * x – 1))|  
|Inverzní kotangens (Acot(x))|2 * Atan(1) - Atan(x)|  
|Hyperbolický sinus (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Hyperbolický kosinus (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Hyperbolický tangens (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Hyperbolický secant – (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Hyperbolický cosecant – (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Hyperbolický kotangens (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Inverzní hyperbolický sinus (Asinh(x))|Log(x + Sqrt(x * x + 1))|  
|Inverzní hyperbolický kosinus (Acosh(x))|Protokol (x + Sqrt (x * x – 1))|  
|Inverzní hyperbolický tangens (Atanh(x))|Protokol ((1 + x) / (1 – x)) / 2|  
|Inverzní hyperbolický secant – (AsecH(x))|Protokol ((Sqrt (-x * x + 1) + 1) / x)|  
|Inverzní hyperbolický cosecant – (Acsch(x))|Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)|  
|Inverzní hyperbolický kotangens (Acoth(x))|Protokol ((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>Viz také:

- [Matematické funkce](../../../visual-basic/language-reference/functions/math-functions.md)
