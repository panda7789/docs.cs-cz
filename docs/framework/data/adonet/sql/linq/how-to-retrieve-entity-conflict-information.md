---
title: "Postupy: načtení informací o konflikt Entity"
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
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e43ca054477b75b5737a8ef8f05fc1874d870ac5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Postupy: načtení informací o konflikt Entity
Můžete použít objekty <xref:System.Data.Linq.ObjectChangeConflict> třídy lze zadat informace o zjištěné při konfliktu <xref:System.Data.Linq.ChangeConflictException> výjimky. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu prochází seznam Akumulovaná konflikty.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
