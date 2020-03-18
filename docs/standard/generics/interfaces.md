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
ms.openlocfilehash: 704ada32d428c468d5b71a3f1390568ca586079e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708321"
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje přehled obecných rozhraní, které poskytují běžné funkce napříč rodinami obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytují typově bezpečné protějšky neobecných rozhraní pro porovnání řazení a rovnosti a pro funkce, které jsou sdíleny obecnými typy kolekcí.  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 jsou parametry typu několika obecných rozhraní označeny jako kovariantní nebo kontravariantní, což poskytuje větší flexibilitu při přiřazování a používání typů, které implementují tato rozhraní. Viz [Kovariance a Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V <xref:System> oboru názvů <xref:System.IComparable%601?displayProperty=nameWithType> a <xref:System.IEquatable%601?displayProperty=nameWithType> obecná rozhraní, stejně jako jejich neobecné protějšky, definovat metody pro řazení porovnání a rovnosti porovnání, v uvedeném pořadí. Typy implementovat tato rozhraní poskytnout možnost provádět takové porovnání.  
  
 V <xref:System.Collections.Generic> oboru názvů <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecná rozhraní nabízejí způsob, jak definovat řazení nebo rovnosti <xref:System.IComparable%601?displayProperty=nameWithType> porovnání <xref:System.IEquatable%601?displayProperty=nameWithType> pro typy, které neimplementují nebo obecné rozhraní a poskytují způsob, jak předefinovat tyto vztahy pro typy, které dělají. Tato rozhraní jsou používány metody a konstruktory mnoha tříd obecné kolekce. Můžete například předat obecný <xref:System.Collections.Generic.IComparer%601> objekt konstruktoru <xref:System.Collections.Generic.SortedDictionary%602> třídy a zadat pořadí řazení pro typ, který neimplementuje obecný <xref:System.IComparable%601?displayProperty=nameWithType>. Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> obecné statické metody a <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody instance pro řazení polí <xref:System.Collections.Generic.IComparer%601> a seznamů pomocí obecných implementací.  
  
 A <xref:System.Collections.Generic.Comparer%601> <xref:System.Collections.Generic.EqualityComparer%601> a obecné třídy poskytují základní <xref:System.Collections.Generic.IComparer%601> <xref:System.Collections.Generic.IEqualityComparer%601> třídy pro implementace a obecné rozhraní a také <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> poskytují <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> výchozí řazení a rovnosti porovnání prostřednictvím jejich příslušné a vlastnosti.  
  
### <a name="collection-functionality"></a>Funkce kolekce  
 Obecné <xref:System.Collections.Generic.ICollection%601> rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidávání, odebírání, kopírování a výčet prvků. <xref:System.Collections.Generic.ICollection%601>dědí jak <xref:System.Collections.Generic.IEnumerable%601> z obecných, tak od generických <xref:System.Collections.IEnumerable>.  
  
 Obecné <xref:System.Collections.Generic.IList%601> rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní o metody indexovaného načítání.  
  
 Obecné <xref:System.Collections.Generic.IDictionary%602> rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní o metody pro načítání pomocí klíče. Obecné typy slovníků v knihovně základních tříd rozhraní <xref:System.Collections.IDictionary> .NET Framework také implementují neobecné rozhraní.  
  
 Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní poskytuje obecnou strukturu výčtu. Obecné <xref:System.Collections.Generic.IEnumerator%601> rozhraní implementované obecnými čítači výčtu dědí neobecné <xref:System.Collections.IEnumerator> rozhraní; a <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator.Reset%2A> členy, které nejsou závislé na `T`parametru typu , se zobrazí pouze v neobecném rozhraní. To znamená, že každý příjemce neobecné rozhraní může také využívat obecné rozhraní.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)
- [Obecní delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
