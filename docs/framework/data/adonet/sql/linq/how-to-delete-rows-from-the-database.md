---
title: 'Postupy: Odstranění řádků z databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 48377aed85aebcf83cb61b4d4dcf9bb732d0cb0e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041181"
---
# <a name="how-to-delete-rows-from-the-database"></a>Postupy: Odstranění řádků z databáze

Řádky v databázi můžete odstranit odebráním odpovídajících [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektů z jejich kolekce související s tabulkami. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Převede změny na příslušné příkazy SQL `DELETE` .

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje ani nerozeznává operace kaskádového odstranění. Pokud chcete odstranit řádek v tabulce, která má omezení proti němu, je nutné provést jednu z následujících úloh:

- `ON DELETE CASCADE` Nastavte pravidlo v omezení cizího klíče v databázi.

- Použijte vlastní kód pro první odstranění podřízených objektů, které brání odstranění nadřazeného objektu.

 V opačném případě je vyvolána výjimka. Viz druhý příklad kódu dále v tomto tématu.

> [!NOTE]
> Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`a `Delete` databázové operace. Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).
>
> Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.

Následující postup předpokládá, že <xref:System.Data.Linq.DataContext> se připojíte k databázi Northwind. Další informace najdete v tématu [jak: Připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).

### <a name="to-delete-a-row-in-the-database"></a>Odstranění řádku v databázi

1. Dotaz na databázi pro řádek, který se má odstranit

2. Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.

3. Odeslat změnu do databáze.

## <a name="example"></a>Příklad

Tento první příklad kódu se dotazuje databáze na Podrobnosti objednávky, které patří k objednávce #11000, označí tyto podrobnosti objednávky k odstranění a odešle tyto změny do databáze.

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a>Příklad

V tomto druhém příkladu je cílem odebrat objednávku (#10250). Kód nejprve prohledá `OrderDetails` tabulku, aby bylo možné zjistit, zda je v pořadí, ve kterém má být odebráno podřízené objekty. Má-li objednávka podřízené položky, nejprve podřízené položky a pořadí jsou označeny pro odebrání. <xref:System.Data.Linq.DataContext> Vrátí skutečné odstranění ve správném pořadí, aby se příkazy DELETE odesílané do databáze dodržovaly omezeními databáze.

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
