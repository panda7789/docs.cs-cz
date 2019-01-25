---
title: 'Postupy: Odstranit řádky z databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 598828f7750fe02082dfccacc64102f96588cb3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554306"
---
# <a name="how-to-delete-rows-from-the-database"></a>Postupy: Odstranit řádky z databáze
Můžete odstranit řádky v databázi tak, že odeberete odpovídající [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty z kolekce související tabulky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží provedené změny do příslušné SQL `DELETE` příkazy.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje ani rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musí být poskytnuto buď z následujících úloh:  
  
-   Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.  
  
-   Pomocí vlastního kódu nejprve odstranit podřízené objekty, které brání nadřazený objekt odstranit.  
  
 V opačném případě je vyvolána výjimka. Viz druhý příklad dále v tomto tématu.  
  
> [!NOTE]
>  Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databázové operace. Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vývoji uložené procedury k tomuto účelu.  
  
 Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> vás připojí k databázi Northwind. Další informace najdete v tématu [jak: Připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Odstranit řádek v databázi  
  
1.  Dotaz na databázi pro řádku, který má být odstraněna.  
  
2.  Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.  
  
3.  Odeslání změn do databáze.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu se dotazuje databáze pro podrobnosti objednávky, která patří #11000 pořadí, označí tato OrderDetails k odstranění a odešle tyto změny do databáze.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 V druhém příkladu cílem je odebrat objednávky (#10250). Kód nejprve zkontroluje `OrderDetails` tabulky ověřte, zda má pořadí odebrání existuje podřízené položky. Pokud pořadí obsahuje podřízené položky, první podřízené objekty a pak pořadí jsou označeny pro odebrání. <xref:System.Data.Linq.DataContext> Vloží skutečné odstraní ve správném pořadí tak, aby odstranění příkazy, odeslané do databáze dodržovat omezení databáze.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
