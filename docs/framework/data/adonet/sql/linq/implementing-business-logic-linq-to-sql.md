---
title: Implementace obchodní logiky (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 51b92549a40d0e5121cc390f5dbdf726cc06404b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174547"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementace obchodní logiky (LINQ to SQL)
Termín "obchodní logika" v tomto tématu odkazuje na všechna vlastní pravidla nebo ověřovací testy, které použijete na data před vložením, aktualizací nebo odstraněním z databáze. Obchodní logika se také někdy označuje jako "obchodní pravidla" nebo "logika domény". V n-vrstvých aplikacích je obvykle navržen jako logická vrstva tak, aby mohla být upravena nezávisle na prezentační vrstvě nebo vrstvě přístupu k datům. Obchodní logiku lze vyvolat vrstvou přístupu k datům před nebo po jakékoli aktualizaci, vložení nebo odstranění dat v databázi.  
  
 Obchodní logika může být stejně jednoduché jako ověření schématu a ujistěte se, že typ pole je kompatibilní s typem sloupce tabulky. Nebo se může skládat ze sady objektů, které interagují libovolně složitými způsoby. Pravidla mohou být implementována jako uložené procedury v databázi nebo jako objekty v paměti. Obchodní logika je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] však implementována, umožňuje použít částečné třídy a částečné metody oddělit obchodní logiku od kódu přístupu k datům.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak LINQ na SQL vyvolává obchodní logiku  
 Při generování třídy entity v době návrhu, ručně nebo pomocí objektu Relační designer nebo SQLMetal, je definovánjako částečná třída. To znamená, že v samostatném souboru kódu můžete definovat jinou část třídy entity, která obsahuje vlastní obchodní logiku. V době kompilace jsou obě části sloučeny do jedné třídy. Ale pokud máte znovu třídy entity pomocí objektu relační návrháře nebo SQLMetal, můžete tak učinit a vaše část třídy nebude změněna.  
  
 Částečné třídy, které definují <xref:System.Data.Linq.DataContext> entity a obsahují částečné metody. Jedná se o body rozšiřitelnosti, které můžete použít k použití obchodní logiky před a po jakékoli aktualizaci, vložení nebo odstranění pro entitu nebo vlastnost entity. Částečné metody si lze myslet jako události kompilace. Generátor kódu definuje podpis metody a volá metody v přístupové objekty `DataContext` get a set vlastnosti, konstruktor a v některých případech na pozadí, když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. Pokud však neimplementujete konkrétní částečnou metodu, budou všechny odkazy na ní a definice odebrány v době kompilace.  
  
 V implementaci definice, kterou napíšete do samostatného souboru kódu, můžete provést bez ohledu na vlastní logiku, která je požadována. Můžete použít částečné třídy sám jako vrstvu domény, nebo můžete volat z implementující definice částečné metody do samostatného objektu nebo objektů. Ať tak či onak, vaše obchodní logika je čistě oddělena od kódu přístupu k datům i od kódu prezentační vrstvy.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bližší pohled na body rozšiřitelnosti  
 Následující příklad ukazuje část kódu generovaného objektrelační návrhář pro `DataContext` `Customers` třídu, která má dvě tabulky: a `Orders`. Všimněte si, že insert, update a delete metody jsou definovány pro každou tabulku ve třídě.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Pokud implementujete insert, update a delete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] metody v částečné třídy, runtime <xref:System.Data.Linq.DataContext.SubmitChanges%2A> bude volat místo své vlastní výchozí metody, když je volána. To umožňuje přepsat výchozí chování pro operace vytváření / čtení / aktualizace / odstranění. Další informace naleznete [v tématu Návod: Přizpůsobení chování vložení, aktualizace a odstranění tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 Metoda `OnCreated` je volána v konstruktoru třídy.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 Třídy entit mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] za běhu při `SubmitChanges` vytvoření entity, načtení a ověření (při volání). Třídy entit mají také dvě částečné metody pro každou vlastnost, jednu, která je volána před nastavením vlastnosti a jedna volána po. Následující příklad kódu ukazuje některé metody generované `Customer` pro třídu:  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Metody jsou volány v přistupujícím objektu `CustomerID` sady vlastností, jak je znázorněno v následujícím příkladu vlastnosti:  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 Ve vaší části třídy napíšete implementační definici metody. V sadě Visual Studio `partial` se po zadání zobrazí technologie IntelliSense pro definice metod v druhé části třídy.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Další informace o tom, jak přidat obchodní logiku do aplikace pomocí částečných metod, naleznete v následujících tématech:  
  
 [Postupy: Přidání ověřování do tříd entit](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Návod: Přidání ověření do tříd entit](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Viz také

- [Částečné třídy a metody](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Částečné metody](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
