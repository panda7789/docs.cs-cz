---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: c35dcadfb40fcb73104af7ee7456e64a68c9e023
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677064"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="30159-102">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="30159-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="30159-103">Ve schématu XML definice jazyk (XSD) schématu **jedinečný** prvek určuje omezení jedinečnosti pro elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="30159-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="30159-104">Právě schématu XML se překládá na relační schéma, jedinečné omezení zadaný v elementu nebo atributu ve schématu XML se mapuje na jedinečné omezení v <xref:System.Data.DataTable> z odpovídajících <xref:System.Data.DataSet> , který je generován.</span><span class="sxs-lookup"><span data-stu-id="30159-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="30159-105">V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **jedinečný** elementu.</span><span class="sxs-lookup"><span data-stu-id="30159-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="30159-106">Název atributu</span><span class="sxs-lookup"><span data-stu-id="30159-106">Attribute name</span></span>|<span data-ttu-id="30159-107">Popis</span><span class="sxs-lookup"><span data-stu-id="30159-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="30159-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="30159-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="30159-109">Pokud tento atribut není zadán, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="30159-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="30159-110">V opačném případě **název** atributu obsahuje hodnotu název omezení.</span><span class="sxs-lookup"><span data-stu-id="30159-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="30159-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="30159-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="30159-112">Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** elementu jedinečné omezení se vytvoří s **isprimarykey hodnotu** vlastnost nastavena na hodnotu **true**.</span><span class="sxs-lookup"><span data-stu-id="30159-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="30159-113">Následující příklad ukazuje schématu XML, který používá **jedinečný** element zadat omezení jedinečnosti.</span><span class="sxs-lookup"><span data-stu-id="30159-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="30159-114">**Jedinečný** element ve schématu, která určuje pro všechny **zákazníkům** prvky v dokumentu instance, hodnota **CustomerID** podřízený element musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="30159-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="30159-115">V sestavení **datovou sadu**, proces mapování čte toto schéma a vygeneruje v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="30159-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="30159-116">Proces mapování také vytvoří jedinečné omezení na **CustomerID** sloupce, jak je znázorněno v následujícím **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="30159-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="30159-117">(Pro jednoduchost, pouze relevantní jsou zobrazeny vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="30159-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="30159-118">V **datovou sadu** , který je generován, **isprimarykey hodnotu** je nastavena na **False** pro jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="30159-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="30159-119">**Jedinečný** vlastnost sloupec znamená, že **CustomerID** hodnot sloupců musí být jedinečné (ale mohou být odkaz s hodnotou null, jak jsou určené **AllowDBNull** Vlastnosti sloupce).</span><span class="sxs-lookup"><span data-stu-id="30159-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="30159-120">Je-li upravit schéma a nastavit volitelný **msdata:PrimaryKey** atribut hodnotu **True**, jedinečné omezení se vytvoří v tabulce.</span><span class="sxs-lookup"><span data-stu-id="30159-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="30159-121">**AllowDBNull** sloupce je nastavena na **False**a **isprimarykey hodnotu** vlastnost nastavit na omezení **True**a proto **CustomerID** sloupec sloupec primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="30159-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="30159-122">Jedinečné omezení na kombinaci elementy nebo atributy můžete zadat ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="30159-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="30159-123">Následující příklad ukazuje, jak určit, že kombinaci **CustomerID** a **CompanyName** hodnoty musí být jedinečné pro všechny **zákazníkům** v žádné instanci podle Přidání dalšího **xs:field** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="30159-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="30159-124">Toto je omezení, který je vytvořen ve výsledné **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="30159-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="30159-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30159-125">See also</span></span>
- [<span data-ttu-id="30159-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="30159-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="30159-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="30159-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="30159-128">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="30159-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
