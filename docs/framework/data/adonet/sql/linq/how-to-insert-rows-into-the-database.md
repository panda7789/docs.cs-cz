---
title: 'Postupy: Vložení řádků do databáze'
description: Naučte se vkládat řádky do databáze přidáním LINQ to SQL objektů do kolekce související s tabulkami. LINQ to SQL překládá přidávání do příkazů SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286349"
---
# <a name="how-to-insert-rows-into-the-database"></a>Postupy: Vložení řádků do databáze

Řádky do databáze vložíte přidáním objektů do přidružené [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a následným odesláním změn do databáze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Převede změny do příslušných `INSERT` příkazů SQL.

> [!NOTE]
> Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert` , `Update` a `Delete` databázové operace. Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md).
>
> Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.

Následující postup předpokládá, že se <xref:System.Data.Linq.DataContext> připojíte k databázi Northwind. Další informace najdete v tématu [Postup: připojení k databázi](how-to-connect-to-a-database.md).

### <a name="to-insert-a-row-into-the-database"></a>Vložení řádku do databáze

1. Vytvoří nový objekt, který obsahuje data sloupce, která se mají odeslat.

2. Přidejte nový objekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekce přidružené k cílové tabulce v databázi.

3. Odeslat změnu do databáze.

## <a name="example"></a>Příklad

Následující příklad kódu vytvoří nový objekt typu `Order` a naplní ho příslušnými hodnotami. Následně přidá nový objekt do `Order` kolekce. Nakonec odešle změnu do databáze jako nový řádek v `Orders` tabulce.

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a>Viz také

- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
