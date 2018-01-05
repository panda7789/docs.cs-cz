---
title: "Implementace obchodní logiky (technologie LINQ to SQL)"
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
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cfdcec277489d269b241b9909a2ae13049c00f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="5ab55-102">Implementace obchodní logiky (technologie LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="5ab55-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="5ab55-103">Termín "obchodní logiky" v tomto tématu vztahuje na všechny vlastní pravidla nebo ověřovací testy, které použijete pro data, než je vložit, aktualizovat nebo odstranit z databáze.</span><span class="sxs-lookup"><span data-stu-id="5ab55-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="5ab55-104">Obchodní logika se také někdy označuje jako "obchodní pravidla" nebo "logiku domény."</span><span class="sxs-lookup"><span data-stu-id="5ab55-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="5ab55-105">Ve vícevrstvé aplikace je obvykle určený jako logické vrstvu tak, aby ho můžete upravit nezávisle na prezentační vrstvy nebo vrstva přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="5ab55-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="5ab55-106">Datová vrstva přístupu může vyvolat obchodní logiky před nebo za všechny aktualizace, vložení nebo odstranění dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="5ab55-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="5ab55-107">Obchodní logiky může být jednoduché, schématu ověření a ujistěte se, že typ pole je kompatibilní s typem sloupce tabulky.</span><span class="sxs-lookup"><span data-stu-id="5ab55-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="5ab55-108">Nebo může sestávat ze sadu objektů, které pracují libovolně komplexní způsoby.</span><span class="sxs-lookup"><span data-stu-id="5ab55-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="5ab55-109">Pravidla mohou být prováděny jako uložené procedury v databázi, nebo jako objekty v paměti.</span><span class="sxs-lookup"><span data-stu-id="5ab55-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="5ab55-110">Ale se implementuje obchodní logiku, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňuje použít částečné třídy a metody částečné jednotlivé obchodní logiku z dat přístupový kód.</span><span class="sxs-lookup"><span data-stu-id="5ab55-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="5ab55-111">Jak technologie LINQ to SQL vyvolá obchodní logiky</span><span class="sxs-lookup"><span data-stu-id="5ab55-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="5ab55-112">Když generujete třídu entity v době návrhu, buď ručně, nebo pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, je definována jako konkrétní třídu.</span><span class="sxs-lookup"><span data-stu-id="5ab55-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="5ab55-113">To znamená, že v samostatném souboru kódu, můžete definovat jinou součástí třídu entity, která obsahuje vaše vlastní obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="5ab55-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="5ab55-114">Při kompilaci dvě části sloučeny do jediné třídy.</span><span class="sxs-lookup"><span data-stu-id="5ab55-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="5ab55-115">Ale pokud máte k opětovnému vytvoření třídy entity pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo SQLMetal, můžete tak učinit a vaše součástí třídy se nezmění.</span><span class="sxs-lookup"><span data-stu-id="5ab55-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="5ab55-116">Částečné třídy, které definují entity a <xref:System.Data.Linq.DataContext> obsahovat částečné metody.</span><span class="sxs-lookup"><span data-stu-id="5ab55-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="5ab55-117">Toto jsou body rozšiřitelnosti, které můžete použít obchodní logiku před a za jakékoli update, insert nebo delete pro entitu nebo vlastnost entity.</span><span class="sxs-lookup"><span data-stu-id="5ab55-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="5ab55-118">Částečné metody lze považovat za kompilace události.</span><span class="sxs-lookup"><span data-stu-id="5ab55-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="5ab55-119">Generátor kódu definuje podpis metody a zavolá metodu get a nastavte vlastnosti přistupující objekty, `DataContext` konstruktoru a v některých případech na pozadí při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="5ab55-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="5ab55-120">Pokud však není implementovat určité částečné metodu, pak všechny odkazy na jeho a definice jsou odebrána v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5ab55-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="5ab55-121">V definici implementující, který zápisu v souboru samostatné kódu můžete provést, ať vlastní logiky se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="5ab55-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="5ab55-122">Vaše vlastní třídy částečné můžete použít jako vrstva vaší domény, nebo můžete volat z implementující definice částečné metody do samostatný objekt nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="5ab55-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="5ab55-123">V obou případech obchodní logiky je řádně oddělená od data přístupový kód a kód prezentační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="5ab55-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="5ab55-124">Bližší pohled na body rozšiřitelnosti</span><span class="sxs-lookup"><span data-stu-id="5ab55-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="5ab55-125">Následující příklad ukazuje součástí kód vygenerovaný [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro `DataContext` třídu, která má dvě tabulky: `Customers` a `Orders`.</span><span class="sxs-lookup"><span data-stu-id="5ab55-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="5ab55-126">Všimněte si, že Insert, Update a odstranit metody jsou definovány pro každou tabulku v třídě.</span><span class="sxs-lookup"><span data-stu-id="5ab55-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="5ab55-127">Pokud budete implementovat úlohy Insert, Update a Delete metody ve třídě částečné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime bude volat místo vlastní výchozí metody při <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="5ab55-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="5ab55-128">To umožňuje přepsat výchozí chování při vytváření / číst / aktualizovat / odstranit operace.</span><span class="sxs-lookup"><span data-stu-id="5ab55-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="5ab55-129">Další informace najdete v tématu [návod: přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="5ab55-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="5ab55-130">`OnCreated` Metoda je volána v konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="5ab55-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="5ab55-131">Entity třídy mají tři metody, které jsou volány [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime při vytvoření, načíst a ověřit entity (když `SubmitChanges` nazývá).</span><span class="sxs-lookup"><span data-stu-id="5ab55-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="5ab55-132">Třídy entity mít také dva částečné metody pro každou vlastnost, jednu, která je volána, než je vlastnost nastavena a jeden, která je volána po.</span><span class="sxs-lookup"><span data-stu-id="5ab55-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="5ab55-133">Následující příklad kódu ukazuje některé metody vygenerované `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="5ab55-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="5ab55-134">Metody jsou volány v přistupující objekt set vlastnosti, jak je znázorněno v následujícím příkladu `CustomerID` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="5ab55-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="5ab55-135">Ve vašem součástí třídy zápisu definici implementuje metody.</span><span class="sxs-lookup"><span data-stu-id="5ab55-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="5ab55-136">V [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], zadejte po `partial` uvidíte IntelliSense pro definice metoda v další části třídy.</span><span class="sxs-lookup"><span data-stu-id="5ab55-136">In [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="5ab55-137">Další informace o tom, jak přidat obchodní logiku do vaší aplikace pomocí částečné metody najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="5ab55-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="5ab55-138">Postupy: přidávání ověření do tříd entit</span><span class="sxs-lookup"><span data-stu-id="5ab55-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="5ab55-139">Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit</span><span class="sxs-lookup"><span data-stu-id="5ab55-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="5ab55-140">Návod: Přidávání ověření do tříd entit</span><span class="sxs-lookup"><span data-stu-id="5ab55-140">Walkthrough: Adding Validation to Entity Classes</span></span>](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a><span data-ttu-id="5ab55-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ab55-141">See Also</span></span>  
 [<span data-ttu-id="5ab55-142">Částečné třídy a metody</span><span class="sxs-lookup"><span data-stu-id="5ab55-142">Partial Classes and Methods</span></span>](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [<span data-ttu-id="5ab55-143">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="5ab55-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [<span data-ttu-id="5ab55-144">Technologie LINQ to SQL nástroje v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5ab55-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [<span data-ttu-id="5ab55-145">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="5ab55-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
