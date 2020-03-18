---
title: 'Postupy: Přidávání a odebírání položek v ConcurrentDictionary'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: dc4d13e09a91633fac1fcf5bd8ab5b043473bd7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711308"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Postupy: Přidávání a odebírání položek v ConcurrentDictionary
Tento příklad ukazuje, jak přidat, načíst, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>aktualizovat a odebrat položky z . Tato třída kolekce je implementace bezpečná pro přístup z více vláken. Doporučujeme jej použít vždy, když více vláken může být pokus o přístup k prvkům současně.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>poskytuje několik convenience metody, které znemožnění pro kód nejprve zkontrolovat, zda klíč existuje před pokusem o přidání nebo odebrání dat. V následující tabulce jsou uvedeny tyto metody pohodlí a popisuje, kdy je použít.  
  
|Metoda|Použijte, když...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcete přidat novou hodnotu pro zadaný klíč a pokud klíč již existuje, chcete nahradit jeho hodnotu.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcete načíst existující hodnotu pro zadaný klíč a pokud klíč neexistuje, chcete zadat dvojici klíč/hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcete přidat, získat, aktualizovat nebo odebrat pár klíč/hodnota a pokud klíč již existuje nebo se pokus nezdaří z jakéhokoli jiného důvodu, chcete provést nějakou alternativní akci.|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Threading.Tasks.Task> dvě instance přidat některé <xref:System.Collections.Concurrent.ConcurrentDictionary%602> prvky souběžně a potom výstupy veškerý obsah ukázat, že prvky byly přidány úspěšně. Příklad také <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>ukazuje, jak <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>používat <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> , a metody pro přidání, aktualizaci a načtení položek z kolekce.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>je určen pro scénáře s více vlákny. Není třeba používat zámky v kódu přidat nebo odebrat položky z kolekce. Je však vždy možné pro jedno vlákno načíst hodnotu a jiné vlákno okamžitě aktualizovat kolekci tím, že stejný klíč novou hodnotu.  
  
 Také i když <xref:System.Collections.Concurrent.ConcurrentDictionary%602> všechny metody jsou bezpečné pro přístup <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> z <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>více vláken, ne všechny metody jsou atomické, konkrétně a . Uživatel delegát, který je předán do těchto metod je vyvolána mimo vnitřní zámek slovníku (to se provádí zabránit neznámý kód z blokování všech podprocesů). Proto je možné, že k této posloupnosti událostí dojde:  
  
 1\) threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>volání , najde žádnou položku a vytvoří novou položku Přidat vyvoláním valueFactory delegáta.  
  
 2\) threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> volání souběžně, jeho valueFactory delegát je vyvolána a dorazí na vnitřní zámek před threadA, a tak jeho nový pár klíč hodnota je přidán do slovníku.  
  
 3\) threadA delegát uživatele dokončí a podproces dorazí na zámek, ale nyní vidí, že položka již existuje.  
  
 4\) threadA provede "Get" a vrátí data, která byla dříve přidána threadB.  
  
 Proto není zaručeno, že data, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> která je vrácena podle je stejná data, která byla vytvořena valueFactory podprocesu. Podobná posloupnost událostí <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> může dojít při volání.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
