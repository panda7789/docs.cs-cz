---
title: 'Postupy: Načtení informací ve stavu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 8b83a77adb02cc2bcc01b274867143887114bb1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669546"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Postupy: Načtení informací ve stavu jen pro čtení
Pokud je nemáte v úmyslu změnit data, můžete zvýšit výkon dotazů jen pro čtení výsledků hledání.  
  
 Implementace zpracování jen pro čtení tak, že nastavíte <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> k `false`.  
  
> [!NOTE]
>  Když <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastavena na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> implicitně nastavena na `false`.  
  
## <a name="example"></a>Příklad  
 Následující kód načte kolekci jen pro čtení dat zaměstnanců.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
