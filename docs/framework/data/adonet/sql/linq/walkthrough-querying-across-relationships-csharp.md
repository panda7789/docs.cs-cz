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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 61586b8d556a9edccace25b75ceb2696ec675dd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="ec0b7-102">Návod: Dotazování napříč relacemi (C#)</span><span class="sxs-lookup"><span data-stu-id="ec0b7-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="ec0b7-103">Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* představují relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="ec0b7-104">Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ec0b7-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec0b7-105">Prerequisites</span></span>  
 <span data-ttu-id="ec0b7-106">Je nutné provést [návod: jednoduché objektový Model a dotazů (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="ec0b7-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="ec0b7-107">Tento návod vytvoří na něm, včetně přítomnost souboru northwnd.mdf v c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ec0b7-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="ec0b7-108">Overview</span></span>  
 <span data-ttu-id="ec0b7-109">Tento názorný postup se skládá z tři hlavní cíle:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="ec0b7-110">Přidání třídy entity představují objednávky tabulky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="ec0b7-111">Poznámky k dodávání `Customer` třída k vylepšení vztah mezi `Customer` a `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="ec0b7-112">Vytváření a spouštění dotazu na test získání `Order` informace pomocí `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="ec0b7-113">Mapování vazeb v rámci tabulky</span><span class="sxs-lookup"><span data-stu-id="ec0b7-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="ec0b7-114">Po `Customer` definici třídy, vytvořte `Order` definice třídy entity, která zahrnuje následující kód, který označuje, že `Order.Customer` má vztah jako cizí klíč k `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="ec0b7-115">Chcete-li přidat třídy entita pořadí</span><span class="sxs-lookup"><span data-stu-id="ec0b7-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="ec0b7-116">Zadejte nebo vložte následující kód po `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="ec0b7-117">Zadávání poznámek k třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="ec0b7-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="ec0b7-118">V tomto kroku přidávat poznámky `Customer` třída indikující její vztah k `Order` třídy.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="ec0b7-119">(Přidání není nezbytně nutné, protože definováním relace v obou směrech je dostačující k vytvoření propojení.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="ec0b7-120">Ale přidávání tato anotace umožňují snadno přejít objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="ec0b7-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="ec0b7-121">K přidání poznámek ke třídě zákazníka</span><span class="sxs-lookup"><span data-stu-id="ec0b7-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="ec0b7-122">Zadejte nebo vložte následující kód do `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="ec0b7-123">Vytvoření a spuštění dotazu pro odběratele objednávku relace</span><span class="sxs-lookup"><span data-stu-id="ec0b7-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="ec0b7-124">Nyní máte přístup `Order` objekty přímo z `Customer` objekty, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="ec0b7-125">Není nutné explicitního *spojení* mezi zákazníci a objednávky.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="ec0b7-126">Pro přístup k objektům pořadí pomocí zákaznických objektů</span><span class="sxs-lookup"><span data-stu-id="ec0b7-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="ec0b7-127">Změnit `Main` metoda zadáním nebo vložením následující kód do metody:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="ec0b7-128">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec0b7-129">Kód SQL z okna konzoly můžete eliminovat tím komentářů se `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3.  <span data-ttu-id="ec0b7-130">Stisknutím klávesy Enter v okně konzoly do Zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="ec0b7-131">Vytvoření zobrazení se silnými typy databáze</span><span class="sxs-lookup"><span data-stu-id="ec0b7-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="ec0b7-132">Je mnohem snazší začínat zobrazení se silnými typy vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="ec0b7-133">Důrazně zadáním <xref:System.Data.Linq.DataContext> objektu, není nutné volání <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="ec0b7-134">Můžete použít silného typu tabulky do vašich dotazů při použití silného typu <xref:System.Data.Linq.DataContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="ec0b7-135">V následujících krocích vytvoříte `Customers` jako silného typu tabulku, která se mapuje na tabulku zákazníků v databázi.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="ec0b7-136">Na typově DataContext objektu</span><span class="sxs-lookup"><span data-stu-id="ec0b7-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="ec0b7-137">Přidejte následující kód výše `Customer` deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  <span data-ttu-id="ec0b7-138">Změnit `Main` metodu použít silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  <span data-ttu-id="ec0b7-139">Stisknutím klávesy F5 ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="ec0b7-140">Okno výstup konzoly je:</span><span class="sxs-lookup"><span data-stu-id="ec0b7-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="ec0b7-141">Stisknutím klávesy Enter v okně konzoly do Zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ec0b7-142">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ec0b7-142">Next Steps</span></span>  
 <span data-ttu-id="ec0b7-143">Další návod ([návod: manipulace dat (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) ukazuje, jak pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="ec0b7-144">Tento návod nevyžaduje, abyste uložili dva postupy z této série, která jste už dokončili.</span><span class="sxs-lookup"><span data-stu-id="ec0b7-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0b7-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec0b7-145">See Also</span></span>  
 [<span data-ttu-id="ec0b7-146">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="ec0b7-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
