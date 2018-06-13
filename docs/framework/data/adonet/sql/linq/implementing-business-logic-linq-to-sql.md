---
title: Implementace obchodní logiky (technologie LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 6216a3d6dd21f1dcb3348565a9f1870be7c7905a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362048"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementace obchodní logiky (technologie LINQ to SQL)
Termín "obchodní logiky" v tomto tématu vztahuje na všechny vlastní pravidla nebo ověřovací testy, které použijete pro data, než je vložit, aktualizovat nebo odstranit z databáze. Obchodní logika se také někdy označuje jako "obchodní pravidla" nebo "logiku domény." Ve vícevrstvé aplikace je obvykle určený jako logické vrstvu tak, aby ho můžete upravit nezávisle na prezentační vrstvy nebo vrstva přístupu k datům. Datová vrstva přístupu může vyvolat obchodní logiky před nebo za všechny aktualizace, vložení nebo odstranění dat v databázi.  
  
 Obchodní logiky může být jednoduché, schématu ověření a ujistěte se, že typ pole je kompatibilní s typem sloupce tabulky. Nebo může sestávat ze sadu objektů, které pracují libovolně komplexní způsoby. Pravidla mohou být prováděny jako uložené procedury v databázi, nebo jako objekty v paměti. Ale se implementuje obchodní logiku, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje použít částečné třídy a metody částečné jednotlivé obchodní logiku z dat přístupový kód.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak technologie LINQ to SQL vyvolá obchodní logiky  
 Když generujete třídu entity v době návrhu, buď ručně, nebo pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, je definována jako konkrétní třídu. To znamená, že v samostatném souboru kódu, můžete definovat jinou součástí třídu entity, která obsahuje vaše vlastní obchodní logiku. Při kompilaci dvě části sloučeny do jediné třídy. Ale pokud máte k opětovnému vytvoření třídy entity pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, můžete tak učinit a vaše součástí třídy se nezmění.  
  
 Částečné třídy, které definují entity a <xref:System.Data.Linq.DataContext> obsahovat částečné metody. Toto jsou body rozšiřitelnosti, které můžete použít obchodní logiku před a za jakékoli update, insert nebo delete pro entitu nebo vlastnost entity. Částečné metody lze považovat za kompilace události. Generátor kódu definuje podpis metody a zavolá metodu get a nastavte vlastnosti přistupující objekty, `DataContext` konstruktoru a v některých případech na pozadí při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. Pokud však není implementovat určité částečné metodu, pak všechny odkazy na jeho a definice jsou odebrána v době kompilace.  
  
 V definici implementující, který zápisu v souboru samostatné kódu můžete provést, ať vlastní logiky se vyžaduje. Vaše vlastní třídy částečné můžete použít jako vrstva vaší domény, nebo můžete volat z implementující definice částečné metody do samostatný objekt nebo objekty. V obou případech obchodní logiky je řádně oddělená od data přístupový kód a kód prezentační vrstvy.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bližší pohled na body rozšiřitelnosti  
 Následující příklad ukazuje součástí kód vygenerovaný [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro `DataContext` třídu, která má dvě tabulky: `Customers` a `Orders`. Všimněte si, že Insert, Update a odstranit metody jsou definovány pro každou tabulku v třídě.  
  
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
  
 Pokud budete implementovat úlohy Insert, Update a Delete metody ve třídě částečné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime bude volat místo vlastní výchozí metody při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. To umožňuje přepsat výchozí chování při vytváření / číst / aktualizovat / odstranit operace. Další informace najdete v tématu [návod: přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
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
  
 Entity třídy mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime při vytvoření, načíst a ověřit entity (když `SubmitChanges` nazývá). Třídy entity mít také dva částečné metody pro každou vlastnost, jednu, která je volána, než je vlastnost nastavena a jeden, která je volána po. Následující příklad kódu ukazuje některé metody vygenerované `Customer` třídy:  
  
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
  
 Metody jsou volány v přistupující objekt set vlastnosti, jak je znázorněno v následujícím příkladu `CustomerID` vlastnost:  
  
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
  
 Ve vašem součástí třídy zápisu definici implementuje metody. V sadě Visual Studio, zadejte po `partial` uvidíte IntelliSense pro definice metoda v další části třídy.  
  
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
  
 Další informace o tom, jak přidat obchodní logiku do vaší aplikace pomocí částečné metody najdete v následujících tématech:  
  
 [Postupy: přidávání ověření do tříd entit](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Návod: Přidávání ověření do tříd entit](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>Viz také  
 [Částečné třídy a metody](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [Částečné metody](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [Technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
