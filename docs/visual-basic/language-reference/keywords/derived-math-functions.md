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
# <a name="derived-math-functions-visual-basic"></a>Derivované matematické funkce (Visual Basic)
V následující tabulce jsou uvedeny nevnitřní matematické funkce, které lze odvodit z vnitřních matematických funkcí <xref:System.Math?displayProperty=nameWithType> objektu. K vnitřním matematickým funkcím můžete přistupovat přidáním `Imports System.Math` do souboru nebo projektu.  
  
|Funkce|Odvozené ekvivalenty|  
|--------------|-------------------------|  
|Sekans (SEC (x))|1/cos (x)|  
|Kosekans (CSC (x))|1/sin (x)|  
|Kotangens (CTAN (x))|1/Tan (x)|  
|Inverzní sinus (ASIN (x))|Atan (x/SQRT (-x * x + 1))|  
|Inverzní kosinus (acos (x))|Atan (-x/SQRT (-x * x + 1)) + 2 \* Atan (1)|  
|Inverzní funkce sekans (asec (x))|2 * Atan (1) – Atan (podpis (x)/SQRT (x \* x – 1))|  
|Inverzní kosekans (acsc (x))|Atan (Sign (x)/SQRT (x * x – 1))|  
|Inverzní kotangens (ACOT (x))|2 * Atan (1) – Atan (x)|  
|Hyperbolický sinus (sinh – (x))|(EXP (x) – EXP (-x))/2|  
|Hyperbolický kosinus (cosh – (x))|(EXP (x) + EXP (-x))/2|  
|Hyperbolický tangens (tanh – (x))|(EXP (x) – EXP (-x))/(EXP (x) + EXP (-x))|  
|Hyperbolický sekans (sech (x))|2/(EXP (x) + EXP (-x))|  
|Hyperbolický kosekans (csch (x))|2/(EXP (x) – EXP (-x))|  
|Hyperbolický kotangens (coth (x))|(EXP (x) + EXP (-x))/(EXP (x) – EXP (-x))|  
|Inverzní hyperbolický sinus (asinh – (x))|Protokol (x + SQRT (x * x + 1))|  
|Inverzní hyperbolický kosinus (acosh – (x))|Protokol (x + SQRT (x * x – 1))|  
|Inverzní hyperbolický tangens (atanh – (x))|Protokol ((1 + x)/(1 – x))/2|  
|Inverzní hyperbolický sekans (AsecH (x))|Log ((sqrt (-x * x + 1) + 1)/x)|  
|Inverzní hyperbolický kosekans (acsch (x))|Log (znaménko (x) * SQRT (x \* x + 1) + 1)/x)|  
|Inverzní hyperbolický kotangens (acoth (x))|Protokol ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Viz také

- [Matematické funkce](../functions/math-functions.md)
