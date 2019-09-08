---
title: Omezení schématu XML a relací
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 76af1c2e9d85d18a68b8c0a947dfba3b3291326c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784189"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="b9da7-102">Omezení schématu XML a relací</span><span class="sxs-lookup"><span data-stu-id="b9da7-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="b9da7-103">Ve schématu XSD (XML Schema Definition Language) můžete určit omezení (jedinečné omezení, klíč a možnost keyref) a vztahy (pomocí poznámky **msdata: Relationship** ).</span><span class="sxs-lookup"><span data-stu-id="b9da7-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="b9da7-104">Toto téma vysvětluje, jak jsou interpretována omezení a vztahy, které jsou zadány ve schématu <xref:System.Data.DataSet>XML pro generování.</span><span class="sxs-lookup"><span data-stu-id="b9da7-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b9da7-105">Obecně platí, že ve schématu XML zadáte anotaci **msdata: Relationship** , pokud chcete generovat pouze relace v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="b9da7-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="b9da7-106">Další informace najdete v tématu [generování vztahů datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="b9da7-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="b9da7-107">Určete omezení (jedinečné, klíč, a keyref), pokud chcete generovat omezení v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="b9da7-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="b9da7-108">Všimněte si, že omezení Key a keyref se také používají ke generování vztahů, jak je vysvětleno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b9da7-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="b9da7-109">Generování vztahu z omezení klíče a elementu keyref</span><span class="sxs-lookup"><span data-stu-id="b9da7-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="b9da7-110">Namísto zadání poznámky **msdata: Relationship** můžete zadat omezení Key a keyref, která se používají během procesu mapování schématu XML pro generování nejen omezení, ale i vztahu v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="b9da7-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="b9da7-111">Pokud však zadáte `msdata:ConstraintOnly="true"` v elementu **keyref** , **datová sada** bude obsahovat pouze omezení a nebude obsahovat vztah.</span><span class="sxs-lookup"><span data-stu-id="b9da7-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="b9da7-112">Následující příklad ukazuje schéma XML, které obsahuje prvky **Order** a **OrderDetail** , které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="b9da7-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="b9da7-113">Schéma také určuje omezení Key a keyref.</span><span class="sxs-lookup"><span data-stu-id="b9da7-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="b9da7-114">**Datová sada** , která je generována během procesu mapování schématu XML, zahrnuje tabulky **Order** a **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="b9da7-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="b9da7-115">Kromě toho **datová sada** zahrnuje vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="b9da7-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="b9da7-116">Následující příklad ukazuje tyto vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="b9da7-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="b9da7-117">Všimněte si, že schéma neurčuje anotaci **msdata: Relationship** ; místo toho se k vygenerování vztahu použijí omezení Key a keyref.</span><span class="sxs-lookup"><span data-stu-id="b9da7-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```  
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
  
 <span data-ttu-id="b9da7-118">V předchozím příkladu schématu nejsou prvky **Order** a **OrderDetail** vnořené.</span><span class="sxs-lookup"><span data-stu-id="b9da7-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="b9da7-119">V následujícím příkladu schématu jsou tyto prvky vnořené.</span><span class="sxs-lookup"><span data-stu-id="b9da7-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="b9da7-120">Nicméně není zadána žádná **msdata: Poznámka vztahu** ; Proto se předpokládá implicitní vztah.</span><span class="sxs-lookup"><span data-stu-id="b9da7-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="b9da7-121">Další informace najdete v tématu [mapování implicitních vztahů mezi prvky vnořeného schématu](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="b9da7-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="b9da7-122">Schéma také určuje omezení Key a keyref.</span><span class="sxs-lookup"><span data-stu-id="b9da7-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="b9da7-123">**Datová sada** výsledná z procesu mapování schématu XML zahrnuje dvě tabulky:</span><span class="sxs-lookup"><span data-stu-id="b9da7-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="b9da7-124">**Datová sada** obsahuje také dvě relace (jedna na základě poznámky **msdata: Relationship** a druhá v závislosti na omezeních Key a keyref) a v různých omezeních.</span><span class="sxs-lookup"><span data-stu-id="b9da7-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="b9da7-125">Následující příklad ukazuje vztahy a omezení.</span><span class="sxs-lookup"><span data-stu-id="b9da7-125">The following example shows the relations and constraints.</span></span>  
  
```  
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
  
 <span data-ttu-id="b9da7-126">Pokud omezení elementu keyref odkazující na vnořenou tabulku obsahuje anotaci **msdata: Nested = "true"** , **datová sada** vytvoří jednu vnořenou relaci, která je založena na omezení elementu keyref a souvisejícím jedinečném omezení/klíče.</span><span class="sxs-lookup"><span data-stu-id="b9da7-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9da7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9da7-127">See also</span></span>

- [<span data-ttu-id="b9da7-128">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b9da7-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="b9da7-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b9da7-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
