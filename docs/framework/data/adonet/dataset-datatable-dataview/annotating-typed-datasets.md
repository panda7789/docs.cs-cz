---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: df6da84dfc120e3f6c3cb0e46729ca2cecc9fe3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040403"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="b6b50-102">Zadávání poznámek k typovým datovým sadám</span><span class="sxs-lookup"><span data-stu-id="b6b50-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="b6b50-103">Poznámky umožňují upravit názvy prvků v zadaných <xref:System.Data.DataSet>ch bez změny podkladového schématu.</span><span class="sxs-lookup"><span data-stu-id="b6b50-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="b6b50-104">Změna názvů prvků v základním schématu způsobí, že zadaná **datová sada** odkazuje na objekty, které neexistují ve zdroji dat, a také ztratí odkaz na objekty, které existují ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="b6b50-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="b6b50-105">Pomocí poznámek můžete přizpůsobit názvy objektů v zadané **datové sadě** s smysluplnými názvy, což usnadňuje čtení kódu a zadaná **datová sada** je pro klienty snazší a přitom ponechá základní schéma beze změny.</span><span class="sxs-lookup"><span data-stu-id="b6b50-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="b6b50-106">Například následující prvek schématu pro tabulku **Customers** databáze **Northwind** má za následek název objektu **DataRow** **CustomersRow** a <xref:System.Data.DataRowCollection> s názvem **Customers**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="b6b50-107">**Kolekci DataRowCollection** jména **zákazníků** jsou v kódu klienta smysluplná, **ale název objektu** **CustomersRow** je zavádějící, protože se jedná o jediný objekt.</span><span class="sxs-lookup"><span data-stu-id="b6b50-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="b6b50-108">Také v běžných scénářích by se objekt odkazoval bez identifikátoru **řádku** a místo toho by se mu musel jednoduše odkazovat jako na objekt **zákazníka** .</span><span class="sxs-lookup"><span data-stu-id="b6b50-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="b6b50-109">Řešením je opatřit poznámkami od schématu a identifikovat nové názvy pro objekty **DataRow** a **kolekci DataRowCollection** .</span><span class="sxs-lookup"><span data-stu-id="b6b50-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="b6b50-110">Níže je uvedena verze předchozího schématu s poznámkou.</span><span class="sxs-lookup"><span data-stu-id="b6b50-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="b6b50-111">Zadání hodnoty **názvu** **zákazníka** bude mít za následek název objektu **DataRow** **zákazníka**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="b6b50-112">Zadáním hodnoty **TypedPlural** **zákazníkům** zachováte **kolekci DataRowCollection** jména **zákazníků**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="b6b50-113">V následující tabulce jsou uvedeny poznámky k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="b6b50-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="b6b50-114">Poznámka</span><span class="sxs-lookup"><span data-stu-id="b6b50-114">Annotation</span></span>|<span data-ttu-id="b6b50-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b6b50-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b6b50-116">**typ typu**</span><span class="sxs-lookup"><span data-stu-id="b6b50-116">**typedName**</span></span>|<span data-ttu-id="b6b50-117">Název objektu.</span><span class="sxs-lookup"><span data-stu-id="b6b50-117">Name of the object.</span></span>|  
|<span data-ttu-id="b6b50-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="b6b50-118">**typedPlural**</span></span>|<span data-ttu-id="b6b50-119">Název kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="b6b50-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="b6b50-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="b6b50-120">**typedParent**</span></span>|<span data-ttu-id="b6b50-121">Název objektu, který je odkazován v nadřazené relaci.</span><span class="sxs-lookup"><span data-stu-id="b6b50-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="b6b50-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="b6b50-122">**typedChildren**</span></span>|<span data-ttu-id="b6b50-123">Název metody pro vrácení objektů z podřízené relace.</span><span class="sxs-lookup"><span data-stu-id="b6b50-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="b6b50-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="b6b50-124">**nullValue**</span></span>|<span data-ttu-id="b6b50-125">Hodnota, pokud je podkladová hodnota **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="b6b50-126">Poznámky **NullValue** naleznete v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b6b50-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="b6b50-127">Výchozí hodnota je **_throw**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="b6b50-128">V následující tabulce jsou uvedeny hodnoty, které lze zadat pro **NullValue** anotaci.</span><span class="sxs-lookup"><span data-stu-id="b6b50-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="b6b50-129">Hodnota nullValue</span><span class="sxs-lookup"><span data-stu-id="b6b50-129">nullValue Value</span></span>|<span data-ttu-id="b6b50-130">Popis</span><span class="sxs-lookup"><span data-stu-id="b6b50-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="b6b50-131">*Nahrazující hodnota*</span><span class="sxs-lookup"><span data-stu-id="b6b50-131">*Replacement Value*</span></span>|<span data-ttu-id="b6b50-132">Zadejte hodnotu, která se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="b6b50-132">Specify a value to be returned.</span></span> <span data-ttu-id="b6b50-133">Vrácená hodnota musí odpovídat typu elementu.</span><span class="sxs-lookup"><span data-stu-id="b6b50-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="b6b50-134">Například použijte `nullValue="0"` k vrácení 0 pro pole s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b6b50-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="b6b50-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="b6b50-135">**_throw**</span></span>|<span data-ttu-id="b6b50-136">Vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="b6b50-136">Throw an exception.</span></span> <span data-ttu-id="b6b50-137">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b6b50-137">This is the default.</span></span>|  
|<span data-ttu-id="b6b50-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="b6b50-138">**_null**</span></span>|<span data-ttu-id="b6b50-139">Vrátí nulový odkaz nebo vyvolá výjimku, pokud se zjistil primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="b6b50-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="b6b50-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="b6b50-140">**_empty**</span></span>|<span data-ttu-id="b6b50-141">V případě řetězců vrátí **řetězec. Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b6b50-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="b6b50-142">Pokud je zjištěn primitivní typ, vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="b6b50-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="b6b50-143">V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v zadané **datové sadě** a poznámky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b6b50-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="b6b50-144">Objekt/metoda/událost</span><span class="sxs-lookup"><span data-stu-id="b6b50-144">Object/Method/Event</span></span>|<span data-ttu-id="b6b50-145">Výchozí</span><span class="sxs-lookup"><span data-stu-id="b6b50-145">Default</span></span>|<span data-ttu-id="b6b50-146">Poznámka</span><span class="sxs-lookup"><span data-stu-id="b6b50-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="b6b50-147">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b6b50-147">**DataTable**</span></span>|<span data-ttu-id="b6b50-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="b6b50-148">TableNameDataTable</span></span>|<span data-ttu-id="b6b50-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="b6b50-149">typedPlural</span></span>|  
|<span data-ttu-id="b6b50-150">**DataTable** Způsobů</span><span class="sxs-lookup"><span data-stu-id="b6b50-150">**DataTable** Methods</span></span>|<span data-ttu-id="b6b50-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6b50-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="b6b50-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6b50-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="b6b50-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6b50-153">DeleteTableNameRow</span></span>|<span data-ttu-id="b6b50-154">typ typu</span><span class="sxs-lookup"><span data-stu-id="b6b50-154">typedName</span></span>|  
|<span data-ttu-id="b6b50-155">**Kolekci DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="b6b50-155">**DataRowCollection**</span></span>|<span data-ttu-id="b6b50-156">Tabulky</span><span class="sxs-lookup"><span data-stu-id="b6b50-156">TableName</span></span>|<span data-ttu-id="b6b50-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="b6b50-157">typedPlural</span></span>|  
|<span data-ttu-id="b6b50-158">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b6b50-158">**DataRow**</span></span>|<span data-ttu-id="b6b50-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6b50-159">TableNameRow</span></span>|<span data-ttu-id="b6b50-160">typ typu</span><span class="sxs-lookup"><span data-stu-id="b6b50-160">typedName</span></span>|  
|<span data-ttu-id="b6b50-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="b6b50-161">**DataColumn**</span></span>|<span data-ttu-id="b6b50-162">DataTable. ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="b6b50-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="b6b50-163">DataRow. ColumnName</span><span class="sxs-lookup"><span data-stu-id="b6b50-163">DataRow.ColumnName</span></span>|<span data-ttu-id="b6b50-164">typ typu</span><span class="sxs-lookup"><span data-stu-id="b6b50-164">typedName</span></span>|  
|<span data-ttu-id="b6b50-165">**Majetek**</span><span class="sxs-lookup"><span data-stu-id="b6b50-165">**Property**</span></span>|<span data-ttu-id="b6b50-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="b6b50-166">PropertyName</span></span>|<span data-ttu-id="b6b50-167">typ typu</span><span class="sxs-lookup"><span data-stu-id="b6b50-167">typedName</span></span>|  
|<span data-ttu-id="b6b50-168">**Podřízená položka** Zbývá</span><span class="sxs-lookup"><span data-stu-id="b6b50-168">**Child** Accessor</span></span>|<span data-ttu-id="b6b50-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="b6b50-169">GetChildTableNameRows</span></span>|<span data-ttu-id="b6b50-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="b6b50-170">typedChildren</span></span>|  
|<span data-ttu-id="b6b50-171">**Nadřazený prvek** Zbývá</span><span class="sxs-lookup"><span data-stu-id="b6b50-171">**Parent** Accessor</span></span>|<span data-ttu-id="b6b50-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="b6b50-172">TableNameRow</span></span>|<span data-ttu-id="b6b50-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="b6b50-173">typedParent</span></span>|  
|<span data-ttu-id="b6b50-174">**Datová sada** Událost</span><span class="sxs-lookup"><span data-stu-id="b6b50-174">**DataSet** Events</span></span>|<span data-ttu-id="b6b50-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="b6b50-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="b6b50-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="b6b50-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="b6b50-177">typ typu</span><span class="sxs-lookup"><span data-stu-id="b6b50-177">typedName</span></span>|  
  
 <span data-ttu-id="b6b50-178">Chcete-li použít typové anotace **datové sady** , musíte zahrnout následující odkaz **xmlns** do schématu XML schématu definice jazyka (XSD).</span><span class="sxs-lookup"><span data-stu-id="b6b50-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="b6b50-179">Chcete-li vytvořit XSD z databázových tabulek, přečtěte si téma <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b6b50-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="b6b50-180">Následuje ukázka schématu s poznámkou, které zveřejňuje tabulku **Customers (zákazníci** ) databáze **Northwind** s relací k uvedené tabulce **Orders** .</span><span class="sxs-lookup"><span data-stu-id="b6b50-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="b6b50-181">Následující příklad kódu používá **datovou sadu** silného typu vytvořenou z ukázkového schématu.</span><span class="sxs-lookup"><span data-stu-id="b6b50-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="b6b50-182">K naplnění tabulky **Customers** používá jednu <xref:System.Data.SqlClient.SqlDataAdapter> a další <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění tabulky **Orders** .</span><span class="sxs-lookup"><span data-stu-id="b6b50-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="b6b50-183">**Datová sada** silného typu definuje **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="b6b50-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6b50-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6b50-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="b6b50-185">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="b6b50-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="b6b50-186">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b6b50-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b6b50-187">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6b50-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
