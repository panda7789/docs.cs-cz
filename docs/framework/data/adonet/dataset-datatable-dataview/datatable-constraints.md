---
title: Omezení datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 68b99e834428261d59c5fb27277b24eb0f6e77e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205051"
---
# <a name="datatable-constraints"></a><span data-ttu-id="3bf04-102">Omezení datových tabulek</span><span class="sxs-lookup"><span data-stu-id="3bf04-102">DataTable Constraints</span></span>
<span data-ttu-id="3bf04-103">Pomocí omezení můžete vynutit omezení pro data v <xref:System.Data.DataTable>nástroji, aby bylo možné zachovat integritu dat.</span><span class="sxs-lookup"><span data-stu-id="3bf04-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="3bf04-104">Omezení je automatické pravidlo, které se použije u sloupce nebo souvisejících sloupců, které určuje průběh akce, když je hodnota řádku nějakým způsobem změněna.</span><span class="sxs-lookup"><span data-stu-id="3bf04-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="3bf04-105">Omezení jsou vynutit, pokud `System.Data.DataSet.EnforceConstraints` vlastnost <xref:System.Data.DataSet> má **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="3bf04-106">Příklad kódu, který ukazuje, jak nastavit `EnforceConstraints` vlastnost, <xref:System.Data.DataSet.EnforceConstraints%2A> naleznete v referenčním tématu.</span><span class="sxs-lookup"><span data-stu-id="3bf04-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="3bf04-107">Existují dva druhy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>a.</span><span class="sxs-lookup"><span data-stu-id="3bf04-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="3bf04-108">Ve výchozím nastavení se obě omezení vytvoří automaticky, když vytvoříte relaci mezi dvěma nebo více tabulkami přidáním <xref:System.Data.DataRelation> k **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="3bf04-109">Toto chování však můžete zakázat zadáním **createConstraints** = **false** při vytváření relace.</span><span class="sxs-lookup"><span data-stu-id="3bf04-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="3bf04-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="3bf04-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="3bf04-111">**Objekt ForeignKeyConstraint** vynutila pravidla, jak se rozšíří aktualizace a odstraňování v souvisejících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="3bf04-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="3bf04-112">Například pokud je hodnota v řádku jedné tabulky aktualizována nebo odstraněna a tato hodnota se používá také v jedné nebo více souvisejících tabulkách, **Objekt ForeignKeyConstraint** určuje, co se stane v souvisejících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="3bf04-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="3bf04-113">Vlastnosti <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> a <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> **Objekt ForeignKeyConstraint** definují akci, která má být provedena, když se uživatel pokusí odstranit nebo aktualizovat řádek v tabulce v relaci.</span><span class="sxs-lookup"><span data-stu-id="3bf04-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="3bf04-114">Následující tabulka popisuje různá nastavení, která jsou k dispozici pro vlastnosti **DeleteRule** a **UpdateRule** **Objekt ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="3bf04-115">Nastavení pravidla</span><span class="sxs-lookup"><span data-stu-id="3bf04-115">Rule setting</span></span>|<span data-ttu-id="3bf04-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3bf04-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3bf04-117">**Nášejí**</span><span class="sxs-lookup"><span data-stu-id="3bf04-117">**Cascade**</span></span>|<span data-ttu-id="3bf04-118">Odstraní nebo aktualizuje související řádky.</span><span class="sxs-lookup"><span data-stu-id="3bf04-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="3bf04-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="3bf04-119">**SetNull**</span></span>|<span data-ttu-id="3bf04-120">Nastavte hodnoty v souvisejících řádcích na **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="3bf04-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="3bf04-121">**SetDefault**</span></span>|<span data-ttu-id="3bf04-122">Nastaví hodnoty v souvisejících řádcích na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3bf04-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="3bf04-123">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="3bf04-123">**None**</span></span>|<span data-ttu-id="3bf04-124">Neprovádět žádnou akci na souvisejících řádcích.</span><span class="sxs-lookup"><span data-stu-id="3bf04-124">Take no action on related rows.</span></span> <span data-ttu-id="3bf04-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3bf04-125">This is the default.</span></span>|  
  
 <span data-ttu-id="3bf04-126">**Objekt ForeignKeyConstraint** může omezit a rozšířit změny v souvisejících sloupcích.</span><span class="sxs-lookup"><span data-stu-id="3bf04-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="3bf04-127">V závislosti na vlastnostech nastavených pro **Objekt ForeignKeyConstraint** sloupce platí, že pokud je vlastnost **EnforceConstraints** pro datovou **sadu** **true**, provádění určitých operací na nadřazeném řádku způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="3bf04-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="3bf04-128">Například pokud vlastnost **DeleteRule** třídy **Objekt ForeignKeyConstraint** je **none**, nadřazený řádek nelze odstranit, pokud má podřízené řádky.</span><span class="sxs-lookup"><span data-stu-id="3bf04-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="3bf04-129">Omezení cizího klíče můžete vytvořit mezi jednotlivými sloupci nebo mezi polem sloupců pomocí konstruktoru **Objekt ForeignKeyConstraint** .</span><span class="sxs-lookup"><span data-stu-id="3bf04-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="3bf04-130">Výsledný objekt **Objekt ForeignKeyConstraint** předejte metodě **Add** vlastnosti **omezení** tabulky, což je objekt **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3bf04-131">Můžete také předat argumenty konstruktoru do několika přetížení metody **Add** třídy **ConstraintCollection** a vytvořit tak **Objekt ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="3bf04-132">Při vytváření **Objekt ForeignKeyConstraint**můžete do konstruktoru předat hodnoty **DeleteRule** a **UpdateRule** jako argumenty, nebo je můžete nastavit jako vlastnosti jako v následujícím příkladu (kde hodnota **DeleteRule** je nastavená na  **Žádný**).</span><span class="sxs-lookup"><span data-stu-id="3bf04-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="3bf04-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="3bf04-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="3bf04-134">Změny v řádcích lze přijmout pomocí metody **AcceptChanges** nebo zrušit pomocí metody **RejectChanges** **objektu DataSet**, **DataTable**nebo **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="3bf04-135">Pokud **datová sada** obsahuje **ForeignKeyConstraints**, volání metod **AcceptChanges** nebo **RejectChanges** vynutila **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="3bf04-136">Vlastnost **AcceptRejectRule** třídy **Objekt ForeignKeyConstraint** určuje, která akce bude provedena na podřízených řádcích v případě, že je v nadřazeném řádku volána metoda **AcceptChanges** nebo **RejectChanges** .</span><span class="sxs-lookup"><span data-stu-id="3bf04-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="3bf04-137">V následující tabulce jsou uvedena dostupná nastavení pro **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="3bf04-138">Nastavení pravidla</span><span class="sxs-lookup"><span data-stu-id="3bf04-138">Rule setting</span></span>|<span data-ttu-id="3bf04-139">Popis</span><span class="sxs-lookup"><span data-stu-id="3bf04-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3bf04-140">**Nášejí**</span><span class="sxs-lookup"><span data-stu-id="3bf04-140">**Cascade**</span></span>|<span data-ttu-id="3bf04-141">Přijměte nebo odmítněte změny v podřízených řádcích.</span><span class="sxs-lookup"><span data-stu-id="3bf04-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="3bf04-142">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="3bf04-142">**None**</span></span>|<span data-ttu-id="3bf04-143">Neprovádět žádnou akci s podřízenými řádky.</span><span class="sxs-lookup"><span data-stu-id="3bf04-143">Take no action on child rows.</span></span> <span data-ttu-id="3bf04-144">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3bf04-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="3bf04-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf04-145">Example</span></span>  
 <span data-ttu-id="3bf04-146">Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví několik vlastností, <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>včetně <xref:System.Data.ConstraintCollection> a, a přidá <xref:System.Data.DataTable> je do objektu.</span><span class="sxs-lookup"><span data-stu-id="3bf04-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="3bf04-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="3bf04-147">UniqueConstraint</span></span>  
 <span data-ttu-id="3bf04-148">Objekt **UniqueConstraint** , který lze přiřadit buď k jednomu sloupci, nebo k poli sloupců v **objektu DataTable**, zajišťuje, aby všechna data v zadaném sloupci nebo sloupcích byla na řádku jedinečná.</span><span class="sxs-lookup"><span data-stu-id="3bf04-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="3bf04-149">Můžete vytvořit jedinečné omezení pro sloupec nebo pole sloupců pomocí konstruktoru **UniqueConstraint** .</span><span class="sxs-lookup"><span data-stu-id="3bf04-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="3bf04-150">Výsledný objekt **UniqueConstraint** předejte metodě **Add** vlastnosti **omezení** tabulky, což je objekt **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="3bf04-151">Můžete také předat argumenty konstruktoru do několika přetížení metody **Add** třídy **ConstraintCollection** a vytvořit tak **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="3bf04-152">Při vytváření **UniqueConstraint** pro sloupec nebo sloupce můžete volitelně zadat, zda se jedná o primární klíč sloupce nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="3bf04-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="3bf04-153">Můžete také vytvořit jedinečné omezení pro sloupec nastavením vlastnosti **Unique** sloupce na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="3bf04-154">Případně nastavení **jedinečné** vlastnosti jednoho sloupce na **hodnotu false** odebere všechna jedinečná omezení, která mohou existovat.</span><span class="sxs-lookup"><span data-stu-id="3bf04-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="3bf04-155">Definování sloupce nebo sloupců jako primárního klíče pro tabulku vytvoří pro zadaný sloupec nebo sloupce automaticky jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="3bf04-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="3bf04-156">Odeberete-li sloupec z vlastnosti **PrimaryKey** objektu **DataTable**, dojde k odebrání **UniqueConstraint** .</span><span class="sxs-lookup"><span data-stu-id="3bf04-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="3bf04-157">Následující příklad vytvoří **UniqueConstraint** pro dva sloupce **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3bf04-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bf04-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bf04-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="3bf04-159">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="3bf04-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="3bf04-160">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="3bf04-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3bf04-161">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="3bf04-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
