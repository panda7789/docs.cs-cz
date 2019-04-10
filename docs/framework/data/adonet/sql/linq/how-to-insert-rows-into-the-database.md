---
title: 'Postupy: Vložení řádků do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cb2319d51e0518114a04eea2fc7ab6b5a836b7ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328592"
---
# <a name="how-to-insert-rows-into-the-database"></a>Postupy: Vložení řádků do databáze
Vkládání řádků do databáze přidáním objektů s příslušnými [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odešlete změny do databáze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží provedené změny do příslušné SQL `INSERT` příkazy.  
  
> [!NOTE]
>  Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databázové operace. Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vývoji uložené procedury k tomuto účelu.  
  
 Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> vás připojí k databázi Northwind. Další informace najdete v tématu [jak: Připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-insert-a-row-into-the-database"></a>Chcete-li vložit řádek do databáze  
  
1. Vytvořte nový objekt, který obsahuje sloupce dat k odeslání.  
  
2. Přidat nový objekt, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekci spojenou s cílovou tabulkou v databázi.  
  
3. Odeslání změn do databáze.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří nový objekt typu `Order` a naplní ji s příslušnými hodnotami. Potom přidá nový objekt, který `Order` kolekce. Nakonec odešle změnu do databáze jako nový řádek v `Orders` tabulky.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Postupy: Přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
