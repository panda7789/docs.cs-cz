---
title: "Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b365d6d3236919f65c840343ec3b33edebea758b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Postupy: Přidávání odebírání jednotlivých položek v BlockingCollection
Tento příklad ukazuje, jak k přidání a odebrání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> blokování a neblokující způsobem. Další informace o <xref:System.Collections.Concurrent.BlockingCollection%601>, najdete v části [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Příklad toho, jak vytvořit výčet <xref:System.Collections.Concurrent.BlockingCollection%601> dokud je prázdný, a budou přidány žádné další prvky, najdete v části [postupy: použití příkazu ForEach k odebrání položek v kolekci BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)  
  
## <a name="example"></a>Příklad  
 Tento první příklad ukazuje, jak přidat a převzít položky tak, aby operace zablokuje, pokud kolekce je buď dočasně prázdná (když se vezme), nebo na maximální kapacity (při přidávání) nebo zadaný časový limit uplynul období. Všimněte si, že blokování na maximální kapacitě je povoleno pouze pokud BlockingCollection byl vytvořen s maximální kapacita určená v konstruktoru.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Příklad  
 Tento druhý příklad ukazuje, jak přidat a převzít položky tak, aby operace se nebude blokovat. Pokud žádná položka se nachází, nebo bylo dosaženo maximální kapacity u ohraničené kolekce nebo uplynutí časového limitu, pak se <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> nebo <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operace vrací hodnotu false. To umožňuje vláknu provádět některé další užitečné činnosti pro chvíli počkat a akci opakujte později buď načíst nové položky, nebo zkuste přidat stejnou položku, kterou nebylo možné přidat dříve. Program také ukazuje, jak implementovat zrušení při přístupu k <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
