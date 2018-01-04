---
title: "Operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načtení dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 84a72642636be2238a81f1b9c00e3ac4e7037272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Operace vytvoření ve víceúrovňových aplikacích (technologie LINQ to SQL) a načtení dat
Při serializaci objektů entity například zákazníků nebo objednávky klienta přes síť, jsou tyto entity odpojit od jejich data kontextu. Data kontextu už sleduje, jejich změny nebo jejich přidružení s jinými objekty. Nejedná se o problém, dokud klienti jsou jen ke čtení dat. Také je poměrně jednoduché umožníte klientům přidat nové řádky k databázi. Ale pokud vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, pak je potřeba přiřadit entity nový kontext data před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Kromě toho pokud používáte kontrola optimistickou metodu souběžného s původní hodnoty, pak je také nutné způsob, jak poskytnout databázi původní entitu a entitu jako upravená. `Attach` Metod jsou uvedeny umožnit entity vložena nový kontext dat po nějaké době odpojit.  
  
 I když jsou serializaci objektů proxy místě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entity, musíte ještě vytvořit entitu na vrstva přístupu k datům (DAL) a jeho připojení k nové <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je zcela je mi to o tom, jak se serializují entity. Další informace o tom, jak používat [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] a SQLMetal nástroje pro generování tříd, které jsou serializovatelný pomocí Windows Communication Foundation (WCF), najdete v části [postup: Zkontrolujte serializovatelný entity](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Volat pouze `Attach` metody na nový nebo deserializovat entity. Jediným způsobem pro entitu jako odpojit od jeho původní kontextu dat je pro něj k serializaci. Pokud se pokusíte připojit undetached entity pro nový kontext dat a dané entity má stále odložení zavaděče jeho předchozí kontextu dat nástroje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dojde k výjimce. Entity s odložené zavaděče ze dvou různých datových kontextů může způsobit nežádoucí výsledky při provádění insert, update a delete operací na dané entity. Další informace o odložených zavaděče najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Načítání dat  
  
### <a name="client-method-call"></a>Volání metody klienta  
 Následující příklady ukazují volání metoda ukázka DAL z klienta Windows Forms. V tomto příkladu je DAL implementovaný jako knihovny služby systému Windows:  
  
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
 Následující příklad ukazuje implementace metody rozhraní ve střední vrstvě. Toto jsou dva hlavní body poznamenat:  
  
-   <xref:System.Data.Linq.DataContext> Je deklarován v oboru metoda.  
  
-   Vrátí metodu <xref:System.Collections.IEnumerable> kolekce skutečné výsledky. Serializátor spustí dotaz tak, aby odesílala výsledky zpět do klienta nebo prezentační vrstvy. Pro přístup k výsledky dotazu místně na střední vrstvy, můžete vynutit spuštění voláním `ToList` nebo `ToArray` na proměnnou dotazu. Potom můžete vrátit tohoto seznamu, nebo jako pole `IEnumerable`.  
  
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
  
 Instanci třídy kontextu dat by měl mít životnost jeden "jednotka práce." V prostředí volně vázány jednotka práce je obvykle malý, případně jeden optimistické transakce, včetně jediné volání `SubmitChanges`. Proto kontextu dat je vytvořen a uvolnění v oboru metoda. Pokud jednotku práce zahrnuje volání obchodní logiku pravidla a potom obvykle budete chtít zachovat `DataContext` instance pro tento celou operaci. V každém případě `DataContext` instance nejsou určeny k zachovány zachování připojení pro dlouhou dobu mezi libovolný počet transakcí.  
  
 Tato metoda vrátí objekty produktu, ale ne kolekce z Order_Detail objekty, které jsou přiřazeny u každého produktu. Použití <xref:System.Data.Linq.DataLoadOptions> objekt, který chcete změnit toto výchozí chování. Další informace najdete v tématu [postupy: řízení jak mnohem související Data se načítají](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Vkládání dat  
 Pokud chcete vložit nový objekt, prezentační vrstvou právě volá metodu relevantní na rozhraní střední vrstvy a předá v dialogu Nový objekt vložit. V některých případech může být efektivnější klient předat jenom některé hodnoty a vytvořit úplnou objekt střední vrstvy.  
  
### <a name="middle-tier-implementation"></a>Implementace střední vrstvy  
 Ve střední vrstvě novou <xref:System.Data.Linq.DataContext> je vytvořen, objekt je připojen k <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metoda a objekt je vložen při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. Výjimky, zpětná volání a chybové stavy můžete zpracovává stejně jako všechny další scénáře webové služby.  
  
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
  
## <a name="deleting-data"></a>Odstraňování dat  
 Pokud chcete odstranit existující objekt z databáze, prezentační vrstvou volá metodu relevantní na rozhraní střední vrstvy a předá v jeho kopii, která obsahuje původní hodnoty objektu, který chcete odstranit.  
  
 Odstranit operací se zapojují optimistickou metodu souběžného kontroly a objekt, který chcete odstranit, musí být nejprve připojené k nový kontext data. V tomto příkladu `Boolean` parametr je nastaven na `false` indikující, že objekt nemá časového razítka (RowVersion). Pokud vaše databáze tabulka vygenerovat časová razítka pro každý záznam, jsou kontrolách souběžnosti mnohem jednodušší, zejména pro klienta. Právě předejte v původní nebo upravené objektu a nastavte `Boolean` parametru `true`. V každém případě ve střední vrstvě je obvykle potřeba catch <xref:System.Data.Linq.ChangeConflictException>. Další informace o tom, jak je v konfliktu optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Při odstraňování entity, které mají omezení cizího klíče na přidružené tabulky, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekce.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v těchto scénářích zahrnující optimistickou metodu souběžného podporuje aktualizace:  
  
-   Optimistickou metodu souběžného na základě časová razítka nebo RowVersion čísla.  
  
-   Optimistickou metodu souběžného založené na původní hodnoty podmnožinu vlastností entity.  
  
-   Optimistickou metodu souběžného založené na dokončení původní a upravené entity.  
  
 Můžete také provést aktualizace nebo odstranění na entitu společně s jeho vztahů, například zákazník a kolekce jejích přidružených objektů pořadí. Pokud provedete změny v klientském počítači do grafu. entity objektů a jejich podřízené (`EntitySet`) kolekce a kontroly optimistickou metodu souběžného vyžadují původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každé entity a <xref:System.Data.Linq.EntitySet%601> objekt. Pokud chcete povolit klientským počítačům provádět sadu související aktualizace, odstranění a vložení v rámci jednoho volání metody, je nutné zadat klienta způsob označení, jaký typ operace provést u každé entity. Na střední vrstvy, pak musí volat odpovídající <xref:System.Data.Linq.ITable.Attach%2A> metoda a potom <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, pro vložení) pro každou entitu před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Není načtení dat z databáze jako způsob, jak získat původní hodnoty, než se pokusíte aktualizace.  
  
 Další informace o optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Podrobné informace o řešení optimistickou metodu souběžného změnit je v konfliktu, najdete v části [postupy: Správa konfliktů změnit](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Následující příklady ukazují jednotlivých scénářů:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optimistickou metodu souběžného časová razítka  
  
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
  
### <a name="with-subset-of-original-values"></a>S podmnožinou původní hodnoty  
 V tomto přístupu klienta vrátí dokončení serializovaný objekt společně s hodnoty, které mají být upraven.  
  
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
  
### <a name="with-complete-entities"></a>S kompletní entity  
  
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
  
 Chcete-li aktualizovat kolekci, volejte <xref:System.Data.Linq.ITable.AttachAll%2A> místo `Attach`.  
  
### <a name="expected-entity-members"></a>Členy očekávané entit  
 Jak jsme uvedli dříve, je potřeba nastavit před voláním jenom určité členy objekt entity `Attach` metody. Členy entit, které jsou nutné k nastavit musí splňovat následující kritéria:  
  
-   Být součástí entity identity.  
  
-   Dají se očekávat má být změněn.  
  
-   Být časového razítka, nebo jeho <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atribut nastaven na něco kromě `Never`.  
  
 Pokud tabulka používá číslo verze nebo časové razítko pro kontrolu optimistickou metodu souběžného, musíte nastavit členů, před voláním <xref:System.Data.Linq.ITable.Attach%2A>. Člen je vyhrazen pro optimistickou metodu souběžného při kontrole <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je nastavena na hodnotu true na tento atribut sloupce. Všechny požadované aktualizace bude odeslána, pouze v případě, že verze číslo nebo časové razítko hodnoty jsou stejné v databázi.  
  
 Člen se také používá v kontrola optimistickou metodu souběžného tak dlouho, dokud člen nemá <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nastavena na `Never`. Výchozí hodnota je `Always` Pokud není určena žádná jiná hodnota.  
  
 V případě potřeby některého z těchto chybí členy <xref:System.Data.Linq.ChangeConflictException> je vyvolána při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změnit").  
  
### <a name="state"></a>Stav  
 Po entity objekt je připojený k <xref:System.Data.Linq.DataContext> instance, objekt se považuje za v `PossiblyModified` stavu. Existují tři způsoby, jak vynutit objekt připojené tak, aby se dalo považovat za `Modified`.  
  
1.  Připojit jako beze změny a potom upravte přímo pole.  
  
2.  Připojte ji s <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá aktuální a původní objekt instancí. To poskytuje modul sledování změny s starých a nových hodnot, bude automaticky věděli, která pole se změnily.  
  
3.  Připojte ji s <xref:System.Data.Linq.Table%601.Attach%2A> přetížení, které přijímá druhý parametr typu Boolean (nastavený na hodnotu true). Se tak dozví, modul sledování změny vzít v úvahu objekt změnit bez nutnosti poskytnout všechny původní hodnoty. V tomto přístupu musí mít objekt pole verze/časové razítko.  
  
 Další informace najdete v tématu [stavy objektů a sledování změn](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Pokud objekt entity se již nachází v mezipaměti ID se stejnou identitou jako objekt připojovaný, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.  
  
 Když se připojíte `IEnumerable` sadu objektů, <xref:System.Data.Linq.DuplicateKeyException> se vyvolá, když je k dispozici již existující klíč. Nejsou připojeny zbývající objekty.  
  
## <a name="see-also"></a>Viz také  
 [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
