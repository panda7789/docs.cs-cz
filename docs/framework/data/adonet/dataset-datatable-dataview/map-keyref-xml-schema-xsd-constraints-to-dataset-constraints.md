---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: b5ffe69886b08903feab4373b1cd5c5244b3b3b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784509"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d502a-102">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d502a-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d502a-103">Element **keyref** umožňuje vytvořit propojení mezi prvky v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d502a-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="d502a-104">To se podobá relaci cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="d502a-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="d502a-105">Pokud schéma určuje element **keyref** , je element převeden během procesu mapování schématu na odpovídající omezení cizího klíče pro sloupce v tabulkách <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="d502a-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d502a-106">Ve výchozím nastavení element **keyref** také generuje relaci s vlastnostmi **nadřazené tabulky**, **podřízenosti**, **ParentColumn**a **ChildColumn** , které jsou zadány v relaci.</span><span class="sxs-lookup"><span data-stu-id="d502a-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="d502a-107">Následující tabulka popisuje atributy **msdata** , které lze zadat v elementu **keyref** .</span><span class="sxs-lookup"><span data-stu-id="d502a-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="d502a-108">Název atributu</span><span class="sxs-lookup"><span data-stu-id="d502a-108">Attribute name</span></span>|<span data-ttu-id="d502a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d502a-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d502a-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="d502a-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="d502a-111">Pokud je v elementu **keyref** ve schématu zadán parametr **ConstraintOnly = "true"** , je vytvořeno omezení, ale není vytvořena žádná relace.</span><span class="sxs-lookup"><span data-stu-id="d502a-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="d502a-112">Pokud tento atribut není zadán (nebo je nastaven na **hodnotu false**), je omezení i vztah vytvořen v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d502a-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="d502a-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="d502a-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="d502a-114">Pokud je zadán atribut **Constraint** , použije se jako název omezení jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="d502a-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="d502a-115">Jinak atribut **Name** elementu **keyref** ve schématu poskytuje název omezení v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d502a-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="d502a-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="d502a-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="d502a-117">Pokud je atribut **UpdateRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **UpdateRule** v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d502a-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="d502a-118">V opačném případě je vlastnost **UpdateRule** nastavena na hodnotu **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="d502a-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="d502a-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="d502a-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="d502a-120">Pokud je atribut **DeleteRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **DeleteRule** v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d502a-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="d502a-121">V opačném případě je vlastnost **DeleteRule** nastavena na hodnotu **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="d502a-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="d502a-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="d502a-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="d502a-123">Pokud je atribut **AcceptRejectRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **AcceptRejectRule** v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="d502a-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="d502a-124">V opačném případě je vlastnost **AcceptRejectRule** nastavena na **hodnotu None**.</span><span class="sxs-lookup"><span data-stu-id="d502a-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="d502a-125">Následující příklad obsahuje schéma, které určuje vztahy **Key** a **keyref** mezi podřízeným prvkem **OrderNumber** elementu **Order** a podřízeným prvkem **OrderNo** **OrderDetail** objekt.</span><span class="sxs-lookup"><span data-stu-id="d502a-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="d502a-126">V příkladu podřízený element **OrderNumber** elementu **OrderDetail** odkazuje na podřízený element Key elementu **OrderNo** elementu **Order** .</span><span class="sxs-lookup"><span data-stu-id="d502a-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="d502a-127">Proces mapování schématu XSD (XML Schema Definition Language) vytvoří následující **datovou sadu** se dvěma tabulkami:</span><span class="sxs-lookup"><span data-stu-id="d502a-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="d502a-128">Kromě toho **datová sada** definuje následující omezení:</span><span class="sxs-lookup"><span data-stu-id="d502a-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="d502a-129">Jedinečné omezení v tabulce **Order** .</span><span class="sxs-lookup"><span data-stu-id="d502a-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="d502a-130">Vztah mezi tabulkami **Order** a **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="d502a-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="d502a-131">**Vnořená** vlastnost je nastavena na **hodnotu false** , protože tyto dva prvky nejsou vnořené ve schématu.</span><span class="sxs-lookup"><span data-stu-id="d502a-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="d502a-132">Omezení cizího klíče v tabulce **OrderDetail**</span><span class="sxs-lookup"><span data-stu-id="d502a-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d502a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d502a-133">See also</span></span>

- [<span data-ttu-id="d502a-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d502a-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="d502a-135">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d502a-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="d502a-136">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d502a-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
