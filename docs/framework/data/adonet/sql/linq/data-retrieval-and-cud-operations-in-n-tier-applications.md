---
title: Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 5ab829993b8f8faa6dcb91d3f23e8442b8aa95bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148410"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="c89f8-102">Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="c89f8-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="c89f8-103">Při serializaci objektů entity, jako jsou zákazníci nebo objednávky klientovi v síti, jsou tyto entity odpojeny od jejich datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="c89f8-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="c89f8-104">Kontext dat již nesleduje jejich změny nebo jejich přidružení k jiným objektům.</span><span class="sxs-lookup"><span data-stu-id="c89f8-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="c89f8-105">To není problém, pokud klienti pouze čtou data.</span><span class="sxs-lookup"><span data-stu-id="c89f8-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="c89f8-106">Je také poměrně jednoduché povolit klientům přidávat nové řádky do databáze.</span><span class="sxs-lookup"><span data-stu-id="c89f8-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="c89f8-107">Pokud však vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, je nutné <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>připojit entity k novému kontextu dat před voláním .</span><span class="sxs-lookup"><span data-stu-id="c89f8-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c89f8-108">Kromě toho pokud používáte optimistické souběžnosti kontrolu s původními hodnotami, pak budete také potřebovat způsob, jak poskytnout databázi původní entity a entity, jak změněn.</span><span class="sxs-lookup"><span data-stu-id="c89f8-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="c89f8-109">Metody `Attach` jsou k dispozici k dispozici, aby vám umožní umístit entity do nového kontextu dat poté, co byly odpojeny.</span><span class="sxs-lookup"><span data-stu-id="c89f8-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="c89f8-110">I v případě, že serializujete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proxy objekty místo entit, stále musíte vytvořit entitu ve <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>vrstvě přístupu k datům (DAL) a připojit ji k nové aplikaci , aby bylo možné odeslat data do databáze.</span><span class="sxs-lookup"><span data-stu-id="c89f8-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c89f8-111">je zcela lhostejný o tom, jak jsou entity serializovány.</span><span class="sxs-lookup"><span data-stu-id="c89f8-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="c89f8-112">Další informace o použití nástrojů Object Relational Designer a SQLMetal ke generování tříd, které lze serializovat pomocí služby Windows Communication Foundation (WCF), naleznete v [tématu How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c89f8-113">Volání metod `Attach` pouze u nových nebo rekonstruované entity.</span><span class="sxs-lookup"><span data-stu-id="c89f8-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="c89f8-114">Jediný způsob, jak může být entita odpojena od původního datového kontextu, je serializovat ji.</span><span class="sxs-lookup"><span data-stu-id="c89f8-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="c89f8-115">Pokud se pokusíte připojit neodpojenou entitu k novému kontextu dat a tato [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entita má stále odložené zavaděče z předchozího kontextu dat, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="c89f8-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="c89f8-116">Entita s odloženými zavaděči ze dvou různých datových kontextů může způsobit nežádoucí výsledky při provádění operací vložení, aktualizace a odstranění této entity.</span><span class="sxs-lookup"><span data-stu-id="c89f8-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="c89f8-117">Další informace o odložené zavaděče, naleznete v [tématu Odloženo versus okamžité načítání](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="c89f8-118">Načítání dat</span><span class="sxs-lookup"><span data-stu-id="c89f8-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="c89f8-119">Volání metody klienta</span><span class="sxs-lookup"><span data-stu-id="c89f8-119">Client Method Call</span></span>  
 <span data-ttu-id="c89f8-120">Následující příklady ukazují ukázkové volání metody DAL z klienta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c89f8-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="c89f8-121">V tomto příkladu je DAL implementován jako knihovna služeb systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c89f8-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="c89f8-122">Implementace střední úrovně</span><span class="sxs-lookup"><span data-stu-id="c89f8-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="c89f8-123">Následující příklad ukazuje implementaci metody rozhraní na střední vrstvě.</span><span class="sxs-lookup"><span data-stu-id="c89f8-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="c89f8-124">Níže jsou uvedeny dva hlavní body, které je třeba poznamenat:</span><span class="sxs-lookup"><span data-stu-id="c89f8-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="c89f8-125">Je <xref:System.Data.Linq.DataContext> deklarována v oboru metody.</span><span class="sxs-lookup"><span data-stu-id="c89f8-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="c89f8-126">Metoda vrátí <xref:System.Collections.IEnumerable> kolekci skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="c89f8-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="c89f8-127">Serializátor spustí dotaz k odeslání výsledků zpět do klientské/prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="c89f8-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="c89f8-128">Chcete-li získat přístup k výsledkům dotazu místně `ToList` na `ToArray` střední vrstvě, můžete vynutit spuštění voláním nebo na proměnnou dotazu.</span><span class="sxs-lookup"><span data-stu-id="c89f8-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="c89f8-129">Potom můžete vrátit tento seznam `IEnumerable`nebo pole jako .</span><span class="sxs-lookup"><span data-stu-id="c89f8-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="c89f8-130">Instance kontextu dat by měla mít životnost jedné "jednotky práce".</span><span class="sxs-lookup"><span data-stu-id="c89f8-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="c89f8-131">Ve volně vázaném prostředí je jednotka práce obvykle malá, možná jedna optimistická transakce, včetně jediného volání do aplikace `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="c89f8-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="c89f8-132">Proto kontext dat je vytvořen a uvolněn v oboru metody.</span><span class="sxs-lookup"><span data-stu-id="c89f8-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="c89f8-133">Pokud jednotka práce obsahuje volání logiky obchodních pravidel, pak `DataContext` obecně budete chtít zachovat instanci pro celou operaci.</span><span class="sxs-lookup"><span data-stu-id="c89f8-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="c89f8-134">V každém `DataContext` případě nejsou instance určeny k tomu, aby byly udržovány naživu po dlouhou dobu napříč libovolným počtem transakcí.</span><span class="sxs-lookup"><span data-stu-id="c89f8-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="c89f8-135">Tato metoda vrátí Product objekty, ale ne kolekce Order_Detail objekty, které jsou přidruženy ke každému produktu.</span><span class="sxs-lookup"><span data-stu-id="c89f8-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="c89f8-136">Pomocí <xref:System.Data.Linq.DataLoadOptions> objektu změňte toto výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="c89f8-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="c89f8-137">Další informace naleznete v [tématu How to: Control How Much Related data is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="c89f8-138">Vkládání dat</span><span class="sxs-lookup"><span data-stu-id="c89f8-138">Inserting Data</span></span>  
 <span data-ttu-id="c89f8-139">Chcete-li vložit nový objekt, prezentační vrstva pouze volá příslušnou metodu na rozhraní střední vrstvy a předá v novém objektu vložit.</span><span class="sxs-lookup"><span data-stu-id="c89f8-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="c89f8-140">V některých případech může být efektivnější pro klienta předat pouze některé hodnoty a střední vrstvy konstrukce úplný objekt.</span><span class="sxs-lookup"><span data-stu-id="c89f8-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="c89f8-141">Implementace střední úrovně</span><span class="sxs-lookup"><span data-stu-id="c89f8-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="c89f8-142">Na střední vrstvě <xref:System.Data.Linq.DataContext> je vytvořen nový, objekt je <xref:System.Data.Linq.DataContext> připojen <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> k pomocí metody a objekt <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je vložen, když je volán.</span><span class="sxs-lookup"><span data-stu-id="c89f8-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="c89f8-143">Výjimky, zpětná volání a chybové stavy lze zpracovat stejně jako v jakémkoli jiném scénáři webové služby.</span><span class="sxs-lookup"><span data-stu-id="c89f8-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="c89f8-144">Odstranění dat</span><span class="sxs-lookup"><span data-stu-id="c89f8-144">Deleting Data</span></span>  
 <span data-ttu-id="c89f8-145">Chcete-li odstranit existující objekt z databáze, prezentační vrstva volá příslušnou metodu na rozhraní střední vrstvy a předá v jeho kopii, která obsahuje původní hodnoty objektu, který má být odstraněn.</span><span class="sxs-lookup"><span data-stu-id="c89f8-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="c89f8-146">Operace odstranění zahrnují optimistické kontroly souběžnosti a objekt, který má být odstraněn, musí být nejprve připojen k novému kontextu dat.</span><span class="sxs-lookup"><span data-stu-id="c89f8-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="c89f8-147">V tomto příkladu `Boolean` je `false` parametr nastaven tak, aby označoval, že objekt nemá časové razítko (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="c89f8-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="c89f8-148">Pokud databázová tabulka generuje časová razítka pro každý záznam, jsou kontroly souběžnosti mnohem jednodušší, zejména pro klienta.</span><span class="sxs-lookup"><span data-stu-id="c89f8-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="c89f8-149">Stačí předat původní nebo upravený objekt `Boolean` a `true`nastavit parametr na .</span><span class="sxs-lookup"><span data-stu-id="c89f8-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="c89f8-150">V každém případě, na střední vrstvě je <xref:System.Data.Linq.ChangeConflictException>obvykle nutné zachytit .</span><span class="sxs-lookup"><span data-stu-id="c89f8-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="c89f8-151">Další informace o tom, jak zpracovat optimistické konflikty souběžnosti, naleznete [v tématu Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="c89f8-152">Při odstraňování entit, které mají omezení cizího klíče v přidružených tabulkách, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekcích.</span><span class="sxs-lookup"><span data-stu-id="c89f8-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="c89f8-153">Aktualizace dat</span><span class="sxs-lookup"><span data-stu-id="c89f8-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c89f8-154">podporuje aktualizace v těchto scénářích zahrnující optimistické souběžnosti:</span><span class="sxs-lookup"><span data-stu-id="c89f8-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="c89f8-155">Optimistická souběžnost založená na časových razítkách nebo číslech RowVersion.</span><span class="sxs-lookup"><span data-stu-id="c89f8-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="c89f8-156">Optimistická souběžnost založená na původních hodnotách podmnožiny vlastností entity.</span><span class="sxs-lookup"><span data-stu-id="c89f8-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="c89f8-157">Optimistická souběžnost založená na úplných původních a změněných entitách.</span><span class="sxs-lookup"><span data-stu-id="c89f8-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="c89f8-158">Můžete také provádět aktualizace nebo odstranění entity společně s jejími vztahy, například zákazníkem a kolekcí přidružených objektů objednávky.</span><span class="sxs-lookup"><span data-stu-id="c89f8-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="c89f8-159">Když provedete změny na klienta grafu objektů entity`EntitySet`a jejich podřízené ( ) kolekce a optimistické kontroly souběžnosti vyžadují <xref:System.Data.Linq.EntitySet%601> původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a objekt.</span><span class="sxs-lookup"><span data-stu-id="c89f8-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="c89f8-160">Pokud chcete klientům povolit provádění sad souvisejících aktualizací, odstranění a vložení v volání jedné metody, musíte klientovi poskytnout způsob, jak určit, jaký typ operace má být u každé entity provádět.</span><span class="sxs-lookup"><span data-stu-id="c89f8-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="c89f8-161">Na střední vrstvě pak musíte <xref:System.Data.Linq.ITable.Attach%2A> před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>volat <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> příslušnou `Attach`metodu a potom <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>nebo (bez vložení) pro každou entitu .</span><span class="sxs-lookup"><span data-stu-id="c89f8-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="c89f8-162">Nenačítat data z databáze jako způsob, jak získat původní hodnoty před pokusem o aktualizace.</span><span class="sxs-lookup"><span data-stu-id="c89f8-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="c89f8-163">Další informace o optimistické souběžnosti naleznete [v tématu Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="c89f8-164">Podrobné informace o řešení optimistických konfliktů změn souběžnosti naleznete v [tématu How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="c89f8-165">Následující příklady ukazují každý scénář:</span><span class="sxs-lookup"><span data-stu-id="c89f8-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="c89f8-166">Optimistická souběžnost s časovými razítky</span><span class="sxs-lookup"><span data-stu-id="c89f8-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="c89f8-167">S podmnožinou původních hodnot</span><span class="sxs-lookup"><span data-stu-id="c89f8-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="c89f8-168">V tomto přístupu klient vrátí kompletní serializované objektu, spolu s hodnotami, které mají být změněny.</span><span class="sxs-lookup"><span data-stu-id="c89f8-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="c89f8-169">S úplnými entitami</span><span class="sxs-lookup"><span data-stu-id="c89f8-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="c89f8-170">Chcete-li aktualizovat <xref:System.Data.Linq.ITable.AttachAll%2A> kolekci, volání namísto `Attach`.</span><span class="sxs-lookup"><span data-stu-id="c89f8-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="c89f8-171">Očekávaní členové entity</span><span class="sxs-lookup"><span data-stu-id="c89f8-171">Expected Entity Members</span></span>  
 <span data-ttu-id="c89f8-172">Jak již bylo uvedeno dříve, pouze některé členy objektu `Attach` entity musí být nastaveny před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="c89f8-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="c89f8-173">Členové entity, které musí být nastaveny, musí splňovat následující kritéria:</span><span class="sxs-lookup"><span data-stu-id="c89f8-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="c89f8-174">Být součástí identity entity.</span><span class="sxs-lookup"><span data-stu-id="c89f8-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="c89f8-175">Očekáváse, že bude změněn.</span><span class="sxs-lookup"><span data-stu-id="c89f8-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="c89f8-176">Být časové razítko <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nebo mít jeho `Never`atribut nastaven na něco kromě .</span><span class="sxs-lookup"><span data-stu-id="c89f8-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="c89f8-177">Pokud tabulka používá časové razítko nebo číslo verze pro optimistickou kontrolu souběžnosti, je nutné nastavit tyto členy před voláním <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="c89f8-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="c89f8-178">Člen je vyhrazena pro optimistické <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> souběžnosti kontroly při vlastnost je nastavena na hodnotu true na tento atribut Column.</span><span class="sxs-lookup"><span data-stu-id="c89f8-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="c89f8-179">Všechny požadované aktualizace budou odeslány pouze v případě, že číslo verze nebo časové razítko hodnoty jsou stejné v databázi.</span><span class="sxs-lookup"><span data-stu-id="c89f8-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="c89f8-180">Člen se také používá v optimistické kontrole souběžnosti, <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> pokud `Never`člen nemá nastavena na .</span><span class="sxs-lookup"><span data-stu-id="c89f8-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="c89f8-181">Výchozí hodnota `Always` je, pokud není zadána žádná jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c89f8-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="c89f8-182">Pokud některý z těchto požadovaných <xref:System.Data.Linq.ChangeConflictException> členů chybí, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je vyvolána během ("Řádek nebyl nalezen nebo změněn").</span><span class="sxs-lookup"><span data-stu-id="c89f8-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="c89f8-183">Stav</span><span class="sxs-lookup"><span data-stu-id="c89f8-183">State</span></span>  
 <span data-ttu-id="c89f8-184">Poté, co je objekt <xref:System.Data.Linq.DataContext> entity připojen k instanci, `PossiblyModified` objekt je považován za ve stavu.</span><span class="sxs-lookup"><span data-stu-id="c89f8-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="c89f8-185">Existují tři způsoby, jak vynutit `Modified`připojené objektu, které mají být považovány .</span><span class="sxs-lookup"><span data-stu-id="c89f8-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="c89f8-186">Připojte jej jako nezměněné a potom přímo upravte pole.</span><span class="sxs-lookup"><span data-stu-id="c89f8-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="c89f8-187">Připojte jej <xref:System.Data.Linq.Table%601.Attach%2A> s přetížením, které přebírá aktuální a původní instance objektu.</span><span class="sxs-lookup"><span data-stu-id="c89f8-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="c89f8-188">To poskytuje sledování změn se starými a novými hodnotami, takže bude automaticky vědět, která pole se změnila.</span><span class="sxs-lookup"><span data-stu-id="c89f8-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="c89f8-189">Připojte jej <xref:System.Data.Linq.Table%601.Attach%2A> s přetížením, které přebírá druhý logický parametr (nastavený na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="c89f8-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="c89f8-190">To bude říkat sledování změn zvážit objekt změněn bez nutnosti zadat žádné původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c89f8-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="c89f8-191">V tomto přístupu musí mít objekt pole verze/časového razítka.</span><span class="sxs-lookup"><span data-stu-id="c89f8-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="c89f8-192">Další informace naleznete [v tématu Stavy objektů a Sledování změn](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="c89f8-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="c89f8-193">Pokud objekt entity již dochází v mezipaměti ID se stejnou identitou <xref:System.Data.Linq.DuplicateKeyException> jako objekt, který je připojen, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c89f8-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="c89f8-194">Při připojení se `IEnumerable` sadou <xref:System.Data.Linq.DuplicateKeyException> objektů, je vyvolána, když již existující klíč je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c89f8-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="c89f8-195">Zbývající objekty nejsou připojeny.</span><span class="sxs-lookup"><span data-stu-id="c89f8-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c89f8-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="c89f8-196">See also</span></span>

- [<span data-ttu-id="c89f8-197">N-vrstvé a vzdálené aplikace s LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c89f8-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="c89f8-198">Základní informace</span><span class="sxs-lookup"><span data-stu-id="c89f8-198">Background Information</span></span>](background-information.md)
