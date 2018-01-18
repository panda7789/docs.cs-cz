---
title: "Návod: Dotazování napříč relacemi (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3357fa598cb00b5fa0146540f676d7463a05f146
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-c"></a>Návod: Dotazování napříč relacemi (C#)
Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Je nutné provést [návod: jednoduché objektový Model a dotazů (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Tento návod vytvoří na něm, včetně přítomnost souboru northwnd.mdf v c:\linqtest5.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z tři hlavní cíle:  
  
-   Přidání třídy entity představují objednávky tabulky v ukázkové databázi Northwind.  
  
-   Poznámky k dodávání `Customer` třída k vylepšení vztah mezi `Customer` a `Order` třídy.  
  
-   Vytváření a spouštění dotazu na test získání `Order` informace pomocí `Customer` třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování vazeb v rámci tabulky  
 Po `Customer` definici třídy, vytvořte `Order` definice třídy entity, která zahrnuje následující kód, který označuje, že `Order.Customer` má vztah jako cizí klíč k `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Chcete-li přidat třídy entita pořadí  
  
-   Zadejte nebo vložte následující kód po `Customer` třídy:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Zadávání poznámek k třídě zákazníka  
 V tomto kroku přidávat poznámky `Customer` třída indikující její vztah k `Order` třídy. (Přidání není nezbytně nutné, protože definováním relace v obou směrech je dostačující k vytvoření propojení. Ale přidávání tato anotace umožňují snadno přejít objekty v obou směrech.)  
  
#### <a name="to-annotate-the-customer-class"></a>K přidání poznámek ke třídě zákazníka  
  
-   Zadejte nebo vložte následující kód do `Customer` třídy:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu pro odběratele objednávku relace  
 Nyní máte přístup `Order` objekty přímo z `Customer` objekty, nebo v opačném pořadí. Není nutné explicitního *spojení* mezi zákazníci a objednávky.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Pro přístup k objektům pořadí pomocí zákaznických objektů  
  
1.  Změnit `Main` metoda zadáním nebo vložením následující kód do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Stisknutím klávesy F5 ladění aplikace.  
  
    > [!NOTE]
    >  Kód SQL z okna konzoly můžete eliminovat tím komentářů se `db.Log = Console.Out;`.  
  
3.  Stisknutím klávesy Enter v okně konzoly do Zastavte ladění.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení se silnými typy databáze  
 Je mnohem snazší začínat zobrazení se silnými typy vaší databáze. Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>. Můžete použít silného typu tabulky do vašich dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.  
  
 V následujících krocích vytvoříte `Customers` jako silného typu tabulku, která se mapuje na tabulku zákazníků v databázi.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Na typově DataContext objektu  
  
1.  Přidejte následující kód výše `Customer` deklarace třídy.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Změnit `Main` metodu použít silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Stisknutím klávesy F5 ladění aplikace.  
  
     Okno výstup konzoly je:  
  
     `ID=WHITC`  
  
4.  Stisknutím klávesy Enter v okně konzoly do Zastavte ladění.  
  
## <a name="next-steps"></a>Další kroky  
 Další návod ([návod: manipulace dat (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) ukazuje, jak pracovat s daty. Tento návod nevyžaduje, abyste uložili dva postupy z této série, která jste už dokončili.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
