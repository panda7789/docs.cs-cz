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
ms.openlocfilehash: 3b95a322377e82249a0375af589df74c658fcbf4
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507413"
---
# <a name="numerics-in-net"></a>Číslovky v technologii .NET

.NET poskytuje celou řadu číselná celá čísla a primitivních koncových bodů, a také <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, což je celočíselný typ bez teoretické horní nebo dolní meze, <xref:System.Numerics.Complex?displayProperty=nameWithType>, který představuje komplexní čísla a sadu typů SIMD v <xref:System.Numerics> oboru názvů.
  
## <a name="integer-types"></a>Celočíselné typy

Rozhraní .NET podporuje typy celého čísla se znaménkem a bez znaménka 8, 16, 32 a 64, které jsou uvedeny v následující tabulce:
  
|Typ|Signed/unsigned|Velikost (v bajtech)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Celé|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisy|2|-32 768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisy|4|-2 147 483 648|2 147 483 647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisy|8|– 9223372036854775808|9 223 372 036 854 775 807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisy|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Celé|2|0|65 535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Celé|4|0|4 294 967 295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Celé|8|0|18446744073709551615|  
  
Každý typ Integer podporuje sadu standardních aritmetických operátorů. <xref:System.Math?displayProperty=nameWithType> Třída poskytuje metody pro širší sadu matematických funkcí.

Můžete také pracovat s jednotlivými bity v celočíselné hodnotě pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.  

> [!NOTE]  
> Typy unsigned integer nejsou kompatibilní se specifikací CLS. Další informace najdete v tématu [nezávislost jazyka a jazykové komponenty nezávislé na jazyce](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura je neměnný typ, který představuje libovolně velké celé číslo, jehož hodnota teoreticky nemá žádné horní ani dolní meze. Metody <xref:System.Numerics.BigInteger> typu úzce rovnoběžně s dalšími celočíselnými typy.
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou

Rozhraní .NET zahrnuje tři primitivní typy s plovoucí desetinnou čárkou, které jsou uvedeny v následující tabulce:
  
|Typ|Velikost (v bajtech)|Přibližný rozsah|Přesnost|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup>|~ 6-9 číslic|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 číslic|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup>|28-29 číslic|  
  
Oba <xref:System.Single> typy <xref:System.Double> i podporují speciální hodnoty, které nepředstavují nečíselné a nekonečno. Například <xref:System.Double> typ poskytuje následující hodnoty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, a. <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> K otestování <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>těchto <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>speciálních <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>hodnot použijte <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> metody,, a.

Každý typ s plovoucí desetinnou čárkou podporuje sadu standardních aritmetických operátorů. <xref:System.Math?displayProperty=nameWithType> Třída poskytuje metody pro širší sadu matematických funkcí. .NET Core 2,0 a novější obsahuje <xref:System.MathF?displayProperty=nameWithType> třídu, která poskytuje metody, které přijímají argumenty <xref:System.Single> typu.

Můžete také pracovat s jednotlivými bity v <xref:System.Double> hodnotách <xref:System.Single> a pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy. <xref:System.Decimal?displayProperty=nameWithType> Struktura má své vlastní metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> a pro práci s jednotlivými bity desítkové hodnoty a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29>také s vlastní sadou metod pro provádění některých dalších matematických operací.
  
Typy <xref:System.Double> a <xref:System.Single> jsou určeny k použití pro hodnoty, které jsou podle jejich povahy nepřesné (například vzdálenost mezi dvěma hvězdičkami) a pro aplikace, ve kterých není vyžadován vysoký stupeň přesnosti a menší chyba zaokrouhlení. Použijte <xref:System.Decimal?displayProperty=nameWithType> typ pro případy, kdy je potřeba větší přesnost a Minimalizujte chyby při zaokrouhlování.

> [!NOTE]
> <xref:System.Decimal> Typ neeliminuje nutnost zaokrouhlování. Místo toho minimalizuje chyby z důvodu zaokrouhlení.
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> Struktura představuje komplexní číslo, tedy číslo s částí reálného čísla a imaginární část čísla. Podporuje standardní sadu aritmetických operátorů, porovnání, rovnosti, explicitního a implicitního převodu a také matematické, algebraických a trigonometrické metody.  
  
## <a name="simd-enabled-types"></a>Typy s povolenou SIMD

<xref:System.Numerics> Obor názvů obsahuje sadu typů s podporou .NET SIMD. Operace SIMD (Single Instruction Multiple Data) se dají paralelně nacházet na úrovni hardwaru. To zvyšuje propustnost vektorových výpočtů, které jsou běžné v matematických, vědeckých a grafických aplikacích.
  
Mezi typy s podporou .NET SIMD patří následující:

- Typy, a <xref:System.Numerics.Vector4> , které reprezentují vektory s hodnotami 2, 3 a 4 <xref:System.Single> <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3>

- Dva typy matrice <xref:System.Numerics.Matrix3x2>,, které představují matici 3x2 a <xref:System.Numerics.Matrix4x4>které představují matici 4x4.

- <xref:System.Numerics.Plane> Typ, který představuje rovinu v trojrozměrném prostoru.

- <xref:System.Numerics.Quaternion> Typ, který představuje vektor, který se používá ke kódování trojrozměrných fyzických otočení.

- <xref:System.Numerics.Vector%601> Typ, který představuje vektor zadaného číselného typu a poskytuje širokou škálu operátorů, které využívají podporu SIMD. Počet <xref:System.Numerics.Vector%601> instancí je opraven, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěn kód.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Typ není zahrnutý do .NET Framework. Aby bylo možné získat přístup k tomuto typu, je nutné nainstalovat balíček NuGet [System. Numerics. Vectors.](https://www.nuget.org/packages/System.Numerics.Vectors)
  
Typy s podporou SIMD jsou implementovány takovým způsobem, že je lze použít s neSIMD hardwarem nebo kompilátory JIT. Aby bylo možné využít SIMD instrukcí, musí být vaše 64 aplikace spuštěny modulem runtime, který používá kompilátor RyuJIT, který je součástí .NET Core a v .NET Framework 4,6 a novějších verzích. Přidá podporu SIMD, pokud cílíte na 64 procesorů.

Další informace najdete v tématu [použití číselných typů SIMD-Accelerated](simd.md).

## <a name="see-also"></a>Viz také

- [Řetězce standardního číselného formátu](base-types/standard-numeric-format-strings.md)
