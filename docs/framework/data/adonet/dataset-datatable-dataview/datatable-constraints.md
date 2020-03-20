---
title: Omezení datových tabulek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151283"
---
# <a name="datatable-constraints"></a><span data-ttu-id="f6ae4-102">Omezení datových tabulek</span><span class="sxs-lookup"><span data-stu-id="f6ae4-102">DataTable Constraints</span></span>
<span data-ttu-id="f6ae4-103">Omezení můžete použít k vynucení omezení <xref:System.Data.DataTable>dat v , za účelem zachování integrity dat.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="f6ae4-104">Omezení je automatické pravidlo použité na sloupec nebo související sloupce, které určuje průběh akce při změně hodnoty řádku.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="f6ae4-105">Omezení jsou vynucena, `System.Data.DataSet.EnforceConstraints` pokud <xref:System.Data.DataSet> je **vlastnost true**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="f6ae4-106">Příklad kódu, který ukazuje, `EnforceConstraints` jak nastavit <xref:System.Data.DataSet.EnforceConstraints%2A> vlastnost, naleznete v tématu odkazu.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="f6ae4-107">Existují dva druhy omezení v ADO.NET: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>a .</span><span class="sxs-lookup"><span data-stu-id="f6ae4-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="f6ae4-108">Ve výchozím nastavení jsou obě omezení vytvořena automaticky při vytváření relace <xref:System.Data.DataRelation> mezi dvěma nebo více tabulkami přidáním a do **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="f6ae4-109">Toto chování však můžete zakázat zadáním **funkce createConstraints** = **false** při vytváření vztahu.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="f6ae4-110">Foreignkeyconstraint</span><span class="sxs-lookup"><span data-stu-id="f6ae4-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="f6ae4-111">A **ForeignKeyConstraint** vynucuje pravidla o tom, jak jsou rozšířeny aktualizace a odstranění do souvisejících tabulek.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="f6ae4-112">Například pokud hodnota v řádku jedné tabulky je aktualizován nebo odstraněn a že stejná hodnota se používá také v jedné nebo více souvisejících tabulek, **ForeignKeyConstraint** určuje, co se stane v souvisejících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="f6ae4-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Vlastnosti <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> a **ForeignKeyConstraint** definovat akci, která má být provedena, když se uživatel pokusí odstranit nebo aktualizovat řádek v související tabulce.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="f6ae4-114">Následující tabulka popisuje různá nastavení, která jsou k dispozici pro vlastnosti **DeleteRule** a **UpdateRule** **služby ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="f6ae4-115">Nastavení pravidla</span><span class="sxs-lookup"><span data-stu-id="f6ae4-115">Rule setting</span></span>|<span data-ttu-id="f6ae4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ae4-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="f6ae4-117">**Kaskády**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-117">**Cascade**</span></span>|<span data-ttu-id="f6ae4-118">Odstranit nebo aktualizovat související řádky.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="f6ae4-119">**Nastavit hodnotu Null**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-119">**SetNull**</span></span>|<span data-ttu-id="f6ae4-120">Nastavte hodnoty v souvisejících řádcích na **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="f6ae4-121">**Nastavit výchozí nastavení**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-121">**SetDefault**</span></span>|<span data-ttu-id="f6ae4-122">Nastavte hodnoty v souvisejících řádcích na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="f6ae4-123">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-123">**None**</span></span>|<span data-ttu-id="f6ae4-124">U souvisejících řádků neprovádějte žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-124">Take no action on related rows.</span></span> <span data-ttu-id="f6ae4-125">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-125">This is the default.</span></span>|  
  
 <span data-ttu-id="f6ae4-126">A **ForeignKeyConstraint** můžete omezit, stejně jako šířit, změny související chvatcích.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="f6ae4-127">V závislosti na vlastnostech nastavených pro **ForeignKeyConstraint** sloupce, pokud **EnforceConstraints** vlastnost **DataSet** je **true**, provádění určitých operací na nadřazený řádek bude mít za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="f6ae4-128">Například pokud **DeleteRule** vlastnost **ForeignKeyConstraint** je **None**, nadřazený řádek nelze odstranit, pokud má všechny podřízené řádky.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="f6ae4-129">Můžete vytvořit omezení cizího klíče mezi jednotlivými sloupci nebo mezi pole sloupců pomocí konstruktoru **ForeignKeyConstraint.**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="f6ae4-130">Předajte výsledný objekt **ForeignKeyConstraint** metodě **Add** vlastnosti **Constraints** tabulky, která je **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="f6ae4-131">Můžete také předat argumenty konstruktoru na několik přetížení **Add** metoda **ConstraintCollection** vytvořit **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="f6ae4-132">Při vytváření **ForeignKeyConstraint**, můžete předat **DeleteRule** a **UpdateRule** hodnoty konstruktoru jako argumenty, nebo můžete nastavit jako vlastnosti jako v následujícím příkladu (kde **DeleteRule** hodnota je **nastavena**na none ).</span><span class="sxs-lookup"><span data-stu-id="f6ae4-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
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
  
