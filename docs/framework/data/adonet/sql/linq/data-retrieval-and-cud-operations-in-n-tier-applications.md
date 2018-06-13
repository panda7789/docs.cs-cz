---
title: Operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načtení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ea27d6406ed588f2046dc938f5167a6c0200329e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365836"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="eaa98-102">Operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načtení dat</span><span class="sxs-lookup"><span data-stu-id="eaa98-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="eaa98-103">Při serializaci objektů entity například zákazníků nebo objednávky klienta přes síť, jsou tyto entity odpojit od jejich data kontextu.</span><span class="sxs-lookup"><span data-stu-id="eaa98-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="eaa98-104">Data kontextu už sleduje, jejich změny nebo jejich přidružení s jinými objekty.</span><span class="sxs-lookup"><span data-stu-id="eaa98-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="eaa98-105">Nejedná se o problém, dokud klienti jsou jen ke čtení dat.</span><span class="sxs-lookup"><span data-stu-id="eaa98-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="eaa98-106">Také je poměrně jednoduché umožníte klientům přidat nové řádky k databázi.</span><span class="sxs-lookup"><span data-stu-id="eaa98-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="eaa98-107">Ale pokud vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, pak je potřeba přiřadit entity nový kontext data před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eaa98-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eaa98-108">Kromě toho pokud používáte kontrola optimistickou metodu souběžného s původní hodnoty, pak je také nutné způsob, jak poskytnout databázi původní entitu a entitu jako upravená.</span><span class="sxs-lookup"><span data-stu-id="eaa98-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="eaa98-109">`Attach` Metod jsou uvedeny umožnit entity vložena nový kontext dat po nějaké době odpojit.</span><span class="sxs-lookup"><span data-stu-id="eaa98-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="eaa98-110">I když jsou serializaci objektů proxy místě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entity, musíte ještě vytvořit entitu na vrstva přístupu k datům (DAL) a jeho připojení k nové <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.</span><span class="sxs-lookup"><span data-stu-id="eaa98-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eaa98-111"> je zcela je mi to o tom, jak se serializují entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-111"> is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="eaa98-112">Další informace o tom, jak používat [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] a SQLMetal nástroje pro generování tříd, které jsou serializovatelný pomocí Windows Communication Foundation (WCF), najdete v části [postup: Zkontrolujte serializovatelný entity](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaa98-113">Volat pouze `Attach` metody na nový nebo deserializovat entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="eaa98-114">Jediným způsobem pro entitu jako odpojit od jeho původní kontextu dat je pro něj k serializaci.</span><span class="sxs-lookup"><span data-stu-id="eaa98-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="eaa98-115">Pokud se pokusíte připojit undetached entity pro nový kontext dat a dané entity má stále odložení zavaděče jeho předchozí kontextu dat nástroje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="eaa98-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="eaa98-116">Entity s odložené zavaděče ze dvou různých datových kontextů může způsobit nežádoucí výsledky při provádění insert, update a delete operací na dané entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="eaa98-117">Další informace o odložených zavaděče najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="eaa98-118">Načítání dat</span><span class="sxs-lookup"><span data-stu-id="eaa98-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="eaa98-119">Volání metody klienta</span><span class="sxs-lookup"><span data-stu-id="eaa98-119">Client Method Call</span></span>  
 <span data-ttu-id="eaa98-120">Následující příklady ukazují volání metoda ukázka DAL z klienta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eaa98-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="eaa98-121">V tomto příkladu je DAL implementovaný jako knihovny služby systému Windows:</span><span class="sxs-lookup"><span data-stu-id="eaa98-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="eaa98-122">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="eaa98-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="eaa98-123">Následující příklad ukazuje implementace metody rozhraní ve střední vrstvě.</span><span class="sxs-lookup"><span data-stu-id="eaa98-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="eaa98-124">Toto jsou dva hlavní body poznamenat:</span><span class="sxs-lookup"><span data-stu-id="eaa98-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="eaa98-125"><xref:System.Data.Linq.DataContext> Je deklarován v oboru metoda.</span><span class="sxs-lookup"><span data-stu-id="eaa98-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="eaa98-126">Vrátí metodu <xref:System.Collections.IEnumerable> kolekce skutečné výsledky.</span><span class="sxs-lookup"><span data-stu-id="eaa98-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="eaa98-127">Serializátor spustí dotaz tak, aby odesílala výsledky zpět do klienta nebo prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="eaa98-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="eaa98-128">Pro přístup k výsledky dotazu místně na střední vrstvy, můžete vynutit spuštění voláním `ToList` nebo `ToArray` na proměnnou dotazu.</span><span class="sxs-lookup"><span data-stu-id="eaa98-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="eaa98-129">Potom můžete vrátit tohoto seznamu, nebo jako pole `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="eaa98-130">Instanci třídy kontextu dat by měl mít životnost jeden "jednotka práce."</span><span class="sxs-lookup"><span data-stu-id="eaa98-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="eaa98-131">V prostředí volně vázány jednotka práce je obvykle malý, případně jeden optimistické transakce, včetně jediné volání `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="eaa98-132">Proto kontextu dat je vytvořen a uvolnění v oboru metoda.</span><span class="sxs-lookup"><span data-stu-id="eaa98-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="eaa98-133">Pokud jednotku práce zahrnuje volání obchodní logiku pravidla a potom obvykle budete chtít zachovat `DataContext` instance pro tento celou operaci.</span><span class="sxs-lookup"><span data-stu-id="eaa98-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="eaa98-134">V každém případě `DataContext` instance nejsou určeny k zachovány zachování připojení pro dlouhou dobu mezi libovolný počet transakcí.</span><span class="sxs-lookup"><span data-stu-id="eaa98-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="eaa98-135">Tato metoda vrátí objekty produktu, ale ne kolekce z Order_Detail objekty, které jsou přiřazeny u každého produktu.</span><span class="sxs-lookup"><span data-stu-id="eaa98-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="eaa98-136">Použití <xref:System.Data.Linq.DataLoadOptions> objekt, který chcete změnit toto výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="eaa98-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="eaa98-137">Další informace najdete v tématu [postupy: řízení jak mnohem související Data se načítají](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="eaa98-138">Vkládání dat</span><span class="sxs-lookup"><span data-stu-id="eaa98-138">Inserting Data</span></span>  
 <span data-ttu-id="eaa98-139">Pokud chcete vložit nový objekt, prezentační vrstvou právě volá metodu relevantní na rozhraní střední vrstvy a předá v dialogu Nový objekt vložit.</span><span class="sxs-lookup"><span data-stu-id="eaa98-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="eaa98-140">V některých případech může být efektivnější klient předat jenom některé hodnoty a vytvořit úplnou objekt střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="eaa98-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="eaa98-141">Implementace střední vrstvy</span><span class="sxs-lookup"><span data-stu-id="eaa98-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="eaa98-142">Ve střední vrstvě novou <xref:System.Data.Linq.DataContext> je vytvořen, objekt je připojen k <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metoda a objekt je vložen při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="eaa98-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="eaa98-143">Výjimky, zpětná volání a chybové stavy můžete zpracovává stejně jako všechny další scénáře webové služby.</span><span class="sxs-lookup"><span data-stu-id="eaa98-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="eaa98-144">Odstraňování dat</span><span class="sxs-lookup"><span data-stu-id="eaa98-144">Deleting Data</span></span>  
 <span data-ttu-id="eaa98-145">Pokud chcete odstranit existující objekt z databáze, prezentační vrstvou volá metodu relevantní na rozhraní střední vrstvy a předá v jeho kopii, která obsahuje původní hodnoty objektu, který chcete odstranit.</span><span class="sxs-lookup"><span data-stu-id="eaa98-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="eaa98-146">Odstranit operací se zapojují optimistickou metodu souběžného kontroly a objekt, který chcete odstranit, musí být nejprve připojené k nový kontext data.</span><span class="sxs-lookup"><span data-stu-id="eaa98-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="eaa98-147">V tomto příkladu `Boolean` parametr je nastaven na `false` indikující, že objekt nemá časového razítka (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="eaa98-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="eaa98-148">Pokud vaše databáze tabulka vygenerovat časová razítka pro každý záznam, jsou kontrolách souběžnosti mnohem jednodušší, zejména pro klienta.</span><span class="sxs-lookup"><span data-stu-id="eaa98-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="eaa98-149">Právě předejte v původní nebo upravené objektu a nastavte `Boolean` parametru `true`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="eaa98-150">V každém případě ve střední vrstvě je obvykle potřeba catch <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="eaa98-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="eaa98-151">Další informace o tom, jak je v konfliktu optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="eaa98-152">Při odstraňování entity, které mají omezení cizího klíče na přidružené tabulky, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="eaa98-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="eaa98-153">Aktualizace dat</span><span class="sxs-lookup"><span data-stu-id="eaa98-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eaa98-154"> v těchto scénářích zahrnující optimistickou metodu souběžného podporuje aktualizace:</span><span class="sxs-lookup"><span data-stu-id="eaa98-154"> supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="eaa98-155">Optimistickou metodu souběžného na základě časová razítka nebo RowVersion čísla.</span><span class="sxs-lookup"><span data-stu-id="eaa98-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="eaa98-156">Optimistickou metodu souběžného založené na původní hodnoty podmnožinu vlastností entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="eaa98-157">Optimistickou metodu souběžného založené na dokončení původní a upravené entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="eaa98-158">Můžete také provést aktualizace nebo odstranění na entitu společně s jeho vztahů, například zákazník a kolekce jejích přidružených objektů pořadí.</span><span class="sxs-lookup"><span data-stu-id="eaa98-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="eaa98-159">Pokud provedete změny v klientském počítači do grafu. entity objektů a jejich podřízené (`EntitySet`) kolekce a kontroly optimistickou metodu souběžného vyžadují původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každé entity a <xref:System.Data.Linq.EntitySet%601> objekt.</span><span class="sxs-lookup"><span data-stu-id="eaa98-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="eaa98-160">Pokud chcete povolit klientským počítačům provádět sadu související aktualizace, odstranění a vložení v rámci jednoho volání metody, je nutné zadat klienta způsob označení, jaký typ operace provést u každé entity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="eaa98-161">Na střední vrstvy, pak musí volat odpovídající <xref:System.Data.Linq.ITable.Attach%2A> metoda a potom <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, pro vložení) pro každou entitu před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="eaa98-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="eaa98-162">Není načtení dat z databáze jako způsob, jak získat původní hodnoty, než se pokusíte aktualizace.</span><span class="sxs-lookup"><span data-stu-id="eaa98-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="eaa98-163">Další informace o optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="eaa98-164">Podrobné informace o řešení optimistickou metodu souběžného změnit je v konfliktu, najdete v části [postupy: Správa konfliktů změnit](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="eaa98-165">Následující příklady ukazují jednotlivých scénářů:</span><span class="sxs-lookup"><span data-stu-id="eaa98-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="eaa98-166">Optimistickou metodu souběžného časová razítka</span><span class="sxs-lookup"><span data-stu-id="eaa98-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="eaa98-167">S podmnožinou původní hodnoty</span><span class="sxs-lookup"><span data-stu-id="eaa98-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="eaa98-168">V tomto přístupu klienta vrátí dokončení serializovaný objekt společně s hodnoty, které mají být upraven.</span><span class="sxs-lookup"><span data-stu-id="eaa98-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="eaa98-169">S kompletní entity</span><span class="sxs-lookup"><span data-stu-id="eaa98-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="eaa98-170">Chcete-li aktualizovat kolekci, volejte <xref:System.Data.Linq.ITable.AttachAll%2A> místo `Attach`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="eaa98-171">Členy očekávané entit</span><span class="sxs-lookup"><span data-stu-id="eaa98-171">Expected Entity Members</span></span>  
 <span data-ttu-id="eaa98-172">Jak jsme uvedli dříve, je potřeba nastavit před voláním jenom určité členy objekt entity `Attach` metody.</span><span class="sxs-lookup"><span data-stu-id="eaa98-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="eaa98-173">Členy entit, které jsou nutné k nastavit musí splňovat následující kritéria:</span><span class="sxs-lookup"><span data-stu-id="eaa98-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="eaa98-174">Být součástí entity identity.</span><span class="sxs-lookup"><span data-stu-id="eaa98-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="eaa98-175">Dají se očekávat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="eaa98-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="eaa98-176">Být časového razítka, nebo jeho <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atribut nastaven na něco kromě `Never`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="eaa98-177">Pokud tabulka používá číslo verze nebo časové razítko pro kontrolu optimistickou metodu souběžného, musíte nastavit členů, před voláním <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="eaa98-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="eaa98-178">Člen je vyhrazen pro optimistickou metodu souběžného při kontrole <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je nastavena na hodnotu true na tento atribut sloupce.</span><span class="sxs-lookup"><span data-stu-id="eaa98-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="eaa98-179">Všechny požadované aktualizace bude odeslána, pouze v případě, že verze číslo nebo časové razítko hodnoty jsou stejné v databázi.</span><span class="sxs-lookup"><span data-stu-id="eaa98-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="eaa98-180">Člen se také používá v kontrola optimistickou metodu souběžného tak dlouho, dokud člen nemá <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nastavena na `Never`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="eaa98-181">Výchozí hodnota je `Always` Pokud není určena žádná jiná hodnota.</span><span class="sxs-lookup"><span data-stu-id="eaa98-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="eaa98-182">V případě potřeby některého z těchto chybí členy <xref:System.Data.Linq.ChangeConflictException> je vyvolána při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změnit").</span><span class="sxs-lookup"><span data-stu-id="eaa98-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="eaa98-183">Stav</span><span class="sxs-lookup"><span data-stu-id="eaa98-183">State</span></span>  
 <span data-ttu-id="eaa98-184">Po entity objekt je připojený k <xref:System.Data.Linq.DataContext> instance, objekt se považuje za v `PossiblyModified` stavu.</span><span class="sxs-lookup"><span data-stu-id="eaa98-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="eaa98-185">Existují tři způsoby, jak vynutit objekt připojené tak, aby se dalo považovat za `Modified`.</span><span class="sxs-lookup"><span data-stu-id="eaa98-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1.  <span data-ttu-id="eaa98-186">Připojit jako beze změny a potom upravte přímo pole.</span><span class="sxs-lookup"><span data-stu-id="eaa98-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2.  <span data-ttu-id="eaa98-187">Připojte ji s <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá aktuální a původní objekt instancí.</span><span class="sxs-lookup"><span data-stu-id="eaa98-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="eaa98-188">To poskytuje modul sledování změny s starých a nových hodnot, bude automaticky věděli, která pole se změnily.</span><span class="sxs-lookup"><span data-stu-id="eaa98-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3.  <span data-ttu-id="eaa98-189">Připojte ji s <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá druhý parametr typu Boolean (nastavený na hodnotu true).</span><span class="sxs-lookup"><span data-stu-id="eaa98-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="eaa98-190">Se tak dozví, modul sledování změny vzít v úvahu objekt změnit bez nutnosti poskytnout všechny původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eaa98-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="eaa98-191">V tomto přístupu musí mít objekt pole verze/časové razítko.</span><span class="sxs-lookup"><span data-stu-id="eaa98-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="eaa98-192">Další informace najdete v tématu [stavy objektů a sledování změn](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="eaa98-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="eaa98-193">Pokud objekt entity se již nachází v mezipaměti ID se stejnou identitou jako objekt připojovaný, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="eaa98-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="eaa98-194">Když se připojíte `IEnumerable` sadu objektů, <xref:System.Data.Linq.DuplicateKeyException> se vyvolá, když je k dispozici již existující klíč.</span><span class="sxs-lookup"><span data-stu-id="eaa98-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="eaa98-195">Nejsou připojeny zbývající objekty.</span><span class="sxs-lookup"><span data-stu-id="eaa98-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa98-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaa98-196">See Also</span></span>  
 [<span data-ttu-id="eaa98-197">N-vrstvé a vzdálené aplikace s LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="eaa98-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [<span data-ttu-id="eaa98-198">Základní informace</span><span class="sxs-lookup"><span data-stu-id="eaa98-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
