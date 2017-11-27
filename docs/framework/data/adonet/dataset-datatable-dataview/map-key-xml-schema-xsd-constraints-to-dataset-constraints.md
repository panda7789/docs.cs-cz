---
title: "Mapa klíč omezení schématu XML (XSD) k omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f5247d0ccfd2ceec641ff29d29b889a55c1a5e12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="53442-102">Mapa klíč omezení schématu XML (XSD) k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="53442-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="53442-103">Ve schématu, můžete určit klíče omezení na element nebo atribut, pomocí **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="53442-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="53442-104">Element nebo atribut, na kterém je zadán omezení klíče musí mít jedinečné hodnoty v žádné instanci schématu a nesmí obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="53442-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="53442-105">Omezení klíče je podobná jedinečné omezení, s tím rozdílem, že sloupec, na kterém je definovaný omezení klíče nesmí mít hodnotu null. hodnoty.</span><span class="sxs-lookup"><span data-stu-id="53442-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="53442-106">V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="53442-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="53442-107">Název atributu</span><span class="sxs-lookup"><span data-stu-id="53442-107">Attribute name</span></span>|<span data-ttu-id="53442-108">Popis</span><span class="sxs-lookup"><span data-stu-id="53442-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="53442-109">**MSDATA:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="53442-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="53442-110">Pokud tento atribut je určen, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="53442-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="53442-111">Jinak **název** atribut poskytuje hodnota název omezení.</span><span class="sxs-lookup"><span data-stu-id="53442-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="53442-112">**MSDATA:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="53442-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="53442-113">Pokud `PrimaryKey="true"` je k dispozici, **IsPrimaryKey** omezení je nastavena na **true**, a tím primární klíč.</span><span class="sxs-lookup"><span data-stu-id="53442-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="53442-114">**AllowDBNull** sloupce je nastavena na **false**, protože primární klíče nesmí mít hodnotu null. hodnoty.</span><span class="sxs-lookup"><span data-stu-id="53442-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="53442-115">Převádění, ve kterém je omezení klíče zadané schéma, proces mapování vytvoří omezení unique u tabulky s **AllowDBNull** sloupce vlastnost nastavena na hodnotu **false** pro každý sloupec v omezení.</span><span class="sxs-lookup"><span data-stu-id="53442-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="53442-116">**IsPrimaryKey** jedinečné omezení je také nastavena na **false** Pokud jste zadali `msdata:PrimaryKey="true"` na **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="53442-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="53442-117">Toto je stejný jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="53442-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="53442-118">V následujícím příkladu schématu **klíč** element určuje klíče omezení na **CustomerID** elementu.</span><span class="sxs-lookup"><span data-stu-id="53442-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="53442-119">**Klíč** element určuje, že hodnoty **CustomerID** podřízený element **zákazníci** element musí mít jedinečné hodnoty a nesmí obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="53442-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="53442-120">V překladu schéma schématu XML definition language (XSD), proces mapování vytvoří v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="53442-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="53442-121">Mapování schémat XML také vytvoří **UniqueConstraint** na **CustomerID** sloupce, jak je znázorněno v následující <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="53442-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="53442-122">(Pro jednoduchost, jsou pouze relevantní vlastnosti zobrazené.)</span><span class="sxs-lookup"><span data-stu-id="53442-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="53442-123">V **datovou sadu** , která je vytvořena **IsPrimaryKey** vlastnost **UniqueConstraint** je nastaven na **true** protože schématu Určuje `msdata:PrimaryKey="true"` v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="53442-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="53442-124">Hodnota **ConstraintName** vlastnost **UniqueConstraint** v **datovou sadu** je hodnota **msdata:ConstraintName** Zadaný atribut v **klíč** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="53442-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53442-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="53442-125">See Also</span></span>  
 [<span data-ttu-id="53442-126">Omezení (XSD) schématu XML mapování k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="53442-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="53442-127">Generování datovou sadu vztahů ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="53442-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="53442-128">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="53442-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
