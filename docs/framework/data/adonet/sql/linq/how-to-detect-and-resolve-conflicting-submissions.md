---
title: "Postupy: zjištění a vyřešení konfliktu odesílání"
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
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2abd54a7ce2500a1fda39dc781052b9d7656afee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Postupy: zjištění a vyřešení konfliktu odesílání
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]poskytuje mnoho prostředků pro zjišťování a řešení konfliktů, které vyplývají z více uživateli změny do databáze. Další informace najdete v tématu [postupy: Správa konfliktů změnu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `try` / `catch` blok, který zachytí <xref:System.Data.Linq.ChangeConflictException> výjimka. Informace o jednotlivých konflikt entity a člen se zobrazí v okně konzoly.  
  
> [!NOTE]
>  Musí zahrnovat `using System.Reflection` – direktiva (`Imports System.Reflection` v jazyce Visual Basic) pro podporu načítání informací. Další informace naleznete v tématu <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
