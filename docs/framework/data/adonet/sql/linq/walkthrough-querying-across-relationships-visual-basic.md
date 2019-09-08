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
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="10b31-102">Návod: Dotazování napříč relacemi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10b31-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="10b31-103">Tento návod ukazuje použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *přidružení* pro reprezentaci vztahů cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="10b31-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="10b31-104">Tento návod byl napsán pomocí Visual Basic nastavení vývoje.</span><span class="sxs-lookup"><span data-stu-id="10b31-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="10b31-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10b31-105">Prerequisites</span></span>  
 <span data-ttu-id="10b31-106">Musíte mít dokončený [Návod: Jednoduchý objektový model a dotaz (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="10b31-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="10b31-107">Tento návod sestaví sestavení, včetně přítomnosti souboru northwnd. mdf v c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="10b31-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="10b31-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="10b31-108">Overview</span></span>  
 <span data-ttu-id="10b31-109">Tento názorný postup se skládá ze tří hlavních úloh:</span><span class="sxs-lookup"><span data-stu-id="10b31-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="10b31-110">Přidání třídy entity, která představuje tabulku Orders v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="10b31-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="10b31-111">Doplnění poznámek ke `Customer` třídě za účelem vylepšení vztahů `Customer` mezi třídami a `Order` .</span><span class="sxs-lookup"><span data-stu-id="10b31-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="10b31-112">Vytvoření a spuštění dotazu pro otestování procesu získání `Order` informací `Customer` pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="10b31-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="10b31-113">Mapování vztahů mezi tabulkami</span><span class="sxs-lookup"><span data-stu-id="10b31-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="10b31-114">Po definici `Order` `Orders.Customer` třídy vytvořte definici třídy entity, která obsahuje následující kód, který označuje, že se týká cizího klíče `Customers.CustomerID`. `Customer`</span><span class="sxs-lookup"><span data-stu-id="10b31-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="10b31-115">Přidání třídy Order entity</span><span class="sxs-lookup"><span data-stu-id="10b31-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="10b31-116">Zadejte nebo vložte následující kód za `Customer` třídu:</span><span class="sxs-lookup"><span data-stu-id="10b31-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="10b31-117">Anotace třídy zákazníka</span><span class="sxs-lookup"><span data-stu-id="10b31-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="10b31-118">V tomto kroku označíte `Customer` třídu tak, aby označovala její vztah `Order` ke třídě.</span><span class="sxs-lookup"><span data-stu-id="10b31-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="10b31-119">(Toto přidání není bezpodmínečně nutné, protože definování vztahu v obou směrech stačí pro vytvoření odkazu.</span><span class="sxs-lookup"><span data-stu-id="10b31-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="10b31-120">Přidání této poznámky vám ale umožní snadno procházet objekty v obou směrech.)</span><span class="sxs-lookup"><span data-stu-id="10b31-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="10b31-121">Anotace třídy zákazníka</span><span class="sxs-lookup"><span data-stu-id="10b31-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="10b31-122">Do `Customer` třídy zadejte nebo vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="10b31-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="10b31-123">Vytvoření a spuštění dotazu ve vztahu zákazníka – objednávky</span><span class="sxs-lookup"><span data-stu-id="10b31-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="10b31-124">Nyní můžete přistupovat k `Order` objektům přímo `Customer` z objektů, nebo v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="10b31-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="10b31-125">Mezi zákazníky a objednávkami nemusíte explicitní *spojení* .</span><span class="sxs-lookup"><span data-stu-id="10b31-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="10b31-126">Přístup k objektům pořadí pomocí zákaznických objektů</span><span class="sxs-lookup"><span data-stu-id="10b31-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="10b31-127">`Sub Main` Upravte metodu zadáním nebo vložením následujícího kódu do metody:</span><span class="sxs-lookup"><span data-stu-id="10b31-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="10b31-128">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="10b31-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="10b31-129">V okně se zprávou se zobrazí dva názvy a v okně konzoly se zobrazí vygenerovaný kód SQL.</span><span class="sxs-lookup"><span data-stu-id="10b31-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="10b31-130">Zavřete okno se zprávou pro zastavení ladění.</span><span class="sxs-lookup"><span data-stu-id="10b31-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="10b31-131">Vytvoření zobrazení databáze silného typu</span><span class="sxs-lookup"><span data-stu-id="10b31-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="10b31-132">Je mnohem snazší začít s zobrazením silného typu vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="10b31-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="10b31-133">Silným zadáním <xref:System.Data.Linq.DataContext> objektu není nutné <xref:System.Data.Linq.DataContext.GetTable%2A>volat.</span><span class="sxs-lookup"><span data-stu-id="10b31-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="10b31-134">Při použití objektu silného typu <xref:System.Data.Linq.DataContext> můžete ve všech dotazech použít tabulky se silnými typy.</span><span class="sxs-lookup"><span data-stu-id="10b31-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="10b31-135">V následujících krocích vytvoříte `Customers` jako tabulku se silným typem, která bude mapována na tabulku Customers v databázi.</span><span class="sxs-lookup"><span data-stu-id="10b31-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="10b31-136">Silného typu objektu DataContext</span><span class="sxs-lookup"><span data-stu-id="10b31-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="10b31-137">Do deklarace `Customer` třídy přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="10b31-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="10b31-138">Upravte `Sub Main` pro použití silného typu <xref:System.Data.Linq.DataContext> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="10b31-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="10b31-139">Pro ladění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="10b31-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="10b31-140">Výstup okna konzoly:</span><span class="sxs-lookup"><span data-stu-id="10b31-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="10b31-141">V okně konzoly stiskněte klávesu ENTER, aby se aplikace zavřela.</span><span class="sxs-lookup"><span data-stu-id="10b31-141">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="10b31-142">V nabídce **soubor** klikněte na **Uložit vše** , pokud chcete tuto aplikaci uložit.</span><span class="sxs-lookup"><span data-stu-id="10b31-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="10b31-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="10b31-143">Next Steps</span></span>  
 <span data-ttu-id="10b31-144">V dalším návodu ([Návod: Manipulace s daty (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) ukazuje, jak manipulovat s daty.</span><span class="sxs-lookup"><span data-stu-id="10b31-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="10b31-145">Tento návod nevyžaduje, abyste uložili dva návody v této sérii, které jste již dokončili.</span><span class="sxs-lookup"><span data-stu-id="10b31-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b31-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10b31-146">See also</span></span>

- [<span data-ttu-id="10b31-147">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="10b31-147">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
