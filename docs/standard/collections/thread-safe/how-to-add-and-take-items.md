---
title: 'Postupy: Přidat a jednotlivě převzít položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e24c6b5aa02e8bc7ca4bcbf2c69bffd06216962
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535437"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Postupy: Přidat a jednotlivě převzít položek v BlockingCollection
Tento příklad ukazuje, jak přidávat a odebírat položky z <xref:System.Collections.Concurrent.BlockingCollection%601> blokování a neblokující způsobem. Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601>, naleznete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Příklad toho, jak vytvořit výčet <xref:System.Collections.Concurrent.BlockingCollection%601> dokud je prázdný a nebudou přidány žádné další prvky, naleznete v tématu [jak: Použití příkazu ForEach k odebrání položek v BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Příklad  
 Tento první příklad ukazuje, jak přidat a převzít položky tak, aby operace budou blokovat, pokud kolekce je buď dočasně prázdný (když se vezme) nebo na maximální kapacita (při přidávání), nebo pokud má zadaný časový limit vypršel. Všimněte si, že blokování maximální kapacity je povolená jenom při BlockingCollection byl vytvořen s maximální kapacita určená v konstruktoru.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Příklad  
 Tento druhý příklad ukazuje, jak přidat a pořiďte položek nebude blokovat operace. Pokud není k dispozici žádná položka, bylo dosaženo maximální kapacity na ohraničené kolekce nebo vypršel časový limit, pak bude <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace vrátí hodnotu false. To umožňuje vláknu provádět další užitečné operace nějakou dobu a opakujte akci později k načtení nové položky, nebo znovu zkusíte přidat stejnou položku, kterou nebylo možné přidat dříve. Program také ukazuje, jak implementovat při přístupu ke zrušení <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
