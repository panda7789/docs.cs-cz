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
ms.openlocfilehash: 1d253e7a32d5f302b095a86ddb5c296d5fa8fa11
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209481"
---
# <a name="numerics-in-the-net-framework"></a>Číslovky v architektuře .NET Framework
Rozhraní .NET Framework podporuje standardní číselný s plovoucí desetinnou čárkou a integrální primitiv, stejně jako <xref:System.Numerics.BigInteger>, celočíselný typ bez teoretické horní nebo dolní mez <xref:System.Numerics.Complex>, typ, který představuje komplexní čísla a s podporou SIMD sady vektorové typy v <xref:System.Numerics> oboru názvů.  
  
 Kromě toho System.Numerics.Vectors, podporou SIMD knihovny typů vectory byla vydána jako balíček NuGet.  
  
## <a name="integral-types"></a>Celočíselné typy  
 Rozhraní .NET Framework podporuje podepsané i nepodepsané celá čísla v rozsahu od jeden bajt na délku osmi bajtů. Následující tabulka obsahuje seznam celočíselných typů a jejich velikost, označuje, zda jsou podepsané nebo nepodepsané a dokumenty jejich rozsah. Všechny celá čísla jsou typy hodnot.  
  
|Typ|Signed/Unsigned|Velikost (bajty)|Minimální hodnota|Maximální hodnota|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|bez znaménka|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|podepsané|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|podepsané|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|podepsané|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|podepsané|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|bez znaménka|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|bez znaménka|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|bez znaménka|8|0|18,446,744,073,709,551,615|  
  
 Každý integrální typ podporuje standardní sadu aritmetické operace porovnání, rovnosti, explicitního převodu a operátory implicitního převodu. Každé celé číslo obsahuje také metody k provádění porovnání rovnosti a relativní porovnání, převést řetězcové vyjádření čísla na tomto celé číslo a k převodu celého čísla na jeho řetězcovou reprezentaci. Některé další matematických operací nad rámec těch, zpracovat standardní operátory, jako jsou k dispozici z zaokrouhlení a menší nebo větší hodnoty dvou celých čísel, určení <xref:System.Math> třídy. Jednotlivé bitů v celočíselnou hodnotou. můžete také pracovat s použitím <xref:System.BitConverter> třídy.  
  
 Všimněte si, že nejsou kompatibilní se Specifikací CLS celočíselných typů bez znaménka. Další informace najdete v tématu [jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Typy s plovoucí desetinnou čárkou  
 Rozhraní .NET Framework obsahuje tři primitivní typy plovoucího bodu, které jsou uvedeny v následující tabulce.  
  
|Typ|Velikost (v bajtech)|Minimální|Maximum|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1.79769313486232E308 až|1.79769313486232E308 až|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3.402823e38|3.402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Každý typ s plovoucí desetinnou čárkou podporuje standardní sadu aritmetické operace porovnání, rovnosti, explicitního převodu a operátory implicitního převodu. Každý také zahrnuje metody k provádění porovnání rovnosti a relativní porovnání, chcete-li převést řetězcové vyjádření čísla s plovoucí desetinnou čárkou a pro převod čísla s plovoucí desetinnou čárkou na jeho řetězcovou reprezentaci. Některé další matematické, algebraických a trigonometrické operace jsou k dispozici <xref:System.Math> třídy. Můžete také pracovat s jednotlivých bity v <xref:System.Double> a <xref:System.Single> hodnot pomocí <xref:System.BitConverter> třídy. <xref:System.Decimal?displayProperty=nameWithType> Struktura má své vlastní metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, pro práci s desetinnou hodnotou jednotlivé služby bits, stejně jako vlastní sadu metod pro provádění některých dalších matematických operací.  
  
 <xref:System.Double> a <xref:System.Single> typy jsou určeny k použití pro hodnoty, které jsou ze své podstaty nepřesný (jako je například vzdálenost mezi dvěma hvězdičkami systému solární) a pro aplikace, ve kterých je vysoký stupeň přesnost a malé zaokrouhlení chyba není povinné. Měli byste použít <xref:System.Decimal?displayProperty=nameWithType> typ pro případy, kdy větší přesnost je povinný a chyby zaokrouhlení není žádoucí,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> je neměnný typ, který představuje celé libovolně velké, jehož hodnota teoreticky nemá žádné horní nebo dolní meze. Metody <xref:System.Numerics.BigInteger> typ úzce paralelní u jiné typy celých čísel.  
  
## <a name="complex"></a>Komplexní  
 <xref:System.Numerics.Complex> Typ představuje komplexní čísla, tedy číslo s část reálné číslo a je součástí imaginary číslo. Podporuje standardní sadu aritmetický, porovnání, rovnosti, explicitní převod, operátory implicitního převodu, i matematické algebraických a trigonometrických metody.  
  
## <a name="simd-enabled-vector-types"></a>Typy vektorů s podporou SIMD  
 <xref:System.Numerics> Obor názvů obsahuje sadu typy vektorů s podporou SIMD pro rozhraní .NET Framework. SIMD (jedné instrukce více operací dat) umožňuje některých operací paralelizovaná na úrovni hardwaru, což vede k zlepšení velký výkon v matematické, vědecká, a grafické aplikace, které provádí výpočty přes vektorů.  
  
 Typy vektoru SIMD povolené v rozhraní .NET Framework zahrnuje následující:.  Kromě toho zahrnuje System.Numerics.Vectors roviny typ a typ Quaternion.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4> typů, které jsou 2, 3 a 4rozměrné vektory typu <xref:System.Single>.  
  
-   Dva typy matice, <xref:System.Numerics.Matrix3x2>, která představuje matice 3 x 2; a <xref:System.Numerics.Matrix4x4>, která představuje matice 4 x 4.  
  
-   <xref:System.Numerics.Plane> a <xref:System.Numerics.Quaternion> typy.  
  
 Typy vektorů s podporou SimD jsou implementovány v IL, odkud můžou použít na SimD nepodporujícím hardwaru a kompilátorů JIT. Abyste mohli využívat SIMD pokyny, 64bitové aplikace musí být zkompilovány pomocí nového 64bitového kompilátoru JIT pro spravovaný kód, který je součástí rozhraní .NET Framework 4.6; Přidá podporu SIMD při cílení na x64 procesory.  
  
 SIMD můžete také stáhnout jako [balíček NuGet](https://www.nuget.org/packages/System.Numerics.Vectors).  Balíček NuGET také obsahuje obecný <xref:System.Numerics.Vector%601> struktura, která vám umožní vytvořit vektor jakýkoli primitivní číselný typ. (Zahrnout všechny číselné typy v primitivní číselné typy <xref:System> oboru názvů s výjimkou <xref:System.Decimal>.) Kromě toho <xref:System.Numerics.Vector%601> struktury poskytuje knihovnu vhodné metody, které můžete volat při práci s vektorů.  
  
## <a name="see-also"></a>Viz také:

- [Základy vytváření aplikací](../../docs/standard/application-essentials.md)
