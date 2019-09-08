---
title: 'Postupy: Načtení informací ve stavu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793312"
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

- [Koncepty dotazů](query-concepts.md)
- [Dotazování na databázi](querying-the-database.md)
- [Odložené versus okamžité načítání](deferred-versus-immediate-loading.md)
