---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: d6fcdae77c2f2ac07ea5cd16baf07cd5de36d25b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203474"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="4e479-102">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="4e479-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="4e479-103">Ve schématu můžete zadat omezení klíče pro element nebo atribut pomocí elementu **Key** .</span><span class="sxs-lookup"><span data-stu-id="4e479-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="4e479-104">Element nebo atribut, u kterého je zadáno omezení klíče, musí mít jedinečné hodnoty v libovolné instanci schématu a nesmí mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="4e479-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="4e479-105">Omezení klíče je podobné omezení UNIQUE s tím rozdílem, že sloupec, na kterém je definováno omezení klíče, nemůže mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="4e479-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="4e479-106">Následující tabulka popisuje atributy **msdata** , které lze zadat v elementu **Key** .</span><span class="sxs-lookup"><span data-stu-id="4e479-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="4e479-107">Název atributu</span><span class="sxs-lookup"><span data-stu-id="4e479-107">Attribute name</span></span>|<span data-ttu-id="4e479-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4e479-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4e479-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="4e479-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="4e479-110">Pokud je tento atribut zadán, použije se jako název omezení jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="4e479-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="4e479-111">V opačném případě atribut **Name** poskytuje hodnotu názvu omezení.</span><span class="sxs-lookup"><span data-stu-id="4e479-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="4e479-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="4e479-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="4e479-113">Pokud `PrimaryKey="true"` je k dispozici, vlastnost omezení **IsPrimaryKey** je nastavena na **hodnotu true**, takže ji vytvoří primární klíč.</span><span class="sxs-lookup"><span data-stu-id="4e479-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="4e479-114">Vlastnost **AllowDBNull** sloupce je nastavena na **hodnotu false**, protože primární klíče nemohou mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="4e479-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="4e479-115">Při převádění schématu, ve kterém je zadáno omezení klíče, proces mapování vytvoří v tabulce jedinečné omezení s vlastností **AllowDBNull** Column nastavenou na **hodnotu false** pro každý sloupec v omezení.</span><span class="sxs-lookup"><span data-stu-id="4e479-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="4e479-116">Vlastnost **IsPrimaryKey** jedinečného omezení je také nastavena na **hodnotu false** , pokud jste neurčili `msdata:PrimaryKey="true"` u elementu **Key** .</span><span class="sxs-lookup"><span data-stu-id="4e479-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="4e479-117">Toto je stejné jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="4e479-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="4e479-118">V následujícím příkladu schématu **klíč** elementu určuje omezení klíče u elementu **CustomerID** .</span><span class="sxs-lookup"><span data-stu-id="4e479-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="4e479-119">**Klíčový** prvek určuje, že hodnoty podřízeného prvku **KódZákazníka** elementu Customers musí mít jedinečné hodnoty a nesmí mít hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="4e479-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="4e479-120">V rámci překladu schématu XML Schema Definition Language (XSD) vytvoří proces mapování následující tabulku:</span><span class="sxs-lookup"><span data-stu-id="4e479-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="4e479-121">Mapování schématu XML také vytvoří **UniqueConstraint** ve sloupci **KódZákazníka** , jak je znázorněno v následujícím <xref:System.Data.DataSet>příkladu.</span><span class="sxs-lookup"><span data-stu-id="4e479-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4e479-122">(Pro jednoduchost se zobrazí pouze příslušné vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="4e479-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="4e479-123">V **datové sadě** , která je generována, vlastnost **IsPrimaryKey** třídy **UniqueConstraint** je nastavena na **hodnotu true** , protože schéma `msdata:PrimaryKey="true"` určuje element **Key** .</span><span class="sxs-lookup"><span data-stu-id="4e479-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="4e479-124">Hodnota vlastnosti **Constraint** objektu **UniqueConstraint** v **datové sadě** je hodnota atributu **msdata: Constraint** uvedená v elementu **Key** ve schématu.</span><span class="sxs-lookup"><span data-stu-id="4e479-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e479-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e479-125">See also</span></span>

- [<span data-ttu-id="4e479-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="4e479-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="4e479-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="4e479-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="4e479-128">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4e479-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
