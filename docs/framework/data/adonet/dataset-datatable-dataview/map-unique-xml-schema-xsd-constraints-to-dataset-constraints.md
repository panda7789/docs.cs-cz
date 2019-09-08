---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 4aa94dfaf088a2a934c8901e2720f166d3a38dae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784406"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="82b84-102">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="82b84-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="82b84-103">Ve schématu XSD (XML Schema Definition Language) definuje **jedinečný** element omezení jedinečnosti pro element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="82b84-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="82b84-104">V procesu překladu schématu XML do relačního schématu je jedinečné omezení zadané u elementu nebo atributu ve schématu XML mapováno na jedinečné omezení v <xref:System.Data.DataTable> v odpovídajícím <xref:System.Data.DataSet> generovaném objektu.</span><span class="sxs-lookup"><span data-stu-id="82b84-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="82b84-105">Následující tabulka popisuje atributy **msdata** , které lze zadat v **jedinečném** prvku.</span><span class="sxs-lookup"><span data-stu-id="82b84-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="82b84-106">Název atributu</span><span class="sxs-lookup"><span data-stu-id="82b84-106">Attribute name</span></span>|<span data-ttu-id="82b84-107">Popis</span><span class="sxs-lookup"><span data-stu-id="82b84-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="82b84-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="82b84-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="82b84-109">Pokud je tento atribut zadán, použije se jako název omezení jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="82b84-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="82b84-110">V opačném případě atribut **Name** poskytuje hodnotu názvu omezení.</span><span class="sxs-lookup"><span data-stu-id="82b84-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="82b84-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="82b84-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="82b84-112">Pokud `PrimaryKey="true"` se nachází v **jedinečném** elementu, je vytvořeno jedinečné omezení s vlastností **IsPrimaryKey** nastavenou na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="82b84-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="82b84-113">Následující příklad ukazuje schéma XML, které používá **jedinečný** element k určení omezení jedinečnosti.</span><span class="sxs-lookup"><span data-stu-id="82b84-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="82b84-114">**Jedinečný** prvek ve schématu určuje, že pro všechny **zákazníky** v instanci dokumentu musí být hodnota podřízeného elementu **CustomerID** jedinečná.</span><span class="sxs-lookup"><span data-stu-id="82b84-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="82b84-115">Při sestavování **datové sady**načte proces mapování toto schéma a vygeneruje následující tabulku:</span><span class="sxs-lookup"><span data-stu-id="82b84-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="82b84-116">Proces mapování také vytvoří jedinečné omezení pro sloupec **KódZákazníka** , jak je znázorněno v následující **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="82b84-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="82b84-117">(Pro jednoduchost se zobrazí pouze příslušné vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="82b84-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="82b84-118">V **datové sadě** , která je vygenerována, je vlastnost **IsPrimaryKey** pro jedinečné omezení nastavena na **hodnotu false** .</span><span class="sxs-lookup"><span data-stu-id="82b84-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="82b84-119">Vlastnost **Unique** sloupce označuje, že hodnoty sloupce **KódZákazníka** musí být jedinečné (ale mohou být odkazem s hodnotou null, jak je určeno vlastností **AllowDBNull** sloupce).</span><span class="sxs-lookup"><span data-stu-id="82b84-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="82b84-120">Pokud schéma upravíte a nastavíte volitelnou hodnotu atributu **msdata: PrimaryKey** na hodnotu **true**, v tabulce se vytvoří jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="82b84-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="82b84-121">Vlastnost Column **AllowDBNull** je nastavena na **hodnotu false**a vlastnost **IsPrimaryKey** omezení je nastavena na **hodnotu true**, čímž se sloupec **KódZákazníka** nastaví jako sloupec primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="82b84-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="82b84-122">Můžete zadat jedinečné omezení na kombinaci prvků nebo atributů ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="82b84-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="82b84-123">Následující příklad ukazuje, jak určit, že kombinace hodnot **KódZákazníka** a **CompanyName** musí být jedinečná pro všechny **zákazníky** v jakékoli instanci přidáním jiného prvku **xs: Field** ve schématu.</span><span class="sxs-lookup"><span data-stu-id="82b84-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="82b84-124">Toto je omezení vytvořené ve výsledné **sadě dat**.</span><span class="sxs-lookup"><span data-stu-id="82b84-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="82b84-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82b84-125">See also</span></span>

- [<span data-ttu-id="82b84-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="82b84-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="82b84-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="82b84-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="82b84-128">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="82b84-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
