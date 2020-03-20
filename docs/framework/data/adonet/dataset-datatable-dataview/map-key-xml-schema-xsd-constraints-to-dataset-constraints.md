---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150932"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="46cd0-102">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="46cd0-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="46cd0-103">Ve schématu můžete určit omezení klíče pro prvek nebo atribut pomocí **klíčového** prvku.</span><span class="sxs-lookup"><span data-stu-id="46cd0-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="46cd0-104">Prvek nebo atribut, na kterém je zadáno omezení klíče, musí mít jedinečné hodnoty v libovolné instanci schématu a nemůže mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="46cd0-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="46cd0-105">Omezení klíče je podobné jedinečnému omezení s tím rozdílem, že sloupec, ve kterém je definováno omezení klíče, nemůže mít nulové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="46cd0-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="46cd0-106">Následující tabulka popisuje atributy **msdata,** které můžete zadat v **elementu klíče.**</span><span class="sxs-lookup"><span data-stu-id="46cd0-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="46cd0-107">Název atributu</span><span class="sxs-lookup"><span data-stu-id="46cd0-107">Attribute name</span></span>|<span data-ttu-id="46cd0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="46cd0-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="46cd0-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="46cd0-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="46cd0-110">Pokud je tento atribut zadán, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="46cd0-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="46cd0-111">V opačném případě atribut **name** poskytuje hodnotu názvu omezení.</span><span class="sxs-lookup"><span data-stu-id="46cd0-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="46cd0-112">**msdata:Primární klíč**</span><span class="sxs-lookup"><span data-stu-id="46cd0-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="46cd0-113">Pokud `PrimaryKey="true"` je k dispozici, je vlastnost omezení **IsPrimaryKey** nastavena na **hodnotu true**, čímž se jedná o primární klíč.</span><span class="sxs-lookup"><span data-stu-id="46cd0-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="46cd0-114">Vlastnost sloupec **AllowDBNull** je nastavena na **hodnotu false**, protože primární klíče nemohou mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="46cd0-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="46cd0-115">Při převodu schématu, ve kterém je zadáno omezení klíče, vytvoří proces mapování jedinečné omezení v tabulce s vlastností sloupce **AllowDBNull** nastavenou na **hodnotu false** pro každý sloupec v omezení.</span><span class="sxs-lookup"><span data-stu-id="46cd0-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="46cd0-116">Vlastnost **IsPrimaryKey** jedinečného omezení je také nastavena `msdata:PrimaryKey="true"` na **hodnotu false,** pokud jste nezadali prvek **klíče.**</span><span class="sxs-lookup"><span data-stu-id="46cd0-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="46cd0-117">Toto je totožné s jedinečným `PrimaryKey="true"`omezením ve schématu, ve kterém .</span><span class="sxs-lookup"><span data-stu-id="46cd0-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="46cd0-118">V následujícím příkladu schématu určuje prvek **klíče** omezení klíče pro prvek **CustomerID.**</span><span class="sxs-lookup"><span data-stu-id="46cd0-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="46cd0-119">Klíčový **key** prvek určuje, že hodnoty podřízeného prvku **CustomerID** prvku **Customers** musí mít jedinečné hodnoty a nemohou mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="46cd0-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="46cd0-120">Při překladu schématu jazyka definice schématu XML (XSD) vytvoří proces mapování následující tabulku:</span><span class="sxs-lookup"><span data-stu-id="46cd0-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="46cd0-121">Mapování schématu XML také vytvoří **UniqueConstraint** na **CustomerID** sloupec, jak <xref:System.Data.DataSet>je znázorněno v následujícím .</span><span class="sxs-lookup"><span data-stu-id="46cd0-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="46cd0-122">(Pro jednoduchost jsou zobrazeny pouze relevantní vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="46cd0-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="46cd0-123">V **dataset,** který je generován, **IsPrimaryKey** vlastnost **UniqueConstraint** je nastavena na **hodnotu true,** protože schéma určuje `msdata:PrimaryKey="true"` v **elementu klíče.**</span><span class="sxs-lookup"><span data-stu-id="46cd0-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="46cd0-124">Hodnota vlastnosti **ConstraintName** **vlastnosti UniqueConstraint** v **datové sadě** je hodnota atributu **msdata:ConstraintName** zadaného v elementu **klíče** ve schématu.</span><span class="sxs-lookup"><span data-stu-id="46cd0-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cd0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="46cd0-125">See also</span></span>

- [<span data-ttu-id="46cd0-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="46cd0-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="46cd0-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="46cd0-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="46cd0-128">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46cd0-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
