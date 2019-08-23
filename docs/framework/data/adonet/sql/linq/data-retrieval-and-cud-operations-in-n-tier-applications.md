---
title: Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ccd30e3d1b0d716b6393fdb093d47cddf7302f8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963279"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
Při serializaci objektů entit, jako jsou například zákazníci nebo objednávky, na klienta prostřednictvím sítě, jsou tyto entity odpojeny od kontextu dat. Kontext dat již nesleduje jejich změny nebo jejich přidružení s jinými objekty. Nejedná se o problém, pokud klienti čtou pouze data. Je také poměrně snadné povolit klientům přidávat nové řádky do databáze. Pokud však vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstraňovat data, je nutné před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>připojit entity k novému datovému kontextu. Pokud navíc používáte optimistickou kontrolu souběžnosti s původními hodnotami, budete také potřebovat způsob, jak poskytnout databázi jak původní entitu, tak i entitu jako upravenou. `Attach` Metody jsou k dispozici, aby bylo možné vkládat entity do nového kontextu dat poté, co byly odpojeny.  
  
 I v případě, že provádíte serializaci objektů proxy místo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entit, je stále nutné vytvořit entitu na vrstvě pro přístup k datům (dal) a připojit ji k novému <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je zcela nerozdílný na způsobu serializace entit. Další informace o použití nástrojů Návrhář relací objektů a SqlMetal ke generování tříd, které jsou serializovatelný pomocí Windows Communication Foundation (WCF), naleznete v tématu [How to: Proveďte serializaci](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)entit.  
  
