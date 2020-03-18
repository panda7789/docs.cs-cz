---
title: Porovnávání a řazení v kolekcích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: 3360652f22ed39ccfd99f9863052fe584b78562f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159257"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porovnávání a řazení v kolekcích
Třídy <xref:System.Collections> provádět porovnání v téměř všechny procesy, které se podílejí na správě kolekcí, zda hledání prvku odebrat nebo vrácení hodnoty páru klíč a hodnota.  
  
 Kolekce obvykle využívají porovnání rovnosti a/nebo porovnávání pořadí. Pro porovnání se používají dvě konstrukce.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Kontrola rovnosti  
 Metody, `Contains`jako <xref:System.Collections.IList.IndexOf%2A> <xref:System.Collections.Generic.List%601.LastIndexOf%2A>je `Remove` například , , a použít porovnávání rovnosti pro prvky kolekce. Pokud kolekce je obecný, než položky jsou porovnány pro rovnost podle následujících pokynů:  
  
- Pokud typ T <xref:System.IEquatable%601> implementuje obecné rozhraní, pak <xref:System.IEquatable%601.Equals%2A> porovnávání rovnosti je metoda tohoto rozhraní.  
  
- Pokud typ T <xref:System.IEquatable%601>neimplementuje , <xref:System.Object.Equals%2A?displayProperty=nameWithType> se používá.  
  
 Kromě toho některé přetížení konstruktoru pro kolekce <xref:System.Collections.Generic.IEqualityComparer%601> slovníku přijmout implementaci, která se používá k porovnání klíčů pro rovnost. Například viz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktor.  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Určení pořadí řazení  
 Metody, `BinarySearch` jako `Sort` je například a použít porovnání pořadí pro prvky kolekce. Porovnání může být mezi prvky kolekce nebo mezi elementem a zadanou hodnotou. Pro porovnání objektů je koncept a `default comparer` a `explicit comparer`.  
  
 Výchozí porovnávání spoléhá alespoň na jeden z objektů, které jsou porovnány s implementací rozhraní **IComparable.** Je vhodné implementovat **IComparable** na všechny třídy se používají jako hodnoty v seznamu kolekce nebo jako klíče v kolekci slovníku. Pro obecnou kolekci porovnání rovnosti je určena podle následujících:  
  
- Pokud typ T <xref:System.IComparable%601?displayProperty=nameWithType> implementuje obecné rozhraní, pak <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> výchozí porovnávání je metoda tohoto rozhraní  
  
- Pokud typ T implementuje <xref:System.IComparable?displayProperty=nameWithType> neobecné rozhraní, pak <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> výchozí porovnávání je metoda tohoto rozhraní.  
  
- Pokud typ T neimplementuje žádné rozhraní, pak neexistuje žádný výchozí porovnávání a porovnávání nebo porovnání delegát musí být poskytnuty explicitně.  
  
 Chcete-li poskytnout explicitní porovnání, některé metody přijmout **IComparer** implementace jako parametr. Metoda například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci.  
  
 Aktuální nastavení jazykové verze systému může ovlivnit porovnání a řazení v rámci kolekce. Ve výchozím nastavení porovnání a řazení ve **třídách Kolekce** jsou citlivé na jazykovou verzi. Chcete-li ignorovat nastavení jazykové verze a proto získat <xref:System.Globalization.CultureInfo.InvariantCulture%2A> konzistentní porovnání a <xref:System.Globalization.CultureInfo>řazení výsledků, použijte s přetížení majestátu, které přijímají . Další informace naleznete [v tématu Provádění řetězcových operací necitlivých na jazykovou verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací necitlivých na jazykovou verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Příklad rovnosti a řazení  
 Následující kód ukazuje implementaci <xref:System.IEquatable%601> a <xref:System.IComparable%601> na jednoduchý obchodní objekt. Kromě toho, když je objekt uložen v seznamu a seřazeny, uvidíte, že <xref:System.Collections.Generic.List%601.Sort> volání `Part` metody má <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> za následek použití výchozího porovnávání pro typ a metodu implementovanou pomocí anonymní metody.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
