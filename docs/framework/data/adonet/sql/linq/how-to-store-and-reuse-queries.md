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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1d0e0a094148e609dddcb703bd3840d091af8d3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
