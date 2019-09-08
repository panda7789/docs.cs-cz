---
title: Implementace obchodní logiky (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 5261aab1ef6641651f856b8ebb024f64ad32ee59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781438"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementace obchodní logiky (LINQ to SQL)
Termín "obchodní logika" v tomto tématu se týká libovolných vlastních pravidel nebo ověřovacích testů, které se použijí na data před jejich vložením, aktualizací a odstraněním z databáze. Obchodní logika se také někdy označuje jako "obchodní pravidla" nebo "logika domény". V n-vrstvých aplikacích je obvykle navržen jako logická vrstva, aby ji bylo možné upravovat nezávisle na prezentační vrstvě nebo vrstvě přístupu k datům. Obchodní logiku může vyvolávat vrstva přístupu k datům před nebo po jakékoli aktualizaci, vložení nebo odstranění dat v databázi.  
  
 Obchodní logika může být jednoduché jako ověřování schématu, aby bylo zajištěno, že typ pole je kompatibilní s typem sloupce tabulky. Nebo se může skládat ze sady objektů, které pracují v libovolně složitých způsobech. Pravidla mohou být implementována jako uložené procedury v databázi nebo jako objekty v paměti. Obchodní logika je však implementována, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje používat částečné třídy a částečné metody k oddělení obchodní logiky z kódu přístupu k datům.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak LINQ to SQL vyvolá vaši obchodní logiku  
 Při generování třídy entity v době návrhu, buď ručně nebo pomocí Návrhář relací objektů nebo SQLMetal, je definována jako částečná třída. To znamená, že v samostatném souboru kódu můžete definovat další část třídy entity, která obsahuje vlastní obchodní logiku. V době kompilace jsou dvě části sloučeny do jedné třídy. Pokud ale potřebujete třídy entit znovu vygenerovat pomocí Návrhář relací objektů nebo SQLMetal, můžete tak učinit a vaše část třídy se neupraví.  
  
 Částečné třídy, které definují entity a <xref:System.Data.Linq.DataContext> obsahují částečné metody. Jedná se o body rozšiřitelnosti, které můžete použít k aplikování obchodní logiky před a po jakékoli aktualizaci, vložení nebo odstranění vlastnosti entity nebo entity. Částečné metody lze představit jako události při kompilaci. Generátor kódu definuje signaturu metody a volá metody v přístupových objektech vlastnosti get a set, `DataContext` konstruktor a v některých případech na pozadí při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání. Pokud však neimplementujete určitou částečnou metodu, jsou všechny odkazy na ni a definice odebrány v době kompilace.  
  
 V implementaci definice, kterou zapisujete do samostatného souboru kódu, můžete provádět libovolné vlastní logiky. Můžete použít svou částečnou třídu jako vrstvu vaší domény nebo můžete volat z implementace částečné metody do samostatného objektu nebo objektů. V obou případech je vaše obchodní logika čistě oddělená od kódu pro přístup k datům a kódu prezentační vrstvy.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bližší pohled na body rozšiřitelnosti  
 Následující příklad ukazuje část kódu vygenerovaného Návrhář relací objektů pro `DataContext` třídu, která má dvě tabulky: `Customers` a `Orders`. Všimněte si, že metody Insert, Update a DELETE jsou definovány pro každou tabulku ve třídě.  
  
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
  
 Pokud implementujete metody Insert, Update a DELETE v dílčí třídě, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modul runtime je zavolá namísto vlastních výchozích metod, pokud <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána metoda. To vám umožní přepsat výchozí chování pro operace vytvoření, čtení, aktualizace a odstranění. Další informace najdete v tématu [Návod: Přizpůsobení chování funkce INSERT, Update a DELETE u tříd](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)entit.  
  
 `OnCreated` Metoda je volána v konstruktoru třídy.  
  
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
  
 Třídy entit mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modulem runtime při vytvoření, načtení a ověření entity (když `SubmitChanges` je volána). Třídy entit mají také dvě částečné metody pro každou vlastnost, jednu, která je volána před nastavením vlastnosti, a jednu, která je volána po. Následující příklad kódu ukazuje některé z metod vygenerovaných pro `Customer` třídu:  
  
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
  
 Metody jsou volány v přístupovém objektu sady vlastností, jak je znázorněno v následujícím `CustomerID` příkladu pro vlastnost:  
  
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
  
 V rámci třídy napíšete implementující definici metody. V aplikaci Visual Studio se po zadání `partial` zobrazí technologie IntelliSense pro definice metod v jiné části třídy.  
  
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
  
 [Návod: Přidání ověřování do tříd entit](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Viz také:

- [Částečné třídy a metody](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Částečné metody](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
