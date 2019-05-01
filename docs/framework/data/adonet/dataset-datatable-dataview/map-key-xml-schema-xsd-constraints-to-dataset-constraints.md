---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 46a980f06198c6f06bb13824c65cfb5309eec154
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034226"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="cf5c6-102">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="cf5c6-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="cf5c6-103">Ve schématu, můžete určit klíče omezení na element nebo atribut, pomocí **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="cf5c6-104">Element nebo atribut, na kterém je zadáno klíčové omezení musí mít jedinečné hodnoty v žádné instanci schéma a nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="cf5c6-105">Omezení klíče je podobná omezení unique, s tím rozdílem, že sloupec, na kterém je definována omezení klíče nesmí obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="cf5c6-106">V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="cf5c6-107">Název atributu</span><span class="sxs-lookup"><span data-stu-id="cf5c6-107">Attribute name</span></span>|<span data-ttu-id="cf5c6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cf5c6-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cf5c6-109">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="cf5c6-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="cf5c6-110">Pokud tento atribut není zadán, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="cf5c6-111">V opačném případě **název** atributu obsahuje hodnotu název omezení.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="cf5c6-112">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="cf5c6-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="cf5c6-113">Pokud `PrimaryKey="true"` je k dispozici, **isprimarykey hodnotu** omezení je nastavena na **true**, díky čemuž je primární klíč.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="cf5c6-114">**AllowDBNull** sloupce je nastavena na **false**, protože primární klíče nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="cf5c6-115">Při převodu schématu, ve které je zadáno klíčových omezení, proces mapování vytvoří omezení unique u tabulky se **AllowDBNull** sloupce nastavenou na **false** pro každý sloupec v omezení.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="cf5c6-116">**Isprimarykey hodnotu** jedinečné omezení je také nastavena na **false** mít uvedeno `msdata:PrimaryKey="true"` na **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="cf5c6-117">To je stejný jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="cf5c6-118">V následujícím příkladu schématu **klíč** prvek určuje klíče omezení na **CustomerID** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="cf5c6-119">**Klíč** element určuje, že hodnoty **CustomerID** podřízený prvek **zákazníkům** element musí mít jedinečné hodnoty a nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="cf5c6-120">Při překladu jazyk (XSD) schématu definice schématu XML, proces mapování vytvoří v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="cf5c6-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="cf5c6-121">Také vytvoří mapování schématu XML **UniqueConstraint** na **CustomerID** sloupce, jak je znázorněno v následujícím <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cf5c6-122">(Pro jednoduchost, pouze relevantní jsou zobrazeny vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="cf5c6-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="cf5c6-123">V **datovou sadu** , který je generován, **isprimarykey hodnotu** vlastnost **UniqueConstraint** je nastavena na **true** protože schématu Určuje `msdata:PrimaryKey="true"` v **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="cf5c6-124">Hodnota **ConstraintName** vlastnost **UniqueConstraint** v **datovou sadu** je hodnota **msdata:ConstraintName** zadaný v atributu **klíč** element ve schématu.</span><span class="sxs-lookup"><span data-stu-id="cf5c6-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5c6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf5c6-125">See also</span></span>

- [<span data-ttu-id="cf5c6-126">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="cf5c6-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="cf5c6-127">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="cf5c6-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="cf5c6-128">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="cf5c6-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
