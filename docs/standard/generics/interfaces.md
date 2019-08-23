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
ms.openlocfilehash: 09e9a51fe9c1fd25a6791cf924180329718138c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915895"
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje přehled obecných rozhraní, která poskytují společné funkce napříč rodinami obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytují typově bezpečné protějšky pro neobecná rozhraní pro porovnání řazení a rovnosti a pro funkce, které jsou sdíleny pomocí obecných typů kolekcí.  
  
> [!NOTE]
> Počínaje .NET Framework 4 jsou parametry typu několika obecných rozhraní označeny kovariantní nebo kontravariantní a poskytují větší flexibilitu při přiřazování a používání typů, které implementují tato rozhraní. Viz [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V oboru názvů <xref:System.IComparable%601?displayProperty=nameWithType> ,<xref:System.IEquatable%601?displayProperty=nameWithType> Obecná rozhraní, jako jsou jejich neobecné protějšky, definujte metody pro řazení porovnávání a porovnávání rovnosti v uvedeném pořadí. <xref:System> Typy implementují tato rozhraní, aby poskytovaly možnost provádět taková porovnání.  
  
 <xref:System.Collections.Generic.IEqualityComparer%601> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> V oboru názvů <xref:System.Collections.Generic.IComparer%601> nabízí Obecná rozhraní a možnost definovat porovnání řazení nebo rovnosti pro typy, které neimplementují obecné rozhraní nebo a poskytují způsob, jak <xref:System.Collections.Generic> předefinujte tyto relace pro typy, které mají. Tato rozhraní jsou používána metodami a konstruktory mnoha obecných tříd kolekcí. Například můžete předat obecný <xref:System.Collections.Generic.IComparer%601> objekt konstruktoru <xref:System.Collections.Generic.SortedDictionary%602> třídy pro určení pořadí řazení pro typ, který neimplementuje obecné <xref:System.IComparable%601?displayProperty=nameWithType>. Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> obecné statické metody <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> a metody instance pro řazení polí a seznamů pomocí obecných <xref:System.Collections.Generic.IComparer%601> implementací.  
  
 <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IEqualityComparer%601> Obecné třídy <xref:System.Collections.Generic.EqualityComparer%601> a poskytují základní třídy pro implementaci a Obecná rozhraní a také poskytují výchozí porovnání řazení a rovnosti přes jejich příslušné <xref:System.Collections.Generic.Comparer%601> a <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> vlastnosti.  
  
### <a name="collection-functionality"></a>Funkce kolekce  
 <xref:System.Collections.Generic.ICollection%601> Obecné rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidávání, odebírání, kopírování a vytváření výčtu prvků. <xref:System.Collections.Generic.ICollection%601>dědí z obecného <xref:System.Collections.Generic.IEnumerable%601> i neobecného <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Obecné rozhraní<xref:System.Collections.Generic.ICollection%601> rozšiřuje obecné rozhraní o metody pro indexované načítání.  
  
 <xref:System.Collections.Generic.IDictionary%602> Obecné rozhraní<xref:System.Collections.Generic.ICollection%601> rozšiřuje obecné rozhraní o metody pro načtení klíčů. Obecné typy slovníku v knihovně .NET Framework Base Class Library také implementují neobecné <xref:System.Collections.IDictionary> rozhraní.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Obecné rozhraní poskytuje obecnou strukturu výčtu. <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator> `T` <xref:System.Collections.IEnumerator.Reset%2A> Obecné rozhraní implementované obecnými enumerátory dědí neobecné rozhraní; členy a, které nejsou závislé na parametru typu, se zobrazí pouze u neobecných. <xref:System.Collections.Generic.IEnumerator%601> prostředí. To znamená, že každý příjemce neobecného rozhraní může také spotřebovat obecné rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)
- [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
