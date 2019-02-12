---
title: Provádění obchodní logiky (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 9ea8960b74cd44734eb68a07c6959727bf1ac797
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093967"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Provádění obchodní logiky (LINQ to SQL)
Termín "obchodní logiky" v tomto tématu se odkazuje na všechny vlastní pravidla nebo ověřovací testy, které můžete použít pro data předtím, než je vložena, aktualizována nebo odstraněna z databáze. Obchodní logiky se také někdy označuje jako "obchodní pravidla" nebo "logiku domény." V n vrstvá aplikace obvykle slouží jako logické vrstvy tak, aby jej můžete upravit nezávisle na prezentační vrstva a vrstva přístupu k datům. Obchodní logika může vyvolávat vrstvy přístupu k datům před nebo za všechny aktualizace, vložení nebo odstranění dat v databázi.  
  
 Obchodní logika může být stejně snadné jako ověřování schématu, abyste měli jistotu, že typ pole je kompatibilní s typem sloupce tabulky. Nebo může sestávat z několika objektů, které libovolně složité interagovali. Pravidla mohou být implementovány jako uložené procedury v databázi nebo objektů v paměti. Nicméně se implementuje obchodní logiku, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje použít částečné třídy a částečné metody k oddělení obchodní logiku z kód přístupu k datům.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak vyvolá obchodní logiku v LINQ to SQL  
 Když vygenerujete třídu entity v době návrhu ručně nebo pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, je definován jako částečné třídy. To znamená, že v samostatném souboru kódu, můžete definovat jiné části třídy entity, která obsahuje vaše vlastní obchodní logiky. V době kompilace jsou dvě části sloučeny do jediné třídy. Ale pokud máte k opětovnému vytvoření tříd entit pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, můžete tak učinit a vaše část třídy se nezmění.  
  
 Částečné třídy, které definují entity a <xref:System.Data.Linq.DataContext> obsahovat částečné metody. Toto jsou body rozšiřitelnosti, které vám umožní použít obchodní logiku, před a za jakékoli update, insert nebo delete pro entity nebo vlastnosti entity. Částečné metody můžete představit jako události za kompilace. Generátor kódu definuje podpis metody a volání metody get a nastavte přistupující objekty vlastnosti `DataContext` konstruktoru a v některých případech na pozadí při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. Ale pokud nejsou implementovat konkrétní částečnou metodu, pak všechny odkazy a definice se odeberou v době kompilace.  
  
 V implementaci definici, který píšete v souboru samostatného kódu můžete provést vyžádáním libovolnou vlastní logiku. Samotný dílčí třídu můžete použít jako vrstva vaší domény, nebo můžete volat z implementující definice částečné metody do samostatného objekt nebo objekty. V obou případech obchodní logiky je čistě oddělená od data přístupový kód a kód prezentační vrstvy.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bližší pohled na body rozšiřitelnosti  
 Následující příklad ukazuje část kód vygenerovaný [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro `DataContext` třídu, která má dvě tabulky: `Customers` a `Orders`. Všimněte si, že Insert, Update a Delete metody jsou definovány pro každou tabulku ve třídě.  
  
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
  
 Pokud se rozhodnete implementovat vložit, aktualizovat a odstraňovat metody v dílčí třídě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modul runtime bude volat bez vlastní výchozí metody při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána. To umožňuje potlačit výchozí chování pro vytvoření / číst / aktualizovat / odstranit operace. Další informace najdete v tématu [názorný postup: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
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
  
 Entity třídy mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modulu runtime, když je entita vytvoří, načten a ověřen (při `SubmitChanges` nazývá). Entity třídy také mají dvě částečné metody pro každou vlastnost, jednu, která je volána před je vlastnost nastavena a jednu, která je volána pro provedení. Následující příklad kódu ukazuje některé metody pro vygenerovat `Customer` třídy:  
  
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
  
 Metody jsou volány v přistupující objekt množiny vlastností, jak je znázorněno v následujícím příkladu `CustomerID` vlastnost:  
  
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
  
 Ve vaší části třídy napíšete implementující definice metody. V sadě Visual Studio, po zadání `partial` uvidíte technologie IntelliSense pro definice metod v další části třídy.  
  
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
  
 Další informace o tom, jak přidat obchodní logiky pomocí částečných metod do vaší aplikace naleznete v následujících tématech:  
  
 [Postupy: Přidání ověřování do tříd entit](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Návod: Přidání ověřování do tříd entit](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Viz také:
- [Částečné třídy a metody](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Částečné metody](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
