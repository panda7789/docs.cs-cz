---
title: 'Postupy: Načtení informací ve stavu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: b98c5e6ea49695015eb566ca2176b23c5260017a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928703"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Postupy: Načtení informací ve stavu jen pro čtení
Pokud nechcete data změnit, můžete zvýšit výkon dotazů hledáním výsledků jen pro čtení.  
  
 Implementujete zpracování <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> jen pro čtení nastavením na `false`.  
  
> [!NOTE]
> Pokud <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastaveno na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> je implicitně nastaveno na `false`.  
  
## <a name="example"></a>Příklad  
 Následující kód načte kolekci kalendářních dat o přijímácích zaměstnanců jen pro čtení.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
