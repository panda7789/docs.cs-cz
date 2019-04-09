---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085126"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="66f76-102">Zadávání poznámek k typovým datovým sadám</span><span class="sxs-lookup"><span data-stu-id="66f76-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="66f76-103">Anotace umožňují změnit názvy prvků v váš zadaný <xref:System.Data.DataSet> beze změny podkladového schématu.</span><span class="sxs-lookup"><span data-stu-id="66f76-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="66f76-104">Úprava názvy prvků v podkladové schéma by způsobilo zadaného **datovou sadu** k odkazování na objekty, které nejsou existují ve zdroji dat, jakož i odkazovaly, ztratily odkaz na objekty, které existují ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="66f76-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="66f76-105">Použití poznámek, můžete přizpůsobit názvy objektů v váš zadaný **datovou sadu** s více smysluplné názvy, takže kód lépe čitelný a váš zadaný **datovou sadu** usnadňuje klientům používat při opuštění základní schéma beze změn.</span><span class="sxs-lookup"><span data-stu-id="66f76-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="66f76-106">Například následující element schématu pro **zákazníkům** tabulku **Northwind** výsledkem by byla databáze **DataRow** název objektu  **CustomersRow** a <xref:System.Data.DataRowCollection> s názvem **zákazníkům**.</span><span class="sxs-lookup"><span data-stu-id="66f76-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="66f76-107">A **kolekci DataRowCollection** název **zákazníkům** má smysl v klientském kódu, ale **DataRow** název **CustomersRow** je zavádějící protože je jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="66f76-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="66f76-108">V běžných scénářů, objekt by se označovat taky bez **řádek** identifikátor a místo toho by jednoduše odkazovat jako **zákazníka** objektu.</span><span class="sxs-lookup"><span data-stu-id="66f76-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="66f76-109">Řešením je přidání poznámek ke schématu a identifikovat nové názvy pro **DataRow** a **kolekci DataRowCollection** objekty.</span><span class="sxs-lookup"><span data-stu-id="66f76-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="66f76-110">Tady je s poznámkami verzi předchozí schématu.</span><span class="sxs-lookup"><span data-stu-id="66f76-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="66f76-111">Určení **TypedName služby Active Directory** hodnotu **zákazníka** bude mít za následek **DataRow** název objektu **zákazníka**.</span><span class="sxs-lookup"><span data-stu-id="66f76-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="66f76-112">Určení **typedPlural** hodnotu **zákazníkům** zachová **kolekci DataRowCollection** název **zákazníkům**.</span><span class="sxs-lookup"><span data-stu-id="66f76-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="66f76-113">Poznámky k dispozici pro použití v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="66f76-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="66f76-114">Poznámka</span><span class="sxs-lookup"><span data-stu-id="66f76-114">Annotation</span></span>|<span data-ttu-id="66f76-115">Popis</span><span class="sxs-lookup"><span data-stu-id="66f76-115">Description</span></span>|  
|----------------|-----------------|  
|**<span data-ttu-id="66f76-116">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-116">typedName</span></span>**|<span data-ttu-id="66f76-117">Název objektu.</span><span class="sxs-lookup"><span data-stu-id="66f76-117">Name of the object.</span></span>|  
|**<span data-ttu-id="66f76-118">typedPlural</span><span class="sxs-lookup"><span data-stu-id="66f76-118">typedPlural</span></span>**|<span data-ttu-id="66f76-119">Název kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="66f76-119">Name of a collection of objects.</span></span>|  
|**<span data-ttu-id="66f76-120">typedParent</span><span class="sxs-lookup"><span data-stu-id="66f76-120">typedParent</span></span>**|<span data-ttu-id="66f76-121">Název objektu podle nadřazenou relací.</span><span class="sxs-lookup"><span data-stu-id="66f76-121">Name of the object when referred to in a parent relationship.</span></span>|  
|**<span data-ttu-id="66f76-122">typedChildren</span><span class="sxs-lookup"><span data-stu-id="66f76-122">typedChildren</span></span>**|<span data-ttu-id="66f76-123">Název metody, která vrací objekty z podřízeného vztahu.</span><span class="sxs-lookup"><span data-stu-id="66f76-123">Name of the method to return objects from a child relationship.</span></span>|  
|**<span data-ttu-id="66f76-124">nullValue</span><span class="sxs-lookup"><span data-stu-id="66f76-124">nullValue</span></span>**|<span data-ttu-id="66f76-125">Hodnotu, pokud je zadaná hodnota **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="66f76-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="66f76-126">V následující tabulce najdete **nullValue** poznámky.</span><span class="sxs-lookup"><span data-stu-id="66f76-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="66f76-127">Výchozí hodnota je **_throw**.</span><span class="sxs-lookup"><span data-stu-id="66f76-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="66f76-128">V následující tabulce jsou uvedeny hodnoty, které je možné zadat pro **nullValue** poznámky.</span><span class="sxs-lookup"><span data-stu-id="66f76-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="66f76-129">nullValue hodnotu</span><span class="sxs-lookup"><span data-stu-id="66f76-129">nullValue Value</span></span>|<span data-ttu-id="66f76-130">Popis</span><span class="sxs-lookup"><span data-stu-id="66f76-130">Description</span></span>|  
|---------------------|-----------------|  
|*<span data-ttu-id="66f76-131">Nahrazující hodnotou</span><span class="sxs-lookup"><span data-stu-id="66f76-131">Replacement Value</span></span>*|<span data-ttu-id="66f76-132">Zadejte hodnotu má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="66f76-132">Specify a value to be returned.</span></span> <span data-ttu-id="66f76-133">Vrácená hodnota musí odpovídat typu elementu.</span><span class="sxs-lookup"><span data-stu-id="66f76-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="66f76-134">Například použít `nullValue="0"` vrátit 0 pro pole null typu integer.</span><span class="sxs-lookup"><span data-stu-id="66f76-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|**<span data-ttu-id="66f76-135">_throw</span><span class="sxs-lookup"><span data-stu-id="66f76-135">_throw</span></span>**|<span data-ttu-id="66f76-136">Vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="66f76-136">Throw an exception.</span></span> <span data-ttu-id="66f76-137">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="66f76-137">This is the default.</span></span>|  
|**<span data-ttu-id="66f76-138">_null</span><span class="sxs-lookup"><span data-stu-id="66f76-138">_null</span></span>**|<span data-ttu-id="66f76-139">Vrátí odkaz s hodnotou null nebo vyvolat výjimku, pokud je primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="66f76-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|**<span data-ttu-id="66f76-140">_prázdný</span><span class="sxs-lookup"><span data-stu-id="66f76-140">_empty</span></span>**|<span data-ttu-id="66f76-141">Pro řetězce, vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="66f76-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="66f76-142">Pokud je nalezen primitivní typ, vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="66f76-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="66f76-143">V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v typovaného **datovou sadu** a poznámky k dispozici.</span><span class="sxs-lookup"><span data-stu-id="66f76-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="66f76-144">Objekt nebo metoda/událost</span><span class="sxs-lookup"><span data-stu-id="66f76-144">Object/Method/Event</span></span>|<span data-ttu-id="66f76-145">Výchozí</span><span class="sxs-lookup"><span data-stu-id="66f76-145">Default</span></span>|<span data-ttu-id="66f76-146">Poznámka</span><span class="sxs-lookup"><span data-stu-id="66f76-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|**<span data-ttu-id="66f76-147">DataTable</span><span class="sxs-lookup"><span data-stu-id="66f76-147">DataTable</span></span>**|<span data-ttu-id="66f76-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="66f76-148">TableNameDataTable</span></span>|<span data-ttu-id="66f76-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="66f76-149">typedPlural</span></span>|  
|<span data-ttu-id="66f76-150">**Objekt DataTable** metody</span><span class="sxs-lookup"><span data-stu-id="66f76-150">**DataTable** Methods</span></span>|<span data-ttu-id="66f76-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="66f76-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="66f76-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="66f76-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="66f76-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="66f76-153">DeleteTableNameRow</span></span>|<span data-ttu-id="66f76-154">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-154">typedName</span></span>|  
|**<span data-ttu-id="66f76-155">DataRowCollection</span><span class="sxs-lookup"><span data-stu-id="66f76-155">DataRowCollection</span></span>**|<span data-ttu-id="66f76-156">TableName</span><span class="sxs-lookup"><span data-stu-id="66f76-156">TableName</span></span>|<span data-ttu-id="66f76-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="66f76-157">typedPlural</span></span>|  
|**<span data-ttu-id="66f76-158">DataRow</span><span class="sxs-lookup"><span data-stu-id="66f76-158">DataRow</span></span>**|<span data-ttu-id="66f76-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="66f76-159">TableNameRow</span></span>|<span data-ttu-id="66f76-160">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-160">typedName</span></span>|  
|**<span data-ttu-id="66f76-161">Objekt DataColumn</span><span class="sxs-lookup"><span data-stu-id="66f76-161">DataColumn</span></span>**|<span data-ttu-id="66f76-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="66f76-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="66f76-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="66f76-163">DataRow.ColumnName</span></span>|<span data-ttu-id="66f76-164">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-164">typedName</span></span>|  
|**<span data-ttu-id="66f76-165">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="66f76-165">Property</span></span>**|<span data-ttu-id="66f76-166">Vlastnost PropertyName</span><span class="sxs-lookup"><span data-stu-id="66f76-166">PropertyName</span></span>|<span data-ttu-id="66f76-167">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-167">typedName</span></span>|  
|<span data-ttu-id="66f76-168">**Podřízené** přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="66f76-168">**Child** Accessor</span></span>|<span data-ttu-id="66f76-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="66f76-169">GetChildTableNameRows</span></span>|<span data-ttu-id="66f76-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="66f76-170">typedChildren</span></span>|  
|<span data-ttu-id="66f76-171">**Nadřazené** přístupového objektu</span><span class="sxs-lookup"><span data-stu-id="66f76-171">**Parent** Accessor</span></span>|<span data-ttu-id="66f76-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="66f76-172">TableNameRow</span></span>|<span data-ttu-id="66f76-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="66f76-173">typedParent</span></span>|  
|<span data-ttu-id="66f76-174">**Datová sada** události</span><span class="sxs-lookup"><span data-stu-id="66f76-174">**DataSet** Events</span></span>|<span data-ttu-id="66f76-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="66f76-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="66f76-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="66f76-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="66f76-177">TypedName služby Active Directory</span><span class="sxs-lookup"><span data-stu-id="66f76-177">typedName</span></span>|  
  
 <span data-ttu-id="66f76-178">Použití typu **datovou sadu** poznámky, musí zahrnovat následující **xmlns** odkaz ve schématu schématu XML definice jazyk (XSD).</span><span class="sxs-lookup"><span data-stu-id="66f76-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="66f76-179">Vytvoření xsd z tabulky databáze najdete v tématu <xref:System.Data.DataSet.WriteXmlSchema%2A> nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="66f76-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="66f76-180">Tady je ukázka s poznámkami schématu, která zveřejňuje **zákazníkům** tabulku **Northwind** databáze s vztah k položce **objednávky** tabulku obsahuje.</span><span class="sxs-lookup"><span data-stu-id="66f76-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="66f76-181">Následující příklad kódu používá silného typu **datovou sadu** vytvořené ze vzorku schématu.</span><span class="sxs-lookup"><span data-stu-id="66f76-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="66f76-182">Používá jednu <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **zákazníkům** tabulkami <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění **objednávky** tabulky.</span><span class="sxs-lookup"><span data-stu-id="66f76-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="66f76-183">Silného typu **datovou sadu** definuje **datových relací**.</span><span class="sxs-lookup"><span data-stu-id="66f76-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66f76-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66f76-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="66f76-185">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="66f76-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [<span data-ttu-id="66f76-186">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="66f76-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="66f76-187">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="66f76-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
