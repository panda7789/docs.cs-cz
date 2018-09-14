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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8266db66abb46ffc9503bdaeaf4ec4078177760
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521355"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy
Toto téma obsahuje základní informace o obecných delegátů pro převody, predikáty vyhledávání a akce mají být provedeny na elementy pole nebo kolekce.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Obecní delegáty pro manipulaci s poli a seznamy  
 <xref:System.Action%601> Obecný delegát představuje metodu, která provede určitou akci na prvek zadaného typu. Můžete vytvořit metodu, která provede požadovanou akci na elementu, vytvořte instanci <xref:System.Action%601> delegáta pro reprezentaci metody a pak předejte pole a delegáta <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statické obecné metody. Metoda je volána pro každý prvek pole.  
  
 <xref:System.Collections.Generic.List%601> Obecná třída rovněž poskytuje <xref:System.Collections.Generic.List%601.ForEach%2A> metodu, která se používá <xref:System.Action%601> delegovat. Tato metoda není obecná.  
  
> [!NOTE]
>  Díky tomu je zajímavé bod týkající se obecné typy a metody. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Metoda musí být statická (`Shared` v jazyce Visual Basic) a obecná protože <xref:System.Array> není obecný typ, můžete určit typ pro jediným důvodem <xref:System.Array.ForEach%2A?displayProperty=nameWithType> ovládajících je, že tato metoda má svůj vlastní seznam parametrů typu. Naopak neobecné <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda patří do obecné třídy <xref:System.Collections.Generic.List%601>, takže stačí používá parametr typu své třídy. Třída je silně typováno, takže metoda může být metoda instance.  
  
 <xref:System.Predicate%601> Obecný delegát představuje metodu, která určuje, jestli konkrétní prvek splňuje kritéria, které definujete. Můžete ji použijete s následující statických obecných metod <xref:System.Array> vyhledat prvek nebo sadu elementů: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, a <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> funguje taky s odpovídající instance neobecné metody <xref:System.Collections.Generic.List%601> obecnou třídu.  
  
 <xref:System.Comparison%601> Obecného delegátu umožňuje zadat pořadí řazení pro pole nebo seznam prvků, které nemají nativní pořadí řazení nebo přepsat nativní pořadí řazení. Vytvoření metody, která provádí porovnání, vytvořte instanci <xref:System.Comparison%601> delegáta reprezentující metodu, a pak předejte pole a delegáta <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statické obecné metody. <xref:System.Collections.Generic.List%601> Obecná třída obsahuje odpovídající přetížení metody instance, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Obecného delegátu umožňuje definovat převod mezi dvěma typy a převod pole jednoho typu na celou řadu druhou nebo převést seznam jednoho typu na druhý seznam. Vytvořit metodu, která převede prvky ze seznamu existujících nového typu, vytvořte instanci delegáta k reprezentaci dané metody a použít <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> obecný statickou metodu pro vytvoření nového typu z původní pole, pole nebo <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> obecné instance metodu za účelem vytvoření seznamu nový typ z původního seznamu.  
  
### <a name="chaining-delegates"></a>Zřetězení delegátů  
 Mnoho metod, které používají tyto delegáty vracet pole nebo seznamu, které mohou být předány jiné metodě. Například pokud chcete vybrat některé prvky pole, převést tyto prvky na nový typ a uložit je do nového pole, můžete předat pole vrácené metodou <xref:System.Array.FindAll%2A> obecnou metodu pro <xref:System.Array.ConvertAll%2A> obecné metody. Pokud nový typ elementu chybí přirozené pořadí řazení, můžete předat pole vrácené metodou <xref:System.Array.ConvertAll%2A> obecnou metodu pro <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> obecné metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Obecné typy](../../../docs/standard/generics/index.md)  
- [Generování kolekcí v architektuře .NET Framework](../../../docs/standard/generics/collections.md)  
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)  
- [Kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)
