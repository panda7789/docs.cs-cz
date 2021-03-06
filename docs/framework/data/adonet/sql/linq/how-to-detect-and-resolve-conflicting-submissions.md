---
title: 'Postupy: Zjištění a vyřešení konfliktních odeslání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 2de0182cc0b87768a9cff553b7ec6e77f8ccc7b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793772"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Postupy: Zjištění a vyřešení konfliktních odeslání
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají ze změn více uživatelů v databázi. Další informace najdete v tématu [jak: Spravujte konflikty](how-to-manage-change-conflicts.md)změn.  
  
## <a name="example"></a>Příklad  
 Následující `try` příklad ukazuje / <xref:System.Data.Linq.ChangeConflictException> blok, který zachycuje výjimku. `catch` Informace o entitách a členech pro každý konflikt se zobrazí v okně konzoly.  
  
> [!NOTE]
> Pro podporu načítání informací `using System.Reflection` musíte použít`Imports System.Reflection` direktivu (v Visual Basic). Další informace naleznete v tématu <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
