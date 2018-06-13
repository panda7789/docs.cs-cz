---
title: 'Postupy: zjištění a vyřešení konfliktu odesílání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: dfe1fac4285b915c316fb70d1e3bd1e7b99f145a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354391"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Postupy: zjištění a vyřešení konfliktu odesílání
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají z více uživateli změny do databáze. Další informace najdete v tématu [postupy: Správa konfliktů změnu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `try` / `catch` blok, který zachytí <xref:System.Data.Linq.ChangeConflictException> výjimka. Informace o jednotlivých konflikt entity a člen se zobrazí v okně konzoly.  
  
> [!NOTE]
>  Musí zahrnovat `using System.Reflection` – direktiva (`Imports System.Reflection` v jazyce Visual Basic) pro podporu načítání informací. Další informace naleznete v tématu <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
