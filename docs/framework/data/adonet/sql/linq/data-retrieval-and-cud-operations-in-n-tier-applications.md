---
title: Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: d55c85ae0af567c5af0fd421b612809eaf5bb789
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318426"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="a926b-102">Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="a926b-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="a926b-103">Při serializaci objektů entity jako je například Zákazníci a objednávky na klienta přes síť, tyto entity jsou odpojeny od jejich místní data.</span><span class="sxs-lookup"><span data-stu-id="a926b-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="a926b-104">Datový kontext již sleduje jejich změny nebo jejich přidružení s jinými objekty.</span><span class="sxs-lookup"><span data-stu-id="a926b-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="a926b-105">To není problém, tak dlouho, dokud klienti jsou jen ke čtení data.</span><span class="sxs-lookup"><span data-stu-id="a926b-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="a926b-106">Také je poměrně jednoduchá, aby mohli klienti k přidání nových řádků do databáze.</span><span class="sxs-lookup"><span data-stu-id="a926b-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="a926b-107">Nicméně pokud vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, pak je nutné připojit entity k nový kontext dat před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a926b-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a926b-108">Navíc pokud použijete kontrolu optimistického řízení souběžnosti s původní hodnoty, pak musíte také poskytnout databázi původní entitu a entitu jako upravená.</span><span class="sxs-lookup"><span data-stu-id="a926b-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="a926b-109">`Attach` Metody jsou k dispozici umožňuje entity přejde do nového kontextu dat byla odpojena.</span><span class="sxs-lookup"><span data-stu-id="a926b-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="a926b-110">I když je serializována objekty proxy místo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entity, stále musíte vytvořit entitu na vrstvy přístupu k datům (DAL) a připojit ho k nové <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.</span><span class="sxs-lookup"><span data-stu-id="a926b-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a926b-111">je zcela je mi to o způsob, jakým serializují entity.</span><span class="sxs-lookup"><span data-stu-id="a926b-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="a926b-112">Další informace o tom, jak používat [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] a SQLMetal nástroje pro generování třídy, které jsou serializovatelné s použitím Windows Communication Foundation (WCF), najdete v článku [jak: Nastavení entit jako serializovatelných](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a926b-113">Volat pouze `Attach` metod v nové nebo deserializovat entit.</span><span class="sxs-lookup"><span data-stu-id="a926b-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="a926b-114">Jediným způsobem, který se má odpojit z jeho původního kontextu dat entity je pro ni mají být serializován.</span><span class="sxs-lookup"><span data-stu-id="a926b-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="a926b-115">Pokud dané entity má stále odložení zavaděče z jeho předchozí kontext dat, a pokusíte připojit entitu undetached nový kontext dat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a926b-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="a926b-116">Entita s odložené zavaděče ze dvou různých datových kontextech může způsobit nežádoucí výsledky, když provádíte insert, update a operace odstranění na dané entitě.</span><span class="sxs-lookup"><span data-stu-id="a926b-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="a926b-117">Další informace o odložených zavaděče, naleznete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="a926b-118">Načítání dat</span><span class="sxs-lookup"><span data-stu-id="a926b-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="a926b-119">Volání metody klienta</span><span class="sxs-lookup"><span data-stu-id="a926b-119">Client Method Call</span></span>  
 <span data-ttu-id="a926b-120">Následující příklady ukazují volání metody ukázka vrstvy Dal z klienta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a926b-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="a926b-121">V tomto příkladu je DAL implementován jako knihovna služby Windows:</span><span class="sxs-lookup"><span data-stu-id="a926b-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="a926b-122">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="a926b-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="a926b-123">Následující příklad ukazuje implementaci metody rozhraní ve střední vrstvě.</span><span class="sxs-lookup"><span data-stu-id="a926b-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="a926b-124">Tady jsou dva hlavní body k mějte na paměti:</span><span class="sxs-lookup"><span data-stu-id="a926b-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="a926b-125"><xref:System.Data.Linq.DataContext> Je deklarována v rozsahu metody.</span><span class="sxs-lookup"><span data-stu-id="a926b-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="a926b-126">Metoda vrátí <xref:System.Collections.IEnumerable> kolekce skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="a926b-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="a926b-127">Serializátor spustí dotaz pro výsledky odeslat zpět do klienta a prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="a926b-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="a926b-128">Pro přístup k místně ve střední vrstvě. výsledky dotazu, můžete vynutit spuštění voláním `ToList` nebo `ToArray` v proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="a926b-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="a926b-129">Potom tento seznam nebo pole jako `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="a926b-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 <span data-ttu-id="a926b-130">Instance kontextu dat má životnost jeden "jednotku práce."</span><span class="sxs-lookup"><span data-stu-id="a926b-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="a926b-131">V prostředí s minimálním počtem vazeb určitou jednotku práce je obvykle malý, případně jeden optimistické transakce, včetně jedním voláním `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="a926b-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="a926b-132">Proto kontext dat je vytvořen a uvolněn v oboru metody.</span><span class="sxs-lookup"><span data-stu-id="a926b-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="a926b-133">Pokud jednotku práce zahrnuje volání obchodní logiku pravidla a potom obvykle budete chtít zachovat `DataContext` instance pro danou celou operaci.</span><span class="sxs-lookup"><span data-stu-id="a926b-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="a926b-134">V každém případě `DataContext` instance nemají být zachováno po dlouhou dobu mezi libovolného počtu transakcí.</span><span class="sxs-lookup"><span data-stu-id="a926b-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="a926b-135">Tato metoda vrátí objekty produktu, ale ne na kolekci z Order_Detail objekty, které jsou spojeny s každého produktu.</span><span class="sxs-lookup"><span data-stu-id="a926b-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="a926b-136">Použití <xref:System.Data.Linq.DataLoadOptions> objektu, chcete-li změnit toto výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="a926b-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="a926b-137">Další informace najdete v tématu [jak: Ovládací prvek, kolik souvisejících dat](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="a926b-138">Vkládání dat</span><span class="sxs-lookup"><span data-stu-id="a926b-138">Inserting Data</span></span>  
 <span data-ttu-id="a926b-139">Vložit nový objekt, prezentační vrstvy jen volá metodu relevantní na střední vrstvu rozhraní a předá nový objekt pro vložení.</span><span class="sxs-lookup"><span data-stu-id="a926b-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="a926b-140">V některých případech může být efektivnější pro klienta a předejte pouze některé hodnoty mají střední vrstva, sestavit úplný objekt.</span><span class="sxs-lookup"><span data-stu-id="a926b-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="a926b-141">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="a926b-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="a926b-142">Ve střední vrstvě nový <xref:System.Data.Linq.DataContext> je vytvořen, objekt je připojen ke <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metoda a objekt při vložení <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="a926b-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="a926b-143">Stejně jako u jakékoli jiné scénář webových služeb mohou zpracovat výjimky, zpětná volání a chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="a926b-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="a926b-144">Odstranění dat</span><span class="sxs-lookup"><span data-stu-id="a926b-144">Deleting Data</span></span>  
 <span data-ttu-id="a926b-145">Z databáze odstranit existující objekt, prezentační vrstvy volá metodu relevantní na střední vrstvě rozhraní a předá v jeho kopii, která obsahuje původní hodnoty objekt, který chcete odstranit.</span><span class="sxs-lookup"><span data-stu-id="a926b-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="a926b-146">Odstranit operace zahrnují kontroly optimistického řízení souběžnosti a objekt, který chcete odstranit, musí být nejprve připojený k nový datový kontext.</span><span class="sxs-lookup"><span data-stu-id="a926b-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="a926b-147">V tomto příkladu `Boolean` parametr je nastaven na `false` k označení, že objekt nemá časové razítko (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="a926b-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="a926b-148">Pokud vaše databázové tabulky generovat časová razítka pro každý záznam, kontrolách souběžnosti jsou mnohem jednodušší, zejména u klienta.</span><span class="sxs-lookup"><span data-stu-id="a926b-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="a926b-149">Stačí předat do původního nebo upravené objektu a nastavit `Boolean` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="a926b-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="a926b-150">V každém případě ve střední vrstvě je obvykle potřeba zachytit <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="a926b-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="a926b-151">Další informace o tom, jak se řeší konflikty optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="a926b-152">Při odstraňování entity, které mají omezení cizího klíče v přidružené tabulky, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="a926b-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="a926b-153">Aktualizace dat</span><span class="sxs-lookup"><span data-stu-id="a926b-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a926b-154">v těchto scénářích zahrnující optimistického řízení souběžnosti podporuje aktualizace:</span><span class="sxs-lookup"><span data-stu-id="a926b-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="a926b-155">Optimistického řízení souběžnosti na základě časových razítek nebo RowVersion čísla.</span><span class="sxs-lookup"><span data-stu-id="a926b-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="a926b-156">Optimistického řízení souběžnosti založené na původní hodnoty podmnožinu vlastností entity.</span><span class="sxs-lookup"><span data-stu-id="a926b-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="a926b-157">Optimistického řízení souběžnosti založené na dokončení původní a změny entity.</span><span class="sxs-lookup"><span data-stu-id="a926b-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="a926b-158">Aktualizace nebo odstranění můžete provést také s entitou společně s jeho vztahy, například zákazník a kolekce jejích přidružených objektů pořadí.</span><span class="sxs-lookup"><span data-stu-id="a926b-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="a926b-159">Pokud provedete změny v klientském počítači do grafu objekty entity a jejich podřízené (`EntitySet`) kolekce a kontroly optimistického řízení souběžnosti vyžadují původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a <xref:System.Data.Linq.EntitySet%601> objekt.</span><span class="sxs-lookup"><span data-stu-id="a926b-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="a926b-160">Pokud chcete povolit klientským počítačům provádět sadu související aktualizace, odstranění a vložení v rámci jednoho volání metody, je nutné zadat klienta způsob, jak určit, jaký typ operace se má provést u každé entity.</span><span class="sxs-lookup"><span data-stu-id="a926b-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="a926b-161">Ve střední vrstvě, pak musíte volat odpovídající <xref:System.Data.Linq.ITable.Attach%2A> metodu a poté <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, pro vložení) pro každou entitu před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="a926b-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="a926b-162">Nelze načíst data z databáze jako způsob, jak získat původní hodnoty, než se pokusíte aktualizace.</span><span class="sxs-lookup"><span data-stu-id="a926b-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="a926b-163">Další informace o optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="a926b-164">Podrobné informace o řešení optimistického řízení souběžnosti změna je v konfliktu, najdete v článku [jak: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="a926b-165">Následující příklady ukazují jednotlivých scénářů:</span><span class="sxs-lookup"><span data-stu-id="a926b-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="a926b-166">Optimistického řízení souběžnosti ovládacím prvkem časová razítka</span><span class="sxs-lookup"><span data-stu-id="a926b-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="a926b-167">S podmnožinou původní hodnoty</span><span class="sxs-lookup"><span data-stu-id="a926b-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="a926b-168">V takovém případě vrátí klientovi kompletní serializovaný objekt spolu s hodnotami, které má být upraven.</span><span class="sxs-lookup"><span data-stu-id="a926b-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="a926b-169">S kompletní entity</span><span class="sxs-lookup"><span data-stu-id="a926b-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 <span data-ttu-id="a926b-170">Chcete-li aktualizovat kolekci, zavolejte <xref:System.Data.Linq.ITable.AttachAll%2A> místo `Attach`.</span><span class="sxs-lookup"><span data-stu-id="a926b-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="a926b-171">Členové očekávanou entitu</span><span class="sxs-lookup"><span data-stu-id="a926b-171">Expected Entity Members</span></span>  
 <span data-ttu-id="a926b-172">Jak bylo uvedeno dříve, jsou jen některé členy objektu entity musí být nastavena dříve než zavoláte `Attach` metody.</span><span class="sxs-lookup"><span data-stu-id="a926b-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="a926b-173">Členové entit, které je potřeba nastavit musí splňovat následující kritéria:</span><span class="sxs-lookup"><span data-stu-id="a926b-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="a926b-174">Být součástí identity subjektu.</span><span class="sxs-lookup"><span data-stu-id="a926b-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="a926b-175">Očekávat, že se změnil.</span><span class="sxs-lookup"><span data-stu-id="a926b-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="a926b-176">Časové razítko nebo má jeho <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atribut nastaven na něco kromě `Never`.</span><span class="sxs-lookup"><span data-stu-id="a926b-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="a926b-177">Pokud tabulka používá číslo verze nebo časové razítko pro kontrolu optimistického řízení souběžnosti, musíte nastavit tyto členy před voláním <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="a926b-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="a926b-178">Člen je vyhrazený pro optimistického řízení souběžnosti při kontrole <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je nastavena na hodnotu true u tohoto sloupce atributu.</span><span class="sxs-lookup"><span data-stu-id="a926b-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="a926b-179">Všechny požadované aktualizace budou odeslány pouze v případě, že hodnoty, číslo nebo časového razítka verze jsou stejné pro databázi.</span><span class="sxs-lookup"><span data-stu-id="a926b-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="a926b-180">Člen se používá také v kontroly optimistického řízení souběžnosti, tak dlouho, dokud člen nemá <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nastavena na `Never`.</span><span class="sxs-lookup"><span data-stu-id="a926b-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="a926b-181">Výchozí hodnota je `Always` Pokud není zadána žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a926b-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="a926b-182">V případě potřeby některou z těchto členů chybí, <xref:System.Data.Linq.ChangeConflictException> dojde během <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změněn").</span><span class="sxs-lookup"><span data-stu-id="a926b-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="a926b-183">Stav</span><span class="sxs-lookup"><span data-stu-id="a926b-183">State</span></span>  
 <span data-ttu-id="a926b-184">Po entity je přiřazena objektu <xref:System.Data.Linq.DataContext> instance, objekt je považován za v `PossiblyModified` stavu.</span><span class="sxs-lookup"><span data-stu-id="a926b-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="a926b-185">Existují tři způsoby, jak vynutit připojeného objektu považovat `Modified`.</span><span class="sxs-lookup"><span data-stu-id="a926b-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="a926b-186">Připojit jako nezměněný a přímo upravit pole.</span><span class="sxs-lookup"><span data-stu-id="a926b-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="a926b-187">Připojí se <xref:System.Data.Linq.Table%601.Attach%2A> přetížení přebírající aktuální a původní objekt instance.</span><span class="sxs-lookup"><span data-stu-id="a926b-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="a926b-188">To poskytuje modul sledování změny pomocí staré a nové hodnoty tak, že bude automaticky znát, pole, která jste změnili.</span><span class="sxs-lookup"><span data-stu-id="a926b-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="a926b-189">Připojí se <xref:System.Data.Linq.Table%601.Attach%2A> přetížení přebírající druhý parametr logické hodnoty (nastavenou na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="a926b-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="a926b-190">Se tak dozví, modul sledování změny, které byste měli zvážit objektu změnit, aniž by bylo nutné zadat všechny původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a926b-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="a926b-191">V takovém případě musí mít objekt pole verze/časové razítko.</span><span class="sxs-lookup"><span data-stu-id="a926b-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="a926b-192">Další informace najdete v tématu [stavy objektů a sledování změn](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="a926b-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="a926b-193">Dojde-li objekt entity již v mezipaměti ID se stejnou identitou jako objekt připojovaný, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a926b-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="a926b-194">Jestliže se pokusíte připojit s `IEnumerable` sadu objektů, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána, když je k dispozici již existujícího klíče.</span><span class="sxs-lookup"><span data-stu-id="a926b-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="a926b-195">Zbývající objekty nejsou připojeny.</span><span class="sxs-lookup"><span data-stu-id="a926b-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a926b-196">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a926b-196">See also</span></span>

- [<span data-ttu-id="a926b-197">N-vrstvé a vzdálené aplikace s LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a926b-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="a926b-198">Základní informace</span><span class="sxs-lookup"><span data-stu-id="a926b-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