> [!NOTE]
> Volejte `Attach` pouze metody pro nové nebo deserializovatelné entity. Jediným způsobem, jak se entita odpojit od původního kontextu dat, je pro její serializaci. Pokud se pokusíte připojit neodpojenou entitu k novému datovému kontextu a tato entita stále obsahuje odložené zavaděče z předchozího kontextu dat, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyvolá výjimku. Entita s odloženými zavaděči ze dvou různých kontextů dat může při provádění operací vložení, aktualizace a odstranění v této entitě způsobit nechtěné výsledky. Další informace o odložených zavaděčích naleznete v tématu Odložené a [okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Načítání dat  
  
### <a name="client-method-call"></a>Volání metody klienta  
 Následující příklady ukazují ukázkovou metodu volání metody DAL z klienta model Windows Forms. V tomto příkladu je DAL implementován jako knihovna služby systému Windows:  
  
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
  
### <a name="middle-tier-implementation"></a>Implementace střední vrstvy  
 Následující příklad ukazuje implementaci metody rozhraní na střední úrovni. Níže jsou uvedené dva hlavní body:  
  
- <xref:System.Data.Linq.DataContext> Je deklarována v oboru metody.  
  
- Metoda vrátí <xref:System.Collections.IEnumerable> kolekci skutečných výsledků. Serializátor spustí dotaz k odeslání výsledků zpět do vrstvy klienta nebo prezentace. Chcete-li získat přístup k výsledkům dotazu místně na střední úrovni, můžete vynutit `ToList` provádění `ToArray` voláním nebo na proměnné dotazu. Pak můžete tento seznam nebo pole vrátit jako `IEnumerable`.  
  
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
  
 Instance kontextu dat by měla mít životnost jedné "pracovní jednotky". V volně odděleném prostředí je jednotka práce obvykle malá, možná jedna optimistická transakce, včetně jednoho volání `SubmitChanges`. Proto je datový kontext vytvořen a odstraněn v oboru metody. Pokud pracovní jednotka obsahuje volání logiky obchodních pravidel, pak obecně budete chtít zachovat `DataContext` instanci pro tuto celou operaci. V žádném případě `DataContext` instance nejsou určeny k udržování naživu po dlouhou dobu napříč libovolným počtem transakcí.  
  
 Tato metoda vrátí objekty produktu, ale ne kolekci objektů Order_Detail, které jsou spojeny s každým produktem. Toto výchozí chování můžete změnit pomocí objektu.<xref:System.Data.Linq.DataLoadOptions> Další informace najdete v tématu [jak: Určuje, kolik souvisejících dat se načítají](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Vkládání dat  
 Chcete-li vložit nový objekt, prezentační vrstva pouze volá příslušnou metodu v rozhraní střední vrstvy a předá do nového objektu pro vložení. V některých případech může být efektivnější, aby klient předával jenom některé hodnoty a aby měl úplný objekt konstrukce prostřední vrstvy.  
  
### <a name="middle-tier-implementation"></a>Implementace střední vrstvy  
 Na střední úrovni <xref:System.Data.Linq.DataContext> se vytvoří nový objekt, který je připojen <xref:System.Data.Linq.DataContext> k <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> objektu pomocí metody, a objekt je vložen při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání. Výjimky, zpětná volání a chybové podmínky lze zpracovat stejně jako v jakémkoli jiném scénáři webové služby.  
  
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
 Chcete-li odstranit existující objekt z databáze, prezentační vrstva volá příslušnou metodu v rozhraní střední vrstvy a předá její kopii, která obsahuje původní hodnoty objektu, který má být odstraněn.  
  
 Operace odstranění zahrnují optimistické kontroly souběžnosti a objekt, který má být odstraněn, musí být nejprve připojen k novému datovému kontextu. V tomto příkladu `Boolean` je parametr `false` nastaven na hodnotu, aby označoval, že objekt nemá časové razítko (rowversion). Pokud vaše databázová tabulka vygeneruje časová razítka pro každý záznam, jsou kontroly souběžnosti mnohem jednodušší, zejména pro klienta. Stačí předat buď původní nebo upravený objekt, a nastavit `Boolean` parametr na. `true` V každém případě je obvykle nutné zachytit <xref:System.Data.Linq.ChangeConflictException>na střední úrovni. Další informace o tom, jak zpracovat optimistické konflikty souběžnosti, naleznete [v tématu Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Při odstraňování entit, které mají omezení cizího klíče v přidružených tabulkách, je nutné nejprve odstranit všechny objekty ve <xref:System.Data.Linq.EntitySet%601> svých kolekcích.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje aktualizace v těchto scénářích, které zahrnují optimistickou souběžnost:  
  
- Optimistická souběžnost na základě časových razítek nebo RowVersion čísel.  
  
- Optimistická souběžnost na základě původních hodnot podmnožiny vlastností entity.  
  
- Optimistická souběžnost založená na kompletní původní a upravené entitě.  
  
 V entitě můžete také provádět aktualizace nebo je odstranit spolu s jejími vztahy, například zákazníkem a kolekcí svých přidružených objektů objednávky. Když provedete úpravy klienta na graf objektů entit a jejich podřízených (`EntitySet`) kolekcí a optimistická kontrola souběžnosti vyžaduje původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a <xref:System.Data.Linq.EntitySet%601> předmětů. Pokud chcete klientům povolit sadu souvisejících aktualizací, odstranění a vkládání v rámci jediného volání metody, je nutné klientovi poskytnout způsob, jak určit, jaký typ operace se má v každé entitě provést. Na střední úrovni je nutné před <xref:System.Data.Linq.ITable.Attach%2A> voláním <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> `Attach` <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> volat<xref:System.Data.Linq.DataContext.SubmitChanges%2A>odpovídající metodu a pak, nebo (bez pro vložení) pro každou entitu. Neobnovujte data z databáze jako způsob získání původních hodnot před tím, než zkusíte aktualizace.  
  
 Další informace o optimistické souběžnosti najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Podrobné informace o řešení konfliktů změn optimistického řízení souběžnosti naleznete [v tématu How to: Spravujte konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)změn.  
  
 Následující příklady znázorňují jednotlivé scénáře:  
  
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
 V tomto přístupu klient vrátí kompletní serializovaný objekt spolu s hodnotami, které mají být změněny.  
  
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
  
### <a name="with-complete-entities"></a>S dokončenými entitami  
  
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
  
 Chcete-li aktualizovat kolekci, <xref:System.Data.Linq.ITable.AttachAll%2A> zavolejte `Attach`místo.  
  
### <a name="expected-entity-members"></a>Očekávané členy entity  
 Jak bylo uvedeno dříve, musí být před voláním `Attach` metod nastaveny pouze určité členy objektu entity. Členy entity, které je třeba nastavit, musí splňovat následující kritéria:  
  
- Být součástí identity entity.  
  
- Očekává se, že se má změnit.  
  
- Být časové razítko nebo mít <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> jeho atribut nastaven na něco `Never`kromě.  
  
 Pokud tabulka používá časové razítko nebo číslo verze pro optimistickou kontrolu souběžnosti, musíte tyto členy nastavit před voláním <xref:System.Data.Linq.ITable.Attach%2A>. Člen je vyhrazen pro kontrolu optimistického souběžnosti, pokud <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je vlastnost nastavena na hodnotu true u daného atributu sloupce. Všechny požadované aktualizace budou odeslány pouze v případě, že je číslo verze nebo hodnoty časového razítka v databázi stejné.  
  
 Člen se používá také v kontrole optimistického řízení souběžnosti, pokud člen <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nemá `Never`nastavenou hodnotu. Výchozí hodnota je `Always` , pokud není zadána jiná hodnota.  
  
 Pokud některý z požadovaných členů chybí, je vyvolána výjimka v <xref:System.Data.Linq.ChangeConflictException> průběhu <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změněn").  
  
### <a name="state"></a>Stav  
 Po připojení objektu entity k <xref:System.Data.Linq.DataContext> instanci je objekt považován za `PossiblyModified` ve stavu. Existují tři způsoby, jak vynutit zvážení `Modified`připojeného objektu.  
  
1. Připojte jej jako nezměněný a potom přímo upravte pole.  
  
2. Připojte ho k <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přebírá aktuální a původní instance objektů. To poskytuje sledování změn se starými a novými hodnotami tak, aby se automaticky vědělo, která pole se změnila.  
  
3. Připojte jej k <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá Druhý logický parametr (nastaveno na hodnotu true). Tím se nástroj pro sledování změn upozorní, že se objekt změnil, aniž by musel zadávat žádné původní hodnoty. V tomto přístupu musí mít objekt pole verze nebo časové razítko.  
  
 Další informace najdete v tématech [stavy objektů a sledování změn](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Pokud objekt entity již v mezipaměti ID existuje se stejnou identitou jako připojenému objektu, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.  
  
 Když se připojíte se `IEnumerable` sadou objektů <xref:System.Data.Linq.DuplicateKeyException> , vyvolá se, když je přítomen již existující klíč. Zbývající objekty nejsou připojeny.  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
