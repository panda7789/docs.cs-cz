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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159257"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porovnávání a řazení v kolekcích
Třídy <xref:System.Collections> provádějí porovnání téměř všemi procesy zapojenými do správy kolekcí, bez ohledu na to, zda se má element vyhledat, nebo vrátit hodnotu páru klíč-hodnota.  
  
 Kolekce obvykle využívají porovnávání rovnosti a/nebo porovnávací řazení. Pro porovnání se používají dva konstrukce.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Kontroluje se rovnost.  
 Metody jako `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>a `Remove` používají pro prvky kolekce porovnávání rovnosti. Pokud je kolekce obecná, než jsou položky porovnány podle následujících pokynů:  
  
- Pokud typ T implementuje obecné rozhraní <xref:System.IEquatable%601>, pak je porovnávání rovnosti metodou <xref:System.IEquatable%601.Equals%2A> tohoto rozhraní.  
  
- Pokud typ T neimplementuje <xref:System.IEquatable%601>, použije se <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
 Kromě toho některé přetížení konstruktoru pro kolekce slovníku přijímají implementaci <xref:System.Collections.Generic.IEqualityComparer%601>, která se používá k porovnání klíčů pro rovnost. Příklad naleznete v <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktoru.  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Určování pořadí řazení  
 Metody jako `BinarySearch` a `Sort` používají pro prvky kolekce porovnávací řazení. Porovnání mohou být mezi prvky kolekce nebo mezi prvkem a zadanou hodnotou. Pro porovnávání objektů existuje pojem `default comparer` a `explicit comparer`.  
  
 Výchozí porovnávání spoléhá alespoň na jeden objekt, který je porovnán pro implementaci rozhraní **IComparable** . Je vhodné implementovat **IComparable** u všech tříd, které se používají jako hodnoty v kolekci seznamu nebo jako klíče v kolekci slovníku. Pro obecnou kolekci je porovnání rovnosti určeno podle následujících hodnot:  
  
- Pokud typ T implementuje obecné rozhraní <xref:System.IComparable%601?displayProperty=nameWithType>, pak je výchozí porovnávací metodou <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> tohoto rozhraní.  
  
- Pokud typ T implementuje jiné než obecné <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávací metoda <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> tohoto rozhraní.  
  
- Pokud typ T neimplementuje rozhraní, pak neexistuje žádná výchozí porovnávací hodnota a explicitní porovnávací nebo relační delegát musí být poskytnut explicitně.  
  
 Aby bylo možné poskytnout explicitní porovnání, některé metody přijímají implementaci **IComparer** jako parametr. Například metoda <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci.  
  
 Aktuální nastavení jazykové verze systému může ovlivnit porovnání a seřazení v rámci kolekce. Ve výchozím nastavení porovnání a řazení v **kolekcích** tříd jsou závislé na jazykové verzi. Chcete-li ignorovat nastavení jazykové verze, a proto získat konzistentní porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> s přetíženími členů, která přijímají <xref:System.Globalization.CultureInfo>. Další informace naleznete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Příklad rovnosti a řazení  
 Následující kód ukazuje implementaci <xref:System.IEquatable%601> a <xref:System.IComparable%601> v jednoduchém obchodním objektu. Kromě toho, když je objekt uložen v seznamu a seřazen, se zobrazí, že volání metody <xref:System.Collections.Generic.List%601.Sort> má za následek použití výchozí porovnávací metody pro `Part` typ a metoda <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> implementovaná pomocí anonymní metody.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
