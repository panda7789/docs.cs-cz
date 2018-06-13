---
title: Mapování jedinečná omezení schématu XML (XSD) na omezení datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8aed9830d613eeb7d49d2339a8ac1892c0e28e93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761165"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="2e0e7-102">Mapování jedinečná omezení schématu XML (XSD) na omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="2e0e7-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="2e0e7-103">Ve schématu XML definition language (XSD) schématu **jedinečný** element určuje omezení jedinečnosti k elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="2e0e7-104">Probíhá proces překladu schématu XML na relační schéma, jedinečné omezení zadaný na element nebo atribut ve schématu XML se mapuje na jedinečné omezení v <xref:System.Data.DataTable> do odpovídajícího <xref:System.Data.DataSet> generovanou.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="2e0e7-105">V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **jedinečný** elementu.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="2e0e7-106">Název atributu</span><span class="sxs-lookup"><span data-stu-id="2e0e7-106">Attribute name</span></span>|<span data-ttu-id="2e0e7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e0e7-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2e0e7-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="2e0e7-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="2e0e7-109">Pokud tento atribut je určen, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="2e0e7-110">Jinak **název** atribut poskytuje hodnota název omezení.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="2e0e7-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="2e0e7-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="2e0e7-112">Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** element, jedinečné omezení je vytvořen s **IsPrimaryKey** vlastnost nastavena na hodnotu **true**.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="2e0e7-113">Následující příklad ukazuje schéma XML, který používá **jedinečný** elementu, který chcete zadat omezení jedinečnosti.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="2e0e7-114">**Jedinečný** element ve schématu určuje, že pro všechny **zákazníci** instance elementy v dokumentu, hodnota **CustomerID** podřízený element musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="2e0e7-115">V sestavení **datovou sadu**, proces mapování čte toto schéma a generuje v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="2e0e7-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="2e0e7-116">Proces mapování také vytvoří jedinečné omezení na **CustomerID** sloupce, jak je znázorněno v následující **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="2e0e7-117">(Pro jednoduchost, jsou pouze relevantní vlastnosti zobrazené.)</span><span class="sxs-lookup"><span data-stu-id="2e0e7-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="2e0e7-118">V **datovou sadu** , která je vytvořena **IsPrimaryKey** je nastavena na **False** pro jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="2e0e7-119">**Jedinečný** vlastnost sloupec znamená, že **CustomerID** hodnoty sloupců musí být jedinečné (ale může být odkaz s hodnotou null, podle specifikace **AllowDBNull** vlastnost sloupce).</span><span class="sxs-lookup"><span data-stu-id="2e0e7-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="2e0e7-120">Upravíte-li schéma a nastavit volitelné **msdata:PrimaryKey** atribut hodnotu **True**, jedinečné omezení je vytvořit v tabulce.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="2e0e7-121">**AllowDBNull** sloupce je nastavena na **False**a **IsPrimaryKey** vlastnost nastavit na omezení **True**, proto provedení **CustomerID** sloupec sloupcem primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="2e0e7-122">Můžete zadat omezení unique u kombinaci elementy nebo atributy ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="2e0e7-123">Následující příklad ukazuje, jak určit, že kombinaci **CustomerID** a **#companyname** hodnoty musí být jedinečné pro všechny **zákazníci** v žádné instanci podle přidáním další **xs:field** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="2e0e7-124">Toto je omezení, který je vytvořen v výsledná **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="2e0e7-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e0e7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e0e7-125">See Also</span></span>  
 [<span data-ttu-id="2e0e7-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="2e0e7-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="2e0e7-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2e0e7-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="2e0e7-128">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2e0e7-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
