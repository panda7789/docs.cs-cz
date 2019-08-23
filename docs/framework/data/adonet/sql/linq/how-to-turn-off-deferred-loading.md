---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938680"
---
# <a name="how-to-turn-off-deferred-loading"></a>Postupy: Vypnutí odloženého načítání
Odložené načítání můžete vypnout nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false` Další informace najdete v tématu [odložené porovnání a okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Odložené načítání je vypnuto, je-li sledování objektu vypnuto. Další informace najdete v tématu [jak: Načte informace jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
