---
title: Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: c43935cd53d1b58ce695164e957b4b5376d52536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209811"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Operace načítání dat a vytvoření, aktualizace a odstranění v N-úrovňových aplikacích (LINQ to SQL)
Při serializaci objektů entity jako je například Zákazníci a objednávky na klienta přes síť, tyto entity jsou odpojeny od jejich místní data. Datový kontext již sleduje jejich změny nebo jejich přidružení s jinými objekty. To není problém, tak dlouho, dokud klienti jsou jen ke čtení data. Také je poměrně jednoduchá, aby mohli klienti k přidání nových řádků do databáze. Nicméně pokud vaše aplikace vyžaduje, aby klienti mohli aktualizovat nebo odstranit data, pak je nutné připojit entity k nový kontext dat před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Navíc pokud použijete kontrolu optimistického řízení souběžnosti s původní hodnoty, pak musíte také poskytnout databázi původní entitu a entitu jako upravená. `Attach` Metody jsou k dispozici umožňuje entity přejde do nového kontextu dat byla odpojena.  
  
 I když je serializována objekty proxy místo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entity, stále musíte vytvořit entitu na vrstvy přístupu k datům (DAL) a připojit ho k nové <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby bylo možné odeslat data do databáze.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je zcela je mi to o způsob, jakým serializují entity. Další informace o tom, jak používat [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] a SQLMetal nástroje pro generování třídy, které jsou serializovatelné s použitím Windows Communication Foundation (WCF), najdete v článku [jak: Nastavení entit jako serializovatelných](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Volat pouze `Attach` metod v nové nebo deserializovat entit. Jediným způsobem, který se má odpojit z jeho původního kontextu dat entity je pro ni mají být serializován. Pokud dané entity má stále odložení zavaděče z jeho předchozí kontext dat, a pokusíte připojit entitu undetached nový kontext dat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bude vyvolána výjimka. Entita s odložené zavaděče ze dvou různých datových kontextech může způsobit nežádoucí výsledky, když provádíte insert, update a operace odstranění na dané entitě. Další informace o odložených zavaděče, naleznete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Načítání dat  
  
### <a name="client-method-call"></a>Volání metody klienta  
 Následující příklady ukazují volání metody ukázka vrstvy Dal z klienta Windows Forms. V tomto příkladu je DAL implementován jako knihovna služby Windows:  
  
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
 Následující příklad ukazuje implementaci metody rozhraní ve střední vrstvě. Tady jsou dva hlavní body k mějte na paměti:  
  
-   <xref:System.Data.Linq.DataContext> Je deklarována v rozsahu metody.  
  
-   Metoda vrátí <xref:System.Collections.IEnumerable> kolekce skutečné výsledky. Serializátor spustí dotaz pro výsledky odeslat zpět do klienta a prezentační vrstvy. Pro přístup k místně ve střední vrstvě. výsledky dotazu, můžete vynutit spuštění voláním `ToList` nebo `ToArray` v proměnné dotazu. Potom tento seznam nebo pole jako `IEnumerable`.  
  
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
  
 Instance kontextu dat má životnost jeden "jednotku práce." V prostředí s minimálním počtem vazeb určitou jednotku práce je obvykle malý, případně jeden optimistické transakce, včetně jedním voláním `SubmitChanges`. Proto kontext dat je vytvořen a uvolněn v oboru metody. Pokud jednotku práce zahrnuje volání obchodní logiku pravidla a potom obvykle budete chtít zachovat `DataContext` instance pro danou celou operaci. V každém případě `DataContext` instance nemají být zachováno po dlouhou dobu mezi libovolného počtu transakcí.  
  
 Tato metoda vrátí objekty produktu, ale ne na kolekci z Order_Detail objekty, které jsou spojeny s každého produktu. Použití <xref:System.Data.Linq.DataLoadOptions> objektu, chcete-li změnit toto výchozí chování. Další informace najdete v tématu [jak: Ovládací prvek, kolik souvisejících dat](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Vkládání dat  
 Vložit nový objekt, prezentační vrstvy jen volá metodu relevantní na střední vrstvu rozhraní a předá nový objekt pro vložení. V některých případech může být efektivnější pro klienta a předejte pouze některé hodnoty mají střední vrstva, sestavit úplný objekt.  
  
### <a name="middle-tier-implementation"></a>Implementace střední vrstvy  
 Ve střední vrstvě nový <xref:System.Data.Linq.DataContext> je vytvořen, objekt je připojen ke <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metoda a objekt při vložení <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. Stejně jako u jakékoli jiné scénář webových služeb mohou zpracovat výjimky, zpětná volání a chybové stavy.  
  
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
 Z databáze odstranit existující objekt, prezentační vrstvy volá metodu relevantní na střední vrstvě rozhraní a předá v jeho kopii, která obsahuje původní hodnoty objekt, který chcete odstranit.  
  
 Odstranit operace zahrnují kontroly optimistického řízení souběžnosti a objekt, který chcete odstranit, musí být nejprve připojený k nový datový kontext. V tomto příkladu `Boolean` parametr je nastaven na `false` k označení, že objekt nemá časové razítko (RowVersion). Pokud vaše databázové tabulky generovat časová razítka pro každý záznam, kontrolách souběžnosti jsou mnohem jednodušší, zejména u klienta. Stačí předat do původního nebo upravené objektu a nastavit `Boolean` parametr `true`. V každém případě ve střední vrstvě je obvykle potřeba zachytit <xref:System.Data.Linq.ChangeConflictException>. Další informace o tom, jak se řeší konflikty optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Při odstraňování entity, které mají omezení cizího klíče v přidružené tabulky, musíte nejprve odstranit všechny objekty v jeho <xref:System.Data.Linq.EntitySet%601> kolekce.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] v těchto scénářích zahrnující optimistického řízení souběžnosti podporuje aktualizace:  
  
-   Optimistického řízení souběžnosti na základě časových razítek nebo RowVersion čísla.  
  
-   Optimistického řízení souběžnosti založené na původní hodnoty podmnožinu vlastností entity.  
  
-   Optimistického řízení souběžnosti založené na dokončení původní a změny entity.  
  
 Aktualizace nebo odstranění můžete provést také s entitou společně s jeho vztahy, například zákazník a kolekce jejích přidružených objektů pořadí. Pokud provedete změny v klientském počítači do grafu objekty entity a jejich podřízené (`EntitySet`) kolekce a kontroly optimistického řízení souběžnosti vyžadují původní hodnoty, klient musí poskytnout tyto původní hodnoty pro každou entitu a <xref:System.Data.Linq.EntitySet%601> objekt. Pokud chcete povolit klientským počítačům provádět sadu související aktualizace, odstranění a vložení v rámci jednoho volání metody, je nutné zadat klienta způsob, jak určit, jaký typ operace se má provést u každé entity. Ve střední vrstvě, pak musíte volat odpovídající <xref:System.Data.Linq.ITable.Attach%2A> metodu a poté <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, nebo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, pro vložení) pro každou entitu před voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Nelze načíst data z databáze jako způsob, jak získat původní hodnoty, než se pokusíte aktualizace.  
  
 Další informace o optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Podrobné informace o řešení optimistického řízení souběžnosti změna je v konfliktu, najdete v článku [jak: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Následující příklady ukazují jednotlivých scénářů:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optimistického řízení souběžnosti ovládacím prvkem časová razítka  
  
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
 V takovém případě vrátí klientovi kompletní serializovaný objekt spolu s hodnotami, které má být upraven.  
  
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
  
 Chcete-li aktualizovat kolekci, zavolejte <xref:System.Data.Linq.ITable.AttachAll%2A> místo `Attach`.  
  
### <a name="expected-entity-members"></a>Členové očekávanou entitu  
 Jak bylo uvedeno dříve, jsou jen některé členy objektu entity musí být nastavena dříve než zavoláte `Attach` metody. Členové entit, které je potřeba nastavit musí splňovat následující kritéria:  
  
-   Být součástí identity subjektu.  
  
-   Očekávat, že se změnil.  
  
-   Časové razítko nebo má jeho <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atribut nastaven na něco kromě `Never`.  
  
 Pokud tabulka používá číslo verze nebo časové razítko pro kontrolu optimistického řízení souběžnosti, musíte nastavit tyto členy před voláním <xref:System.Data.Linq.ITable.Attach%2A>. Člen je vyhrazený pro optimistického řízení souběžnosti při kontrole <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je nastavena na hodnotu true u tohoto sloupce atributu. Všechny požadované aktualizace budou odeslány pouze v případě, že hodnoty, číslo nebo časového razítka verze jsou stejné pro databázi.  
  
 Člen se používá také v kontroly optimistického řízení souběžnosti, tak dlouho, dokud člen nemá <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> nastavena na `Never`. Výchozí hodnota je `Always` Pokud není zadána žádná hodnota.  
  
 V případě potřeby některou z těchto členů chybí, <xref:System.Data.Linq.ChangeConflictException> dojde během <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("řádek nebyl nalezen nebo změněn").  
  
### <a name="state"></a>Stav  
 Po entity je přiřazena objektu <xref:System.Data.Linq.DataContext> instance, objekt je považován za v `PossiblyModified` stavu. Existují tři způsoby, jak vynutit připojeného objektu považovat `Modified`.  
  
1.  Připojit jako nezměněný a přímo upravit pole.  
  
2.  Připojí se <xref:System.Data.Linq.Table%601.Attach%2A> přetížení přebírající aktuální a původní objekt instance. To poskytuje modul sledování změny pomocí staré a nové hodnoty tak, že bude automaticky znát, pole, která jste změnili.  
  
3.  Připojí se <xref:System.Data.Linq.Table%601.Attach%2A> přetížení přebírající druhý parametr logické hodnoty (nastavenou na hodnotu true). Se tak dozví, modul sledování změny, které byste měli zvážit objektu změnit, aniž by bylo nutné zadat všechny původní hodnoty. V takovém případě musí mít objekt pole verze/časové razítko.  
  
 Další informace najdete v tématu [stavy objektů a sledování změn](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Dojde-li objekt entity již v mezipaměti ID se stejnou identitou jako objekt připojovaný, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána výjimka.  
  
 Jestliže se pokusíte připojit s `IEnumerable` sadu objektů, <xref:System.Data.Linq.DuplicateKeyException> je vyvolána, když je k dispozici již existujícího klíče. Zbývající objekty nejsou připojeny.  
  
## <a name="see-also"></a>Viz také:

- [N-vrstvé a vzdálené aplikace s LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
