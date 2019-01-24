---
title: INSERT, Update a operace odstranění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 7dd2eb64a9320d88c7bc3b5feb6578d70f5910b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503661"
---
# <a name="insert-update-and-delete-operations"></a>INSERT, Update a operace odstranění
Provedete `Insert`, `Update`, a `Delete` operace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přidáním, změně a odebrání objekty v objektovém modelu. Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží své akce pro SQL a odeslání změn do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nabízí maximální flexibilitu při manipulaci a při zachování změn, které jste provedli objekty. Jakmile objekty entity jsou k dispozici (buď načítat pomocí dotazu nebo tak, že je nový vytváří), můžete změnit jejich jako typický objekty ve vaší aplikaci. To znamená můžete změnit jejich hodnoty, můžete je přidat do kolekce a můžete ho odebrat z kolekce. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sleduje změny a je připravený k přenosu zpět do databáze při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje ani rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, je nutné buď nastaven `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi, nebo pomocí vlastního kódu nejprve odstranit podřízené objekty, které brání nadřazený objekt odstranit. V opačném případě je vyvolána výjimka. Další informace najdete v tématu [jak: Odstranit řádky z databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Následující ukázky použijte `Customer` a `Order` třídy z ukázkové databáze Northwind. Definice tříd nejsou zobrazeny pro zkrácení.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticky generuje a provede příkazy SQL, které musí mít přenést vaše změny zpět do databáze.  
  
> [!NOTE]
>  Toto chování můžete přepsat pomocí vlastních vlastní logiku, obvykle prostřednictvím uložené procedury. Další informace najdete v tématu [odpovědnosti pro vývojáře v přepisuje výchozí chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vývoji uložené procedury pro tento účel.  
  
## <a name="see-also"></a>Viz také:
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
