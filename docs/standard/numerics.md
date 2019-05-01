---
title: Číslovky v technologii .NET
ms.date: 10/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f180e459764d6e8e4484072218f01c8bab8a3b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973456"
---
# <a name="numerics-in-net"></a>Číslovky v technologii .NET

.NET poskytuje celou řadu číselné celé číslo s plovoucí desetinnou čárkou primitiv, stejně jako <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, což je celočíselný typ bez teoretické horní nebo dolní mez <xref:System.Numerics.Complex?displayProperty=nameWithType>, která představuje komplexní čísla a sadu typů v spodporouSIMD<xref:System.Numerics> oboru názvů.
  
## <a name="integer-types"></a>Celočíselné typy

.NET podporuje jak znaménkem a bez znaménka 8, 16, 32 a 64bitové celočíselné typy, které jsou uvedeny v následující tabulce:
  
|Type|Signed/Unsigned|Velikost (v bajtech)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|bez znaménka|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|podepsané|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|podepsané|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|podepsané|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|podepsané|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|bez znaménka|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|bez znaménka|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|bez znaménka|8|0|18,446,744,073,709,551,615|  
  
Každý typ celé číslo podporuje sadu standardních aritmetické operátory. <xref:System.Math?displayProperty=nameWithType> Třída poskytuje metody pro pestřejší škálu matematických funkcí.

Jednotlivé bitů v celočíselnou hodnotou. můžete také pracovat s použitím <xref:System.BitConverter?displayProperty=nameWithType> třídy.  

> [!NOTE]  
> Celé číslo bez znaménka typy nejsou kompatibilní se Specifikací CLS. Další informace najdete v tématu [jazyková nezávislost a jazykově nezávislé komponenty](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura je neumlčitelným typem, který představuje celé libovolně velké, jehož hodnota teoreticky nemá žádné horní nebo dolní meze. Metody <xref:System.Numerics.BigInteger> typ úzce paralelní u jiné typy celých čísel.
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou

.NET obsahuje tři primitivní typy s plovoucí čárkou, které jsou uvedeny v následující tabulce:
  
|Type|Velikost (v bajtech)|Přibližný rozsah|Přesnost|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1.5 x 10<sup>−45</sup> k ±3.4 x 10<sup>38</sup>|~ 6. až 9 číslic|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5.0 × 10<sup>−324</sup> k ±1.7 × 10<sup>308</sup>|~ 15-17 číslic|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1.0 x 10<sup>– 28</sup> k ±7.9228 x 10<sup>28</sup>|28 – 29 číslic|  
  
Obě <xref:System.Single> a <xref:System.Double> typů podporuje speciální hodnot, které představují not a number a nekonečno. Například <xref:System.Double> typ poskytuje následující hodnoty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Můžete použít <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>, a <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> metody testování pro tyto speciální hodnoty.

Každý typ s plovoucí desetinnou čárkou podporuje sadu standardních aritmetické operátory. <xref:System.Math?displayProperty=nameWithType> Třída poskytuje metody pro pestřejší škálu matematických funkcí. Zahrnuje .NET core 2.0 a novější <xref:System.MathF?displayProperty=nameWithType> třídu, která poskytuje metody, které přijímají argumenty <xref:System.Single> typu.

Můžete také pracovat s jednotlivých bity v <xref:System.Double> a <xref:System.Single> hodnot pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy. <xref:System.Decimal?displayProperty=nameWithType> Struktura má své vlastní metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, pro práci s desetinnou hodnotou jednotlivé služby bits, stejně jako vlastní sadu metod pro provádění některých dalších matematických operací.
  
<xref:System.Double> a <xref:System.Single> typy mají být použita pro hodnoty, které jsou ze své podstaty nepřesný (například vzdálenost mezi dvěma hvězdičkami) a pro aplikace, ve kterých vysoký stupeň přesnost a malé zaokrouhlení chyby se nevyžaduje. Měli byste použít <xref:System.Decimal?displayProperty=nameWithType> typ pro případy, kdy větší přesnost je povinný a předešlo chybám při zaokrouhlování byste měli minimalizovat.

> [!NOTE]
> <xref:System.Decimal> Typ nemá eliminovat potřebu zaokrouhluje se směrem. Místo toho minimalizuje chyby vzniklé v důsledku zaokrouhlení.
  
## <a name="complex"></a>Komplexní

<xref:System.Numerics.Complex?displayProperty=nameWithType> Struktura představuje komplexní čísla, tedy číslo s část reálné číslo a je součástí imaginary číslo. Podporuje standardní sadu aritmetický, porovnání, rovnosti, převod explicitní a implicitní operátory, jakož i matematické algebraických a trigonometrických metody.  
  
## <a name="simd-enabled-types"></a>Typy s podporou SIMD

<xref:System.Numerics> Obor názvů obsahuje sadu typů podporou .NET SIMD. Operace SIMD (jeden více dat instrukce) může být paralelizována na úrovni hardwaru. Která se zvyšuje propustnost vektorizovaných výpočty, které jsou běžné v matematické, vědecká a grafické aplikace.
  
Podporou .NET SIMD typy zahrnují následující:

- <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, A <xref:System.Numerics.Vector4> typy, které představují vektorů s 2, 3 a 4 <xref:System.Single> hodnoty.

- Dva typy matice, <xref:System.Numerics.Matrix3x2>, která představuje matici 3 x 2, a <xref:System.Numerics.Matrix4x4>, která představuje matice 4 x 4.

- <xref:System.Numerics.Plane> Typ, který představuje roviny v trojrozměrném prostoru.

- <xref:System.Numerics.Quaternion> Typ, který představuje vektor, který se používá ke kódování trojrozměrné rotace fyzické.

- <xref:System.Numerics.Vector%601> Typ, který představuje vektor zadaný číselný typ a poskytuje širokou škálu operátory, které využívají samosprávné SIMD podpory. Počet <xref:System.Numerics.Vector%601> instance je pevně daná, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je kód spuštěn.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Typ není součástí rozhraní .NET Framework. Je nutné nainstalovat [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) balíčku NuGet získáte přístup k tomuto typu.
  
Typy podporou SIMD jsou implementovány způsobem, že jde použít s SIMD nepodporujícím hardwaru nebo kompilátorů JIT. Abyste mohli využívat SIMD pokyny, 64bitové aplikace musí spustit modul runtime, který používá kompilátor komponentách RyuJIT, která je zahrnuta v .NET Core a .NET Framework 4.6 a novějším. Přidá podporu SIMD při cílení na 64bitové procesory.

## <a name="see-also"></a>Viz také:

- [Základy vytváření aplikací](application-essentials.md)
- [Standardní řetězce číselného formátu](base-types/standard-numeric-format-strings.md)
