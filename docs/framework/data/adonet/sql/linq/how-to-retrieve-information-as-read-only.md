---
title: "Postupy: načtení informací o jen pro čtení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 04a20a06cd8ed8785b37bdc604a817b475f93873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
