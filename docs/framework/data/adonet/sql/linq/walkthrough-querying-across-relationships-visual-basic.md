---
title: 'Návod: Dotazování napříč relacemi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 3164656bb183e7773b098cab79d8fe5e0dc5de34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792145"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Návod: Dotazování napříč relacemi (Visual Basic)
Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* pro reprezentaci vztahů cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán pomocí Visual Basic nastavení vývoje.  
  
## <a name="prerequisites"></a>Požadavky  
 Musíte mít dokončený [Návod: Jednoduchý objektový model a dotaz (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md). Tento návod sestaví sestavení, včetně přítomnosti souboru northwnd. mdf v c:\linqtest.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze tří hlavních úloh:  
  
- Přidání třídy entity, která představuje tabulku Orders v ukázkové databázi Northwind.  
  
- Doplnění poznámek ke `Customer` třídě za účelem vylepšení vztahů `Customer` mezi třídami a `Order` .  
  
- Vytvoření a spuštění dotazu pro otestování procesu získání `Order` informací `Customer` pomocí třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování vztahů mezi tabulkami  
 Po definici `Order` `Orders.Customer` třídy vytvořte definici třídy entity, která obsahuje následující kód, který označuje, že se týká cizího klíče `Customers.CustomerID`. `Customer`  
  
#### <a name="to-add-the-order-entity-class"></a>Přidání třídy Order entity  
  
- Zadejte nebo vložte následující kód za `Customer` třídu:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Anotace třídy zákazníka  
 V tomto kroku označíte `Customer` třídu tak, aby označovala její vztah `Order` ke třídě. (Toto přidání není bezpodmínečně nutné, protože definování vztahu v obou směrech stačí pro vytvoření odkazu. Přidání této poznámky vám ale umožní snadno procházet objekty v obou směrech.)  
  
#### <a name="to-annotate-the-customer-class"></a>Anotace třídy zákazníka  
  
- Do `Customer` třídy zadejte nebo vložte následující kód:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu ve vztahu zákazníka – objednávky  
 Nyní můžete přistupovat k `Order` objektům přímo `Customer` z objektů, nebo v opačném pořadí. Mezi zákazníky a objednávkami nemusíte explicitní *spojení* .  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Přístup k objektům pořadí pomocí zákaznických objektů  
  
1. `Sub Main` Upravte metodu zadáním nebo vložením následujícího kódu do metody:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Pro ladění aplikace stiskněte klávesu F5.  
  
     V okně se zprávou se zobrazí dva názvy a v okně konzoly se zobrazí vygenerovaný kód SQL.  
  
3. Zavřete okno se zprávou pro zastavení ladění.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení databáze silného typu  
 Je mnohem snazší začít s zobrazením silného typu vaší databáze. Silným zadáním <xref:System.Data.Linq.DataContext> objektu není nutné <xref:System.Data.Linq.DataContext.GetTable%2A>volat. Při použití objektu silného typu <xref:System.Data.Linq.DataContext> můžete ve všech dotazech použít tabulky se silnými typy.  
  
 V následujících krocích vytvoříte `Customers` jako tabulku se silným typem, která bude mapována na tabulku Customers v databázi.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Silného typu objektu DataContext  
  
1. Do deklarace `Customer` třídy přidejte následující kód.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Upravte `Sub Main` pro použití silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Pro ladění aplikace stiskněte klávesu F5.  
  
     Výstup okna konzoly:  
  
     `ID=WHITC`  
  
4. V okně konzoly stiskněte klávesu ENTER, aby se aplikace zavřela.  
  
5. V nabídce **soubor** klikněte na **Uložit vše** , pokud chcete tuto aplikaci uložit.  
  
## <a name="next-steps"></a>Další kroky  
 V dalším návodu ([Návod: Manipulace s daty (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak manipulovat s daty. Tento návod nevyžaduje, abyste uložili dva návody v této sérii, které jste již dokončili.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](learning-by-walkthroughs.md)
