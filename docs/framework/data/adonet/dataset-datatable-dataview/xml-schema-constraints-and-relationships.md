---
title: Omezení schématu XML a relací
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150711"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="17a5c-102">Omezení schématu XML a relací</span><span class="sxs-lookup"><span data-stu-id="17a5c-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="17a5c-103">Ve schématu jazyka definice schématu XML (XSD) můžete určit omezení (jedinečná omezení, omezení klíče a klíčenky) a vztahy (pomocí anotace **msdata:Relationship).**</span><span class="sxs-lookup"><span data-stu-id="17a5c-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="17a5c-104">Toto téma vysvětluje, jak jsou interpretována omezení a vztahy zadané ve <xref:System.Data.DataSet>schématu XML pro generování .</span><span class="sxs-lookup"><span data-stu-id="17a5c-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="17a5c-105">Obecně platí, že ve schématu XML zadáte poznámku **msdata:Relationship,** pokud chcete generovat pouze relace v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="17a5c-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="17a5c-106">Další informace naleznete [v tématu Generování vztahů sady dat ze schématu XML (XSD).](generating-dataset-relations-from-xml-schema-xsd.md)</span><span class="sxs-lookup"><span data-stu-id="17a5c-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="17a5c-107">Omezení (jedinečný, klíč a keyref) zadáte, pokud chcete generovat omezení v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="17a5c-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="17a5c-108">Všimněte si, že omezení klíče a keyref se také používají ke generování vztahů, jak je vysvětleno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="17a5c-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="17a5c-109">Generování relace z omezení klíče a klíčové reference</span><span class="sxs-lookup"><span data-stu-id="17a5c-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="17a5c-110">Namísto určení anotace **msdata:Relationship** můžete zadat omezení klíče a klíče, která se používají během procesu mapování schématu XML ke generování nejen omezení, ale také vztahu v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="17a5c-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="17a5c-111">Pokud však `msdata:ConstraintOnly="true"` zadáte v elementu **keyref,** **dataset** bude obsahovat pouze omezení a nebude zahrnovat vztah.</span><span class="sxs-lookup"><span data-stu-id="17a5c-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="17a5c-112">Následující příklad ukazuje schéma XML, které obsahuje prvky **Order** a **OrderDetail,** které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="17a5c-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="17a5c-113">Schéma také určuje omezení klíče a klíče.</span><span class="sxs-lookup"><span data-stu-id="17a5c-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="17a5c-114">Sada **dat,** která je generována během procesu mapování schématu XML, zahrnuje tabulky **Order** a **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="17a5c-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="17a5c-115">Kromě toho **DataSet** obsahuje vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="17a5c-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="17a5c-116">Následující příklad ukazuje tyto vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="17a5c-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="17a5c-117">Všimněte si, že schéma neurčuje anotaci **msdata:Relationship;** místo toho klíč a keyref omezení se používají ke generování vztahu.</span><span class="sxs-lookup"><span data-stu-id="17a5c-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="17a5c-118">V předchozím příkladu schématu nejsou vnořené prvky **Order** a **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="17a5c-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="17a5c-119">V následujícím příkladu schématu jsou tyto prvky vnořeny.</span><span class="sxs-lookup"><span data-stu-id="17a5c-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="17a5c-120">Není však zadána žádná anotace **msdata:Relationship;** proto se předpokládá implicitní vztah.</span><span class="sxs-lookup"><span data-stu-id="17a5c-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="17a5c-121">Další informace naleznete v [tématu Mapa implicitních vztahů mezi vnořené prvky schématu](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="17a5c-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="17a5c-122">Schéma také určuje omezení klíče a klíče.</span><span class="sxs-lookup"><span data-stu-id="17a5c-122">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 <span data-ttu-id="17a5c-123">Sada **dat,** která je výsledkem procesu mapování schématu XML, obsahuje dvě tabulky:</span><span class="sxs-lookup"><span data-stu-id="17a5c-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="17a5c-124">**DataSet** také obsahuje dvě relace (jeden na základě anotace **msdata:vztah** a druhý na základě omezení klíče a keyref) a různá omezení.</span><span class="sxs-lookup"><span data-stu-id="17a5c-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="17a5c-125">Následující příklad ukazuje vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="17a5c-125">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="17a5c-126">Pokud omezení keyref odkazující na vnořenou tabulku obsahuje anotaci **msdata:IsNested="true",** **dataset** vytvoří jednu vnořenou relaci, která je založena na omezení keyref a souvisejícím jedinečném omezení/klíči.</span><span class="sxs-lookup"><span data-stu-id="17a5c-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a5c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="17a5c-127">See also</span></span>

- [<span data-ttu-id="17a5c-128">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="17a5c-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="17a5c-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17a5c-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
