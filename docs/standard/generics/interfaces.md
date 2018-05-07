---
title: Obecná rozhraní
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9d1323918d42884f5e2fdf8a5905d13283c74c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje přehled obecných rozhraní, které tvoří běžné funkce celé řady obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytují protějšky zajišťující bezpečnost typů na neobecné rozhraní pro porovnání rovnosti a řazení a funkce, které sdílí obecné typy kolekcí.  
  
> [!NOTE]
>  Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], parametry typu několika obecných rozhraní jsou označeny kovariantní nebo kontravariant, poskytuje větší flexibilitu při přiřazování a použití typů, které implementují tato rozhraní. V tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V <xref:System> obor názvů, <xref:System.IComparable%601?displayProperty=nameWithType> a <xref:System.IEquatable%601?displayProperty=nameWithType> obecná rozhraní, jako je jejich neobecné protějšky definice metod pro porovnání řazení a porovnání rovnosti v uvedeném pořadí. Typy implementovat tato rozhraní zajistit schopnost provádět takové porovnání.  
  
 V <xref:System.Collections.Generic> obor názvů, <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecná rozhraní nabízí způsob, jak definovat porovnávání řazení nebo rovnosti pro typy, které neimplementují <xref:System.IComparable%601?displayProperty=nameWithType> nebo <xref:System.IEquatable%601?displayProperty=nameWithType> obecné rozhraní a poskytují způsob, jak předefinování těchto vztahů pro typy, které provádějí. Tato rozhraní jsou používány metody a konstruktory mnoha obecné třídy kolekcí. Můžete například předat obecný <xref:System.Collections.Generic.IComparer%601> objektu do konstruktoru objektu <xref:System.Collections.Generic.SortedDictionary%602> třídu k určení pořadí řazení pro typ, který neimplementuje obecné <xref:System.IComparable%601?displayProperty=nameWithType>. Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> obecné statickou metodu a <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> instance metody pro řazení polí a seznamů pomocí Obecné <xref:System.Collections.Generic.IComparer%601> implementace.  
  
 <xref:System.Collections.Generic.Comparer%601> a <xref:System.Collections.Generic.EqualityComparer%601> obecné třídy poskytují základní třídy pro implementace <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecná rozhraní a také poskytují výchozí porovnání řazení a porovnávání prostřednictvím jejich odpovídajících <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> a <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> vlastnosti.  
  
### <a name="collection-functionality"></a>Kolekce funkcí  
 <xref:System.Collections.Generic.ICollection%601> Obecné rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidání, odebrání, kopírování a vytvoření výčtu prvků. <xref:System.Collections.Generic.ICollection%601> dědí z obou obecného <xref:System.Collections.Generic.IEnumerable%601> a neobecné <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní s metody načítání.  
  
 <xref:System.Collections.Generic.IDictionary%602> Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní s metody načítání podle klíčů. Slovník obecné typy v knihovně základní třídy rozhraní .NET Framework také implementuje neobecné <xref:System.Collections.IDictionary> rozhraní.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Obecné rozhraní poskytuje obecnou strukturu pro výčty. <xref:System.Collections.Generic.IEnumerator%601> Obecné rozhraní implementované obecnými čítači dědí z neobecného <xref:System.Collections.IEnumerator> rozhraní; <xref:System.Collections.IEnumerator.MoveNext%2A> a <xref:System.Collections.IEnumerator.Reset%2A> členy, které nezávisí na parametr typu `T`, se zobrazí pouze v neobecné rozhraní. To znamená, že všichni příjemci neobecného rozhraní můžete také využívat obecné rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Obecné typy](../../../docs/standard/generics/index.md)  
 [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)  
 [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
