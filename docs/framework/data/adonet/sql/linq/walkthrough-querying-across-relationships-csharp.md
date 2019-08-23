---
title: 'Návod: Dotazování napříč relacemi (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a9e0583b14c07df2b1de23ba37fa88552a4c5c7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946944"
---
# <a name="walkthrough-querying-across-relationships-c"></a>Návod: Dotazování napříč relacemi (C#)
Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* pro reprezentaci vztahů cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.  
  
## <a name="prerequisites"></a>Požadavky  
 Musíte mít dokončený [Návod: Jednoduchý objektový model a dotaz (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Tento návod sestaví sestavení, včetně přítomnosti souboru northwnd. mdf v c:\linqtest5.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze tří hlavních úloh:  
  
- Přidání třídy entity, která představuje tabulku Orders v ukázkové databázi Northwind.  
  
- Doplnění poznámek ke `Customer` třídě za účelem vylepšení vztahů `Customer` mezi třídami a `Order` .  
  
- Vytvoření a spuštění dotazu pro otestování získání `Order` informací `Customer` pomocí třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování vztahů mezi tabulkami  
 Po definici `Order` `Order.Customer` třídy vytvořte definici třídy entity, která obsahuje následující kód, který označuje, že se týká cizího klíče `Customer.CustomerID`. `Customer`  
  
### <a name="to-add-the-order-entity-class"></a>Přidání třídy Order entity  
  
- Zadejte nebo vložte následující kód za `Customer` třídu:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Anotace třídy zákazníka  
 V tomto kroku označíte `Customer` třídu tak, aby označovala její vztah `Order` ke třídě. (Toto přidání není bezpodmínečně nutné, protože definování vztahu v obou směrech stačí pro vytvoření odkazu. Přidání této poznámky vám ale umožní snadno procházet objekty v obou směrech.)  
  
### <a name="to-annotate-the-customer-class"></a>Anotace třídy zákazníka  
  
- Do `Customer` třídy zadejte nebo vložte následující kód:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu ve vztahu zákazníka – objednávky  
 Nyní můžete přistupovat k `Order` objektům přímo `Customer` z objektů, nebo v opačném pořadí. Mezi zákazníky a objednávkami nemusíte explicitní *spojení* .  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a>Přístup k objektům pořadí pomocí zákaznických objektů  
  
1. `Main` Upravte metodu zadáním nebo vložením následujícího kódu do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. Pro ladění aplikace stiskněte klávesu F5.  
  
    > [!NOTE]
    > Kód SQL můžete v okně konzoly eliminovat tím, že naplníte `db.Log = Console.Out;`komentáře.  
  
3. V okně konzoly stiskněte klávesu ENTER a zastavte ladění.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení databáze silného typu  
 Je mnohem snazší začít s zobrazením silného typu vaší databáze. Silným zadáním <xref:System.Data.Linq.DataContext> objektu není nutné <xref:System.Data.Linq.DataContext.GetTable%2A>volat. Při použití objektu silného typu <xref:System.Data.Linq.DataContext> můžete ve všech dotazech použít tabulky se silnými typy.  
  
 V následujících krocích vytvoříte `Customers` jako tabulku se silným typem, která bude mapována na tabulku Customers v databázi.  
  
### <a name="to-strongly-type-the-datacontext-object"></a>Silného typu objektu DataContext  
  
1. Do deklarace `Customer` třídy přidejte následující kód.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. Upravte metodu pro použití silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem: `Main`  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. Pro ladění aplikace stiskněte klávesu F5.  
  
     Výstup okna konzoly:  
  
     `ID=WHITC`  
  
4. V okně konzoly stiskněte klávesu ENTER a zastavte ladění.  
  
## <a name="next-steps"></a>Další kroky  
 V dalším návodu ([Návod: Manipulace s daty (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) ukazuje, jak manipulovat s daty. Tento návod nevyžaduje, abyste uložili dva návody v této sérii, které jste již dokončili.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
