---
title: Matematické funkce
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: ea30ae3b30484c1a13d6d540f121c03afb30ba26
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794598"
---
# <a name="math-functions-visual-basic"></a>Matematické funkce (Visual Basic)

Metody třídy <xref:System.Math?displayProperty=nameWithType> poskytují trigonometrické, logaritmické a další běžné matematické funkce.

## <a name="remarks"></a>Poznámky

Následující tabulka uvádí metody třídy <xref:System.Math?displayProperty=nameWithType>. Můžete je použít v Visual Basic programu:
  
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

Následující tabulka uvádí metody <xref:System.Math?displayProperty=nameWithType> třídy, které neexistují v .NET Framework, ale jsou přidány v .NET Standard nebo .NET Core:

|Metoda .NET|Popis|K dispozici v|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|Vrací úhel, jehož hyperbolický kosinus je zadané číslo.|Počínaje .NET Core 2,1 a .NET Standard 2,1|
|<xref:System.Math.Asinh%2A>|Vrací úhel, jehož hyperbolický sinus je zadané číslo.|Počínaje .NET Core 2,1 a .NET Standard 2,1|
|<xref:System.Math.Atanh%2A>|Vrací úhel, jehož hyperbolický tangens je zadané číslo.|Počínaje .NET Core 2,1 a .NET Standard 2,1|
|<xref:System.Math.BitDecrement%2A>|Vrátí nejbližší nejmenší hodnotu, která porovnává méně než `x`.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.BitIncrement%2A>|Vrátí další největší hodnotu, která porovnává větší hodnotu než `x`.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.Cbrt%2A>|Vrátí kořenovou složku datové krychle zadaného čísla.|Počínaje .NET Core 2,1 a .NET Standard 2,1|
|<xref:System.Math.Clamp%2A>|Vrátí `value` připnuté do celkového rozsahu `min` a `max`.|Počínaje .NET Core 2,0 a .NET Standard 2,1|
|<xref:System.Math.CopySign%2A>|Vrátí hodnotu s velikostí `x` a znaménkem `y`.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.FusedMultiplyAdd%2A>|Vrátí (x \* y) + z a zaokrouhlí se jako jedna Ternární operace.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.ILogB%2A>|Vrátí logaritmus desítkové hodnoty základního 2 zadaného čísla.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.Log2%2A>|Vrátí logaritmus o základu 2 zadaného čísla.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.MaxMagnitude%2A>|Vrátí větší velikost dvou čísel s plovoucí desetinnou čárkou s dvojitou přesností.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.MinMagnitude%2A>|Vrátí menší velikost dvou čísel s plovoucí desetinnou čárkou s dvojitou přesností.|Počínaje rozhraním .NET Core 3,0|
|<xref:System.Math.ScaleB%2A>|Vrátí hodnotu x \* 2 ^ n, která je vypočítána efektivně.|Počínaje rozhraním .NET Core 3,0|

Chcete-li použít tyto funkce bez kvalifikace, importujte <xref:System.Math?displayProperty=nameWithType> obor názvů do projektu přidáním následujícího kódu do horní části zdrojového souboru:

```vb
Imports System.Math
```

## <a name="example---abs"></a>Příklad – ABS

Tento příklad používá metodu <xref:System.Math.Abs%2A> třídy <xref:System.Math> k výpočtu absolutní hodnoty čísla.

```vb
Dim x As Double = Math.Abs(50.3)
Dim y As Double = Math.Abs(-50.3)
Console.WriteLine(x)
Console.WriteLine(y)
' This example produces the following output:
' 50.3
' 50.3
```  

## <a name="example---atan"></a>Příklad – Atan

Tento příklad používá metodu <xref:System.Math.Atan%2A> třídy <xref:System.Math> k výpočtu hodnoty PI.

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> Třída <xref:System.Math?displayProperty=nameWithType> obsahuje <xref:System.Math.PI?displayProperty=nameWithType> pole konstanty. Místo výpočtu ho můžete použít.

## <a name="example---cos"></a>Příklad – cos

V tomto příkladu se používá metoda <xref:System.Math.Cos%2A> třídy <xref:System.Math>, která vrátí kosinus úhlu.

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>Příklad – exp

V tomto příkladu se používá metoda <xref:System.Math.Exp%2A> třídy <xref:System.Math>, která vrátí hodnotu e umocněnou na mocninu.

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>Příklad – protokol

Tento příklad používá metodu <xref:System.Math.Log%2A> třídy <xref:System.Math>, která vrací přirozený logaritmus čísla.

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>Příklad – Round

Tento příklad používá metodu <xref:System.Math.Round%2A> třídy <xref:System.Math> k zaokrouhlení čísla na nejbližší celé číslo.

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>Příklad – Sign

Tento příklad používá metodu <xref:System.Math.Sign%2A> třídy <xref:System.Math> k určení znaménka čísla.

```vb
Dim mySign1 As Integer = Math.Sign(12)
Dim mySign2 As Integer = Math.Sign(-2.4)
Dim mySign3 As Integer = Math.Sign(0)
Console.WriteLine(mySign1)
Console.WriteLine(mySign2)
Console.WriteLine(mySign3)
' The code produces the following output:
' 1
' -1
' 0
```

## <a name="example---sin"></a>Příklad – Sin

Tento příklad používá metodu <xref:System.Math.Sin%2A> třídy <xref:System.Math> k vrácení sinus úhlu.

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>Příklad – odmocnina

Tento příklad používá metodu <xref:System.Math.Sqrt%2A> třídy <xref:System.Math> k výpočtu čtvercového odmocniny čísla.

```vb
Dim mySqrt1 As Double = Math.Sqrt(4)
Dim mySqrt2 As Double = Math.Sqrt(23)
Dim mySqrt3 As Double = Math.Sqrt(0)
Dim mySqrt4 As Double = Math.Sqrt(-4)
Console.WriteLine(mySqrt1)
Console.WriteLine(mySqrt2)
Console.WriteLine(mySqrt3)
Console.WriteLine(mySqrt4)
' The code produces the following output:
' 2
' 4.79583152331272
' 0
' NaN
```

## <a name="example---tan"></a>Příklad – šedobéžová

V tomto příkladu se používá metoda <xref:System.Math.Tan%2A> třídy <xref:System.Math>, která vrací tangens úhlu.

```vb
Public Function Ctan(angle As Double) As Double
    ' Calculate cotangent of an angle, in radians.
    Return 1.0 / Math.Tan(angle)
End Function
```

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Derivované matematické funkce](../keywords/derived-math-functions.md)
- [Aritmetické operátory](../operators/arithmetic-operators.md)
