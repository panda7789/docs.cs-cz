---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033610"
---
# <a name="how-to-turn-off-deferred-loading"></a>Postupy: Vypnutí odloženého načítání
Můžete ji vypnout odloženého načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`. Další informace najdete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Odložené načítání je vypnuto již při objektů pro sledování je vypnuté. Další informace najdete v tématu [jak: Načtení informací ve stavu jen pro čtení](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vypnutí odloženého načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> k `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
