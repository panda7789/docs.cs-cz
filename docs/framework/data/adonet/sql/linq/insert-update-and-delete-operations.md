---
title: "INSERT, Update a operace odstranění"
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
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bc279fa541ed14244ea093dcd3ea52c37a4698f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="insert-update-and-delete-operations"></a>INSERT, Update a operace odstranění
Můžete provést `Insert`, `Update`, a `Delete` operace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přidání, změně a odebírání objektů v objektovém modelu. Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znamená, že je vaše akce jazyka SQL a odešle změny do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nabízí větší manipulace a zachování změn, které jste provedli k objektům. Jakmile objekty entity jsou k dispozici (buď je pomocí dotazu načítání nebo vytváření je znovu), můžete je změnit jako typický objekty ve vaší aplikaci. To znamená můžete změnit jejich hodnoty, můžete je přidat do kolekce a můžete je odebrat z kolekce. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sleduje změny a je připravený k přenosu zpět do databáze při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje nebo rozpoznat kaskádové odstranění operace. Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte buď sadu `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi, nebo pomocí vlastní kód nejprve odstranit podřízené objekty, které zabránit odstranění nadřazený objekt. V opačném případě je vyvolána výjimka. Další informace najdete v tématu [postupy: odstranění řádků z databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Následující úryvky použití `Customer` a `Order` třídy z ukázková databáze Northwind. Definice tříd nejsou zobrazeny jako stručný výtah.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticky generuje a spouští příkazy SQL, které musí mít přenést vaše změny zpět do databáze.  
  
> [!NOTE]
>  Toto chování můžete přepsat pomocí vlastní vlastní logiky, obvykle prostřednictvím uložené procedury. Další informace najdete v tématu [odpovědnosti vývojáře v přepsání výchozí chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vývoji uložené procedury pro tento účel.  
  
## <a name="see-also"></a>Viz také  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
