---
title: Zadávání poznámek k typovým datovým sadám
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151517"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="246a9-102">Zadávání poznámek k typovým datovým sadám</span><span class="sxs-lookup"><span data-stu-id="246a9-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="246a9-103">Poznámky umožňují změnit názvy prvků v zadaném <xref:System.Data.DataSet> textu bez úpravy základního schématu.</span><span class="sxs-lookup"><span data-stu-id="246a9-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="246a9-104">Změna názvů prvků v podkladovém schématu by způsobila, že zadaný **DataSet** odkazuje na objekty, které ve zdroji dat neexistují, a také ztratí odkaz na objekty, které existují ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="246a9-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="246a9-105">Pomocí anotací můžete přizpůsobit názvy objektů v zadané **datové sadě** s smysluplnějšími názvy, čímž usnadníte čitelný kód a zadávaný **soubor DataSet** snadněji používajíte klientům, přičemž základní schéma zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="246a9-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="246a9-106">Například následující prvek schématu pro tabulku **Zákazníci** databáze **Northwind** by mělo za následek název <xref:System.Data.DataRowCollection> objektu **DataRow** **customersrow** a pojmenované **zákazníci**.</span><span class="sxs-lookup"><span data-stu-id="246a9-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="246a9-107">A **DataRowCollection** název **customers** je smysluplné v kódu klienta, ale **Název DataRow** **CustomersRow** je zavádějící, protože je jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="246a9-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="246a9-108">Také v běžných scénářích by objekt být odkazoval se na bez identifikátor **u řádku** a místo toho by jednoduše označovány jako **objekt Zákazník.**</span><span class="sxs-lookup"><span data-stu-id="246a9-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="246a9-109">Řešením je anotovat schéma a identifikovat nové názvy pro **DataRow** a **DataRowCollection** objekty.</span><span class="sxs-lookup"><span data-stu-id="246a9-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="246a9-110">Následuje anotovaná verze předchozího schématu.</span><span class="sxs-lookup"><span data-stu-id="246a9-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="246a9-111">Zadání hodnoty **typedName** **zákazníka** bude mít za následek název objektu **DataRow** **zákazníka**.</span><span class="sxs-lookup"><span data-stu-id="246a9-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="246a9-112">Zadání **množného** čísla **Hodnota Zákazníci** zachová název **DataRowCollection** **zákazníky**.</span><span class="sxs-lookup"><span data-stu-id="246a9-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="246a9-113">V následující tabulce jsou uvedeny poznámky, které jsou k dispozici pro použití.</span><span class="sxs-lookup"><span data-stu-id="246a9-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="246a9-114">Poznámka</span><span class="sxs-lookup"><span data-stu-id="246a9-114">Annotation</span></span>|<span data-ttu-id="246a9-115">Popis</span><span class="sxs-lookup"><span data-stu-id="246a9-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="246a9-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="246a9-116">**typedName**</span></span>|<span data-ttu-id="246a9-117">Název objektu.</span><span class="sxs-lookup"><span data-stu-id="246a9-117">Name of the object.</span></span>|  
|<span data-ttu-id="246a9-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="246a9-118">**typedPlural**</span></span>|<span data-ttu-id="246a9-119">Název kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="246a9-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="246a9-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="246a9-120">**typedParent**</span></span>|<span data-ttu-id="246a9-121">Název objektu, na který se odkazuje v nadřazeném vztahu.</span><span class="sxs-lookup"><span data-stu-id="246a9-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="246a9-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="246a9-122">**typedChildren**</span></span>|<span data-ttu-id="246a9-123">Název metody pro vrácení objektů z podřízeného vztahu.</span><span class="sxs-lookup"><span data-stu-id="246a9-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="246a9-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="246a9-124">**nullValue**</span></span>|<span data-ttu-id="246a9-125">Hodnota, pokud je základní hodnota **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="246a9-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="246a9-126">V následující tabulce naleznete poznámky **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="246a9-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="246a9-127">Výchozí hodnota je **_throw**.</span><span class="sxs-lookup"><span data-stu-id="246a9-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="246a9-128">V následující tabulce jsou uvedeny hodnoty, které lze zadat pro poznámku **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="246a9-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="246a9-129">hodnota nullHodnota</span><span class="sxs-lookup"><span data-stu-id="246a9-129">nullValue Value</span></span>|<span data-ttu-id="246a9-130">Popis</span><span class="sxs-lookup"><span data-stu-id="246a9-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="246a9-131">*Náhradní hodnota*</span><span class="sxs-lookup"><span data-stu-id="246a9-131">*Replacement Value*</span></span>|<span data-ttu-id="246a9-132">Zadejte hodnotu, která má být vrácena.</span><span class="sxs-lookup"><span data-stu-id="246a9-132">Specify a value to be returned.</span></span> <span data-ttu-id="246a9-133">Vrácená hodnota musí odpovídat typu prvku.</span><span class="sxs-lookup"><span data-stu-id="246a9-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="246a9-134">Slouží `nullValue="0"` například k vrácení 0 pro pole s nulovým sdělovým číselně.</span><span class="sxs-lookup"><span data-stu-id="246a9-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="246a9-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="246a9-135">**_throw**</span></span>|<span data-ttu-id="246a9-136">Vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="246a9-136">Throw an exception.</span></span> <span data-ttu-id="246a9-137">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="246a9-137">This is the default.</span></span>|  
|<span data-ttu-id="246a9-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="246a9-138">**_null**</span></span>|<span data-ttu-id="246a9-139">Vrátí nulový odkaz nebo vyvolat výjimku, pokud je zjištěn primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="246a9-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="246a9-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="246a9-140">**_empty**</span></span>|<span data-ttu-id="246a9-141">Pro řetězce vrátí **String.Empty**, jinak vrátí objekt vytvořený z prázdného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="246a9-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="246a9-142">Pokud dojde k primitivní typ, vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="246a9-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="246a9-143">V následující tabulce jsou uvedeny výchozí hodnoty pro objekty v zadané **datové sadě** a dostupné poznámky.</span><span class="sxs-lookup"><span data-stu-id="246a9-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="246a9-144">Objekt/Metoda/událost</span><span class="sxs-lookup"><span data-stu-id="246a9-144">Object/Method/Event</span></span>|<span data-ttu-id="246a9-145">Výchozí</span><span class="sxs-lookup"><span data-stu-id="246a9-145">Default</span></span>|<span data-ttu-id="246a9-146">Poznámka</span><span class="sxs-lookup"><span data-stu-id="246a9-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="246a9-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="246a9-147">**DataTable**</span></span>|<span data-ttu-id="246a9-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="246a9-148">TableNameDataTable</span></span>|<span data-ttu-id="246a9-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="246a9-149">typedPlural</span></span>|  
|<span data-ttu-id="246a9-150">**Tabulka dat** Metody</span><span class="sxs-lookup"><span data-stu-id="246a9-150">**DataTable** Methods</span></span>|<span data-ttu-id="246a9-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="246a9-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="246a9-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="246a9-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="246a9-153">Odstranitnázev_řádku</span><span class="sxs-lookup"><span data-stu-id="246a9-153">DeleteTableNameRow</span></span>|<span data-ttu-id="246a9-154">typedName</span><span class="sxs-lookup"><span data-stu-id="246a9-154">typedName</span></span>|  
|<span data-ttu-id="246a9-155">**Datarowcollection**</span><span class="sxs-lookup"><span data-stu-id="246a9-155">**DataRowCollection**</span></span>|<span data-ttu-id="246a9-156">TableName</span><span class="sxs-lookup"><span data-stu-id="246a9-156">TableName</span></span>|<span data-ttu-id="246a9-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="246a9-157">typedPlural</span></span>|  
|<span data-ttu-id="246a9-158">**Datarow**</span><span class="sxs-lookup"><span data-stu-id="246a9-158">**DataRow**</span></span>|<span data-ttu-id="246a9-159">Název_tabulky</span><span class="sxs-lookup"><span data-stu-id="246a9-159">TableNameRow</span></span>|<span data-ttu-id="246a9-160">typedName</span><span class="sxs-lookup"><span data-stu-id="246a9-160">typedName</span></span>|  
|<span data-ttu-id="246a9-161">**Datacolumn**</span><span class="sxs-lookup"><span data-stu-id="246a9-161">**DataColumn**</span></span>|<span data-ttu-id="246a9-162">Sloupec Název_sloupce DataTable.Column</span><span class="sxs-lookup"><span data-stu-id="246a9-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="246a9-163">Název_řádku_data</span><span class="sxs-lookup"><span data-stu-id="246a9-163">DataRow.ColumnName</span></span>|<span data-ttu-id="246a9-164">typedName</span><span class="sxs-lookup"><span data-stu-id="246a9-164">typedName</span></span>|  
|<span data-ttu-id="246a9-165">**Vlastnost**</span><span class="sxs-lookup"><span data-stu-id="246a9-165">**Property**</span></span>|<span data-ttu-id="246a9-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="246a9-166">PropertyName</span></span>|<span data-ttu-id="246a9-167">typedName</span><span class="sxs-lookup"><span data-stu-id="246a9-167">typedName</span></span>|  
|<span data-ttu-id="246a9-168">**Dítě** Přístupové</span><span class="sxs-lookup"><span data-stu-id="246a9-168">**Child** Accessor</span></span>|<span data-ttu-id="246a9-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="246a9-169">GetChildTableNameRows</span></span>|<span data-ttu-id="246a9-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="246a9-170">typedChildren</span></span>|  
|<span data-ttu-id="246a9-171">**Nadřazená** Přístupové</span><span class="sxs-lookup"><span data-stu-id="246a9-171">**Parent** Accessor</span></span>|<span data-ttu-id="246a9-172">Název_tabulky</span><span class="sxs-lookup"><span data-stu-id="246a9-172">TableNameRow</span></span>|<span data-ttu-id="246a9-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="246a9-173">typedParent</span></span>|  
|<span data-ttu-id="246a9-174">**Datová sada** Události</span><span class="sxs-lookup"><span data-stu-id="246a9-174">**DataSet** Events</span></span>|<span data-ttu-id="246a9-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="246a9-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="246a9-176">Obslužná rutina_události TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="246a9-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="246a9-177">typedName</span><span class="sxs-lookup"><span data-stu-id="246a9-177">typedName</span></span>|  
  
 <span data-ttu-id="246a9-178">Chcete-li použít zadané poznámky **DataSet,** musíte do schématu jazyka Xml Schema (XSD) zahrnout následující odkaz **xmlns.**</span><span class="sxs-lookup"><span data-stu-id="246a9-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="246a9-179">Chcete-li vytvořit xsd z <xref:System.Data.DataSet.WriteXmlSchema%2A> databázových tabulek, přečtěte si další informace nebo [práce s datovými sadami v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="246a9-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="246a9-180">Následuje ukázkové schéma s anotovanými notami, které zpřístupňuje tabulku **Zákazníci** databáze **Northwind** s vztahem k tabulce **Objednávky.**</span><span class="sxs-lookup"><span data-stu-id="246a9-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="246a9-181">Následující příklad kódu používá silně zadaný **DataSet** vytvořený z ukázkového schématu.</span><span class="sxs-lookup"><span data-stu-id="246a9-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="246a9-182">Používá jeden <xref:System.Data.SqlClient.SqlDataAdapter> k naplnění tabulky <xref:System.Data.SqlClient.SqlDataAdapter> **Zákazníci** a jiný k naplnění tabulky **Objednávky.**</span><span class="sxs-lookup"><span data-stu-id="246a9-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="246a9-183">Silně zadaný **dataset** definuje **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="246a9-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="246a9-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="246a9-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="246a9-185">Typové datové sady</span><span class="sxs-lookup"><span data-stu-id="246a9-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="246a9-186">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="246a9-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="246a9-187">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="246a9-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
