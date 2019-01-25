---
title: 'Průvodce: Dotazování napříč relacemi (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a24d96c9d138f0dcd2f162dad474da01f49e45d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563662"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="75a2f-102">Průvodce: Dotazování napříč relacemi (C#)</span><span class="sxs-lookup"><span data-stu-id="75a2f-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="75a2f-103">Tento návod demonstruje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="75a2f-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="75a2f-104">Tento návod byl napsán s použitím Visual C# vývojovým nastavením.</span><span class="sxs-lookup"><span data-stu-id="75a2f-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="75a2f-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75a2f-105">Prerequisites</span></span>  
 <span data-ttu-id="75a2f-106">Je nutné dokončit [názorný postup: Jednoduchý objektový Model a dotaz (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="75a2f-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="75a2f-107">Tento návod vychází, že jedna, včetně přítomnost souboru northwnd.mdf c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="75a2f-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="75a2f-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="75a2f-108">Overview</span></span>  
 <span data-ttu-id="75a2f-109">Tento názorný postup se skládá ze tří hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="75a2f-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="75a2f-110">Přidání entity třídy představující v tabulce objednávky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="75a2f-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="75a2f-111">Poznámky k doplnění `Customer` třídy k vylepšení vztah mezi `Customer` a `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="75a2f-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="75a2f-112">Vytváření a spouštění dotazů k otestování získání `Order` informace s použitím `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="75a2f-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="75a2f-113">Mapování relací mezi tabulkami</span><span class="sxs-lookup"><span data-stu-id="75a2f-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="75a2f-114">Po `Customer` definici třídy, vytvořte `Order` definici třídy, která obsahuje následující kód, což znamená, že `Order.Customer` souvisí jako cizí klíč k `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="75a2f-115">Chcete-li přidat pořadí třída entity</span><span class="sxs-lookup"><span data-stu-id="75a2f-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="75a2f-116">Zadejte nebo vložte následující kód za `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="75a2f-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="75a2f-117">Zadávání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="75a2f-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="75a2f-118">V tomto kroku přidáte poznámky `Customer` třídy k jeho vztah k označení `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="75a2f-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="75a2f-119">(Toto přidání není nezbytně nutné, protože definováním relace v obou směrech je dostatečná pro vytvoření odkazu.</span><span class="sxs-lookup"><span data-stu-id="75a2f-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="75a2f-120">Ale přidání tato poznámka umožňují snadno procházet objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="75a2f-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="75a2f-121">K přidání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="75a2f-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="75a2f-122">Zadejte nebo vložte následující kód do `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="75a2f-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="75a2f-123">Vytvoření a spuštění dotazu v relaci Zákazník objednávky</span><span class="sxs-lookup"><span data-stu-id="75a2f-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="75a2f-124">Teď umožňuje přistupovat k `Order` objekty přímo `Customer` objektů, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="75a2f-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="75a2f-125">Není nutné explicitně *spojení* mezi zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="75a2f-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="75a2f-126">Pro přístup k objektům pořadí pomocí objektů zákazníka</span><span class="sxs-lookup"><span data-stu-id="75a2f-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="75a2f-127">Upravit `Main` metoda zadáním nebo vložením následujícího kódu do metody:</span><span class="sxs-lookup"><span data-stu-id="75a2f-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="75a2f-128">Stisknutím klávesy F5 pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="75a2f-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75a2f-129">Můžete eliminovat kód SQL z okna konzoly tak `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="75a2f-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3.  <span data-ttu-id="75a2f-130">Stisknutím klávesy Enter v okně konzoly se Zastavit ladění.</span><span class="sxs-lookup"><span data-stu-id="75a2f-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="75a2f-131">Vytvoření zobrazení se silnými typy vaší databáze</span><span class="sxs-lookup"><span data-stu-id="75a2f-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="75a2f-132">Je mnohem jednodušší začínat zobrazení se silnými typy vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="75a2f-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="75a2f-133">Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="75a2f-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="75a2f-134">Můžete použít silného typu tabulky ve všech dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="75a2f-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="75a2f-135">V následujících krocích vytvoříte `Customers` jako tabulku silného typu, který se mapuje na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="75a2f-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="75a2f-136">Chcete-li silného typu DataContext object</span><span class="sxs-lookup"><span data-stu-id="75a2f-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="75a2f-137">Přidejte následující kód nad `Customer` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="75a2f-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  <span data-ttu-id="75a2f-138">Upravit `Main` metodu použít silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="75a2f-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  <span data-ttu-id="75a2f-139">Stisknutím klávesy F5 pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="75a2f-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="75a2f-140">Výstup okna konzoly je:</span><span class="sxs-lookup"><span data-stu-id="75a2f-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="75a2f-141">Stisknutím klávesy Enter v okně konzoly se Zastavit ladění.</span><span class="sxs-lookup"><span data-stu-id="75a2f-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="75a2f-142">Další kroky</span><span class="sxs-lookup"><span data-stu-id="75a2f-142">Next Steps</span></span>  
 <span data-ttu-id="75a2f-143">Dalšího názorného postupu ([názorný postup: Zpracování dat (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) ukazuje, jak pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="75a2f-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="75a2f-144">Tento názorný postup nevyžaduje uložit dva postupy v této sérii, které již byly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="75a2f-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a2f-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75a2f-145">See also</span></span>
- [<span data-ttu-id="75a2f-146">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="75a2f-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
