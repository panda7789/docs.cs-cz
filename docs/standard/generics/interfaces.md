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
ms.openlocfilehash: 21a244a5d44b036a987d8eb8a79aef2c4b8e9a76
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287516"
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje přehled obecných rozhraní, která poskytují společné funkce napříč rodinami obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytují typově bezpečné protějšky pro neobecná rozhraní pro porovnání řazení a rovnosti a pro funkce, které jsou sdíleny pomocí obecných typů kolekcí.  
  
> [!NOTE]
> Počínaje .NET Framework 4 jsou parametry typu několika obecných rozhraní označeny kovariantní nebo kontravariantní a poskytují větší flexibilitu při přiřazování a používání typů, které implementují tato rozhraní. Viz [kovariance a kontravariance](covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V <xref:System> oboru názvů, <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> Obecná rozhraní, jako jsou jejich neobecné protějšky, definujte metody pro řazení porovnávání a porovnávání rovnosti v uvedeném pořadí. Typy implementují tato rozhraní, aby poskytovaly možnost provádět taková porovnání.  
  
 V <xref:System.Collections.Generic> oboru názvů, <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.IEqualityComparer%601> Obecná rozhraní a nabízejí způsob, jak definovat řazení nebo porovnávání rovnosti pro typy, které neimplementují <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> Obecné rozhraní nebo, a poskytují způsob, jak předefinovat tyto relace pro typy, které mají. Tato rozhraní jsou používána metodami a konstruktory mnoha obecných tříd kolekcí. Například můžete předat obecný <xref:System.Collections.Generic.IComparer%601> objekt konstruktoru <xref:System.Collections.Generic.SortedDictionary%602> třídy pro určení pořadí řazení pro typ, který neimplementuje obecné <xref:System.IComparable%601?displayProperty=nameWithType> . Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> Obecné statické metody a <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody instance pro řazení polí a seznamů pomocí obecných <xref:System.Collections.Generic.IComparer%601> implementací.  
  
 <xref:System.Collections.Generic.Comparer%601> <xref:System.Collections.Generic.EqualityComparer%601> Obecné třídy a poskytují základní třídy pro implementaci <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> Obecná rozhraní a také poskytují výchozí porovnání řazení a rovnosti prostřednictvím jejich odpovídajících <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> vlastností a.  
  
### <a name="collection-functionality"></a>Funkce kolekce  
 <xref:System.Collections.Generic.ICollection%601>Obecné rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidávání, odebírání, kopírování a vytváření výčtu prvků. <xref:System.Collections.Generic.ICollection%601>dědí z obecného <xref:System.Collections.Generic.IEnumerable%601> i neobecného <xref:System.Collections.IEnumerable> .  
  
 <xref:System.Collections.Generic.IList%601>Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> Obecné rozhraní o metody pro indexované načítání.  
  
 <xref:System.Collections.Generic.IDictionary%602>Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> Obecné rozhraní o metody pro načtení klíčů. Obecné typy slovníku v knihovně .NET Framework Base Class Library také implementují neobecné <xref:System.Collections.IDictionary> rozhraní.  
  
 <xref:System.Collections.Generic.IEnumerable%601>Obecné rozhraní poskytuje obecnou strukturu výčtu. <xref:System.Collections.Generic.IEnumerator%601>Obecné rozhraní implementované obecnými enumerátory dědí neobecné <xref:System.Collections.IEnumerator> rozhraní; <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator.Reset%2A> členy a, které nejsou závislé na parametru typu `T` , se zobrazí pouze v neobecném rozhraní. To znamená, že každý příjemce neobecného rozhraní může také spotřebovat obecné rozhraní.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](index.md)
- [Generování kolekcí v architektuře .NET Framework](collections.md)
- [Obecné delegáty pro manipulaci s poli a seznamy](delegates-for-manipulating-arrays-and-lists.md)
- [Kovariance a kontravariance](covariance-and-contravariance.md)
