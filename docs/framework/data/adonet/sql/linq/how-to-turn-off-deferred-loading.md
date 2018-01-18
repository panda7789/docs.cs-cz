---
title: "Postupy: odložené načítání vypnout."
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
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e5c17d0cfa4fed33c2648173002e5ee1bdcc2c15
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-turn-off-deferred-loading"></a>Postupy: odložené načítání vypnout.
Můžete vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`. Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Odložené načtení je vypnutý nepřímo při sledování objektu je vypnutý. Další informace najdete v tématu [postupy: načtení informací jako jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
