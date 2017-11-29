---
title: "Obecní delegáty pro manipulaci s poli a seznamy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 905f30d8b7e6d7c10a0e2b32109076e2950a99ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy
Toto téma obsahuje přehled obecní delegáti převody, predikáty vyhledávání a akce, které budou provedeny na elementy pole nebo kolekce.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy  
 <xref:System.Action%601> Obecný delegát představuje metodu, která provede určitou akci u elementu zadaného typu. Můžete vytvořit metody, která provádí požadované akce v elementu, vytvořte instanci <xref:System.Action%601> delegáta pro reprezentaci této metody a poté předat pole a delegáta <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statické obecná metoda. Metoda je volána pro každý element pole.  
  
 <xref:System.Collections.Generic.List%601> Obecná třída rovněž poskytuje <xref:System.Collections.Generic.List%601.ForEach%2A> metoda, která používá <xref:System.Action%601> delegovat. Tato metoda není Obecné.  
  
> [!NOTE]
>  Díky tomu zajímavého bodu o obecné typy a metody. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Metoda musí být statická (`Shared` v jazyce Visual Basic) a obecná protože <xref:System.Array> není obecný typ; pouze důvod můžete zadat typ pro <xref:System.Array.ForEach%2A?displayProperty=nameWithType> provoz na je, že metoda má svou vlastní seznam parametrů typu. Naopak neobecná <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda patří obecné třídy <xref:System.Collections.Generic.List%601>, takže jednoduše používá parametr typu jeho třídy. Třída je silného typu, aby bylo možné metodu metodu instance.  
  
 <xref:System.Predicate%601> Obecný delegát představuje metodu, která určuje, zda určitý element splňuje kritéria, které definujete. Můžete ji použít s tyto statické obecné metody <xref:System.Array> k vyhledání elementu nebo sadu elementů: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, a <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>taky spolupracuje se službou odpovídající metody neobecné instance <xref:System.Collections.Generic.List%601> obecná třída.  
  
 <xref:System.Comparison%601> Obecný delegát umožňuje zadat pořadí řazení pro prvky pole nebo seznamu, které nemají nativní pořadí řazení nebo přepsat nativní pořadí řazení. Vytvoření metody, která provede porovnání, vytvořte instanci <xref:System.Comparison%601> delegáta pro reprezentaci metodu a pak předejte pole a delegáta <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statické obecná metoda. <xref:System.Collections.Generic.List%601> Obecná třída poskytuje odpovídající přetížení metody instance <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Obecný delegát umožňuje definovat převod mezi dvěma typy a řadu dalších převést pole jednoho typu nebo převést seznam jeden typ na seznam dalších. Vytvoření metody, která převede prvky existujícího seznamu na nový typ, vytvořte instanci delegáta představovat metodu, a <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> obecné statickou metodu k vytvoření nového typu z původní pole, pole nebo <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> obecné Metoda instance k vytvoření seznamu nového typu z původní seznam.  
  
### <a name="chaining-delegates"></a>Zřetězení delegátů  
 Mnoho z metod, které používají tyto delegáty vrací pole nebo seznam, který se dá předat do jiné metody. Například pokud chcete vybrat určité prvky pole, převést tyto prvky na nový typ a uložit je do nové pole, abyste mohli předávat poli vráceném <xref:System.Array.FindAll%2A> obecná metoda k <xref:System.Array.ConvertAll%2A> obecná metoda. Pokud nový typ elementu chybí přirozené pořadí řazení, můžete předat pole vrácené <xref:System.Array.ConvertAll%2A> obecná metoda k <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> obecná metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Obecné typy](../../../docs/standard/generics/index.md)  
 [Obecné kolekce v rozhraní .NET Framework](../../../docs/standard/generics/collections.md)  
 [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)  
 [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
