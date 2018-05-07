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
ms.openlocfilehash: 11393f4013a1b5ed9dc90154f289466432102a38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="comparisons-and-sorts-within-collections"></a>Porovnávání a řazení v kolekcích
<xref:System.Collections> Třídy provádění porovnávání v téměř všechny procesy související Správa kolekcí, zda hledání elementu, který chcete odebrat nebo vrací hodnotu z dvojice klíč hodnota.  
  
 Kolekce obvykle využívají procedury rovnosti a řazení porovnávací funkce. Pro porovnání se používají dva konstruktory.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Kontrola rovnosti  
 Metody, jako `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, a `Remove` použít procedury rovnosti pro elementy z kolekce. Pokud je kolekce Obecné, než položky jsou porovnána shoda podle následujících pokynů:  
  
-   Pokud se implementuje typu t. <xref:System.IEquatable%601> obecné rozhraní a pak procedury rovnosti je <xref:System.IEquatable%601.Equals%2A> metody tohoto rozhraní.  
  
-   Pokud typ T neimplementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> se používá.  
  
 Kromě toho některé přetěžování konstruktoru pro kolekce slovníku přijímá <xref:System.Collections.Generic.IEqualityComparer%601> implementace, která se používá k porovnání rovnosti klíče. Příklad, naleznete v části <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktor.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Určení pořadí řazení  
 Metody, jako `BinarySearch` a `Sort` použít řazení porovnávače pro elementy z kolekce. Porovnávání může být mezi elementy kolekce nebo mezi elementem a zadanou hodnotu. Pro porovnání objektů, je koncept `default comparer` a `explicit comparer`.  
  
 Výchozí porovnávače spoléhá na alespoň jeden z objektů porovnávané implementovat **IComparable** rozhraní. Je vhodné implementovat **IComparable** na všechny třídy se používají jako hodnoty v seznamu kolekce nebo jako klíče v kolekci slovníku. Pro obecnou kolekci je určen porovnání rovnosti podle následující:  
  
-   Pokud typ T implementuje <xref:System.IComparable%601?displayProperty=nameWithType> obecné rozhraní, činí výchozí porovnávače <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody tohoto rozhraní  
  
-   Pokud typ T implementuje neobecnou <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávače <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tohoto rozhraní.  
  
-   Pokud typ T neimplementuje buď rozhraní, nejsou k dispozici žádné výchozí porovnávače a je třeba explicitně zadat delegáta porovnávače nebo porovnání.  
  
 Pokud chcete zadat explicitní porovnání, některé metody přijmout **IComparer** implementace jako parametr. Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace.  
  
 Aktuální nastavení jazykové verze systému může ovlivnit porovnávání a řazení v rámci kolekce. Ve výchozím nastavení, porovnávání a řazení v **kolekce** třídy jsou závislé na jazykové verzi. Chcete-li ignorovat nastavení jazykové verze a proto získat konzistentní porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> se členy přetížení, které přijímají <xref:System.Globalization.CultureInfo>. Další informace najdete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Příklad porovnávání a řazení  
 Následující kód ukazuje implementaci nástroje <xref:System.IEquatable%601> a <xref:System.IComparable%601> na objekt jednoduché firmy. Kromě toho, pokud je objekt uložený v seznamu a seřadit, zobrazí se tohoto volání <xref:System.Collections.Generic.List%601.Sort> metoda výsledkem použití výchozí porovnávače pro `Part` typ a <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metoda implementována pomocí anonymní metody.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
