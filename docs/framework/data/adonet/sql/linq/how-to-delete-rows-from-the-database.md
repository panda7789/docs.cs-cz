---
title: "Postupy: odstranění řádků z databáze"
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
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ac81e4e18c578f11a5c6f36203e15b5363c54e71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-delete-rows-from-the-database"></a>Postupy: odstranění řádků z databáze
Odstraněním řádků v databázi odebráním odpovídající [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty z kolekce jejich související tabulky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]přeloží všechny změny příslušné SQL `DELETE` příkazy.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje nebo rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte provést některý z následujících úloh:  
  
-   Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.  
  
-   Pomocí vlastního kódu nejprve odstranit podřízené objekty, které zabránit odstranění nadřazený objekt.  
  
 V opačném případě je vyvolána výjimka. Najdete v druhém příkladu dále v tomto tématu.  
  
> [!NOTE]
>  Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace. Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.  
  
 Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind. Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Chcete-li odstranit řádek v databázi  
  
1.  Dotaz na databázi pro řádku, který má být odstraněna.  
  
2.  Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metoda.  
  
3.  Odeslání změn do databáze.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu se dotazuje databáze podrobnosti pořadí, které patří do &#11000; pořadí, označí tyto podrobnosti pořadí k odstranění a odešle tyto změny do databáze.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu druhý cílem je odebrat pořadí (#10250). Kód nejprve hledá `OrderDetails` tabulky, zda má pořadí, které se odeberou existuje podřízené objekty. Pokud pořadí obsahuje podřízené položky, první podřízené objekty a pak pořadí jsou označeny pro odebrání. <xref:System.Data.Linq.DataContext> Vloží skutečného odstranění ve správném pořadí tak, aby odeslal do databáze příkazy odstranění dodržováním omezení databáze.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
