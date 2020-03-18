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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708381"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy
Toto téma obsahuje přehled obecných delegátů pro převody, predikáty hledání a akce, které mají být přijata na prvky pole nebo kolekce.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy  
 Obecný <xref:System.Action%601> delegát představuje metodu, která provádí některé akce na prvek zadaného typu. Můžete vytvořit metodu, která provede požadovanou akci na <xref:System.Action%601> prvek, vytvořit instanci delegáta reprezentovat tuto <xref:System.Array.ForEach%2A?displayProperty=nameWithType> metodu a pak předat pole a delegáta statické obecné metody. Metoda je volána pro každý prvek pole.  
  
 Obecná <xref:System.Collections.Generic.List%601> třída také <xref:System.Collections.Generic.List%601.ForEach%2A> poskytuje metodu, která používá delegáta. <xref:System.Action%601> Tato metoda není obecná.  
  
> [!NOTE]
> To je zajímavý bod o obecných typů a metod. Metoda <xref:System.Array.ForEach%2A?displayProperty=nameWithType> musí být`Shared` statická (v jazyce Visual Basic) a obecná, protože <xref:System.Array> není obecný typ; Jediný důvod, proč můžete <xref:System.Array.ForEach%2A?displayProperty=nameWithType> zadat typ pro provoz, je, že metoda má svůj vlastní seznam parametrů typu. Naproti tomu neobecná <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda patří do <xref:System.Collections.Generic.List%601>obecné třídy , takže jednoduše používá parametr typu své třídy. Třída je silně zadána, takže metoda může být metoda instance.  
  
 Obecný <xref:System.Predicate%601> delegát představuje metodu, která určuje, zda určitý prvek splňuje kritéria, která definujete. Můžete jej použít s následujícími <xref:System.Array> statickými obecnými metodami hledání <xref:System.Array.Exists%2A>prvku <xref:System.Array.Find%2A> <xref:System.Array.FindAll%2A>nebo <xref:System.Array.FindIndex%2A> <xref:System.Array.FindLast%2A>sady <xref:System.Array.FindLastIndex%2A>prvků: , , , , , a <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>také pracuje s odpovídajícími metodami <xref:System.Collections.Generic.List%601> neobecných instancí obecné třídy.  
  
 Obecný <xref:System.Comparison%601> delegát umožňuje zadat pořadí řazení pro prvky pole nebo seznamu, které nemají nativní pořadí řazení, nebo přepsat nativní pořadí řazení. Vytvořte metodu, která provádí porovnání, <xref:System.Comparison%601> vytvořte instanci delegáta, která bude <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> představovat vaši metodu, a pak předejte pole a delegáta statickou obecnou metodu. Obecná <xref:System.Collections.Generic.List%601> třída poskytuje odpovídající přetížení <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>metody instance .  
  
 Obecný <xref:System.Converter%602> delegát umožňuje definovat převod mezi dvěma typy a převést pole jednoho typu na pole druhého nebo převést seznam jednoho typu na seznam druhého. Vytvořte metodu, která převede prvky existujícího seznamu na nový typ, vytvořte <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> instanci delegáta představující metodu a použijte obecnou <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> statickou metodu k vytvoření pole nového typu z původního pole nebo metody obecné instance k vytvoření seznamu nového typu z původního seznamu.  
  
### <a name="chaining-delegates"></a>Řetězení delegátů  
 Mnoho metod, které používají tyto delegáty vrátit pole nebo seznam, který může být předán do jiné metody. Chcete-li například vybrat určité prvky pole, převést tyto prvky na nový typ a uložit je do <xref:System.Array.FindAll%2A> nového <xref:System.Array.ConvertAll%2A> pole, můžete předat pole vrácené obecnou metodou obecné metodě. Pokud nový typ prvku postrádá přirozené pořadí řazení, můžete předat <xref:System.Array.ConvertAll%2A> pole vrácené obecnou metodou <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> obecné metodě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
