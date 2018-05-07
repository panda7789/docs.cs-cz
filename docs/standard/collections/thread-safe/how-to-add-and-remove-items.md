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
ms.openlocfilehash: 6aa309f2c6c44934f491229ac43003a05301bacb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Postupy: Přidávání a odebírání položek v ConcurrentDictionary
Tento příklad ukazuje, jak přidat, získat, aktualizovat a odebrání položek z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Tato třída kolekce je implementace bezpečné pro přístup z více vláken. Doporučujeme vám, že použít kdykoli více vláken může se pokusit o přístup k prvkům.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> poskytuje několik vhodných metod, které není nutné, aby kód nejprve zkontrolujte, jestli existuje klíč, předtím než se pokusí přidat nebo odebrat data. Následující tabulka uvádí tyto metody pohodlí a popisuje jejich použití.  
  
|Metoda|Použijte, když...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcete přidat novou hodnotu pro zadaný klíč, a pokud klíč již existuje, chcete nahradit jeho hodnotu.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Můžete obnovit existující hodnotu pro zadaný klíč, a pokud klíč neexistuje, můžete chtít zadat dvojice klíč/hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcete přidat, získat, aktualizovat nebo odebrat dvojici klíč/hodnota, a pokud klíč již existuje nebo pokus selže z jiného důvodu, kterou chcete provést některé alternativní akce.|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Threading.Tasks.Task> instance k přidání některých prvků <xref:System.Collections.Concurrent.ConcurrentDictionary%602> současně a pak uloží veškerý obsah, aby zobrazil, že byly úspěšně přidány elementy. Příklad také ukazuje způsob použití <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody pro přidání, aktualizace a načítat položky z kolekce.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> je určená pro scénáře s více vlákny. Není nutné používat zámky v kódu k přidání nebo odebrání položky z kolekce. Vždycky je však možné jedno vlákno k načtení hodnoty a jiné vlákno okamžitě aktualizovat kolekci tím, že se stejným klíčem novou hodnotu.  
  
 Také i když všechny metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou bezpečné pro vlákna, ne všechny metody jsou atomic, konkrétně <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Uživatel delegáta, který je předán tyto metody je vyvolána mimo interní zámku slovník. (To se provádí zabránit blokování všechna vlákna neznámý kód). Proto je možné pro toto pořadí k událostem:  
  
 1\) threadA volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, vyhledá žádná položka a vytvoří novou položku do přidat vyvoláním valueFactory delegáta.  
  
 2\) threadB volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> souběžně, je vyvolána jeho valueFactory delegáta a zpráva dorazí na interní zámek před threadA a proto jeho nový pár klíč hodnota se přidá do slovníku.  
  
 3\) dokončí delegáta threadA na uživatele a vlákno dorazí na zámek, ale nyní uvidí, že položka již existuje  
  
 4\) threadA provede "Get" a vrátí data, která byla dříve přidal threadB.  
  
 Proto není zaručeno, že data, která vrátí <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> je stejná data, která byla vytvořená valueFactory vlákna. Podobně jako posloupnost událostí, může dojít, když <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> je volána.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
