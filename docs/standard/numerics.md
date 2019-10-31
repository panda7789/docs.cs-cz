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
ms.openlocfilehash: e5815058898cac165e7a47d761ee86bb9c4cb940
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091594"
---
# <a name="numerics-in-net"></a>Číslovky v technologii .NET

.NET poskytuje celou řadu číselná celá čísla a primitivních koncových bodů a také <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, což je celočíselný typ bez teoretické horní ani dolní meze, <xref:System.Numerics.Complex?displayProperty=nameWithType>, která představuje komplexní čísla a sadu typů s povoleným SIMD v oboru názvů <xref:System.Numerics> .
  
## <a name="integer-types"></a>Celočíselné typy

Rozhraní .NET podporuje typy celého čísla se znaménkem a bez znaménka 8, 16, 32 a 64, které jsou uvedeny v následující tabulce:
  
|Typ|Signed/unsigned|Velikost (v bajtech)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Celé|první|0,8|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisy|odst|-32 768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisy|4|-2 147 483 648|2 147 483 647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisy|8|– 9223372036854775808|9 223 372 036 854 775 807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisy|první|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Celé|odst|0,8|65 535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Celé|4|0,8|4 294 967 295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Celé|8|0,8|18446744073709551615|  
  
Každý typ Integer podporuje sadu standardních aritmetických operátorů. Třída <xref:System.Math?displayProperty=nameWithType> poskytuje metody pro širší sadu matematických funkcí.

Můžete také pracovat s jednotlivými bity v celočíselné hodnotě pomocí třídy <xref:System.BitConverter?displayProperty=nameWithType>.  

> [!NOTE]  
> Typy unsigned integer nejsou kompatibilní se specifikací CLS. Další informace najdete v tématu [nezávislost jazyka a jazykové komponenty nezávislé na jazyce](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

Struktura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> je neměnný typ, který představuje libovolně velké celé číslo, jehož hodnota teoreticky nemá žádné horní ani dolní meze. Metody <xref:System.Numerics.BigInteger> typu úzce rovnoběžně s ostatními integrálními typy.
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou

Rozhraní .NET zahrnuje tři primitivní typy s plovoucí desetinnou čárkou, které jsou uvedeny v následující tabulce:
  
|Typ|Velikost (v bajtech)|Přibližný rozsah|Přesnost|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 × 10<sup>− 45</sup> až ± 3,4 × 10<sup>38</sup>|~ 6-9 číslic|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 číslic|  
|<xref:System.Decimal?displayProperty=nameWithType>|16bitovém|± 1,0 × 10<sup>– 28</sup> až 7,9228 × 10<sup>28</sup>|28-29 číslic|  
  
Typy <xref:System.Single> i <xref:System.Double> podporují speciální hodnoty, které nepředstavují nečíselné a nekonečno. Například typ <xref:System.Double> poskytuje následující hodnoty: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>a <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. K otestování těchto speciálních hodnot můžete použít metody <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>a <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType>.

Každý typ s plovoucí desetinnou čárkou podporuje sadu standardních aritmetických operátorů. Třída <xref:System.Math?displayProperty=nameWithType> poskytuje metody pro širší sadu matematických funkcí. .NET Core 2,0 a novější obsahuje třídu <xref:System.MathF?displayProperty=nameWithType>, která poskytuje metody, které přijímají argumenty typu <xref:System.Single>.

Můžete také pracovat s jednotlivými bity v <xref:System.Double> a <xref:System.Single> hodnoty pomocí třídy <xref:System.BitConverter?displayProperty=nameWithType>. <xref:System.Decimal?displayProperty=nameWithType> struktura má své vlastní metody, <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>pro práci s jednotlivými bity desítkové hodnoty a také s vlastní sadou metod pro provádění některých dalších matematických operací.
  
Typy <xref:System.Double> a <xref:System.Single> jsou určeny k použití pro hodnoty, které jsou jejich povahou nepřesné (například vzdálenost mezi dvěma hvězdičkami) a pro aplikace, u kterých není potřeba vysoký stupeň přesnosti a menší chyba zaokrouhlení. <xref:System.Decimal?displayProperty=nameWithType> typ byste měli použít pro případy, kdy je potřeba větší přesnost a že se mají minimalizovat chyby při zaokrouhlování.

> [!NOTE]
> Typ <xref:System.Decimal> neeliminuje nutnost zaokrouhlování. Místo toho minimalizuje chyby z důvodu zaokrouhlení.
  
## <a name="complex"></a>Komplexní

Struktura <xref:System.Numerics.Complex?displayProperty=nameWithType> představuje komplexní číslo, tedy číslo s částí reálné číslo a imaginární číslo součásti. Podporuje standardní sadu aritmetických operátorů, porovnání, rovnosti, explicitního a implicitního převodu a také matematické, algebraických a trigonometrické metody.  
  
## <a name="simd-enabled-types"></a>Typy s povolenou SIMD

Obor názvů <xref:System.Numerics> obsahuje sadu typů s podporou .NET SIMD. Operace SIMD (Single Instruction Multiple Data) se dají paralelně nacházet na úrovni hardwaru. To zvyšuje propustnost vektorových výpočtů, které jsou běžné v matematických, vědeckých a grafických aplikacích.
  
Mezi typy s podporou .NET SIMD patří následující:

- Typy <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>a <xref:System.Numerics.Vector4>, které reprezentují vektory se 2, 3 a 4 hodnotami <xref:System.Single>.

- Dva typy matric, <xref:System.Numerics.Matrix3x2>, které představují matici 3x2 a <xref:System.Numerics.Matrix4x4>, které představují matici 4x4.

- Typ <xref:System.Numerics.Plane>, který představuje rovinu v trojrozměrném prostoru.

- Typ <xref:System.Numerics.Quaternion>, který představuje vektor, který je použit ke kódování trojrozměrného fyzického otočení.

- Typ <xref:System.Numerics.Vector%601>, který představuje vektor zadaného číselného typu a poskytuje širokou škálu operátorů, které využívají podporu SIMD. Počet instancí <xref:System.Numerics.Vector%601> je pevný, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěný kód.
  > [!NOTE]
  > Typ <xref:System.Numerics.Vector%601> není zahrnutý do .NET Framework. Aby bylo možné získat přístup k tomuto typu, je nutné nainstalovat balíček NuGet [System. Numerics. Vectors.](https://www.nuget.org/packages/System.Numerics.Vectors)
  
Typy s podporou SIMD jsou implementovány takovým způsobem, že je lze použít s neSIMD hardwarem nebo kompilátory JIT. Aby bylo možné využít SIMD instrukcí, musí být vaše 64 aplikace spuštěny modulem runtime, který používá kompilátor RyuJIT, který je součástí .NET Core a v .NET Framework 4,6 a novějších verzích. Přidá podporu SIMD, pokud cílíte na 64 procesorů.

## <a name="see-also"></a>Viz také:

- [Základy vytváření aplikací](application-essentials.md)
- [Standardní řetězce číselného formátu](base-types/standard-numeric-format-strings.md)
