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
ms.openlocfilehash: b0ecd8661b7c58645e49ca884ed0499e8c828af9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287529"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy
Toto téma poskytuje přehled obecných delegátů pro převody, predikáty hledání a akce, které mají být provedeny na prvcích pole nebo kolekce.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy  
 <xref:System.Action%601>Obecný delegát představuje metodu, která provádí určitou akci u prvku zadaného typu. Můžete vytvořit metodu, která provede požadovanou akci u prvku, vytvořit instanci delegáta, která bude <xref:System.Action%601> reprezentovat tuto metodu, a pak předat pole a delegáta <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statické obecné metodě. Metoda je volána pro každý prvek pole.  
  
 <xref:System.Collections.Generic.List%601>Obecná třída také poskytuje <xref:System.Collections.Generic.List%601.ForEach%2A> metodu, která používá <xref:System.Action%601> delegáta. Tato metoda není obecná.  
  
> [!NOTE]
> Tím se vytvoří zajímavý bod týkající se obecných typů a metod. <xref:System.Array.ForEach%2A?displayProperty=nameWithType>Metoda musí být statická ( `Shared` v Visual Basic) a generická <xref:System.Array> , protože není obecný typ; jediný důvod, proč můžete zadat typ, na kterém <xref:System.Array.ForEach%2A?displayProperty=nameWithType> chcete pracovat, je, že metoda má svůj vlastní seznam parametrů typu. Naopak neobecná <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> Metoda patří do obecné třídy <xref:System.Collections.Generic.List%601> , takže jednoduše používá parametr typu své třídy. Třída je silného typu, takže metoda může být metodou instance.  
  
 <xref:System.Predicate%601>Obecný delegát představuje metodu, která určuje, zda konkrétní element splňuje definovaná kritéria. Můžete ji použít s následujícími statickými obecnými metodami pro <xref:System.Array> hledání prvku nebo sady prvků: <xref:System.Array.Exists%2A> , <xref:System.Array.Find%2A> , <xref:System.Array.FindAll%2A> , <xref:System.Array.FindIndex%2A> , <xref:System.Array.FindLast%2A> , <xref:System.Array.FindLastIndex%2A> , a <xref:System.Array.TrueForAll%2A> .  
  
 <xref:System.Predicate%601>funguje také s odpovídajícími neobecnými instančními metodami <xref:System.Collections.Generic.List%601> Obecné třídy.  
  
 <xref:System.Comparison%601>Obecný delegát umožňuje zadat pořadí řazení pro prvky pole nebo seznamu, které nemají nativní pořadí řazení, nebo přepsat nativní pořadí řazení. Vytvořte metodu, která provede porovnání, vytvořte instanci <xref:System.Comparison%601> delegáta, která bude představovat vaši metodu, a pak předejte pole a delegáta <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statické obecné metodě. <xref:System.Collections.Generic.List%601>Obecná třída poskytuje odpovídající přetížení metody instance, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType> .  
  
 <xref:System.Converter%602>Obecný delegát umožňuje definovat převod mezi dvěma typy a převést pole jednoho typu na pole druhé, nebo pro převod seznamu jednoho typu na seznam druhý. Vytvořte metodu, která převede prvky existujícího seznamu na nový typ, vytvořte instanci delegáta představující metodu a použijte <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> obecnou statickou metodu pro vytvoření pole nového typu z původního pole nebo <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> metody generické instance pro vytvoření seznamu nového typu z původního seznamu.  
  
### <a name="chaining-delegates"></a>Zřetězení delegátů  
 Mnohé z metod, které používají tyto delegáty, vracejí pole nebo seznam, které lze předat jiné metodě. Například pokud chcete vybrat určité prvky pole, převést tyto prvky na nový typ a uložit je v novém poli, můžete předat pole vrácené <xref:System.Array.FindAll%2A> obecnou metodou <xref:System.Array.ConvertAll%2A> obecné metodě. Pokud nový typ elementu nemá přirozené pořadí řazení, můžete předat pole vrácené <xref:System.Array.ConvertAll%2A> obecnou metodou <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> obecné metodě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](index.md)
- [Generování kolekcí v architektuře .NET Framework](collections.md)
- [Obecná rozhraní](interfaces.md)
- [Kovariance a kontravariance](covariance-and-contravariance.md)
