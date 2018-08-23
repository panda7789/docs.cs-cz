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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8bb84f2e26471e004678afde99a1dd725db6832
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755103"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Postupy: Přidávání a odebírání položek v ConcurrentDictionary
Tento příklad ukazuje, jak přidat, načíst, aktualizovat a odebírat položky z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Tato kolekce třída je implementace bezpečné pro vlákna. Doporučujeme vám použít ho pokaždé, když se více vláken může být pokus o přístup k prvkům.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> nabízí několik metod pohodlí, které není nutné, aby kód nejprve zkontrolujte, jestli existuje klíč předtím, než se pokusí přidat nebo odebrat data. Následující tabulka uvádí tyto metody pohodlí a popisuje jejich použití.  
  
|Metoda|Použijte v této situaci...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcete přidat novou hodnotu pro zadaný klíč a, pokud klíč již existuje, chcete nahradit její hodnotu.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcete načíst existující hodnotu pro zadaný klíč a, pokud klíč neexistuje, budete chtít zadat dvojice klíč/hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcete přidat, získat, aktualizovat nebo odebrat dvojici klíč/hodnota, a pokud klíč již existuje nebo z jakéhokoli důvodu nezdaří, budete chtít provádět některé alternativní akci.|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Threading.Tasks.Task> instance přidání některých prvků <xref:System.Collections.Concurrent.ConcurrentDictionary%602> současně a potom vypíše veškerý obsah, chcete-li zobrazit, že prvky byly úspěšně přidány. Tento příklad také ukazuje způsob použití <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody pro přidání, aktualizace a načítat položky z kolekce.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> je určená pro scénáře s více vlákny. Nemáte nepoužívají zámky ve vašem kódu přidat nebo odebrat položky z kolekce. Vždy je však možné pro jedno vlákno k načtení hodnoty a jiné vlákno se okamžitě aktualizovat kolekci tím, že stejný klíč novou hodnotu.  
  
 Také Ačkoli všechny metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou bezpečné pro vlákna, ne všechny metody jsou atomické, konkrétně <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Uživatelský delegát, který je předán do těchto metod je vyvolána mimo slovníku interní zámku (to se provádí zabránit zablokování všechna vlákna neznámý kód). Proto je možné toto pořadí k událostem:  
  
 1\) threadA volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, zjistí žádná položka a vytvoří novou položku a přidat tak, že vyvolá delegáta metoda valueFactory.  
  
 2\) threadB volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> souběžně, je vyvolán delegát její metoda valueFactory dorazí na interní zámek před threadA a proto jeho nový pár klíč hodnota se přidá do slovníku.  
  
 3\) dokončí threadA v uživatelském delegátu a vlákna dorazí na zámek, ale teď se zobrazí, že položka již existuje.  
  
 4\) threadA provede "Get" a vrátí data, která byla dříve přidal threadB.  
  
 Proto není zaručeno, že data, která je vrácena <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> je stejná data, která byla vytvořena metoda valueFactory vlákna. Podobně jako posloupnost událostí může dojít, když <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> je volána.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
