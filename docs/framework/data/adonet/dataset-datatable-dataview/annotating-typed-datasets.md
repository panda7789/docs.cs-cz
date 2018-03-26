---
title: Zadávání poznámek k typové datové sady
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: cc09f3f9b43b70b7f9b302d7a9d75428b5a0e6c7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="62d90-102">Zadávání poznámek k typové datové sady</span><span class="sxs-lookup"><span data-stu-id="62d90-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="62d90-103">Poznámky umožňují změnit názvy elementů v váš zadaný <xref:System.Data.DataSet> beze změny základní schéma.</span><span class="sxs-lookup"><span data-stu-id="62d90-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="62d90-104">Úprava názvy elementů v základní schéma by způsobilo zadaného objektu **datovou sadu** k odkazování na objekty, které není neexistuje ve zdroji dat, a také dojít ke ztrátě odkaz na objekty, které existují v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="62d90-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="62d90-105">Použití poznámek, můžete přizpůsobit názvy objektů v váš zadaný **datovou sadu** smysluplnější názvy, provedení čtení kódu a váš zadaný **datovou sadu** usnadňuje klientům používat, a nechat základní schématu beze změn.</span><span class="sxs-lookup"><span data-stu-id="62d90-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="62d90-106">Například následující element schématu pro **zákazníci** tabulky **Northwind** by způsobilo databáze **DataRow** název objektu  **CustomersRow** a <xref:System.Data.DataRowCollection> s názvem **zákazníci**.</span><span class="sxs-lookup"><span data-stu-id="62d90-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="62d90-107">A **kolekci DataRowCollection** název **zákazníci** má smysl v kódu klienta, ale **DataRow** název **CustomersRow** je zavádějící protože je jediný objekt.</span><span class="sxs-lookup"><span data-stu-id="62d90-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="62d90-108">Společné scénáře, objekt by se označovat taky bez **řádek** identifikátor a místo toho by se jednoduše označovat jako **zákazníka** objektu.</span><span class="sxs-lookup"><span data-stu-id="62d90-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="62d90-109">Řešení, je přidání poznámek ke schématu a identifikovat nové názvy pro **DataRow** a **kolekci DataRowCollection** objekty.</span><span class="sxs-lookup"><span data-stu-id="62d90-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="62d90-110">Toto je poznámkami verze předchozí schématu.</span><span class="sxs-lookup"><span data-stu-id="62d90-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="62d90-111">Určení **TypedName služby Active Directory** hodnotu **zákazníka** bude mít za následek **DataRow** název objektu **zákazníka**.</span><span class="sxs-lookup"><span data-stu-id="62d90-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="62d90-112">Určení **typedPlural** hodnotu **zákazníci** zachovává **kolekci DataRowCollection** název **zákazníci**.</span><span class="sxs-lookup"><span data-stu-id="62d90-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="62d90-113">V následující tabulce jsou k dispozici pro použití poznámky.</span><span class="sxs-lookup"><span data-stu-id="62d90-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="62d90-114">Poznámka</span><span class="sxs-lookup"><span data-stu-id="62d90-114">Annotation</span></span>|<span data-ttu-id="62d90-115">Popis</span><span class="sxs-lookup"><span data-stu-id="62d90-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="62d90-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="62d90-116">**typedName**</span></span>|<span data-ttu-id="62d90-117">Název objektu.</span><span class="sxs-lookup"><span data-stu-id="62d90-117">Name of the object.</span></span>|  
|<span data-ttu-id="62d90-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="62d90-118">**typedPlural**</span></span>|<span data-ttu-id="62d90-119">Název kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="62d90-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="62d90-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="62d90-120">**typedParent**</span></span>|<span data-ttu-id="62d90-121">Název objektu při uvedených v nadřazené vztahy.</span><span class="sxs-lookup"><span data-stu-id="62d90-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="62d90-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="62d90-122">**typedChildren**</span></span>|<span data-ttu-id="62d90-123">Název metody, které mají být vráceny od vztahu podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="62d90-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="62d90-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="62d90-124">**nullValue**</span></span>|<span data-ttu-id="62d90-125">Hodnotu, pokud je zadaná hodnota **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="62d90-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="62d90-126">V následující tabulce najdete **nullValue** poznámky.</span><span class="sxs-lookup"><span data-stu-id="62d90-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="62d90-127">Výchozí hodnota je **_throw**.</span><span class="sxs-lookup"><span data-stu-id="62d90-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="62d90-128">V následující tabulce jsou uvedeny hodnoty, které lze zadat pro **nullValue** poznámky.</span><span class="sxs-lookup"><span data-stu-id="62d90-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="62d90-129">nullValue hodnota</span><span class="sxs-lookup"><span data-stu-id="62d90-129">nullValue Value</span></span>|<span data-ttu-id="62d90-130">Popis</span><span class="sxs-lookup"><span data-stu-id="62d90-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="62d90-131">*Nahrazující hodnotou*</span><span class="sxs-lookup"><span data-stu-id="62d90-131">*Replacement Value*</span></span>|<span data-ttu-id="62d90-132">Zadejte hodnotu, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="62d90-132">Specify a value to be returned.</span></span> <span data-ttu-id="62d90-133">Vrácená hodnota se musí shodovat s typem elementu.</span><span class="sxs-lookup"><span data-stu-id="62d90-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="62d90-134">Například použít `nullValue="0"` vrátit 0 pro pole hodnotu null celé číslo.</span><span class="sxs-lookup"><span data-stu-id="62d90-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="62d90-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="62d90-135">**_throw**</span></span>|<span data-ttu-id="62d90-136">Vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="62d90-136">Throw an exception.</span></span> <span data-ttu-id="62d90-137">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="62d90-137">This is the default.</span></span>|  
|<span data-ttu-id="62d90-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="62d90-138">**_null**</span></span>|<span data-ttu-id="62d90-139">Vrátí hodnotu null nebo vyvolána výjimka, pokud je zjištěn primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="62d90-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="62d90-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="62d90-140">**_empty**</span></span>|<span data-ttu-id="62d90-141">Řetězce, vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="62d90-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="62d90-142">Jestliže je primitivní typ, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="62d90-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="62d90-143">Následující tabulka uvádí výchozí hodnoty pro objekty v zadaný **datovou sadu** a poznámky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="62d90-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="62d90-144">Objekt nebo metoda/událost</span><span class="sxs-lookup"><span data-stu-id="62d90-144">Object/Method/Event</span></span>|<span data-ttu-id="62d90-145">Výchozí</span><span class="sxs-lookup"><span data-stu-id="62d90-145">Default</span></span>|<span data-ttu-id="62d90-146">Poznámka</span><span class="sxs-lookup"><span data-stu-id="62d90-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="62d90-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="62d90-147">**DataTable**</span></span>|<span data-ttu-id="62d90-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="62d90-148">TableNameDataTable</span></span>|<span data-ttu-id="62d90-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="62d90-149">typedPlural</span></span>|  
|<span data-ttu-id="62d90-150">**DataTable** metody</span><span class="sxs-lookup"><span data-stu-id="62d90-150">**DataTable** Methods</span></span>|<span data-ttu-id="62d90-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="62d90-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="62d90-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="62d90-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="62d90-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="62d90-153">DeleteTableNameRow</span></span>|<span data-ttu-id="62d90-154">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="62d90-154">typedName</span></span>|  
|<span data-ttu-id="62d90-155">**Kolekci DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="62d90-155">**DataRowCollection**</span></span>|<span data-ttu-id="62d90-156">TableName</span><span class="sxs-lookup"><span data-stu-id="62d90-156">TableName</span></span>|<span data-ttu-id="62d90-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="62d90-157">typedPlural</span></span>|  
|<span data-ttu-id="62d90-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="62d90-158">**DataRow**</span></span>|<span data-ttu-id="62d90-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="62d90-159">TableNameRow</span></span>|<span data-ttu-id="62d90-160">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="62d90-160">typedName</span></span>|  
|<span data-ttu-id="62d90-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="62d90-161">**DataColumn**</span></span>|<span data-ttu-id="62d90-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="62d90-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="62d90-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="62d90-163">DataRow.ColumnName</span></span>|<span data-ttu-id="62d90-164">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="62d90-164">typedName</span></span>|  
|<span data-ttu-id="62d90-165">**Vlastnost**</span><span class="sxs-lookup"><span data-stu-id="62d90-165">**Property**</span></span>|<span data-ttu-id="62d90-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="62d90-166">PropertyName</span></span>|<span data-ttu-id="62d90-167">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="62d90-167">typedName</span></span>|  
|<span data-ttu-id="62d90-168">**Podřízené** přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="62d90-168">**Child** Accessor</span></span>|<span data-ttu-id="62d90-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="62d90-169">GetChildTableNameRows</span></span>|<span data-ttu-id="62d90-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="62d90-170">typedChildren</span></span>|  
|<span data-ttu-id="62d90-171">**Nadřazené** přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="62d90-171">**Parent** Accessor</span></span>|<span data-ttu-id="62d90-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="62d90-172">TableNameRow</span></span>|<span data-ttu-id="62d90-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="62d90-173">typedParent</span></span>|  
|<span data-ttu-id="62d90-174">**Datová sada** události</span><span class="sxs-lookup"><span data-stu-id="62d90-174">**DataSet** Events</span></span>|<span data-ttu-id="62d90-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="62d90-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="62d90-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="62d90-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="62d90-177">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="62d90-177">typedName</span></span>|  
  
 <span data-ttu-id="62d90-178">Použít zadali **datovou sadu** poznámky, musí zahrnovat následující **xmlns** odkaz v schéma schématu XML definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="62d90-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="62d90-179">(Vytvoření xsd z tabulek databáze naleznete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="62d90-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="62d90-180">Tady je ukázka poznámkou schéma, které zpřístupní **zákazníci** tabulky **Northwind** databáze s vztah k **objednávky** tabulku obsahuje.</span><span class="sxs-lookup"><span data-stu-id="62d90-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="62d90-181">Následující příklad kódu používá silného typu **datovou sadu** vytvořené z ukázkové schéma.</span><span class="sxs-lookup"><span data-stu-id="62d90-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="62d90-182">Používá jednu <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **zákazníci** tabulky a druhý <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="62d90-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="62d90-183">Silného typu **datovou sadu** definuje **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="62d90-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
    customers.Customers.NewCustomeromer()  
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
    customers.Customers.NewCustomeromer();  
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
  
## <a name="see-also"></a><span data-ttu-id="62d90-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="62d90-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="62d90-185">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="62d90-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="62d90-186">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="62d90-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="62d90-187">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="62d90-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
