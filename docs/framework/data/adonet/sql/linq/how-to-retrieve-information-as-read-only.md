---
title: 'Postupy: načtení informací o jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: dd3a510339bca8649f5654d00a9cbdfba156d92c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-information-as-read-only"></a>Postupy: načtení informací o jen pro čtení
Pokud jste neměli v úmyslu změnit data, můžete zvýšit výkon dotazů ve vyhledávání výsledky jen pro čtení.  
  
 Implementace zpracování jen pro čtení nastavením <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> k `false`.  
  
> [!NOTE]
>  Když <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> je nastaven na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> implicitně nastavena na `false`.  
  
## <a name="example"></a>Příklad  
 Následující kód načte kolekci jen pro čtení dat zaměstnanců.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
