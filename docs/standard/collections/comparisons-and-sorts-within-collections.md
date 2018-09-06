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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48838a90939899fc1e7e91cdb7bbe98019591416
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036035"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porovnávání a řazení v kolekcích
<xref:System.Collections> Třídy proveďte porovnání v téměř všech procesů zapojených do Správa kolekcí, zda hledání elementu, který chcete odebrat nebo vrátí hodnotu z dvojice klíč hodnota.  
  
 Kolekce obvykle využívají porovnávání rovnosti a/nebo pořadí porovnávací metody. Pro porovnání se používají dva konstruktory.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Kontroly rovnosti  
 Metody jako `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, a `Remove` použít porovnávání rovnosti pro elementy v kolekci. Pokud kolekce je obecný, než položek porovnání rovnosti podle následujících pokynů:  
  
-   Pokud typ T implementuje <xref:System.IEquatable%601> obecné rozhraní a pak procedury rovnosti je <xref:System.IEquatable%601.Equals%2A> metodu rozhraní.  
  
-   Pokud typ T neimplementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> se používá.  
  
 Kromě toho některá přetížení konstruktoru pro kolekce slovníku přijmout <xref:System.Collections.Generic.IEqualityComparer%601> implementace, která se používá k porovnání rovnosti klíčů. Příklad najdete v tématu <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktoru.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Určení pořadí řazení  
 Metody jako `BinarySearch` a `Sort` použijte pořadí porovnávače pro elementy v kolekci. Porovnání může být mezi prvky v kolekci, nebo mezi prvkem a zadanou hodnotu. Pro porovnání objektů, je koncept `default comparer` a `explicit comparer`.  
  
 Výchozí porovnávací metody spoléhá na minimálně jeden z objektů porovnávané hodnotě implementovat **IComparable** rozhraní. Je vhodné provádět **IComparable** na všechny třídy se používají jako hodnoty v seznamu kolekce nebo jako klíče v kolekci slovníku. Pro obecnou kolekci porovnání rovnosti se určuje podle následujícího schématu:  
  
-   Pokud typ T implementuje <xref:System.IComparable%601?displayProperty=nameWithType> obecné rozhraní a pak výchozí porovnávací metody je <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metoda rozhraní  
  
-   Pokud typ T implementuje neobecnou <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávací metody <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metodu rozhraní.  
  
-   Pokud typ T není implementovat buď rozhraní, nejsou k dispozici žádné výchozí porovnávací metody a porovnání nebo porovnání delegáta musí být zadaná explicitně.  
  
 Pokud chcete poskytnout explicitní porovnávání, některé metody přijímají **IComparer** implementace jako parametr. Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace.  
  
 Nastavení aktuální jazykové verze systému může ovlivnit, porovnávání a řazení v rámci kolekce. Ve výchozím nastavení, porovnávání a řazení v **kolekce** třídy jsou závislé na jazykové verzi. Chcete-li ignorovat nastavení jazykové verze a tím získat jednotné porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> pomocí přetížení členů, které přijímají <xref:System.Globalization.CultureInfo>. Další informace najdete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Příklad rovnosti a řazení  
 Následující kód ukazuje implementaci nástroje <xref:System.IEquatable%601> a <xref:System.IComparable%601> na jednoduché obchodní objekt. Kromě toho, pokud objekt je uložená v seznamu a seřazeny, uvidíte, že volání <xref:System.Collections.Generic.List%601.Sort> metodu vede pomocí výchozí porovnávací metody pro `Part` typ a <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metoda implementovaná pomocí anonymní metodu.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.IComparer>  
- <xref:System.IEquatable%601>  
- <xref:System.Collections.Generic.IComparer%601>  
- <xref:System.IComparable>  
- <xref:System.IComparable%601>
