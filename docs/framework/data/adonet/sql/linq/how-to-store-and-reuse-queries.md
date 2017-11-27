---
title: "Postupy: uložení a znovu používat dotazy"
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
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 321be8e2cd38ea1138e54587ee876ceb82f67440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-and-reuse-queries"></a>Postupy: uložení a znovu používat dotazy
Když máte aplikaci, která provádí mnohokrát strukturálně podobné dotazy, můžete zvýšit výkon často kompilování dotazu jednou a spouštění s odlišnými parametry několikrát. Například aplikace může mít načíst všechny zákazníky, kteří jsou z určitého města, kde je zadán Město v době běhu uživatelem ve formuláři. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje použití *zkompilovat dotazy* pro tento účel.  
  
> [!NOTE]
>  Tento vzor využití představuje nejčastěji používá pro kompilované dotazy. Jiné postupy je možné. Například kompilované dotazy mohou být uloženy jako statické členy na částečné třídu, která rozšiřuje kód vygenerovaný návrháře.  
  
## <a name="example"></a>Příklad  
 V mnoha případech můžete chtít znovu používat dotazy napříč hranicemi přístup z více vláken. V takových případech je zvláště efektivní ukládání kompilované dotazy v statické proměnné. Následující příklad kódu předpokládá `Queries` třída určená k uložení zkompilovat dotazy a předpokládá Northwind třída, která představuje silného typu <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Příklad  
 Nemůžete aktuálně dotazy úložiště (v statické proměnné), které vracejí *anonymního typu*, protože typ nemá název zajistit jako obecný argument. Následující příklad ukazuje, jak můžete tento problém obejít tím, že vytvoříte typ, který může představovat výsledek a použít jej jako obecný argument.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.Linq.CompiledQuery>  
 [Koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Dotaz na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
