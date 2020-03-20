---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150841"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="694de-102">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="694de-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="694de-103">V definičním jazyce xml schématu (XSD) **jedinečný** prvek určuje omezení jedinečnosti prvku nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="694de-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="694de-104">V procesu překladu schématu XML do relačního schématu je jedinečné omezení zadané pro prvek nebo atribut ve schématu XML mapováno na jedinečné omezení v <xref:System.Data.DataTable> odpovídajícím, <xref:System.Data.DataSet> který je generován.</span><span class="sxs-lookup"><span data-stu-id="694de-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="694de-105">Následující tabulka popisuje atributy **msdata,** které můžete zadat v **jedinečném** prvku.</span><span class="sxs-lookup"><span data-stu-id="694de-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="694de-106">Název atributu</span><span class="sxs-lookup"><span data-stu-id="694de-106">Attribute name</span></span>|<span data-ttu-id="694de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="694de-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="694de-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="694de-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="694de-109">Pokud je tento atribut zadán, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="694de-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="694de-110">V opačném případě atribut **name** poskytuje hodnotu názvu omezení.</span><span class="sxs-lookup"><span data-stu-id="694de-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="694de-111">**msdata:Primární klíč**</span><span class="sxs-lookup"><span data-stu-id="694de-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="694de-112">Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** prvek, je vytvořen jedinečný omezení s **IsPrimaryKey** vlastnost nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="694de-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="694de-113">Následující příklad ukazuje schéma XML, které používá **jedinečný** prvek k určení omezení jedinečnosti.</span><span class="sxs-lookup"><span data-stu-id="694de-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="694de-114">**Jedinečný** prvek ve schématu určuje, že pro všechny **prvky Customers** v instanci dokumentu musí být hodnota podřízeného prvku **CustomerID** jedinečná.</span><span class="sxs-lookup"><span data-stu-id="694de-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="694de-115">Při vytváření **dataset**, proces mapování přečte toto schéma a generuje následující tabulku:</span><span class="sxs-lookup"><span data-stu-id="694de-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="694de-116">Proces mapování také vytvoří jedinečné omezení ve **sloupci CustomerID,** jak je znázorněno v následujícím **datovém souboru**.</span><span class="sxs-lookup"><span data-stu-id="694de-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="694de-117">(Pro jednoduchost jsou zobrazeny pouze relevantní vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="694de-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
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
  
 <span data-ttu-id="694de-118">V **dataset,** který je generován, **IsPrimaryKey** vlastnost je nastavena na **False** pro jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="694de-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="694de-119">**Jedinečná** vlastnost ve sloupci označuje, že hodnoty sloupce **CustomerID** musí být jedinečné (ale mohou se jednat o nulový odkaz, jak je určeno vlastností **AllowDBNull** sloupce).</span><span class="sxs-lookup"><span data-stu-id="694de-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="694de-120">Pokud změníte schéma a nastavíte volitelnou hodnotu atributu **msdata:PrimaryKey** na **hodnotu True**, vytvoří se v tabulce jedinečné omezení.</span><span class="sxs-lookup"><span data-stu-id="694de-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="694de-121">Vlastnost sloupec **AllowDBNull** je nastavena na **hodnotu False**a vlastnost **IsPrimaryKey** nastaveného omezení na **hodnotu True**, čímž se sloupec **CustomerID** stává sloupcem primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="694de-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="694de-122">Ve schématu XML můžete určit jedinečné omezení kombinace prvků nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="694de-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="694de-123">Následující příklad ukazuje, jak určit, že kombinace **CustomerID** a **CompanyName** hodnoty musí být jedinečný pro všechny **zákazníky** v každém případě přidáním další **xs:field** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="694de-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="694de-124">Toto je omezení, které je vytvořeno ve výsledné **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="694de-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="694de-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="694de-125">See also</span></span>

- [<span data-ttu-id="694de-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="694de-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="694de-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="694de-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="694de-128">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="694de-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
