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
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
Při serializaci objektů entity, jako jsou zákazníci nebo objednávky klientovi v síti, jsou tyto entity odpojeny od jejich datového kontextu. Kontext dat již nesleduje jejich změny nebo jejich přidružení k jiným objektům. To není problém, pokud klienti pouze čtou data. Je také poměrně jednoduché povolit klientům přidávat nové řádky do databáze. Pokud však vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, je nutné <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>připojit entity k novému kontextu dat před voláním . Kromě toho pokud používáte optimistické souběžnosti kontrolu s původními hodnotami, pak budete také potřebovat způsob, jak poskytnout databázi původní entity a entity, jak změněn. Metody `Attach` jsou k dispozici k dispozici, aby vám umožní umístit entity do nového kontextu dat poté, co byly odpojeny.  
  
 I v případě, že serializujete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proxy objekty místo entit, stále musíte vytvořit entitu ve <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>vrstvě přístupu k datům (DAL) a připojit ji k nové aplikaci , aby bylo možné odeslat data do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je zcela lhostejný o tom, jak jsou entity serializovány. Další informace o použití nástrojů Object Relational Designer a SQLMetal ke generování tříd, které lze serializovat pomocí služby Windows Communication Foundation (WCF), naleznete v [tématu How to: Make Entities Serializable](how-to-make-entities-serializable.md).  
  
