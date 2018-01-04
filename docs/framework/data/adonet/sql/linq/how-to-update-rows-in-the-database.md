---
title: "Postupy: aktualizace řádků v databázi"
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
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8999b85da3f7d32cc1c64899dce5cdfeeafbefd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-rows-in-the-database"></a>Postupy: aktualizace řádků v databázi
Řádky v databázi můžete aktualizovat změnou hodnoty členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odeslání změn do databáze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přeloží změny do příslušné SQL `UPDATE` příkazy.  
  
> [!NOTE]
>  Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace. Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.  
  
 Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind. Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-update-a-row-in-the-database"></a>O aktualizaci řádku v databázi  
  
1.  Dotaz na databázi pro aktualizaci řádku.  
  
2.  Provést požadované změny hodnoty členů v výsledná [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.  
  
3.  Odešlete změny do databáze.  
  
## <a name="example"></a>Příklad  
 Následující příklad dotazu na databázi pro pořadí #11000 a poté změní hodnoty `ShipName` a `ShipVia` v výsledná `Order` objektu. Nakonec změny na tyto hodnoty členů se odešlou do databáze jako změny v `ShipName` a `ShipVia` sloupce.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
