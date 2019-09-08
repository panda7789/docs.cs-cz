---
title: 'Návod: Dotazování napříč relacemi (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: ebf96bc575ef68e1190c5b9be7111902c0f69fef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780998"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="1674d-102">Návod: Dotazování napříč relacemi (C#)</span><span class="sxs-lookup"><span data-stu-id="1674d-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="1674d-103">Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* pro reprezentaci vztahů cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="1674d-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1674d-104">Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.</span><span class="sxs-lookup"><span data-stu-id="1674d-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1674d-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1674d-105">Prerequisites</span></span>  
 <span data-ttu-id="1674d-106">Musíte mít dokončený [Návod: Jednoduchý objektový model a dotaz (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="1674d-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="1674d-107">Tento návod sestaví sestavení, včetně přítomnosti souboru northwnd. mdf v c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="1674d-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1674d-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="1674d-108">Overview</span></span>  
 <span data-ttu-id="1674d-109">Tento názorný postup se skládá ze tří hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="1674d-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="1674d-110">Přidání třídy entity, která představuje tabulku Orders v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="1674d-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="1674d-111">Doplnění poznámek ke `Customer` třídě za účelem vylepšení vztahů `Customer` mezi třídami a `Order` .</span><span class="sxs-lookup"><span data-stu-id="1674d-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="1674d-112">Vytvoření a spuštění dotazu pro otestování získání `Order` informací `Customer` pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="1674d-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="1674d-113">Mapování vztahů mezi tabulkami</span><span class="sxs-lookup"><span data-stu-id="1674d-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="1674d-114">Po definici `Order` `Order.Customer` třídy vytvořte definici třídy entity, která obsahuje následující kód, který označuje, že se týká cizího klíče `Customer.CustomerID`. `Customer`</span><span class="sxs-lookup"><span data-stu-id="1674d-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="1674d-115">Přidání třídy Order entity</span><span class="sxs-lookup"><span data-stu-id="1674d-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="1674d-116">Zadejte nebo vložte následující kód za `Customer` třídu:</span><span class="sxs-lookup"><span data-stu-id="1674d-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="1674d-117">Anotace třídy zákazníka</span><span class="sxs-lookup"><span data-stu-id="1674d-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="1674d-118">V tomto kroku označíte `Customer` třídu tak, aby označovala její vztah `Order` ke třídě.</span><span class="sxs-lookup"><span data-stu-id="1674d-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="1674d-119">(Toto přidání není bezpodmínečně nutné, protože definování vztahu v obou směrech stačí pro vytvoření odkazu.</span><span class="sxs-lookup"><span data-stu-id="1674d-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="1674d-120">Přidání této poznámky vám ale umožní snadno procházet objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="1674d-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="1674d-121">Anotace třídy zákazníka</span><span class="sxs-lookup"><span data-stu-id="1674d-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="1674d-122">Do `Customer` třídy zadejte nebo vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1674d-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="1674d-123">Vytvoření a spuštění dotazu ve vztahu zákazníka – objednávky</span><span class="sxs-lookup"><span data-stu-id="1674d-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="1674d-124">Nyní můžete přistupovat k `Order` objektům přímo `Customer` z objektů, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1674d-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="1674d-125">Mezi zákazníky a objednávkami nemusíte explicitní *spojení* .</span><span class="sxs-lookup"><span data-stu-id="1674d-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="1674d-126">Přístup k objektům pořadí pomocí zákaznických objektů</span><span class="sxs-lookup"><span data-stu-id="1674d-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="1674d-127">`Main` Upravte metodu zadáním nebo vložením následujícího kódu do metody:</span><span class="sxs-lookup"><span data-stu-id="1674d-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="1674d-128">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="1674d-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1674d-129">Kód SQL můžete v okně konzoly eliminovat tím, že naplníte `db.Log = Console.Out;`komentáře.</span><span class="sxs-lookup"><span data-stu-id="1674d-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="1674d-130">V okně konzoly stiskněte klávesu ENTER a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="1674d-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="1674d-131">Vytvoření zobrazení databáze silného typu</span><span class="sxs-lookup"><span data-stu-id="1674d-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="1674d-132">Je mnohem snazší začít s zobrazením silného typu vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="1674d-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="1674d-133">Silným zadáním <xref:System.Data.Linq.DataContext> objektu není nutné <xref:System.Data.Linq.DataContext.GetTable%2A>volat.</span><span class="sxs-lookup"><span data-stu-id="1674d-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="1674d-134">Při použití objektu silného typu <xref:System.Data.Linq.DataContext> můžete ve všech dotazech použít tabulky se silnými typy.</span><span class="sxs-lookup"><span data-stu-id="1674d-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="1674d-135">V následujících krocích vytvoříte `Customers` jako tabulku se silným typem, která bude mapována na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="1674d-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="1674d-136">Silného typu objektu DataContext</span><span class="sxs-lookup"><span data-stu-id="1674d-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="1674d-137">Do deklarace `Customer` třídy přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="1674d-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="1674d-138">Upravte metodu pro použití silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem: `Main`</span><span class="sxs-lookup"><span data-stu-id="1674d-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="1674d-139">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="1674d-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1674d-140">Výstup okna konzoly:</span><span class="sxs-lookup"><span data-stu-id="1674d-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="1674d-141">V okně konzoly stiskněte klávesu ENTER a zastavte ladění.</span><span class="sxs-lookup"><span data-stu-id="1674d-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1674d-142">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1674d-142">Next Steps</span></span>  
 <span data-ttu-id="1674d-143">V dalším návodu ([Návod: Manipulace s daty (C#)](walkthrough-manipulating-data-csharp.md)) ukazuje, jak manipulovat s daty.</span><span class="sxs-lookup"><span data-stu-id="1674d-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="1674d-144">Tento návod nevyžaduje, abyste uložili dva návody v této sérii, které jste již dokončili.</span><span class="sxs-lookup"><span data-stu-id="1674d-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1674d-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1674d-145">See also</span></span>

- [<span data-ttu-id="1674d-146">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="1674d-146">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
