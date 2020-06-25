---
title: Přidávání a odebírání položek v ConcurrentDictionary
description: Přečtěte si příklad, jak přidat, načíst, aktualizovat a odebrat položky z třídy ConcurrentDictionary<TKey, TValue> kolekce v rozhraní .NET.
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 0bfc17d93ea3088a7b2e4209e25003856770b9e7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325965"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Postup přidání a odebrání položek z ConcurrentDictionary

Tento příklad ukazuje, jak přidat, načíst, aktualizovat a odebrat položky z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> . Tato třída kolekce je implementace bezpečná pro přístup z více vláken. Doporučujeme, abyste ho používali vždy, když se více vláken může pokusit o přístup k prvkům současně.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>poskytuje několik praktických metod, které neumožňují kódu před tím, než se pokusí přidat nebo odebrat data, nejprve zkontrolovat, zda existuje klíč. Následující tabulka uvádí tyto praktické metody a popisuje, kdy je lze použít.

| Metoda | Použít, když... |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Chcete přidat novou hodnotu pro zadaný klíč a v případě, že klíč již existuje, chcete nahradit jeho hodnotu. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Chcete načíst existující hodnotu pro zadaný klíč, a pokud klíč neexistuje, chcete zadat dvojici klíč/hodnota. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Chcete přidat, získat, aktualizovat nebo odebrat dvojici klíč/hodnota, a pokud klíč již existuje nebo se pokus nezdaří z jiného důvodu, budete chtít provést několik alternativních akcí. |

## <a name="example"></a>Příklad

Následující příklad používá dvě <xref:System.Threading.Tasks.Task> instance pro přidání některých prvků <xref:System.Collections.Concurrent.ConcurrentDictionary%602> souběžně a pak výstup všech obsahu, aby bylo možné zobrazit, že prvky byly úspěšně přidány. Příklad také ukazuje, jak použít <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody, a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> pro přidání, aktualizaci a načtení položek z kolekce.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>je určen pro scénáře s více vlákny. K přidání nebo odebrání položek z kolekce není nutné v kódu používat zámky. Je však vždy možné, že jedno vlákno načte hodnotu a další vlákno okamžitě aktualizuje kolekci tím, že zadává stejnou klíčovou novou hodnotu.

I když všechny metody jsou bezpečné pro přístup z <xref:System.Collections.Concurrent.ConcurrentDictionary%602> více vláken, ne všechny metody jsou atomické, konkrétně <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> . Chcete-li zabránit neznámému kódu v blokování všech vláken, uživatelský delegát, který je předán do těchto metod, je vyvolán mimo vnitřní zámek slovníku. Proto je možné, že dojde k této sekvenci událostí:

1. _vlákno_ volá <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> , nenalezne žádnou položku a vytvoří novou položku, která má být přidána, vyvoláním `valueFactory` delegáta.

1. _threadB_ volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> současně, jeho `valueFactory` delegát je vyvolána a dorazí na interní zámek před _vláknem_, a proto je do slovníku přidána nová dvojice klíč-hodnota.

1. uživatelský delegát _vlákna_ je dokončen a vlákno se dorazí na zámek, ale nyní vidí, že položka již existuje.

1. _threadA_ provede "Get" a vrátí data, která byla dříve přidána pomocí _threadB_.

Proto není zaručeno, že data, která jsou vrácena, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> jsou stejná data, která byla vytvořena vláknem `valueFactory` . Podobná posloupnost událostí může nastat při <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> volání.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekce bezpečné pro přístup z více vláken](index.md)
