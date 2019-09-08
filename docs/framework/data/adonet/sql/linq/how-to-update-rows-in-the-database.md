---
title: 'Postupy: Aktualizace řádků v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: c2055e1dd988352b50a439531ab5533f34a4965e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793131"
---
# <a name="how-to-update-rows-in-the-database"></a>Postupy: Aktualizace řádků v databázi

Řádky v databázi lze aktualizovat úpravou hodnot členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ke kolekci a odesláním změn do databáze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Převede změny do příslušných příkazů SQL `UPDATE` .

> [!NOTE]
> Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`a `Delete` databázové operace. Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md).
>
> Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.

Následující postup předpokládá, že <xref:System.Data.Linq.DataContext> se připojíte k databázi Northwind. Další informace najdete v tématu [jak: Připojení k databázi](how-to-connect-to-a-database.md).

### <a name="to-update-a-row-in-the-database"></a>Aktualizace řádku v databázi

1. Dotaz na databázi pro řádek, který se má aktualizovat

2. Proveďte požadované změny hodnot členů ve výsledném [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.

3. Odešlete změny do databáze.

## <a name="example"></a>Příklad

Následující příklad dotazuje databázi pro pořadí #11000 a poté změní hodnoty `ShipName` a `ShipVia` ve výsledném `Order` objektu. Nakonec se změny těchto hodnot členů odesílají do databáze jako změny ve `ShipName` sloupcích a. `ShipVia`

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
