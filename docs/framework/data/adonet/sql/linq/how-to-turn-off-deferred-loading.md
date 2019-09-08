---
title: 'Postupy: Vypnutí odloženého načítání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781653"
---
# <a name="how-to-turn-off-deferred-loading"></a>Postupy: Vypnutí odloženého načítání
Odložené načítání můžete vypnout nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false` Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Odložené načítání je vypnuto, je-li sledování objektu vypnuto. Další informace najdete v tématu [jak: Načte informace jen pro čtení](how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vypnout odložené načítání nastavením <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> na. `false`  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
- [Dotazování na databázi](querying-the-database.md)
