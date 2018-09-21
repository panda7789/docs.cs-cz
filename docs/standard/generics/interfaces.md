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
ms.openlocfilehash: a6c151798c807206cc7f4b2fbeb21e75e9142379
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489861"
---
# <a name="generic-interfaces"></a>Obecná rozhraní
Toto téma obsahuje základní informace o obecných rozhraní, které poskytují společné funkce napříč řady obecných typů.  
  
## <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní poskytuje typově bezpečné ekvivalenty rozhraním neobecná pro porovnání rovnosti a řazení a funkce, které jsou sdíleny obecných typů kolekce.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], několik obecných rozhraní parametry typu označen jako kovariantní nebo kontravariantní, takže má větší flexibilitu při přiřazování a používání typy, které implementují tato rozhraní. Zobrazit [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### <a name="equality-and-ordering-comparisons"></a>Porovnání rovnosti a řazení  
 V <xref:System> obor názvů, <xref:System.IComparable%601?displayProperty=nameWithType> a <xref:System.IEquatable%601?displayProperty=nameWithType> obecných rozhraní, jako je jejich protějšků, definuje metody pro porovnání řazení a porovnání rovnosti, v uvedeném pořadí. Typy implementují tato rozhraní umožňují provádět takové porovnání.  
  
 V <xref:System.Collections.Generic> obor názvů, <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecných rozhraní nabízejí způsob, jak definovat porovnání řazení nebo rovnost pro typy, které neimplementují <xref:System.IComparable%601?displayProperty=nameWithType> nebo <xref:System.IEquatable%601?displayProperty=nameWithType> obecné rozhraní a poskytují způsob, jak znovu definujte tyto relace pro typy, které provést. Tato rozhraní jsou používány metody a konstruktory mnoha obecné kolekce tříd. Například můžete předat obecný <xref:System.Collections.Generic.IComparer%601> objekt konstruktoru <xref:System.Collections.Generic.SortedDictionary%602> třídu k určení pořadí řazení pro typ, který neimplementuje obecný <xref:System.IComparable%601?displayProperty=nameWithType>. Existují přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> obecné statické metody a <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metodu instance pro řazení polí a seznamů pomocí obecného <xref:System.Collections.Generic.IComparer%601> implementace.  
  
 <xref:System.Collections.Generic.Comparer%601> a <xref:System.Collections.Generic.EqualityComparer%601> obecné třídy poskytují základní třídy pro implementaci <xref:System.Collections.Generic.IComparer%601> a <xref:System.Collections.Generic.IEqualityComparer%601> obecných rozhraní a také poskytují výchozí porovnání rovnosti a řazení prostřednictvím jejich <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> a <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> vlastnosti.  
  
### <a name="collection-functionality"></a>Funkci shromažďování  
 <xref:System.Collections.Generic.ICollection%601> Obecného rozhraní je základní rozhraní pro obecné typy kolekcí. Poskytuje základní funkce pro přidání, odebrání, kopírování a vytvoření výčtu prvků. <xref:System.Collections.Generic.ICollection%601> dědí z obou obecného <xref:System.Collections.Generic.IEnumerable%601> a neobecných <xref:System.Collections.IEnumerable>.  
  
 <xref:System.Collections.Generic.IList%601> Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní pomocí metody načítání.  
  
 <xref:System.Collections.Generic.IDictionary%602> Obecné rozhraní rozšiřuje <xref:System.Collections.Generic.ICollection%601> obecné rozhraní pomocí metody pro načítání s klíčem. Generický slovník typy v knihovně základních tříd rozhraní .NET Framework také implementovat neobecné <xref:System.Collections.IDictionary> rozhraní.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Obecné rozhraní poskytuje obecnou strukturu pro výčty. <xref:System.Collections.Generic.IEnumerator%601> Obecné rozhraní implementované obecný výčty dědí neobecné <xref:System.Collections.IEnumerator> rozhraní; <xref:System.Collections.IEnumerator.MoveNext%2A> a <xref:System.Collections.IEnumerator.Reset%2A> členy, které nezávisí na parametr typu `T`, se zobrazí pouze v neobecné rozhraní. To znamená, že příjemci neobecné rozhraní můžete také využívat její obecná rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Obecné typy](../../../docs/standard/generics/index.md)  
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)  
- [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
