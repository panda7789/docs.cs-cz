---
title: 'Postupy: Filtrování souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037788"
---
# <a name="how-to-filter-related-data"></a>Postupy: Filtrování souvisejících dat
Použití <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metody určíte, poddotazech, chcete-li omezit množství načtena data.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metoda omezení `Orders` načíst na ty, které nebyly dodány ještě dnes. Bez tohoto přístupu všechny `Orders` by byly načteny, i když je požadován pouze podmnožinu.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
