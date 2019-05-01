---
title: 'Návod: Dotazování napříč relacemi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: abd4941697639ec7bdda545b1ead8d57091e9e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038438"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Návod: Dotazování napříč relacemi (Visual Basic)
Tento návod demonstruje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.  
  
## <a name="prerequisites"></a>Požadavky  
 Je nutné dokončit [názorný postup: Jednoduchý objektový Model a dotaz (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). Tento návod vychází, že jedna, včetně přítomnost souboru northwnd.mdf c:\linqtest.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze tří hlavních úloh:  
  
- Přidání entity třídy představující v tabulce objednávky v ukázkové databázi Northwind.  
  
- Poznámky k doplnění `Customer` třídy k vylepšení vztah mezi `Customer` a `Order` třídy.  
  
- Vytváření a spouštění dotazů otestovat proces získávání `Order` informace s použitím `Customer` třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování relací mezi tabulkami  
 Po `Customer` definici třídy, vytvořte `Order` definici třídy, která obsahuje následující kód, což znamená, že `Orders.Customer` souvisí jako cizí klíč k `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Chcete-li přidat pořadí třída entity  
  
- Zadejte nebo vložte následující kód za `Customer` třídy:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Zadávání poznámek ke třídě zákazníka  
 V tomto kroku přidáte poznámky `Customer` třídy k jeho vztah k označení `Order` třídy. (Toto přidání není nezbytně nutné, protože definováním relace v obou směrech je dostatečná pro vytvoření odkazu. Ale přidání tato poznámka umožňují snadno procházet objekty v obou směrech.)  
  
#### <a name="to-annotate-the-customer-class"></a>K přidání poznámek ke třídě zákazníka  
  
- Zadejte nebo vložte následující kód do `Customer` třídy:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu v relaci Zákazník objednávky  
 Teď umožňuje přistupovat k `Order` objekty přímo `Customer` objektů, nebo v opačném pořadí. Není nutné explicitně *spojení* mezi zákazníci a objednávky.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Pro přístup k objektům pořadí pomocí objektů zákazníka  
  
1. Upravit `Sub Main` metoda zadáním nebo vložením následujícího kódu do metody:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Stisknutím klávesy F5 pro ladění vaší aplikace.  
  
     Dva názvy se zobrazí v okně se zprávou a v okně konzoly se zobrazí generovaného kódu SQL.  
  
3. Zavřete okno zpráv Zastavit ladění.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení se silnými typy vaší databáze  
 Je mnohem jednodušší začínat zobrazení se silnými typy vaší databáze. Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>. Můžete použít silného typu tabulky ve všech dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.  
  
 V následujících krocích vytvoříte `Customers` jako tabulku silného typu, který se mapuje na tabulku Customers v databázi.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Chcete-li silného typu DataContext object  
  
1. Přidejte následující kód nad `Customer` deklarace třídy.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Upravit `Sub Main` používat silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Stisknutím klávesy F5 pro ladění vaší aplikace.  
  
     Výstup okna konzoly je:  
  
     `ID=WHITC`  
  
4. Stisknutím klávesy Enter ukončete aplikaci v okně konzoly.  
  
5. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** Pokud chcete uložit této aplikace.  
  
## <a name="next-steps"></a>Další kroky  
 Dalšího názorného postupu ([názorný postup: Manipulace s daty (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak pracovat s daty. Tento názorný postup nevyžaduje uložit dva postupy v této sérii, které již byly dokončeny.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
