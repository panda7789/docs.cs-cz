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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708321"
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje přehled obecných rozhraní, která poskytují společné funkce napříč rodinami obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytují typově bezpečné protějšky pro neobecná rozhraní pro porovnání řazení a rovnosti a pro funkce, které jsou sdíleny pomocí obecných typů kolekcí.  
  
> [!NOTE]
> Počínaje .NET Framework 4 jsou parametry typu několika obecných rozhraní označeny kovariantní nebo kontravariantní a poskytují větší flexibilitu při přiřazování a používání typů, které implementují tato rozhraní. Viz [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V oboru názvů <xref:System>, v obecných rozhraních <xref:System.IComparable%601?displayProperty=nameWithType> a <xref:System.IEquatable%601?displayProperty=nameWithType>, jako jsou jejich neobecné protějšky, definujte metody pro řazení porovnávání a porovnávání rovnosti v uvedeném pořadí. Typy implementují tato rozhraní, aby poskytovaly možnost provádět taková porovnání.  
  
 V oboru názvů <xref:System.Collections.Generic> se obecná rozhraní <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> nabízejí způsob, jak definovat porovnání řazení nebo rovnosti pro typy, které neimplementují obecné rozhraní <xref:System.IComparable%601?displayProperty=nameWithType> nebo <xref:System.IEquatable%601?displayProperty=nameWithType>, a poskytují způsob, jak předefinovat tyto relace pro typy, které mají. Tato rozhraní jsou používána metodami a konstruktory mnoha obecných tříd kolekcí. Například můžete předat obecný objekt <xref:System.Collections.Generic.IComparer%601> konstruktoru třídy <xref:System.Collections.Generic.SortedDictionary%602> a určit tak pořadí řazení pro typ, který neimplementuje obecné <xref:System.IComparable%601?displayProperty=nameWithType>. Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> obecná statická metoda a metoda <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> instance pro řazení polí a seznamů pomocí obecných <xref:System.Collections.Generic.IComparer%601> implementace.  
  
 Obecné třídy <xref:System.Collections.Generic.Comparer%601> a <xref:System.Collections.Generic.EqualityComparer%601> poskytují základní třídy pro implementace <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecných rozhraní a také poskytují standardní porovnávání řazení a rovnosti prostřednictvím příslušných <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> a <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType>ch vlastností.  
  
### <a name="collection-functionality"></a>Funkce kolekce  
 <xref:System.Collections.Generic.ICollection%601> obecné rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidávání, odebírání, kopírování a vytváření výčtu prvků. <xref:System.Collections.Generic.ICollection%601> dědí z obecného <xref:System.Collections.Generic.IEnumerable%601> i z neobecných <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní o metody pro indexované načítání.  
  
 <xref:System.Collections.Generic.IDictionary%602> obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní s metodami pro načtení klíčů. Obecné typy slovníku v knihovně .NET Framework základní třídy také implementují neobecné <xref:System.Collections.IDictionary> rozhraní.  
  
 Obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601> poskytuje obecnou strukturu výčtu. Obecné rozhraní <xref:System.Collections.Generic.IEnumerator%601> implementované obecnými enumerátory dědí neobecné <xref:System.Collections.IEnumerator> rozhraní; členy <xref:System.Collections.IEnumerator.MoveNext%2A> a <xref:System.Collections.IEnumerator.Reset%2A>, které nejsou závislé na parametru typu `T`, se zobrazí pouze v neobecném rozhraní. To znamená, že každý příjemce neobecného rozhraní může také spotřebovat obecné rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)
- [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
