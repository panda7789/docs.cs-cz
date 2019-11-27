---
title: Matematické funkce
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: b1cd6a846a7dc1dddcf6bdb5eb99ebc1c57a012c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348063"
---
# <a name="math-functions-visual-basic"></a>Matematické funkce (Visual Basic)
Metody třídy <xref:System.Math?displayProperty=nameWithType> poskytují trigonometrické, logaritmické a další běžné matematické funkce.  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí metody třídy <xref:System.Math?displayProperty=nameWithType>. Můžete je použít v Visual Basic programu.  
  
|Metoda .NET|Popis|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Vrátí absolutní hodnotu čísla.|  
|<xref:System.Math.Acos%2A>|Vrací úhel, jehož kosinus je zadané číslo.|  
|<xref:System.Math.Asin%2A>|Vrací úhel, jehož sinus je zadané číslo.|  
|<xref:System.Math.Atan%2A>|Vrací úhel, jehož tangens odpovídá určenému číslu.|  
|<xref:System.Math.Atan2%2A>|Vrátí úhel, jehož tangens odpovídá podílu dvou zadaných čísel.|  
|<xref:System.Math.BigMul%2A>|Vrátí úplný součin 2 32 bitů čísel.|  
|<xref:System.Math.Ceiling%2A>|Vrátí nejmenší celočíselnou hodnotu, která je větší nebo rovna zadanému `Decimal` nebo `Double`.|  
|<xref:System.Math.Cos%2A>|Vrací kosinus určeného úhlu.|  
|<xref:System.Math.Cosh%2A>|Vrací hyperbolický kosinus určeného úhlu.|  
|<xref:System.Math.DivRem%2A>|Vrátí podíl 2 32 nebo 64 celých čísel se znaménkem a vrátí zbytek v parametru Output.|  
|<xref:System.Math.Exp%2A>|Vrátí hodnotu e (základ přirozeného logaritmu) vyvolanou pro zadanou mocninu.|  
|<xref:System.Math.Floor%2A>|Vrátí největší celé číslo, které je menší nebo rovno zadanému `Decimal` nebo `Double`mu číslu.|  
|<xref:System.Math.IEEERemainder%2A>|Vrátí zbytek, který je výsledkem dělení zadaného čísla jiným zadaným číslem.|  
|<xref:System.Math.Log%2A>|Vrátí přirozený (základ e) logaritmus zadaného čísla nebo logaritmus zadaného čísla v zadaném základu.|  
|<xref:System.Math.Log10%2A>|Vrátí logaritmus o základu 10 zadaného čísla.|  
|<xref:System.Math.Max%2A>|Vrátí větší ze dvou čísel.|  
|<xref:System.Math.Min%2A>|Vrátí menší ze dvou čísel.|  
|<xref:System.Math.Pow%2A>|Vrátí zadané číslo umocněné na zadané napájení.|  
|<xref:System.Math.Round%2A>|Vrátí `Decimal` nebo hodnotu `Double` zaokrouhlenou na nejbližší celočíselnou hodnotu nebo na zadaný počet zlomkových číslic.|  
|<xref:System.Math.Sign%2A>|Vrací hodnotu `Integer` označující znaménko čísla.|  
|<xref:System.Math.Sin%2A>|Vrací sinus určeného úhlu.|  
|<xref:System.Math.Sinh%2A>|Vrací hyperbolický sinus určeného úhlu.|  
|<xref:System.Math.Sqrt%2A>|Vrátí druhou odmocninu určeného čísla.|  
|<xref:System.Math.Tan%2A>|Vrací tangens určeného úhlu.|  
|<xref:System.Math.Tanh%2A>|Vrací hyperbolický tangens určeného úhlu.|  
|<xref:System.Math.Truncate%2A>|Vypočítá integrální část zadaného `Decimal` nebo `Double` číslo.|  
  
 Chcete-li použít tyto funkce bez kvalifikace, importujte <xref:System.Math?displayProperty=nameWithType> obor názvů do projektu přidáním následujícího kódu do horní části zdrojového souboru:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Abs%2A> třídy <xref:System.Math> k výpočtu absolutní hodnoty čísla.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Atan%2A> třídy <xref:System.Math> k výpočtu hodnoty PI.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá metoda <xref:System.Math.Cos%2A> třídy <xref:System.Math>, která vrátí kosinus úhlu.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá metoda <xref:System.Math.Exp%2A> třídy <xref:System.Math>, která vrátí hodnotu e umocněnou na mocninu.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Log%2A> třídy <xref:System.Math>, která vrací přirozený logaritmus čísla.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Round%2A> třídy <xref:System.Math> k zaokrouhlení čísla na nejbližší celé číslo.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Sign%2A> třídy <xref:System.Math> k určení znaménka čísla.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Sin%2A> třídy <xref:System.Math> k vrácení sinus úhlu.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad používá metodu <xref:System.Math.Sqrt%2A> třídy <xref:System.Math> k výpočtu čtvercového odmocniny čísla.  
  
```vb
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
 V tomto příkladu se používá metoda <xref:System.Math.Tan%2A> třídy <xref:System.Math>, která vrací tangens úhlu.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Požadavky  
 **Třída:** <xref:System.Math>  
  
 **Obor názvů:** <xref:System>  
  
 **Sestavení:** mscorlib (v mscorlib. dll)  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Derivované matematické funkce](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
