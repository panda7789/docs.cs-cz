---
title: 'Návod: Dotazování napříč relacemi (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 6bd3255b49676b61a99f8416ab71c217d342e799
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325368"
---
# <a name="walkthrough-querying-across-relationships-c"></a>Návod: Dotazování napříč relacemi (C#)
Tento návod demonstruje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím Visual C# vývojovým nastavením.  
  
## <a name="prerequisites"></a>Požadavky  
 Je nutné dokončit [názorný postup: Jednoduchý objektový Model a dotaz (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Tento návod vychází, že jedna, včetně přítomnost souboru northwnd.mdf c:\linqtest5.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze tří hlavních úloh:  
  
-   Přidání entity třídy představující v tabulce objednávky v ukázkové databázi Northwind.  
  
-   Poznámky k doplnění `Customer` třídy k vylepšení vztah mezi `Customer` a `Order` třídy.  
  
-   Vytváření a spouštění dotazů k otestování získání `Order` informace s použitím `Customer` třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování relací mezi tabulkami  
 Po `Customer` definici třídy, vytvořte `Order` definici třídy, která obsahuje následující kód, což znamená, že `Order.Customer` souvisí jako cizí klíč k `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Chcete-li přidat pořadí třída entity  
  
-   Zadejte nebo vložte následující kód za `Customer` třídy:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Zadávání poznámek ke třídě zákazníka  
 V tomto kroku přidáte poznámky `Customer` třídy k jeho vztah k označení `Order` třídy. (Toto přidání není nezbytně nutné, protože definováním relace v obou směrech je dostatečná pro vytvoření odkazu. Ale přidání tato poznámka umožňují snadno procházet objekty v obou směrech.)  
  
#### <a name="to-annotate-the-customer-class"></a>K přidání poznámek ke třídě zákazníka  
  
-   Zadejte nebo vložte následující kód do `Customer` třídy:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu v relaci Zákazník objednávky  
 Teď umožňuje přistupovat k `Order` objekty přímo `Customer` objektů, nebo v opačném pořadí. Není nutné explicitně *spojení* mezi zákazníci a objednávky.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Pro přístup k objektům pořadí pomocí objektů zákazníka  
  
1. Upravit `Main` metoda zadáním nebo vložením následujícího kódu do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. Stisknutím klávesy F5 pro ladění vaší aplikace.  
  
    > [!NOTE]
    >  Můžete eliminovat kód SQL z okna konzoly tak `db.Log = Console.Out;`.  
  
3. Stisknutím klávesy Enter v okně konzoly se Zastavit ladění.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení se silnými typy vaší databáze  
 Je mnohem jednodušší začínat zobrazení se silnými typy vaší databáze. Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>. Můžete použít silného typu tabulky ve všech dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.  
  
 V následujících krocích vytvoříte `Customers` jako tabulku silného typu, který se mapuje na tabulku Customers v databázi.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Chcete-li silného typu DataContext object  
  
1. Přidejte následující kód nad `Customer` deklarace třídy.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. Upravit `Main` metodu použít silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. Stisknutím klávesy F5 pro ladění vaší aplikace.  
  
     Výstup okna konzoly je:  
  
     `ID=WHITC`  
  
4. Stisknutím klávesy Enter v okně konzoly se Zastavit ladění.  
  
## <a name="next-steps"></a>Další kroky  
 Dalšího názorného postupu ([názorný postup: Zpracování dat (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) ukazuje, jak pracovat s daty. Tento názorný postup nevyžaduje uložit dva postupy v této sérii, které již byly dokončeny.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
