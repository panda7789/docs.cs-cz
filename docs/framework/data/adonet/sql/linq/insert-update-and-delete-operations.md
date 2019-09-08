---
title: Operace vložení, aktualizace a odstranění
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793055"
---
# <a name="insert-update-and-delete-operations"></a>Operace vložení, aktualizace a odstranění

Operace, `Insert` `Update`a vnástroji[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provádíte přidáním, změnou a odebráním objektů v objektovém modelu. `Delete` Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převede vaše akce na SQL a odešle změny do databáze.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nabízí maximální flexibilitu v manipulaci s a trvalými změnami, které jste provedli u svých objektů. Jakmile jsou objekty entit k dispozici (buď je načtete prostřednictvím dotazu, nebo je sestavíte poruše), můžete je změnit jako typické objekty v aplikaci. To znamená, že můžete změnit jejich hodnoty, můžete je přidat do kolekcí a můžete je odebrat z kolekcí. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sleduje vaše změny a je připravená je přenést zpět do databáze při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje ani nerozeznává operace kaskádového odstranění. Chcete-li odstranit řádek v tabulce, která má omezení proti němu, je nutné buď nastavit `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi, nebo použít vlastní kód pro první odstranění podřízených objektů, které brání odstranění nadřazeného objektu. V opačném případě je vyvolána výjimka. Další informace najdete v tématu [jak: Odstraní řádky z databáze](how-to-delete-rows-from-the-database.md).

Následující výňatky používají `Customer` třídy a `Order` z ukázkové databáze Northwind. Pro zkrácení nejsou zobrazeny definice tříd.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A>zavoláte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , automaticky generuje a spustí příkazy SQL, které musí mít, aby předávaly vaše změny zpět do databáze.

> [!NOTE]
> Toto chování můžete přepsat pomocí vlastní logiky, obvykle prostřednictvím uložené procedury. Další informace najdete v tématu [zodpovědnosti vývojáře při přepisu výchozího chování](responsibilities-of-the-developer-in-overriding-default-behavior.md).
>
> Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro tento účel.

## <a name="see-also"></a>Viz také:

- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md)