### <a name="acceptrejectrule"></a><span data-ttu-id="f6ae4-133">PřijmoutOdmítnoucí pravidlo</span><span class="sxs-lookup"><span data-stu-id="f6ae4-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="f6ae4-134">Změny řádků lze přijmout pomocí metody **AcceptChanges** nebo zrušit pomocí metody **RejectChanges** **dataset**, **DataTable**nebo **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="f6ae4-135">Pokud **DataSet** obsahuje **ForeignKeyConstraints**, vyvolání **AcceptChanges** nebo **RejectChanges** metody vynucuje **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="f6ae4-136">**AcceptRejectRule** vlastnost **ForeignKeyConstraint** určuje, která akce bude provedena na podřízené řádky při **AcceptChanges** nebo **RejectChanges** je volána na nadřazený řádek.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="f6ae4-137">V následující tabulce jsou uvedena dostupná nastavení pravidla **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="f6ae4-138">Nastavení pravidla</span><span class="sxs-lookup"><span data-stu-id="f6ae4-138">Rule setting</span></span>|<span data-ttu-id="f6ae4-139">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ae4-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="f6ae4-140">**Kaskády**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-140">**Cascade**</span></span>|<span data-ttu-id="f6ae4-141">Přijměte nebo zamítněte změny podřízených řádků.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="f6ae4-142">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-142">**None**</span></span>|<span data-ttu-id="f6ae4-143">Neprovádějte žádnou akci na podřízených řádcích.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-143">Take no action on child rows.</span></span> <span data-ttu-id="f6ae4-144">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="f6ae4-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ae4-145">Example</span></span>  
 <span data-ttu-id="f6ae4-146">Následující příklad vytvoří <xref:System.Data.ForeignKeyConstraint>, nastaví několik jeho <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>vlastností, včetně <xref:System.Data.ConstraintCollection> , <xref:System.Data.DataTable> a přidá ji k objektu.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="f6ae4-147">Uniqueconstraint</span><span class="sxs-lookup"><span data-stu-id="f6ae4-147">UniqueConstraint</span></span>  
 <span data-ttu-id="f6ae4-148">Objekt **UniqueConstraint,** který lze přiřadit k jednomu sloupci nebo k poli sloupců v **tabulce DataTable**, zajišťuje, že všechna data v zadaném sloupci nebo sloupcích jsou jedinečná pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="f6ae4-149">Pomocí konstruktoru **UniqueConstraint** můžete vytvořit jedinečné omezení pro sloupec nebo pole sloupců.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="f6ae4-150">Předá výsledný **Objekt UniqueConstraint** metodě **Add** **vlastnosti Constraints** tabulky, která je **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="f6ae4-151">Můžete také předat argumenty konstruktoru na několik přetížení **Add** metoda **ConstraintCollection** vytvořit **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="f6ae4-152">Při vytváření **jedinečného omezení** pro sloupec nebo sloupce můžete volitelně určit, zda jsou sloupce nebo sloupce primárním klíčem.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="f6ae4-153">Můžete také vytvořit jedinečné omezení pro sloupec nastavením **jedinečné** vlastnosti sloupce na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="f6ae4-154">Případně nastavení **Unique** vlastnost jednoho sloupce **false** odebere všechny jedinečné omezení, které může existovat.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="f6ae4-155">Definovánísloupce nebo sloupců jako primárního klíče pro tabulku automaticky vytvoří jedinečné omezení pro zadaný sloupec nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="f6ae4-156">Pokud odeberete sloupec z **Vlastnosti PrimaryKey** **datatable**, **UniqueConstraint** je odebrán.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="f6ae4-157">Následující příklad vytvoří **UniqueConstraint** pro dva sloupce **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="f6ae4-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6ae4-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ae4-158">See also</span></span>

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [<span data-ttu-id="f6ae4-159">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="f6ae4-159">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="f6ae4-160">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="f6ae4-160">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="f6ae4-161">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f6ae4-161">ADO.NET Overview</span></span>](../ado-net-overview.md)
