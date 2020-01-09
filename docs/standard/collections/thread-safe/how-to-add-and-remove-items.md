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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711308"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Postupy: Přidávání a odebírání položek v ConcurrentDictionary
Tento příklad ukazuje, jak přidat, načíst, aktualizovat a odebrat položky z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Tato třída kolekce je implementace bezpečná pro přístup z více vláken. Doporučujeme, abyste ho používali vždy, když se více vláken může pokusit o přístup k prvkům současně.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> poskytuje několik pohodlných metod, které neumožňují kódu před tím, než se pokusí přidat nebo odebrat data, nejprve zkontrolovat, zda existuje klíč. Následující tabulka uvádí tyto praktické metody a popisuje, kdy je lze použít.  
  
|Metoda|Použít, když...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcete přidat novou hodnotu pro zadaný klíč a v případě, že klíč již existuje, chcete nahradit jeho hodnotu.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcete načíst existující hodnotu pro zadaný klíč, a pokud klíč neexistuje, chcete zadat dvojici klíč/hodnota.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcete přidat, získat, aktualizovat nebo odebrat dvojici klíč/hodnota, a pokud klíč již existuje nebo se pokus nezdaří z jiného důvodu, budete chtít provést několik alternativních akcí.|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dvě instance <xref:System.Threading.Tasks.Task> pro přidání některých prvků do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> souběžně a pak výstup všech obsahu, aby bylo možné zobrazit, že prvky byly úspěšně přidány. Příklad také ukazuje, jak použít metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> pro přidání, aktualizaci a načtení položek z kolekce.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> je navržen pro scénáře s více vlákny. K přidání nebo odebrání položek z kolekce není nutné v kódu používat zámky. Je však vždy možné, že jedno vlákno načte hodnotu a další vlákno okamžitě aktualizuje kolekci tím, že zadává stejnou klíčovou novou hodnotu.  
  
 I když jsou všechny metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> bezpečné pro přístup z více vláken, ne všechny metody jsou atomické, konkrétně <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Uživatelský delegát, který je předán těmto metodám, je vyvolán mimo vnitřní zámek slovníku (to je provedeno, aby se zabránilo neznámému kódu v blokování všech vláken). Proto je možné, že dojde k této sekvenci událostí:  
  
 1\) volá <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, nenalezne žádnou položku a vytvoří novou položku, kterou přidáte, voláním delegáta metoda valueFactory.  
  
 2\) threadB volá <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> souběžně, je vyvolán jeho delegát metoda valueFactory a dorazí na interní zámek před vláknem, a proto je do slovníku přidána nová dvojice klíč-hodnota.  
  
 3\) delegování uživatele vlákna a vlákno se dokončí na zámek, ale nyní vidí, že položka již existuje.  
  
 4\) vlákno provede "Get" a vrátí data, která byla dříve přidána pomocí threadB.  
  
 Proto není zaručeno, že data, která jsou vrácena pomocí <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, jsou stejná data, která byla vytvořena metoda valuefactoryem vlákna. Podobná posloupnost událostí může nastat při volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
