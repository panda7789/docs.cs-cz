---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 4cc4cb530b7252f35469fd4bb43bf6da9c1a3e24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604026"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="887d7-102">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="887d7-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="887d7-103">**Keyref** element slouží k vytvoření vazeb mezi prvky v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="887d7-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="887d7-104">Toto je podobný vztahu cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="887d7-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="887d7-105">Pokud schéma určuje **keyref** elementu, element je převeden při rušení mapování schématu odpovídající omezení cizího klíče na sloupce v tabulkách <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="887d7-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="887d7-106">Ve výchozím nastavení **keyref** element zároveň vytvoří relaci, se **ParentTable**, **tabulka**, **ParentColumn**a  **ChildColumn** vlastnosti zadané na vztah.</span><span class="sxs-lookup"><span data-stu-id="887d7-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="887d7-107">V následující tabulce jsou podrobněji popsány dále **msdata** atributy můžete zadat v **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="887d7-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="887d7-108">Název atributu</span><span class="sxs-lookup"><span data-stu-id="887d7-108">Attribute name</span></span>|<span data-ttu-id="887d7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="887d7-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="887d7-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="887d7-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="887d7-111">Pokud **ConstraintOnly = "true"** je zadaný na **keyref** element ve schématu, vytvoření omezení, ale žádný vztah se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="887d7-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="887d7-112">Pokud tento atribut není zadán (nebo je nastaven na **False**), omezení a vztahu se vytvoří v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="887d7-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="887d7-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="887d7-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="887d7-114">Pokud **ConstraintName** je zadán atribut, jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="887d7-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="887d7-115">V opačném případě **název** atribut **keyref** element ve schématu, poskytuje název omezení v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="887d7-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="887d7-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="887d7-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="887d7-117">Pokud **UpdateRule** je zadán atribut v **keyref** element ve schématu, její hodnota je přiřazená **UpdateRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="887d7-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="887d7-118">V opačném případě **UpdateRule** je nastavena na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="887d7-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="887d7-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="887d7-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="887d7-120">Pokud **DeletRule** je zadán atribut v **keyref** element ve schématu, její hodnota je přiřazená **DeletRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="887d7-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="887d7-121">V opačném případě **DeletRule** je nastavena na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="887d7-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="887d7-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="887d7-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="887d7-123">Pokud **AcceptRejectRule** je zadán atribut v **keyref** element ve schématu, jeho hodnota přiřazena **AcceptRejectRule** vlastnost omezení  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="887d7-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="887d7-124">V opačném případě **AcceptRejectRule** je nastavena na **žádný**.</span><span class="sxs-lookup"><span data-stu-id="887d7-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="887d7-125">Následující příklad obsahuje schéma, které se určuje **klíč** a **keyref** vztahy mezi **OrderNumber** podřízený prvek **pořadí**  elementu a **OrderNo** podřízený prvek **OrderDetail** elementu.</span><span class="sxs-lookup"><span data-stu-id="887d7-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="887d7-126">V tomto příkladu **OrderNumber** podřízený prvek **OrderDetail** element odkazuje na **OrderNo** klíče podřízený prvek **pořadí**elementu.</span><span class="sxs-lookup"><span data-stu-id="887d7-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="887d7-127">Proces mapování schématu XML definice jazyk (XSD) schématu vytvoří následující **datovou sadu** se dvěma tabulkami:</span><span class="sxs-lookup"><span data-stu-id="887d7-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="887d7-128">Kromě toho **datovou sadu** definuje následující omezení:</span><span class="sxs-lookup"><span data-stu-id="887d7-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="887d7-129">Omezení unique u **pořadí** tabulky.</span><span class="sxs-lookup"><span data-stu-id="887d7-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="887d7-130">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="887d7-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="887d7-131">**Vnořené** je nastavena na **False** dva prvky nejsou vnořené ve schématu.</span><span class="sxs-lookup"><span data-stu-id="887d7-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
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
  
- <span data-ttu-id="887d7-132">Omezení cizího klíče na **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="887d7-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="887d7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="887d7-133">See also</span></span>

- [<span data-ttu-id="887d7-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="887d7-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="887d7-135">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="887d7-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="887d7-136">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="887d7-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
