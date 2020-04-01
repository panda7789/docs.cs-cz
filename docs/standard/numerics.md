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
ms.openlocfilehash: 89d3eb709bb22913b9539d6ad384384ee701385f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523290"
---
# <a name="numerics-in-net"></a>Číslovky v technologii .NET

.NET poskytuje rozsah číselné celočíselné a plovoucí desetinné třídy primitiv, jakož <xref:System.Numerics.BigInteger?displayProperty=nameWithType>i <xref:System.Numerics.Complex?displayProperty=nameWithType>, což je integrální typ bez teoretické horní nebo dolní mez, , která představuje komplexní čísla a sadu typů s podporou SIMD v oboru <xref:System.Numerics> názvů.
  
## <a name="integer-types"></a>Celočíselné typy

Síť .NET podporuje podepsané i nepodepsané typy osmi, 16,12, 32 a 64bitových čísel, které jsou uvedeny v následující tabulce:
  
|Typ|Podepsáno/Nepodepsáno|Velikost (v bajtech)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Nepodepsané|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podepsané|2|-32,768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podepsané|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podepsané|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podepsané|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Nepodepsané|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Nepodepsané|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Nepodepsané|8|0|18,446,744,073,709,551,615|  
  
Každý typ celéčíslo podporuje sadu standardních aritmetické operátory. Třída <xref:System.Math?displayProperty=nameWithType> poskytuje metody pro širší sadu matematických funkcí.

Můžete také pracovat s jednotlivými bity v celé <xref:System.BitConverter?displayProperty=nameWithType> hodnotě pomocí třídy.  

> [!NOTE]  
> Nepodepsané celočíselné typy nejsou kompatibilní se standardem CLS. Další informace naleznete v [tématu Language Independence and Language-Independent Components](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

Struktura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> je neměnný typ, který představuje libovolně velké celé číslo, jehož hodnota teoreticky nemá žádné horní nebo dolní hranice. Metody typu <xref:System.Numerics.BigInteger> úzce paralelní ty ostatní integrální typy.
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou tálicí

Rozhraní .NET obsahuje tři primitivní typy s plovoucí desetinnou desetinnou a mají následující tabulku:
  
|Typ|Velikost (v bajtech)|Přibližný rozsah|Přesnost|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1,5 x 10<sup>−45</sup> až ±3,4 x 10<sup>38</sup>|~6-9 číslic|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5,0 × 10<sup>−324</sup> až ±1,7 × 10<sup>308</sup>|~15-17 číslic|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1,0 x 10<sup>-28</sup> až ±7,9228 x 10<sup>28</sup>|28-29 číslic|  
  
Oba <xref:System.Single> <xref:System.Double> a typy podporují speciální hodnoty, které představují ne-a-číslo a nekonečno. <xref:System.Double> Například typ obsahuje následující hodnoty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Pomocí metody <xref:System.Double.IsNaN%2A?displayProperty=nameWithType> <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> a metody otestovat tyto speciální hodnoty.

Každý typ s plovoucí desetinnou desetinnou desetinnou hodem podporuje sadu standardních aritmetických operátorů. Třída <xref:System.Math?displayProperty=nameWithType> poskytuje metody pro širší sadu matematických funkcí. .NET Core 2.0 a <xref:System.MathF?displayProperty=nameWithType> novější obsahuje třídu, která <xref:System.Single> poskytuje metody, které přijímají argumenty typu.

Můžete také pracovat s jednotlivými <xref:System.Double> <xref:System.Single> bity a <xref:System.BitConverter?displayProperty=nameWithType> hodnoty pomocí třídy. Struktura <xref:System.Decimal?displayProperty=nameWithType> má své vlastní <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>metody a , pro práci s jednotlivé bity desetinné hodnoty, stejně jako vlastní sadu metod pro provádění některých dalších matematických operací.
  
Typy <xref:System.Double> <xref:System.Single> a jsou určeny k použití pro hodnoty, které jsou svou povahou nepřesné (například vzdálenost mezi dvěma hvězdičkami) a pro aplikace, ve kterých není vyžadován vysoký stupeň přesnosti a malá chyba zaokrouhlení. Typ byste <xref:System.Decimal?displayProperty=nameWithType> měli použít pro případy, ve kterých je vyžadována větší přesnost a chyby zaokrouhlení by měly být minimalizovány.

> [!NOTE]
> Typ <xref:System.Decimal> nevylučuje potřebu zaokrouhlení. Spíše minimalizuje chyby z důvodu zaokrouhlení.
  
## <a name="complex"></a>Complex

Struktura <xref:System.Numerics.Complex?displayProperty=nameWithType> představuje komplexní číslo, to znamená číslo s reálnou číselnou částí a imaginární číselnou částí. Podporuje standardní sadu aritmetické, porovnání, rovnosti, explicitní a implicitní operátory převodu, stejně jako matematické, algebraické a goniometrické metody.  
  
## <a name="simd-enabled-types"></a>Typy s podporou SIMD

Obor <xref:System.Numerics> názvů obsahuje sadu typů s podporou rozhraní .NET SIMD. Operace SIMD (Single Instruction Multiple Data) mohou být paralelizovány na hardwarové úrovni. To zvyšuje propustnost vektorizovaných výpočtů, které jsou běžné v matematických, vědeckých a grafických aplikacích.
  
Typy s podporou SIMD rozhraní .NET zahrnují následující:

- Typy <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3>, <xref:System.Numerics.Vector4> a, které představují vektory s hodnotami 2, 3 a 4. <xref:System.Single>

- Dva typy <xref:System.Numerics.Matrix3x2>matice , které představují matici 3x2 a <xref:System.Numerics.Matrix4x4>, která představuje matici 4x4.

- Typ, <xref:System.Numerics.Plane> který představuje rovinu v trojrozměrném prostoru.

- Typ, <xref:System.Numerics.Quaternion> který představuje vektor, který se používá ke kódování trojrozměrné fyzické rotace.

- Typ, <xref:System.Numerics.Vector%601> který představuje vektor zadaného číselného typu a poskytuje širokou sadu operátorů, které využívají podporu SIMD. Počet <xref:System.Numerics.Vector%601> instance je pevná, ale <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> její hodnota závisí na procesoru počítače, na kterém je spuštěn kód.
  > [!NOTE]
  > Typ <xref:System.Numerics.Vector%601> není součástí rozhraní .NET Framework. Chcete-li získat přístup k tomuto typu, je nutné nainstalovat balíček [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet.
  
Typy s podporou SIMD jsou implementovány tak, aby je bylo možné použít s hardwarem bez SIMD nebo kompilátory JIT. Chcete-li využít pokyny SIMD, musí být 64bitové aplikace spuštěny za běhu, který používá kompilátor RyuJIT, který je součástí .NET Core a v rozhraní .NET Framework 4.6 a novějších verzích. Přidává podporu SIMD při cílení na 64bitové procesory.

## <a name="see-also"></a>Viz také

- [Standardní řetězce formátu čísla](base-types/standard-numeric-format-strings.md)
