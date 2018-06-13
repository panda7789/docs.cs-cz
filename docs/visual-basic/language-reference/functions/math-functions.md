---
title: Matematické funkce (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: 9c55b48cbc285ab5ed8742a23af43d3a017a35e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604533"
---
# <a name="math-functions-visual-basic"></a>Matematické funkce (Visual Basic)
Metody <xref:System.Math?displayProperty=nameWithType> třída poskytnout trigonometrické, logaritmické a další běžné matematické funkce.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí metody <xref:System.Math?displayProperty=nameWithType> třídy. Pomocí těchto v programu jazyka Visual Basic.  
  
|Rozhraní .NET framework – metoda|Popis|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Vrátí absolutní hodnotu čísla.|  
|<xref:System.Math.Acos%2A>|Vrací úhel, jehož kosinus odpovídá určenému číslu.|  
|<xref:System.Math.Asin%2A>|Vrací úhel, jehož sinus odpovídá určenému číslu.|  
|<xref:System.Math.Atan%2A>|Vrací úhel, jehož tangens odpovídá určenému číslu.|  
|<xref:System.Math.Atan2%2A>|Vrací úhel, jehož tangens odpovídá podílu dvou zadaných čísel.|  
|<xref:System.Math.BigMul%2A>|Vrátí úplný součin dvou 32bitových čísel.|  
|<xref:System.Math.Ceiling%2A>|Vrátí nejmenší integrální hodnotu, která je větší než nebo rovna hodnotě zadané `Decimal` nebo `Double`.|  
|<xref:System.Math.Cos%2A>|Vrací kosinus určeného úhlu.|  
|<xref:System.Math.Cosh%2A>|Vrací hyperbolický kosinus určeného úhlu.|  
|<xref:System.Math.DivRem%2A>|Vrátí podíl dvou 32bitovou nebo 64bitovou podepsaná celá čísla a také vrátí zbytek výstupní parametr.|  
|<xref:System.Math.Exp%2A>|Vrátí číslo e (základ přirozeného logaritmu) na zadanou mocninu.|  
|<xref:System.Math.Floor%2A>|Vrátí největší celé číslo, které je menší než nebo rovna zadané `Decimal` nebo `Double` číslo.|  
|<xref:System.Math.IEEERemainder%2A>|Vrátí zbytek, která je výsledkem dělení určeného čísla jiným zadat číslo.|  
|<xref:System.Math.Log%2A>|Vrátí přirozený (základ e) logaritmus určeného čísla nebo logaritmus určeného čísla o zadaném základu.|  
|<xref:System.Math.Log10%2A>|Vrátí logaritmus o základu 10 určeného čísla.|  
|<xref:System.Math.Max%2A>|Vrátí větší dvou čísel.|  
|<xref:System.Math.Min%2A>|Vrátí menší ze dvou čísel.|  
|<xref:System.Math.Pow%2A>|Vrátí zadané číslo na zadanou mocninu.|  
|<xref:System.Math.Round%2A>|Vrátí `Decimal` nebo `Double` hodnota zaokrouhlí na nejbližší hodnotu integrální nebo zadaný počet míst za desetinnou čárkou.|  
|<xref:System.Math.Sign%2A>|Vrátí `Integer` hodnotu udávající znaménko čísla.|  
|<xref:System.Math.Sin%2A>|Vrací sinus určeného úhlu.|  
|<xref:System.Math.Sinh%2A>|Vrací hyperbolický sinus určeného úhlu.|  
|<xref:System.Math.Sqrt%2A>|Vrátí druhou odmocninu určeného čísla.|  
|<xref:System.Math.Tan%2A>|Vrací tangens určeného úhlu.|  
|<xref:System.Math.Tanh%2A>|Vrací hyperbolický tangens určeného úhlu.|  
|<xref:System.Math.Truncate%2A>|Vypočítá nedílnou součástí zadané `Decimal` nebo `Double` číslo.|  
  
 Chcete-li použít tyto funkce bez kvalifikace, importujte <xref:System.Math?displayProperty=nameWithType> oboru názvů do projektu přidáním následující kód do horní části souboru zdroje:  
  
```  
Imports System.Math  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Abs%2A> metodu <xref:System.Math> třídy pro výpočet absolutní hodnotu čísla.  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Atan%2A> metodu <xref:System.Math> třída vypočítat hodnotu čísla pí.  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Cos%2A> metodu <xref:System.Math> třídy vracení kosinus úhlu.  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Exp%2A> metodu <xref:System.Math> třídy vrátí číslo e umocněné na zadanou mocninu.  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Log%2A> metodu <xref:System.Math> třídy vracení přirozený logaritmus čísla.  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Round%2A> metodu <xref:System.Math> třídy Zaokrouhlí číslo na nejbližší celé číslo.  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Sign%2A> metodu <xref:System.Math> třídu k určení znaménko čísla.  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Sin%2A> metodu <xref:System.Math> třídy Vrátí sinus úhlu.  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Sqrt%2A> metodu <xref:System.Math> třídy, které chcete vypočítat druhou odmocninu čísla.  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Math.Tan%2A> metodu <xref:System.Math> třídy Vrátí tangens úhlu.  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Požadavky  
 **Třída:** <xref:System.Math>  
  
 **Namespace:** <xref:System>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [Derivované matematické funkce](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
