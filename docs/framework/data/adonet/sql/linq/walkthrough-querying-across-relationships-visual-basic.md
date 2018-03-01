---
title: "Návod: Dotazování napříč relacemi (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: fef9880d5f9fa652eab2eb0d17bbf782dc64773d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="200c6-102">Návod: Dotazování napříč relacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="200c6-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="200c6-103">Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="200c6-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="200c6-104">Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="200c6-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="200c6-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="200c6-105">Prerequisites</span></span>  
 <span data-ttu-id="200c6-106">Je nutné provést [návod: jednoduché objektový Model a dotazů (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="200c6-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="200c6-107">Tento návod vytvoří na něm, včetně přítomnost souboru northwnd.mdf v c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="200c6-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="200c6-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="200c6-108">Overview</span></span>  
 <span data-ttu-id="200c6-109">Tento názorný postup se skládá z tři hlavní cíle:</span><span class="sxs-lookup"><span data-stu-id="200c6-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="200c6-110">Přidání třídy entity představují objednávky tabulky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="200c6-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="200c6-111">Poznámky k dodávání `Customer` třída k vylepšení vztah mezi `Customer` a `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="200c6-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="200c6-112">Vytváření a spouštění dotazu otestovat proces získání `Order` informace pomocí `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="200c6-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="200c6-113">Mapování vazeb v rámci tabulky</span><span class="sxs-lookup"><span data-stu-id="200c6-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="200c6-114">Po `Customer` definici třídy, vytvořte `Order` definice třídy entity, která zahrnuje následující kód, který označuje, že `Orders.Customer` má vztah jako cizí klíč k `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="200c6-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="200c6-115">Chcete-li přidat třídy entita pořadí</span><span class="sxs-lookup"><span data-stu-id="200c6-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="200c6-116">Zadejte nebo vložte následující kód po `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="200c6-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="200c6-117">Zadávání poznámek k třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="200c6-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="200c6-118">V tomto kroku přidávat poznámky `Customer` třída indikující její vztah k `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="200c6-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="200c6-119">(Přidání není nezbytně nutné, protože definováním relace v obou směrech je dostačující k vytvoření propojení.</span><span class="sxs-lookup"><span data-stu-id="200c6-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="200c6-120">Ale přidávání tato anotace umožňují snadno přejít objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="200c6-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="200c6-121">K přidání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="200c6-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="200c6-122">Zadejte nebo vložte následující kód do `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="200c6-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="200c6-123">Vytvoření a spuštění dotazu pro odběratele objednávku relace</span><span class="sxs-lookup"><span data-stu-id="200c6-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="200c6-124">Nyní máte přístup `Order` objekty přímo z `Customer` objekty, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="200c6-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="200c6-125">Není nutné explicitního *spojení* mezi zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="200c6-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="200c6-126">Pro přístup k objektům pořadí pomocí zákaznických objektů</span><span class="sxs-lookup"><span data-stu-id="200c6-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="200c6-127">Změnit `Sub Main` metoda zadáním nebo vložením následující kód do metody:</span><span class="sxs-lookup"><span data-stu-id="200c6-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="200c6-128">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="200c6-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="200c6-129">Dva názvy se zobrazí v okně zprávy a v okně konzoly zobrazí generovaného kódu SQL.</span><span class="sxs-lookup"><span data-stu-id="200c6-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="200c6-130">Okno zprávy k zastavení ladění zavřete.</span><span class="sxs-lookup"><span data-stu-id="200c6-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="200c6-131">Vytvoření zobrazení se silnými typy databáze</span><span class="sxs-lookup"><span data-stu-id="200c6-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="200c6-132">Je mnohem snazší začínat zobrazení se silnými typy vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="200c6-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="200c6-133">Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="200c6-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="200c6-134">Můžete použít silného typu tabulky do vašich dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="200c6-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="200c6-135">V následujících krocích vytvoříte `Customers` jako silného typu tabulku, která se mapuje na tabulku zákazníků v databázi.</span><span class="sxs-lookup"><span data-stu-id="200c6-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="200c6-136">Na typově DataContext objektu</span><span class="sxs-lookup"><span data-stu-id="200c6-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="200c6-137">Přidejte následující kód výše `Customer` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="200c6-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="200c6-138">Upravit `Sub Main` používat silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="200c6-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="200c6-139">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="200c6-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="200c6-140">Okno výstup konzoly je:</span><span class="sxs-lookup"><span data-stu-id="200c6-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="200c6-141">Stisknutím klávesy Enter v okně konzoly aplikace se zavře.</span><span class="sxs-lookup"><span data-stu-id="200c6-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="200c6-142">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** Pokud chcete uložit tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="200c6-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="200c6-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="200c6-143">Next Steps</span></span>  
 <span data-ttu-id="200c6-144">Další návod ([návod: manipulace dat (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="200c6-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="200c6-145">Tento návod nevyžaduje, abyste uložili dva postupy z této série, která jste už dokončili.</span><span class="sxs-lookup"><span data-stu-id="200c6-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200c6-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="200c6-146">See Also</span></span>  
 [<span data-ttu-id="200c6-147">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="200c6-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
