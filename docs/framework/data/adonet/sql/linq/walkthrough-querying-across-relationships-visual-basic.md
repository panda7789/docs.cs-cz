---
title: 'Návod: Dotazování napříč relacemi (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: abd4941697639ec7bdda545b1ead8d57091e9e7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314656"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="1ef9e-102">Návod: Dotazování napříč relacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef9e-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="1ef9e-103">Tento návod demonstruje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1ef9e-104">Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1ef9e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ef9e-105">Prerequisites</span></span>  
 <span data-ttu-id="1ef9e-106">Je nutné dokončit [názorný postup: Jednoduchý objektový Model a dotaz (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1ef9e-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="1ef9e-107">Tento návod vychází, že jedna, včetně přítomnost souboru northwnd.mdf c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1ef9e-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="1ef9e-108">Overview</span></span>  
 <span data-ttu-id="1ef9e-109">Tento názorný postup se skládá ze tří hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="1ef9e-110">Přidání entity třídy představující v tabulce objednávky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="1ef9e-111">Poznámky k doplnění `Customer` třídy k vylepšení vztah mezi `Customer` a `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="1ef9e-112">Vytváření a spouštění dotazů otestovat proces získávání `Order` informace s použitím `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="1ef9e-113">Mapování relací mezi tabulkami</span><span class="sxs-lookup"><span data-stu-id="1ef9e-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="1ef9e-114">Po `Customer` definici třídy, vytvořte `Order` definici třídy, která obsahuje následující kód, což znamená, že `Orders.Customer` souvisí jako cizí klíč k `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="1ef9e-115">Chcete-li přidat pořadí třída entity</span><span class="sxs-lookup"><span data-stu-id="1ef9e-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="1ef9e-116">Zadejte nebo vložte následující kód za `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="1ef9e-117">Zadávání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="1ef9e-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="1ef9e-118">V tomto kroku přidáte poznámky `Customer` třídy k jeho vztah k označení `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="1ef9e-119">(Toto přidání není nezbytně nutné, protože definováním relace v obou směrech je dostatečná pro vytvoření odkazu.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="1ef9e-120">Ale přidání tato poznámka umožňují snadno procházet objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="1ef9e-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="1ef9e-121">K přidání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="1ef9e-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="1ef9e-122">Zadejte nebo vložte následující kód do `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="1ef9e-123">Vytvoření a spuštění dotazu v relaci Zákazník objednávky</span><span class="sxs-lookup"><span data-stu-id="1ef9e-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="1ef9e-124">Teď umožňuje přistupovat k `Order` objekty přímo `Customer` objektů, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="1ef9e-125">Není nutné explicitně *spojení* mezi zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="1ef9e-126">Pro přístup k objektům pořadí pomocí objektů zákazníka</span><span class="sxs-lookup"><span data-stu-id="1ef9e-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="1ef9e-127">Upravit `Sub Main` metoda zadáním nebo vložením následujícího kódu do metody:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="1ef9e-128">Stisknutím klávesy F5 pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1ef9e-129">Dva názvy se zobrazí v okně se zprávou a v okně konzoly se zobrazí generovaného kódu SQL.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="1ef9e-130">Zavřete okno zpráv Zastavit ladění.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="1ef9e-131">Vytvoření zobrazení se silnými typy vaší databáze</span><span class="sxs-lookup"><span data-stu-id="1ef9e-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="1ef9e-132">Je mnohem jednodušší začínat zobrazení se silnými typy vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="1ef9e-133">Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="1ef9e-134">Můžete použít silného typu tabulky ve všech dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="1ef9e-135">V následujících krocích vytvoříte `Customers` jako tabulku silného typu, který se mapuje na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="1ef9e-136">Chcete-li silného typu DataContext object</span><span class="sxs-lookup"><span data-stu-id="1ef9e-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="1ef9e-137">Přidejte následující kód nad `Customer` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="1ef9e-138">Upravit `Sub Main` používat silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="1ef9e-139">Stisknutím klávesy F5 pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1ef9e-140">Výstup okna konzoly je:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="1ef9e-141">Stisknutím klávesy Enter ukončete aplikaci v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-141">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="1ef9e-142">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** Pokud chcete uložit této aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1ef9e-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1ef9e-143">Next Steps</span></span>  
 <span data-ttu-id="1ef9e-144">Dalšího názorného postupu ([názorný postup: Manipulace s daty (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="1ef9e-145">Tento názorný postup nevyžaduje uložit dva postupy v této sérii, které již byly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef9e-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ef9e-146">See also</span></span>

- [<span data-ttu-id="1ef9e-147">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="1ef9e-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
