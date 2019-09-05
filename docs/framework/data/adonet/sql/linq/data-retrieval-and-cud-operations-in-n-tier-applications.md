---
title: Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 706dbda98d0e1674b76ebc6a25c7a34746720ea2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247367"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="1a70a-102">Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="1a70a-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="1a70a-103">Při serializaci objektů entit, jako jsou například zákazníci nebo objednávky, na klienta prostřednictvím sítě, jsou tyto entity odpojeny od kontextu dat.</span><span class="sxs-lookup"><span data-stu-id="1a70a-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="1a70a-104">Kontext dat již nesleduje jejich změny nebo jejich přidružení s jinými objekty.</span><span class="sxs-lookup"><span data-stu-id="1a70a-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="1a70a-105">Nejedná se o problém, pokud klienti čtou pouze data.</span><span class="sxs-lookup"><span data-stu-id="1a70a-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="1a70a-106">Je také poměrně snadné povolit klientům přidávat nové řádky do databáze.</span><span class="sxs-lookup"><span data-stu-id="1a70a-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="1a70a-107">Pokud však vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstraňovat data, je nutné před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>připojit entity k novému datovému kontextu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a70a-108">Pokud navíc používáte optimistickou kontrolu souběžnosti s původními hodnotami, budete také potřebovat způsob, jak poskytnout databázi jak původní entitu, tak i entitu jako upravenou.</span><span class="sxs-lookup"><span data-stu-id="1a70a-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="1a70a-109">`Attach` Metody jsou k dispozici, aby bylo možné vkládat entity do nového kontextu dat poté, co byly odpojeny.</span><span class="sxs-lookup"><span data-stu-id="1a70a-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="1a70a-110">I v případě, že provádíte serializaci objektů proxy místo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entit, je stále nutné vytvořit entitu na vrstvě pro přístup k datům (dal) a připojit ji k novému <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.</span><span class="sxs-lookup"><span data-stu-id="1a70a-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a70a-111">je zcela nerozdílný na způsobu serializace entit.</span><span class="sxs-lookup"><span data-stu-id="1a70a-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="1a70a-112">Další informace o použití nástrojů Návrhář relací objektů a SqlMetal ke generování tříd, které jsou serializovatelný pomocí Windows Communication Foundation (WCF), naleznete v tématu [How to: Proveďte serializaci](how-to-make-entities-serializable.md)entit.</span><span class="sxs-lookup"><span data-stu-id="1a70a-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a70a-113">Volejte `Attach` pouze metody pro nové nebo deserializovatelné entity.</span><span class="sxs-lookup"><span data-stu-id="1a70a-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="1a70a-114">Jediným způsobem, jak se entita odpojit od původního kontextu dat, je pro její serializaci.</span><span class="sxs-lookup"><span data-stu-id="1a70a-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="1a70a-115">Pokud se pokusíte připojit neodpojenou entitu k novému datovému kontextu a tato entita stále obsahuje odložené zavaděče z předchozího kontextu dat, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="1a70a-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="1a70a-116">Entita s odloženými zavaděči ze dvou různých kontextů dat může při provádění operací vložení, aktualizace a odstranění v této entitě způsobit nechtěné výsledky.</span><span class="sxs-lookup"><span data-stu-id="1a70a-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="1a70a-117">Další informace o odložených zavaděčích naleznete v tématu [odložené a okamžité načítání](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="1a70a-118">Načítání dat</span><span class="sxs-lookup"><span data-stu-id="1a70a-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="1a70a-119">Volání metody klienta</span><span class="sxs-lookup"><span data-stu-id="1a70a-119">Client Method Call</span></span>  
 <span data-ttu-id="1a70a-120">Následující příklady ukazují ukázkovou metodu volání metody DAL z klienta model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1a70a-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="1a70a-121">V tomto příkladu je DAL implementován jako knihovna služby systému Windows:</span><span class="sxs-lookup"><span data-stu-id="1a70a-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="1a70a-122">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="1a70a-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="1a70a-123">Následující příklad ukazuje implementaci metody rozhraní na střední úrovni.</span><span class="sxs-lookup"><span data-stu-id="1a70a-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="1a70a-124">Níže jsou uvedené dva hlavní body:</span><span class="sxs-lookup"><span data-stu-id="1a70a-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="1a70a-125"><xref:System.Data.Linq.DataContext> Je deklarována v oboru metody.</span><span class="sxs-lookup"><span data-stu-id="1a70a-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="1a70a-126">Metoda vrátí <xref:System.Collections.IEnumerable> kolekci skutečných výsledků.</span><span class="sxs-lookup"><span data-stu-id="1a70a-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="1a70a-127">Serializátor spustí dotaz k odeslání výsledků zpět do vrstvy klienta nebo prezentace.</span><span class="sxs-lookup"><span data-stu-id="1a70a-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="1a70a-128">Chcete-li získat přístup k výsledkům dotazu místně na střední úrovni, můžete vynutit `ToList` provádění `ToArray` voláním nebo na proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="1a70a-129">Pak můžete tento seznam nebo pole vrátit jako `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="1a70a-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="1a70a-130">Instance kontextu dat by měla mít životnost jedné "pracovní jednotky".</span><span class="sxs-lookup"><span data-stu-id="1a70a-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="1a70a-131">V volně odděleném prostředí je jednotka práce obvykle malá, možná jedna optimistická transakce, včetně jednoho volání `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="1a70a-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="1a70a-132">Proto je datový kontext vytvořen a odstraněn v oboru metody.</span><span class="sxs-lookup"><span data-stu-id="1a70a-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="1a70a-133">Pokud pracovní jednotka obsahuje volání logiky obchodních pravidel, pak obecně budete chtít zachovat `DataContext` instanci pro tuto celou operaci.</span><span class="sxs-lookup"><span data-stu-id="1a70a-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="1a70a-134">V žádném případě `DataContext` instance nejsou určeny k udržování naživu po dlouhou dobu napříč libovolným počtem transakcí.</span><span class="sxs-lookup"><span data-stu-id="1a70a-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="1a70a-135">Tato metoda vrátí objekty produktu, ale ne kolekci objektů Order_Detail, které jsou spojeny s každým produktem.</span><span class="sxs-lookup"><span data-stu-id="1a70a-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="1a70a-136">Toto výchozí chování můžete změnit pomocí objektu.<xref:System.Data.Linq.DataLoadOptions></span><span class="sxs-lookup"><span data-stu-id="1a70a-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="1a70a-137">Další informace najdete v tématu [jak: Určuje, kolik souvisejících dat se načítají](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="1a70a-138">Vkládání dat</span><span class="sxs-lookup"><span data-stu-id="1a70a-138">Inserting Data</span></span>  
 <span data-ttu-id="1a70a-139">Chcete-li vložit nový objekt, prezentační vrstva pouze volá příslušnou metodu v rozhraní střední vrstvy a předá do nového objektu pro vložení.</span><span class="sxs-lookup"><span data-stu-id="1a70a-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="1a70a-140">V některých případech může být efektivnější, aby klient předával jenom některé hodnoty a aby měl úplný objekt konstrukce prostřední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="1a70a-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="1a70a-141">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="1a70a-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="1a70a-142">Na střední úrovni <xref:System.Data.Linq.DataContext> se vytvoří nový objekt, který je připojen <xref:System.Data.Linq.DataContext> k <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> objektu pomocí metody, a objekt je vložen při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="1a70a-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="1a70a-143">Výjimky, zpětná volání a chybové podmínky lze zpracovat stejně jako v jakémkoli jiném scénáři webové služby.</span><span class="sxs-lookup"><span data-stu-id="1a70a-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="1a70a-144">Odstranění dat</span><span class="sxs-lookup"><span data-stu-id="1a70a-144">Deleting Data</span></span>  
 <span data-ttu-id="1a70a-145">Chcete-li odstranit existující objekt z databáze, prezentační vrstva volá příslušnou metodu v rozhraní střední vrstvy a předá její kopii, která obsahuje původní hodnoty objektu, který má být odstraněn.</span><span class="sxs-lookup"><span data-stu-id="1a70a-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="1a70a-146">Operace odstranění zahrnují optimistické kontroly souběžnosti a objekt, který má být odstraněn, musí být nejprve připojen k novému datovému kontextu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="1a70a-147">V tomto příkladu `Boolean` je parametr `false` nastaven na hodnotu, aby označoval, že objekt nemá časové razítko (rowversion).</span><span class="sxs-lookup"><span data-stu-id="1a70a-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="1a70a-148">Pokud vaše databázová tabulka vygeneruje časová razítka pro každý záznam, jsou kontroly souběžnosti mnohem jednodušší, zejména pro klienta.</span><span class="sxs-lookup"><span data-stu-id="1a70a-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="1a70a-149">Stačí předat buď původní nebo upravený objekt, a nastavit `Boolean` parametr na. `true`</span><span class="sxs-lookup"><span data-stu-id="1a70a-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="1a70a-150">V každém případě je obvykle nutné zachytit <xref:System.Data.Linq.ChangeConflictException>na střední úrovni.</span><span class="sxs-lookup"><span data-stu-id="1a70a-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="1a70a-151">Další informace o tom, jak zpracovat optimistické konflikty souběžnosti, naleznete [v tématu Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="1a70a-152">Při odstraňování entit, které mají omezení cizího klíče v přidružených tabulkách, je nutné nejprve odstranit všechny objekty ve <xref:System.Data.Linq.EntitySet%601> svých kolekcích.</span><span class="sxs-lookup"><span data-stu-id="1a70a-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="1a70a-153">Aktualizace dat</span><span class="sxs-lookup"><span data-stu-id="1a70a-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a70a-154">podporuje aktualizace v těchto scénářích, které zahrnují optimistickou souběžnost:</span><span class="sxs-lookup"><span data-stu-id="1a70a-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="1a70a-155">Optimistická souběžnost na základě časových razítek nebo RowVersion čísel.</span><span class="sxs-lookup"><span data-stu-id="1a70a-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="1a70a-156">Optimistická souběžnost na základě původních hodnot podmnožiny vlastností entity.</span><span class="sxs-lookup"><span data-stu-id="1a70a-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="1a70a-157">Optimistická souběžnost založená na kompletní původní a upravené entitě.</span><span class="sxs-lookup"><span data-stu-id="1a70a-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="1a70a-158">V entitě můžete také provádět aktualizace nebo je odstranit spolu s jejími vztahy, například zákazníkem a kolekcí svých přidružených objektů objednávky.</span><span class="sxs-lookup"><span data-stu-id="1a70a-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="1a70a-159">Když provedete úpravy klienta na graf objektů entit a jejich podřízených (`EntitySet`) kolekcí a optimistická kontrola souběžnosti vyžaduje původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a <xref:System.Data.Linq.EntitySet%601> předmětů.</span><span class="sxs-lookup"><span data-stu-id="1a70a-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="1a70a-160">Pokud chcete klientům povolit sadu souvisejících aktualizací, odstranění a vkládání v rámci jediného volání metody, je nutné klientovi poskytnout způsob, jak určit, jaký typ operace se má v každé entitě provést.</span><span class="sxs-lookup"><span data-stu-id="1a70a-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="1a70a-161">Na střední úrovni je nutné před <xref:System.Data.Linq.ITable.Attach%2A> voláním <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> `Attach` <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> volat<xref:System.Data.Linq.DataContext.SubmitChanges%2A>odpovídající metodu a pak, nebo (bez pro vložení) pro každou entitu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="1a70a-162">Neobnovujte data z databáze jako způsob získání původních hodnot před tím, než zkusíte aktualizace.</span><span class="sxs-lookup"><span data-stu-id="1a70a-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="1a70a-163">Další informace o optimistické souběžnosti najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="1a70a-164">Podrobné informace o řešení konfliktů změn optimistického řízení souběžnosti naleznete [v tématu How to: Spravujte konflikty](how-to-manage-change-conflicts.md)změn.</span><span class="sxs-lookup"><span data-stu-id="1a70a-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="1a70a-165">Následující příklady znázorňují jednotlivé scénáře:</span><span class="sxs-lookup"><span data-stu-id="1a70a-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="1a70a-166">Optimistická souběžnost s časovými razítky</span><span class="sxs-lookup"><span data-stu-id="1a70a-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="1a70a-167">S podmnožinou původních hodnot</span><span class="sxs-lookup"><span data-stu-id="1a70a-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="1a70a-168">V tomto přístupu klient vrátí kompletní serializovaný objekt spolu s hodnotami, které mají být změněny.</span><span class="sxs-lookup"><span data-stu-id="1a70a-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="1a70a-169">S dokončenými entitami</span><span class="sxs-lookup"><span data-stu-id="1a70a-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="1a70a-170">Chcete-li aktualizovat kolekci, <xref:System.Data.Linq.ITable.AttachAll%2A> zavolejte `Attach`místo.</span><span class="sxs-lookup"><span data-stu-id="1a70a-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="1a70a-171">Očekávané členy entity</span><span class="sxs-lookup"><span data-stu-id="1a70a-171">Expected Entity Members</span></span>  
 <span data-ttu-id="1a70a-172">Jak bylo uvedeno dříve, musí být před voláním `Attach` metod nastaveny pouze určité členy objektu entity.</span><span class="sxs-lookup"><span data-stu-id="1a70a-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="1a70a-173">Členy entity, které je třeba nastavit, musí splňovat následující kritéria:</span><span class="sxs-lookup"><span data-stu-id="1a70a-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="1a70a-174">Být součástí identity entity.</span><span class="sxs-lookup"><span data-stu-id="1a70a-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="1a70a-175">Očekává se, že se má změnit.</span><span class="sxs-lookup"><span data-stu-id="1a70a-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="1a70a-176">Být časové razítko nebo mít <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> jeho atribut nastaven na něco `Never`kromě.</span><span class="sxs-lookup"><span data-stu-id="1a70a-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="1a70a-177">Pokud tabulka používá časové razítko nebo číslo verze pro optimistickou kontrolu souběžnosti, musíte tyto členy nastavit před voláním <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a70a-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="1a70a-178">Člen je vyhrazen pro kontrolu optimistického souběžnosti, pokud <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je vlastnost nastavena na hodnotu true u daného atributu sloupce.</span><span class="sxs-lookup"><span data-stu-id="1a70a-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="1a70a-179">Všechny požadované aktualizace budou odeslány pouze v případě, že je číslo verze nebo hodnoty časového razítka v databázi stejné.</span><span class="sxs-lookup"><span data-stu-id="1a70a-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="1a70a-180">Člen se používá také v kontrole optimistického řízení souběžnosti, pokud člen <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nemá `Never`nastavenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="1a70a-181">Výchozí hodnota je `Always` , pokud není zadána jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="1a70a-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="1a70a-182">Pokud některý z požadovaných členů chybí, je vyvolána výjimka v <xref:System.Data.Linq.ChangeConflictException> průběhu <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změněn").</span><span class="sxs-lookup"><span data-stu-id="1a70a-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="1a70a-183">Stav</span><span class="sxs-lookup"><span data-stu-id="1a70a-183">State</span></span>  
 <span data-ttu-id="1a70a-184">Po připojení objektu entity k <xref:System.Data.Linq.DataContext> instanci je objekt považován za `PossiblyModified` ve stavu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="1a70a-185">Existují tři způsoby, jak vynutit zvážení `Modified`připojeného objektu.</span><span class="sxs-lookup"><span data-stu-id="1a70a-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="1a70a-186">Připojte jej jako nezměněný a potom přímo upravte pole.</span><span class="sxs-lookup"><span data-stu-id="1a70a-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="1a70a-187">Připojte ho k <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přebírá aktuální a původní instance objektů.</span><span class="sxs-lookup"><span data-stu-id="1a70a-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="1a70a-188">To poskytuje sledování změn se starými a novými hodnotami tak, aby se automaticky vědělo, která pole se změnila.</span><span class="sxs-lookup"><span data-stu-id="1a70a-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="1a70a-189">Připojte jej k <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá Druhý logický parametr (nastaveno na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="1a70a-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="1a70a-190">Tím se nástroj pro sledování změn upozorní, že se objekt změnil, aniž by musel zadávat žádné původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1a70a-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="1a70a-191">V tomto přístupu musí mít objekt pole verze nebo časové razítko.</span><span class="sxs-lookup"><span data-stu-id="1a70a-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="1a70a-192">Další informace najdete v tématech [stavy objektů a sledování změn](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="1a70a-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="1a70a-193">Pokud objekt entity již v mezipaměti ID existuje se stejnou identitou jako připojenému objektu, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1a70a-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="1a70a-194">Když se připojíte se `IEnumerable` sadou objektů <xref:System.Data.Linq.DuplicateKeyException> , vyvolá se, když je přítomen již existující klíč.</span><span class="sxs-lookup"><span data-stu-id="1a70a-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="1a70a-195">Zbývající objekty nejsou připojeny.</span><span class="sxs-lookup"><span data-stu-id="1a70a-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a70a-196">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a70a-196">See also</span></span>

- [<span data-ttu-id="1a70a-197">N-vrstvé a vzdálené aplikace s LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1a70a-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="1a70a-198">Základní informace</span><span class="sxs-lookup"><span data-stu-id="1a70a-198">Background Information</span></span>](background-information.md)