> [!NOTE]
> Volání metod `Attach` pouze u nových nebo rekonstruované entity. Jediný způsob, jak může být entita odpojena od původního datového kontextu, je serializovat ji. Pokud se pokusíte připojit neodpojenou entitu k novému kontextu dat a tato [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entita má stále odložené zavaděče z předchozího kontextu dat, vyvolá výjimku. Entita s odloženými zavaděči ze dvou různých datových kontextů může způsobit nežádoucí výsledky při provádění operací vložení, aktualizace a odstranění této entity. Další informace o odložené zavaděče, naleznete v [tématu Odloženo versus okamžité načítání](deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Načítání dat  
  
### <a name="client-method-call"></a>Volání metody klienta  
 Následující příklady ukazují ukázkové volání metody DAL z klienta Windows Forms. V tomto příkladu je DAL implementován jako knihovna služeb systému Windows:  
  
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
  
### <a name="middle-tier-implementation"></a>Implementace střední úrovně  
 Následující příklad ukazuje implementaci metody rozhraní na střední vrstvě. Níže jsou uvedeny dva hlavní body, které je třeba poznamenat:  
  
- Je <xref:System.Data.Linq.DataContext> deklarována v oboru metody.  
  
- Metoda vrátí <xref:System.Collections.IEnumerable> kolekci skutečné výsledky. Serializátor spustí dotaz k odeslání výsledků zpět do klientské/prezentační vrstvy. Chcete-li získat přístup k výsledkům dotazu místně `ToList` na `ToArray` střední vrstvě, můžete vynutit spuštění voláním nebo na proměnnou dotazu. Potom můžete vrátit tento seznam `IEnumerable`nebo pole jako .  
  
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
  
 Instance kontextu dat by měla mít životnost jedné "jednotky práce". Ve volně vázaném prostředí je jednotka práce obvykle malá, možná jedna optimistická transakce, včetně jediného volání do aplikace `SubmitChanges`. Proto kontext dat je vytvořen a uvolněn v oboru metody. Pokud jednotka práce obsahuje volání logiky obchodních pravidel, pak `DataContext` obecně budete chtít zachovat instanci pro celou operaci. V každém `DataContext` případě nejsou instance určeny k tomu, aby byly udržovány naživu po dlouhou dobu napříč libovolným počtem transakcí.  
  
 Tato metoda vrátí Product objekty, ale ne kolekce Order_Detail objekty, které jsou přidruženy ke každému produktu. Pomocí <xref:System.Data.Linq.DataLoadOptions> objektu změňte toto výchozí chování. Další informace naleznete v [tématu How to: Control How Much Related data is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Vkládání dat  
 Chcete-li vložit nový objekt, prezentační vrstva pouze volá příslušnou metodu na rozhraní střední vrstvy a předá v novém objektu vložit. V některých případech může být efektivnější pro klienta předat pouze některé hodnoty a střední vrstvy konstrukce úplný objekt.  
  
### <a name="middle-tier-implementation"></a>Implementace střední úrovně  
 Na střední vrstvě <xref:System.Data.Linq.DataContext> je vytvořen nový, objekt je <xref:System.Data.Linq.DataContext> připojen <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> k pomocí metody a objekt <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je vložen, když je volán. Výjimky, zpětná volání a chybové stavy lze zpracovat stejně jako v jakémkoli jiném scénáři webové služby.  
  
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
  
## <a name="deleting-data"></a>Odstranění dat  
 Chcete-li odstranit existující objekt z databáze, prezentační vrstva volá příslušnou metodu na rozhraní střední vrstvy a předá v jeho kopii, která obsahuje původní hodnoty objektu, který má být odstraněn.  
  
 Operace odstranění zahrnují optimistické kontroly souběžnosti a objekt, který má být odstraněn, musí být nejprve připojen k novému kontextu dat. V tomto příkladu `Boolean` je `false` parametr nastaven tak, aby označoval, že objekt nemá časové razítko (RowVersion). Pokud databázová tabulka generuje časová razítka pro každý záznam, jsou kontroly souběžnosti mnohem jednodušší, zejména pro klienta. Stačí předat původní nebo upravený objekt `Boolean` a `true`nastavit parametr na . V každém případě, na střední vrstvě je <xref:System.Data.Linq.ChangeConflictException>obvykle nutné zachytit . Další informace o tom, jak zpracovat optimistické konflikty souběžnosti, naleznete [v tématu Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).  
  
 Při odstraňování entit, které mají omezení cizího klíče v přidružených tabulkách, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekcích.  
  
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
  
## <a name="updating-data"></a>Aktualizace dat  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje aktualizace v těchto scénářích zahrnující optimistické souběžnosti:  
  
- Optimistická souběžnost založená na časových razítkách nebo číslech RowVersion.  
  
- Optimistická souběžnost založená na původních hodnotách podmnožiny vlastností entity.  
  
- Optimistická souběžnost založená na úplných původních a změněných entitách.  
  
 Můžete také provádět aktualizace nebo odstranění entity společně s jejími vztahy, například zákazníkem a kolekcí přidružených objektů objednávky. Když provedete změny na klienta grafu objektů entity`EntitySet`a jejich podřízené ( ) kolekce a optimistické kontroly souběžnosti vyžadují <xref:System.Data.Linq.EntitySet%601> původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a objekt. Pokud chcete klientům povolit provádění sad souvisejících aktualizací, odstranění a vložení v volání jedné metody, musíte klientovi poskytnout způsob, jak určit, jaký typ operace má být u každé entity provádět. Na střední vrstvě pak musíte <xref:System.Data.Linq.ITable.Attach%2A> před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>volat <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> příslušnou `Attach`metodu a potom <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>nebo (bez vložení) pro každou entitu . Nenačítat data z databáze jako způsob, jak získat původní hodnoty před pokusem o aktualizace.  
  
 Další informace o optimistické souběžnosti naleznete [v tématu Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md). Podrobné informace o řešení optimistických konfliktů změn souběžnosti naleznete v [tématu How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).  
  
 Následující příklady ukazují každý scénář:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optimistická souběžnost s časovými razítky  
  
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
  
### <a name="with-subset-of-original-values"></a>S podmnožinou původních hodnot  
 V tomto přístupu klient vrátí kompletní serializované objektu, spolu s hodnotami, které mají být změněny.  
  
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
  
### <a name="with-complete-entities"></a>S úplnými entitami  
  
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
  
 Chcete-li aktualizovat <xref:System.Data.Linq.ITable.AttachAll%2A> kolekci, volání namísto `Attach`.  
  
### <a name="expected-entity-members"></a>Očekávaní členové entity  
 Jak již bylo uvedeno dříve, pouze některé členy objektu `Attach` entity musí být nastaveny před voláním metody. Členové entity, které musí být nastaveny, musí splňovat následující kritéria:  
  
- Být součástí identity entity.  
  
- Očekáváse, že bude změněn.  
  
- Být časové razítko <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nebo mít jeho `Never`atribut nastaven na něco kromě .  
  
 Pokud tabulka používá časové razítko nebo číslo verze pro optimistickou kontrolu souběžnosti, je nutné nastavit tyto členy před voláním <xref:System.Data.Linq.ITable.Attach%2A>. Člen je vyhrazena pro optimistické <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> souběžnosti kontroly při vlastnost je nastavena na hodnotu true na tento atribut Column. Všechny požadované aktualizace budou odeslány pouze v případě, že číslo verze nebo časové razítko hodnoty jsou stejné v databázi.  
  
 Člen se také používá v optimistické kontrole souběžnosti, <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> pokud `Never`člen nemá nastavena na . Výchozí hodnota `Always` je, pokud není zadána žádná jiná hodnota.  
  
 Pokud některý z těchto požadovaných <xref:System.Data.Linq.ChangeConflictException> členů chybí, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je vyvolána během ("Řádek nebyl nalezen nebo změněn").  
  
### <a name="state"></a>Stav  
 Poté, co je objekt <xref:System.Data.Linq.DataContext> entity připojen k instanci, `PossiblyModified` objekt je považován za ve stavu. Existují tři způsoby, jak vynutit `Modified`připojené objektu, které mají být považovány .  
  
1. Připojte jej jako nezměněné a potom přímo upravte pole.  
  
2. Připojte jej <xref:System.Data.Linq.Table%601.Attach%2A> s přetížením, které přebírá aktuální a původní instance objektu. To poskytuje sledování změn se starými a novými hodnotami, takže bude automaticky vědět, která pole se změnila.  
  
3. Připojte jej <xref:System.Data.Linq.Table%601.Attach%2A> s přetížením, které přebírá druhý logický parametr (nastavený na hodnotu true). To bude říkat sledování změn zvážit objekt změněn bez nutnosti zadat žádné původní hodnoty. V tomto přístupu musí mít objekt pole verze/časového razítka.  
  
 Další informace naleznete [v tématu Stavy objektů a Sledování změn](object-states-and-change-tracking.md).  
  
 Pokud objekt entity již dochází v mezipaměti ID se stejnou identitou <xref:System.Data.Linq.DuplicateKeyException> jako objekt, který je připojen, je vyvolána.  
  
 Při připojení se `IEnumerable` sadou <xref:System.Data.Linq.DuplicateKeyException> objektů, je vyvolána, když již existující klíč je k dispozici. Zbývající objekty nejsou připojeny.  
  
## <a name="see-also"></a>Viz také

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Základní informace](background-information.md)
