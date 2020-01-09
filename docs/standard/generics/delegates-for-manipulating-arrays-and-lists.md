---
title: Obecní delegáty pro manipulaci s poli a seznamy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
ms.openlocfilehash: baf8497289ee71c2dbdc544607212de90928289c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708381"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy
Toto téma poskytuje přehled obecných delegátů pro převody, predikáty hledání a akce, které mají být provedeny na prvcích pole nebo kolekce.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy  
 Obecný delegát <xref:System.Action%601> představuje metodu, která provádí určitou akci u prvku zadaného typu. Můžete vytvořit metodu, která provede požadovanou akci u prvku, vytvořit instanci delegáta <xref:System.Action%601> pro reprezentaci této metody a pak předat pole a delegátovi do <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statické obecné metody. Metoda je volána pro každý prvek pole.  
  
 <xref:System.Collections.Generic.List%601> obecná třída také poskytuje metodu <xref:System.Collections.Generic.List%601.ForEach%2A>, která používá delegáta <xref:System.Action%601>. Tato metoda není obecná.  
  
> [!NOTE]
> Tím se vytvoří zajímavý bod týkající se obecných typů a metod. Metoda <xref:System.Array.ForEach%2A?displayProperty=nameWithType> musí být statická (`Shared` ve Visual Basic) a obecná, protože <xref:System.Array> není obecný typ; jediným důvodem je, že lze zadat typ <xref:System.Array.ForEach%2A?displayProperty=nameWithType>, na kterém bude fungovat, je, že metoda má svůj vlastní seznam parametrů typu. Naopak neobecná <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda patří do obecné třídy <xref:System.Collections.Generic.List%601>, takže jednoduše používá parametr typu své třídy. Třída je silného typu, takže metoda může být metodou instance.  
  
 <xref:System.Predicate%601> obecný delegát představuje metodu, která určuje, zda konkrétní prvek splňuje kritéria, která definujete. Můžete ji použít s následujícími statickými obecnými metodami <xref:System.Array> pro hledání prvku nebo sady prvků: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>a <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> také funguje s odpovídajícími neobecnými metodami instance <xref:System.Collections.Generic.List%601> obecné třídy.  
  
 <xref:System.Comparison%601> obecný delegát umožňuje zadat pořadí řazení pro prvky pole nebo seznamu, které nemají nativní pořadí řazení, nebo přepsat nativní pořadí řazení. Vytvořte metodu, která provede porovnání, vytvořte instanci delegáta <xref:System.Comparison%601> pro reprezentaci vaší metody a pak předejte pole a delegátovi do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statické obecné metody. <xref:System.Collections.Generic.List%601> obecná třída poskytuje odpovídající přetížení metody instance, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> obecný delegát umožňuje definovat převod mezi dvěma typy a převést pole jednoho typu na pole druhé, nebo pro převod seznamu jednoho typu na seznam druhý. Vytvořte metodu, která převede prvky existujícího seznamu na nový typ, vytvořte instanci delegáta představující metodu a použijte <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> obecné statické metody k vytvoření pole nového typu z původního pole nebo metody <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> generické instance k vytvoření seznamu nového typu z původního seznamu.  
  
### <a name="chaining-delegates"></a>Zřetězení delegátů  
 Mnohé z metod, které používají tyto delegáty, vracejí pole nebo seznam, které lze předat jiné metodě. Například pokud chcete vybrat určité prvky pole, převést tyto prvky na nový typ a uložit je do nového pole, můžete předat pole vrácené <xref:System.Array.FindAll%2A>ou obecnou metodou do obecné metody <xref:System.Array.ConvertAll%2A>. Pokud nový typ elementu nemá přirozené pořadí řazení, můžete předat pole vrácené <xref:System.Array.ConvertAll%2A>ou obecnou metodou <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> obecné metodě.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
