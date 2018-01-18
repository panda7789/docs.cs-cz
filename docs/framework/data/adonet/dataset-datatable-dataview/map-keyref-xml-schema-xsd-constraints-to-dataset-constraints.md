---
title: "Mapa keyref omezení schématu XML (XSD) k omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e364efe0856a5291fc8157ef6ab185c2438a3347
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="2fcf2-102">Mapa keyref omezení schématu XML (XSD) k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="2fcf2-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="2fcf2-103">**Keyref** element umožňuje vytváření propojení mezi prvky dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="2fcf2-104">Toto je podobná relace cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="2fcf2-105">Pokud schéma určuje **keyref** elementu, element je převést během procesu schéma mapování na odpovídající omezení cizího klíče u sloupců v tabulkách <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="2fcf2-106">Ve výchozím nastavení **keyref** element také vytváří vztah, se **ParentTable**, **tabulka**, **ParentColumn**a  **ChildColumn** na vztah byly zadány vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="2fcf2-107">V následující tabulce jsou podrobněji popsány dále **msdata** atributy můžete zadat v **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="2fcf2-108">Název atributu</span><span class="sxs-lookup"><span data-stu-id="2fcf2-108">Attribute name</span></span>|<span data-ttu-id="2fcf2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2fcf2-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2fcf2-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="2fcf2-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="2fcf2-111">Pokud **ConstraintOnly = "true"** je zadaný na **keyref** element ve schématu omezení je vytvořen, ale je vytvořen žádný vztah.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="2fcf2-112">Pokud tento atribut nezadá (nebo je nastaven na **False**), omezení a vztah se vytvoří v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="2fcf2-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="2fcf2-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="2fcf2-114">Pokud **ConstraintName** zadán atribut, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="2fcf2-115">Jinak **název** atribut **keyref** element ve schématu poskytuje název omezení v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="2fcf2-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="2fcf2-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="2fcf2-117">Pokud **UpdateRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **UpdateRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="2fcf2-118">V opačném případě **UpdateRule** je nastavena na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="2fcf2-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="2fcf2-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="2fcf2-120">Pokud **DeletRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **DeletRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="2fcf2-121">V opačném případě **DeletRule** je nastavena na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="2fcf2-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="2fcf2-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="2fcf2-123">Pokud **AcceptRejectRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **AcceptRejectRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="2fcf2-124">V opačném případě **AcceptRejectRule** je nastavena na **žádné**.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="2fcf2-125">Následující příklad obsahuje schéma, které určuje **klíč** a **keyref** vztahy mezi **OrderNumber** podřízený element **pořadí**  elementu a **OrderNo** podřízený element **OrderDetail** element.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="2fcf2-126">V příkladu **OrderNumber** podřízený element **OrderDetail** element odkazuje **OrderNo** klíče podřízený element **pořadí**elementu.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="2fcf2-127">Proces mapování schématu XML definice jazyka (XSD) schématu vytváří následující **datovou sadu** s dvou tabulek:</span><span class="sxs-lookup"><span data-stu-id="2fcf2-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="2fcf2-128">Kromě toho **datovou sadu** definuje následující omezení:</span><span class="sxs-lookup"><span data-stu-id="2fcf2-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="2fcf2-129">Jedinečná omezení **pořadí** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="2fcf2-130">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="2fcf2-131">**Vnořené** je nastavena na **False** nejsou vnořené dva elementy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
-   <span data-ttu-id="2fcf2-132">Omezení cizího klíče na **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2fcf2-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2fcf2-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fcf2-133">See Also</span></span>  
 [<span data-ttu-id="2fcf2-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="2fcf2-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="2fcf2-135">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2fcf2-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="2fcf2-136">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2fcf2-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
