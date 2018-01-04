---
title: "Postupy: filtrování dat v relaci"
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
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9d51ac97611379cc6c47ef698bc635bbf46d1e5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-related-data"></a>Postupy: filtrování dat v relaci
Použití <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metody určíte, poddotazech, chcete-li omezit množství načíst data.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metoda omezení `Orders` načíst na ty, které nebyly dodány dnes. Bez tohoto přístupu všechny `Orders` by byly získány, i když se požaduje jenom podmnožina.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
