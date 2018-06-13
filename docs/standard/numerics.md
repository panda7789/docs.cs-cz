---
title: Číslovky v architektuře .NET Framework
ms.date: 03/30/2017
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
ms.openlocfilehash: a2a795fb52c123840c1ba7b82f77d6745feba89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588694"
---
# <a name="numerics-in-the-net-framework"></a>Číslovky v architektuře .NET Framework
Rozhraní .NET Framework podporuje standardní číselné integrální a s plovoucí desetinnou čárkou primitiv, a také <xref:System.Numerics.BigInteger>, typ integrální bez teoretické horní nebo dolní mez <xref:System.Numerics.Complex>, typ, který představuje komplexní čísla a sadu SIMD povoleno Vector typy v <xref:System.Numerics> oboru názvů.  
  
 Kromě toho System.Numerics.Vectors, povolené SIMD knihovny typů vectory, byla vydána jako balíčku NuGet.  
  
## <a name="integral-types"></a>Celočíselné typy  
 Rozhraní .NET Framework podporuje signed a unsigned celá čísla od jednoho bajtu až osm délku bajtů. Následující tabulka uvádí integrální typy a jejich velikost, určuje, jestli se jsou podepsané nebo nepodepsané a dokumenty jejich rozsah. Všechny celých čísel jsou typy hodnot.  
  
|Typ|Podepsané nepodepsaných|Velikost (bajty)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bez znaménka|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podepsané|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podepsané|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podepsané|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podepsané|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bez znaménka|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bez znaménka|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bez znaménka|8|0|18,446,744,073,709,551,615|  
  
 Každý typ integrální podporuje standardní sadu aritmetické, porovnání, rovnosti, explicitní převod a operátory implicitního převodu. Každý celé číslo také obsahuje metod, jak provést porovnání rovnosti a relativní porovnání převést řetězcovou reprezentaci číslo na celé číslo. tuto a převést řetězcovou reprezentaci celé číslo. Některé další matematické operace nad rámec těch, které provádí standardní operátory, jako jsou k dispozici z zaokrouhlení a identifikaci menší nebo větší hodnotu dvě celá čísla, <xref:System.Math> třídy. Můžete také pracovat se jednotlivé bity v celočíselnou hodnotu pomocí <xref:System.BitConverter> třídy.  
  
 Všimněte si, že nepodepsaných integrálních typů nejsou kompatibilní se specifikací CLS. Další informace najdete v tématu [jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou  
 Rozhraní .NET Framework zahrnuje tři primitivní plovoucí typy bodů, které jsou uvedeny v následující tabulce.  
  
|Typ|Velikost (v bajtech)|Minimální|Maximum|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1.79769313486232e308|1.79769313486232E308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3.402823e38|3.402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Každý typ s plovoucí desetinnou čárkou podporuje standardní sadu aritmetické, porovnání, rovnosti, explicitní převod a operátory implicitního převodu. Každý také obsahuje metod, jak provést porovnání rovnosti a relativní porovnání, chcete-li převést řetězcové vyjádření čísla s plovoucí desetinnou čárkou a převést řetězcovou reprezentaci číslo s plovoucí desetinnou čárkou. Některé další matematické, algebraických a trigonometrické operace jsou k dispozici na <xref:System.Math> třídy. Může spolupracovat taky s jednotlivé bity v <xref:System.Double> a <xref:System.Single> hodnoty pomocí <xref:System.BitConverter> třídy. <xref:System.Decimal?displayProperty=nameWithType> Struktura má svou vlastní metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, pro práci s desetinnou hodnotou jednotlivé služby bits, jakož i vlastní sadu metody pro provádění některých dalších matematické operace.  
  
 <xref:System.Double> a <xref:System.Single> typy jsou určena k použití pro hodnoty, které jsou svou povahou nepřesný (například vzdálenost mezi dvěma hvězdičkami v systému sluneční) a pro aplikace, ve kterých je vysoký stupeň přesnost a malého zaokrouhlení chyba není vyžaduje se. Měli byste použít <xref:System.Decimal?displayProperty=nameWithType> typ pro případy, kdy větší přesnost je povinná a zaokrouhlení chyba není žádoucí,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> je neměnné typ, který představuje celé libovolně velké, jehož hodnota teoreticky nemá žádné horní nebo dolní meze. Metody <xref:System.Numerics.BigInteger> typ úzce paralelní u celočíselných typů.  
  
## <a name="complex"></a>Komplexní  
 <xref:System.Numerics.Complex> Typ představuje komplexní číslo, který je číslo s součástí reálné číslo a z části imaginary číslo. Podporuje standardní sadu aritmetické, porovnání, rovnosti, explicitní převod a operátory implicitního převodu, jakož i matematické, algebraických a trigonometrické metody.  
  
## <a name="simd-enabled-vector-types"></a>Typy povolené SIMD vektoru  
 <xref:System.Numerics> Obor názvů zahrnuje sadu povoleno SIMD vektoru typů pro rozhraní .NET Framework. SIMD (jeden dat více instrukce operace) umožňuje některých operací se paralelizovaná málo na úrovni hardwaru, což vede k vylepšení výkonu obrovské v matematickém, vědecké, a grafiky aplikace, které provádět výpočty přes vektory.  
  
 Povolené SIMD vektoru typy v rozhraní .NET Framework zahrnují následující:.  Kromě toho zahrnuje System.Numerics.Vectors typu roviny a Quaternion typu.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4> typy, které jsou 2 – 3- a 4 dimenzí vektory typu <xref:System.Single>.  
  
-   Dva typy matice <xref:System.Numerics.Matrix3x2>, která představuje matice 3 x 2; a <xref:System.Numerics.Matrix4x4>, která představuje matice 4 x 4.  
  
-   <xref:System.Numerics.Plane> a <xref:System.Numerics.Quaternion> typy.  
  
 Typy povolené SimD vektoru se implementují ve IL, což vám umožní se použije na nepodporujícím SimD hardwaru a JIT kompilátory. Abyste mohli využívat SIMD pokyny, musí být zkompilovány 64bitové aplikace pomocí nového 64bitový kompilátor JIT pro spravovaný kód, který je součástí rozhraní .NET Framework 4.6; Pokud je cílem x64 přidá podporu SIMD procesory.  
  
 SIMD se dá stáhnout i jako [balíček NuGet](https://www.nuget.org/packages/System.Numerics.Vectors).  Balíček NuGET také obsahuje obecný <xref:System.Numerics.Vector%601> struktura, která vám umožní vytvořit vektoru všechny primitivní číselného typu. (Primitivní číselnými typy zahrnují všechny číselné typy v <xref:System> oboru názvů s výjimkou <xref:System.Decimal>.) Kromě toho <xref:System.Numerics.Vector%601> struktura poskytuje knihovnu usnadňující metody, které můžete volat při práci s vektory.  
  
## <a name="see-also"></a>Viz také  
 [Základy vytváření aplikací](../../docs/standard/application-essentials.md)
