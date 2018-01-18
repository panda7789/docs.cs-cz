---
title: "Návod: Dotazování napříč relacemi (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fef9880d5f9fa652eab2eb0d17bbf782dc64773d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Návod: Dotazování napříč relacemi (Visual Basic)
Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Je nutné provést [návod: jednoduché objektový Model a dotazů (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). Tento návod vytvoří na něm, včetně přítomnost souboru northwnd.mdf v c:\linqtest.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z tři hlavní cíle:  
  
-   Přidání třídy entity představují objednávky tabulky v ukázkové databázi Northwind.  
  
-   Poznámky k dodávání `Customer` třída k vylepšení vztah mezi `Customer` a `Order` třídy.  
  
-   Vytváření a spouštění dotazu otestovat proces získání `Order` informace pomocí `Customer` třídy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapování vazeb v rámci tabulky  
 Po `Customer` definici třídy, vytvořte `Order` definice třídy entity, která zahrnuje následující kód, který označuje, že `Orders.Customer` má vztah jako cizí klíč k `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Chcete-li přidat třídy entita pořadí  
  
-   Zadejte nebo vložte následující kód po `Customer` třídy:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Zadávání poznámek k třídě zákazníka  
 V tomto kroku přidávat poznámky `Customer` třída indikující její vztah k `Order` třídy. (Přidání není nezbytně nutné, protože definováním relace v obou směrech je dostačující k vytvoření propojení. Ale přidávání tato anotace umožňují snadno přejít objekty v obou směrech.)  
  
#### <a name="to-annotate-the-customer-class"></a>K přidání poznámek ke třídě zákazníka  
  
-   Zadejte nebo vložte následující kód do `Customer` třídy:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Vytvoření a spuštění dotazu pro odběratele objednávku relace  
 Nyní máte přístup `Order` objekty přímo z `Customer` objekty, nebo v opačném pořadí. Není nutné explicitního *spojení* mezi zákazníci a objednávky.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Pro přístup k objektům pořadí pomocí zákaznických objektů  
  
1.  Změnit `Sub Main` metoda zadáním nebo vložením následující kód do metody:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  Stisknutím klávesy F5 ladění aplikace.  
  
     Dva názvy se zobrazí v okně zprávy a v okně konzoly zobrazí generovaného kódu SQL.  
  
3.  Okno zprávy k zastavení ladění zavřete.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Vytvoření zobrazení se silnými typy databáze  
 Je mnohem snazší začínat zobrazení se silnými typy vaší databáze. Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>. Můžete použít silného typu tabulky do vašich dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.  
  
 V následujících krocích vytvoříte `Customers` jako silného typu tabulku, která se mapuje na tabulku zákazníků v databázi.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Na typově DataContext objektu  
  
1.  Přidejte následující kód výše `Customer` deklarace třídy.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  Upravit `Sub Main` používat silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  Stisknutím klávesy F5 ladění aplikace.  
  
     Okno výstup konzoly je:  
  
     `ID=WHITC`  
  
4.  Stisknutím klávesy Enter v okně konzoly aplikace se zavře.  
  
5.  Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** Pokud chcete uložit tuto aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 Další návod ([návod: manipulace dat (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak pracovat s daty. Tento návod nevyžaduje, abyste uložili dva postupy z této série, která jste už dokončili.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
