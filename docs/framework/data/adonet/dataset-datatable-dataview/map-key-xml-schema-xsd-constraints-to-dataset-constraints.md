---
title: Mapa klíč omezení schématu XML (XSD) k omezení datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: ad39fd75a3f8872ed2c24a65481209e3c772a638
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="54c34-102">Mapa klíč omezení schématu XML (XSD) k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="54c34-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="54c34-103">Ve schématu, můžete určit klíče omezení na element nebo atribut, pomocí **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="54c34-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="54c34-104">Element nebo atribut, na kterém je zadán omezení klíče musí mít jedinečné hodnoty v žádné instanci schématu a nesmí obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="54c34-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="54c34-105">Omezení klíče je podobná jedinečné omezení, s tím rozdílem, že sloupec, na kterém je definovaný omezení klíče nesmí mít hodnotu null. hodnoty.</span><span class="sxs-lookup"><span data-stu-id="54c34-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="54c34-106">V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="54c34-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="54c34-107">Název atributu</span><span class="sxs-lookup"><span data-stu-id="54c34-107">Attribute name</span></span>|<span data-ttu-id="54c34-108">Popis</span><span class="sxs-lookup"><span data-stu-id="54c34-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="54c34-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="54c34-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="54c34-110">Pokud tento atribut je určen, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="54c34-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="54c34-111">Jinak **název** atribut poskytuje hodnota název omezení.</span><span class="sxs-lookup"><span data-stu-id="54c34-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="54c34-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="54c34-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="54c34-113">Pokud `PrimaryKey="true"` je k dispozici, **IsPrimaryKey** omezení je nastavena na **true**, a tím primární klíč.</span><span class="sxs-lookup"><span data-stu-id="54c34-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="54c34-114">**AllowDBNull** sloupce je nastavena na **false**, protože primární klíče nesmí mít hodnotu null. hodnoty.</span><span class="sxs-lookup"><span data-stu-id="54c34-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="54c34-115">Převádění, ve kterém je omezení klíče zadané schéma, proces mapování vytvoří omezení unique u tabulky s **AllowDBNull** sloupce vlastnost nastavena na hodnotu **false** pro každý sloupec v omezení.</span><span class="sxs-lookup"><span data-stu-id="54c34-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="54c34-116">**IsPrimaryKey** jedinečné omezení je také nastavena na **false** Pokud jste zadali `msdata:PrimaryKey="true"` na **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="54c34-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="54c34-117">Toto je stejný jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="54c34-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="54c34-118">V následujícím příkladu schématu **klíč** element určuje klíče omezení na **CustomerID** elementu.</span><span class="sxs-lookup"><span data-stu-id="54c34-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="54c34-119">**Klíč** element určuje, že hodnoty **CustomerID** podřízený element **zákazníci** element musí mít jedinečné hodnoty a nesmí obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="54c34-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="54c34-120">V překladu schéma schématu XML definition language (XSD), proces mapování vytvoří v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="54c34-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="54c34-121">Mapování schémat XML také vytvoří **UniqueConstraint** na **CustomerID** sloupce, jak je znázorněno v následující <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="54c34-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="54c34-122">(Pro jednoduchost, jsou pouze relevantní vlastnosti zobrazené.)</span><span class="sxs-lookup"><span data-stu-id="54c34-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="54c34-123">V **datovou sadu** , která je vytvořena **IsPrimaryKey** vlastnost **UniqueConstraint** je nastaven na **true** protože schématu Určuje `msdata:PrimaryKey="true"` v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="54c34-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="54c34-124">Hodnota **ConstraintName** vlastnost **UniqueConstraint** v **datovou sadu** je hodnota **msdata:ConstraintName** Zadaný atribut v **klíč** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="54c34-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c34-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="54c34-125">See Also</span></span>  
 [<span data-ttu-id="54c34-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="54c34-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="54c34-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="54c34-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="54c34-128">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="54c34-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
