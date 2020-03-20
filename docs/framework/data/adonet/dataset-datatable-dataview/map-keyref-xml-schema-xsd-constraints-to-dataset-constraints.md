---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150880"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="9a602-102">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9a602-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="9a602-103">**Keyref** element umožňuje vytvořit propojení mezi prvky v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a602-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="9a602-104">To je podobné vztahu cizího klíče v relační databázi.</span><span class="sxs-lookup"><span data-stu-id="9a602-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="9a602-105">Pokud schéma určuje element **keyref,** prvek je převeden během procesu mapování schématu na odpovídající omezení cizího klíče na <xref:System.Data.DataSet>sloupce v tabulkách .</span><span class="sxs-lookup"><span data-stu-id="9a602-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9a602-106">Ve výchozím nastavení element **keyref** také generuje vztah s vlastnostmi **ParentTable**, **ChildTable**, **ParentColumn**a **ChildColumn** určenými pro relaci.</span><span class="sxs-lookup"><span data-stu-id="9a602-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="9a602-107">Následující tabulka popisuje **atributy msdata,** které můžete zadat v elementu **keyref.**</span><span class="sxs-lookup"><span data-stu-id="9a602-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="9a602-108">Název atributu</span><span class="sxs-lookup"><span data-stu-id="9a602-108">Attribute name</span></span>|<span data-ttu-id="9a602-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9a602-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9a602-110">**msdata:Pouze omezení**</span><span class="sxs-lookup"><span data-stu-id="9a602-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="9a602-111">Pokud **constraintOnly="true"** je zadán na **keyref** prvek ve schématu, je vytvořena omezení, ale je vytvořen žádný vztah.</span><span class="sxs-lookup"><span data-stu-id="9a602-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="9a602-112">Pokud tento atribut není zadán (nebo je nastavenna **na False**), jsou v **dataset**vytvořeny omezení i vztah .</span><span class="sxs-lookup"><span data-stu-id="9a602-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="9a602-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="9a602-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="9a602-114">Pokud je zadán atribut **ConstraintName,** jeho hodnota se používá jako název omezení.</span><span class="sxs-lookup"><span data-stu-id="9a602-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="9a602-115">V opačném případě atribut **name** elementu **keyref** ve schématu poskytuje název omezení v **dataset**.</span><span class="sxs-lookup"><span data-stu-id="9a602-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="9a602-116">**msdata:Aktualizovatpravidlo**</span><span class="sxs-lookup"><span data-stu-id="9a602-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="9a602-117">Pokud je atribut **UpdateRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **UpdateRule** v **sadě DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9a602-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9a602-118">V opačném případě je vlastnost **UpdateRule** nastavena na **možnost Kaskáda**.</span><span class="sxs-lookup"><span data-stu-id="9a602-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="9a602-119">**msdata:Odstranitpravidlo**</span><span class="sxs-lookup"><span data-stu-id="9a602-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="9a602-120">Pokud je atribut **DeleteRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti **omezení DeleteRule** v **sadě DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9a602-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9a602-121">V opačném případě je vlastnost **DeleteRule** nastavena na **možnost Kaskáda**.</span><span class="sxs-lookup"><span data-stu-id="9a602-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="9a602-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="9a602-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="9a602-123">Pokud **acceptRejectRule** atribut je zadán v **keyref** element ve schématu, jeho hodnota je **přiřazena AcceptRejectRule** vlastnost omezení v **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9a602-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="9a602-124">V opačném případě je vlastnost **AcceptRejectRule** nastavena na **položku None**.</span><span class="sxs-lookup"><span data-stu-id="9a602-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="9a602-125">Následující příklad obsahuje schéma, které určuje vztahy **klíče** a **keyref** mezi podřízeným prvkem **OrderNumber** elementu **Order** a podřízeným prvkem **OrderNo** prvku **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9a602-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="9a602-126">V příkladu **ordernumber** podřízený prvek **OrderDetail** element odkazuje na **OrderNo** klíčový podřízený prvek **Order** element.</span><span class="sxs-lookup"><span data-stu-id="9a602-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="9a602-127">Proces mapování schématu schématu schématu schématu XML (XSD) vytváří následující **datovou sadu** se dvěma tabulkami:</span><span class="sxs-lookup"><span data-stu-id="9a602-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="9a602-128">Kromě toho **DataSet** definuje následující omezení:</span><span class="sxs-lookup"><span data-stu-id="9a602-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="9a602-129">Jedinečné omezení v tabulce **Objednávka.**</span><span class="sxs-lookup"><span data-stu-id="9a602-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="9a602-130">Vztah mezi tabulkami **Order** a **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9a602-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9a602-131">**Vnořené** Vlastnost je nastavena na **False,** protože dva prvky nejsou vnořeny do schématu.</span><span class="sxs-lookup"><span data-stu-id="9a602-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="9a602-132">Omezení cizího klíče v tabulce **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9a602-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9a602-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a602-133">See also</span></span>

- [<span data-ttu-id="9a602-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9a602-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9a602-135">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9a602-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9a602-136">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9a602-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
