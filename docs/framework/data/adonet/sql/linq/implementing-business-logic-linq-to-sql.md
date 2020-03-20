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
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="66ccd-102">Implementace obchodní logiky (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="66ccd-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="66ccd-103">Termín "obchodní logika" v tomto tématu odkazuje na všechna vlastní pravidla nebo ověřovací testy, které použijete na data před vložením, aktualizací nebo odstraněním z databáze.</span><span class="sxs-lookup"><span data-stu-id="66ccd-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="66ccd-104">Obchodní logika se také někdy označuje jako "obchodní pravidla" nebo "logika domény".</span><span class="sxs-lookup"><span data-stu-id="66ccd-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="66ccd-105">V n-vrstvých aplikacích je obvykle navržen jako logická vrstva tak, aby mohla být upravena nezávisle na prezentační vrstvě nebo vrstvě přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="66ccd-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="66ccd-106">Obchodní logiku lze vyvolat vrstvou přístupu k datům před nebo po jakékoli aktualizaci, vložení nebo odstranění dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="66ccd-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="66ccd-107">Obchodní logika může být stejně jednoduché jako ověření schématu a ujistěte se, že typ pole je kompatibilní s typem sloupce tabulky.</span><span class="sxs-lookup"><span data-stu-id="66ccd-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="66ccd-108">Nebo se může skládat ze sady objektů, které interagují libovolně složitými způsoby.</span><span class="sxs-lookup"><span data-stu-id="66ccd-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="66ccd-109">Pravidla mohou být implementována jako uložené procedury v databázi nebo jako objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="66ccd-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="66ccd-110">Obchodní logika je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] však implementována, umožňuje použít částečné třídy a částečné metody oddělit obchodní logiku od kódu přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="66ccd-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="66ccd-111">Jak LINQ na SQL vyvolává obchodní logiku</span><span class="sxs-lookup"><span data-stu-id="66ccd-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="66ccd-112">Při generování třídy entity v době návrhu, ručně nebo pomocí objektu Relační designer nebo SQLMetal, je definovánjako částečná třída.</span><span class="sxs-lookup"><span data-stu-id="66ccd-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="66ccd-113">To znamená, že v samostatném souboru kódu můžete definovat jinou část třídy entity, která obsahuje vlastní obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="66ccd-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="66ccd-114">V době kompilace jsou obě části sloučeny do jedné třídy.</span><span class="sxs-lookup"><span data-stu-id="66ccd-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="66ccd-115">Ale pokud máte znovu třídy entity pomocí objektu relační návrháře nebo SQLMetal, můžete tak učinit a vaše část třídy nebude změněna.</span><span class="sxs-lookup"><span data-stu-id="66ccd-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="66ccd-116">Částečné třídy, které definují <xref:System.Data.Linq.DataContext> entity a obsahují částečné metody.</span><span class="sxs-lookup"><span data-stu-id="66ccd-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="66ccd-117">Jedná se o body rozšiřitelnosti, které můžete použít k použití obchodní logiky před a po jakékoli aktualizaci, vložení nebo odstranění pro entitu nebo vlastnost entity.</span><span class="sxs-lookup"><span data-stu-id="66ccd-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="66ccd-118">Částečné metody si lze myslet jako události kompilace.</span><span class="sxs-lookup"><span data-stu-id="66ccd-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="66ccd-119">Generátor kódu definuje podpis metody a volá metody v přístupové objekty `DataContext` get a set vlastnosti, konstruktor a v některých případech na pozadí, když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="66ccd-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="66ccd-120">Pokud však neimplementujete konkrétní částečnou metodu, budou všechny odkazy na ní a definice odebrány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="66ccd-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="66ccd-121">V implementaci definice, kterou napíšete do samostatného souboru kódu, můžete provést bez ohledu na vlastní logiku, která je požadována.</span><span class="sxs-lookup"><span data-stu-id="66ccd-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="66ccd-122">Můžete použít částečné třídy sám jako vrstvu domény, nebo můžete volat z implementující definice částečné metody do samostatného objektu nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="66ccd-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="66ccd-123">Ať tak či onak, vaše obchodní logika je čistě oddělena od kódu přístupu k datům i od kódu prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="66ccd-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="66ccd-124">Bližší pohled na body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="66ccd-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="66ccd-125">Následující příklad ukazuje část kódu generovaného objektrelační návrhář pro `DataContext` `Customers` třídu, která má dvě tabulky: a `Orders`.</span><span class="sxs-lookup"><span data-stu-id="66ccd-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="66ccd-126">Všimněte si, že insert, update a delete metody jsou definovány pro každou tabulku ve třídě.</span><span class="sxs-lookup"><span data-stu-id="66ccd-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="66ccd-127">Pokud implementujete insert, update a delete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] metody v částečné třídy, runtime <xref:System.Data.Linq.DataContext.SubmitChanges%2A> bude volat místo své vlastní výchozí metody, když je volána.</span><span class="sxs-lookup"><span data-stu-id="66ccd-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="66ccd-128">To umožňuje přepsat výchozí chování pro operace vytváření / čtení / aktualizace / odstranění.</span><span class="sxs-lookup"><span data-stu-id="66ccd-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="66ccd-129">Další informace naleznete [v tématu Návod: Přizpůsobení chování vložení, aktualizace a odstranění tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="66ccd-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="66ccd-130">Metoda `OnCreated` je volána v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="66ccd-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="66ccd-131">Třídy entit mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] za běhu při `SubmitChanges` vytvoření entity, načtení a ověření (při volání).</span><span class="sxs-lookup"><span data-stu-id="66ccd-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="66ccd-132">Třídy entit mají také dvě částečné metody pro každou vlastnost, jednu, která je volána před nastavením vlastnosti a jedna volána po.</span><span class="sxs-lookup"><span data-stu-id="66ccd-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="66ccd-133">Následující příklad kódu ukazuje některé metody generované `Customer` pro třídu:</span><span class="sxs-lookup"><span data-stu-id="66ccd-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="66ccd-134">Metody jsou volány v přistupujícím objektu `CustomerID` sady vlastností, jak je znázorněno v následujícím příkladu vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="66ccd-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="66ccd-135">Ve vaší části třídy napíšete implementační definici metody.</span><span class="sxs-lookup"><span data-stu-id="66ccd-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="66ccd-136">V sadě Visual Studio `partial` se po zadání zobrazí technologie IntelliSense pro definice metod v druhé části třídy.</span><span class="sxs-lookup"><span data-stu-id="66ccd-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="66ccd-137">Další informace o tom, jak přidat obchodní logiku do aplikace pomocí částečných metod, naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="66ccd-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="66ccd-138">Postupy: Přidání ověřování do tříd entit</span><span class="sxs-lookup"><span data-stu-id="66ccd-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="66ccd-139">Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění</span><span class="sxs-lookup"><span data-stu-id="66ccd-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="66ccd-140">[Návod: Přidání ověření do tříd entit](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="66ccd-140">[Walkthrough: Adding Validation to Entity Classes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ccd-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="66ccd-141">See also</span></span>

- [<span data-ttu-id="66ccd-142">Částečné třídy a metody</span><span class="sxs-lookup"><span data-stu-id="66ccd-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="66ccd-143">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="66ccd-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="66ccd-144">Nástroje LINQ to SQL v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66ccd-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="66ccd-145">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="66ccd-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
