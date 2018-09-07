---
title: Omezení schématu XML a relací
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: bcb6e257a40040701612b73768a98e056bccd6c5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086995"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="7f30e-102">Omezení schématu XML a relací</span><span class="sxs-lookup"><span data-stu-id="7f30e-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="7f30e-103">Ve schématu XML definice jazyk (XSD) schématu, můžete zadat omezení (jedinečný, klíče a omezení keyref) a vztahů (pomocí **msdata:Relationship** poznámky).</span><span class="sxs-lookup"><span data-stu-id="7f30e-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="7f30e-104">Toto téma vysvětluje, jak se interpretují omezení a vztahů zadané ve schématu XML ke generování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7f30e-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7f30e-105">Obecně platí, ve schématu XML, můžete zadat **msdata:Relationship** anotace, pokud chcete vygenerovat pouze vztahy v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="7f30e-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="7f30e-106">Další informace najdete v tématu [generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7f30e-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="7f30e-107">Zadat omezení (jedinečný, klíč a keyref) Pokud chcete generovat omezení **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="7f30e-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="7f30e-108">Všimněte si, že key ani keyref omezení se také používají ke generování relace, jak je popsáno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7f30e-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="7f30e-109">Generování vztahu z klíče a keyref omezení</span><span class="sxs-lookup"><span data-stu-id="7f30e-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="7f30e-110">Místo zadání **msdata:Relationship** poznámky, můžete zadat klíč a keyref omezení, které se používají během procesu mapování schématu XML ke generování nejen omezení, ale také relace v  **Datová sada**.</span><span class="sxs-lookup"><span data-stu-id="7f30e-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="7f30e-111">Ale pokud zadáte `msdata:ConstraintOnly="true"` v **keyref** elementu, **datovou sadu** bude obsahovat pouze omezení a nebudou obsahovat relace.</span><span class="sxs-lookup"><span data-stu-id="7f30e-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="7f30e-112">Následující příklad ukazuje schématu XML, který zahrnuje **pořadí** a **OrderDetail** elementy, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="7f30e-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="7f30e-113">Schéma také určuje key ani keyref omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="7f30e-114">**Datovou sadu** , který je generován během schématu XML, zahrnuje proces mapování **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="7f30e-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="7f30e-115">Kromě toho **datovou sadu** zahrnuje relace a omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="7f30e-116">Následující příklad ukazuje tyto relace a omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="7f30e-117">Všimněte si, že schéma neurčuje **msdata:Relationship** anotaci; místo toho key ani keyref omezení slouží ke generování vztah.</span><span class="sxs-lookup"><span data-stu-id="7f30e-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
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
  
 <span data-ttu-id="7f30e-118">V předchozím příkladu schématu **pořadí** a **OrderDetail** nejsou vnořené elementy.</span><span class="sxs-lookup"><span data-stu-id="7f30e-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="7f30e-119">V následujícím příkladu schéma těchto elementů je vnořeno.</span><span class="sxs-lookup"><span data-stu-id="7f30e-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="7f30e-120">Ale žádný **msdata:Relationship** je určena anotace; proto se předpokládá implicitní vztah.</span><span class="sxs-lookup"><span data-stu-id="7f30e-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="7f30e-121">Další informace najdete v tématu [mapy implicitní vztahy mezi vnořené elementy schématu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="7f30e-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="7f30e-122">Schéma také určuje key ani keyref omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="7f30e-123">**Datovou sadu** vyplývající z procesu mapování schématu XML obsahuje dvě tabulky:</span><span class="sxs-lookup"><span data-stu-id="7f30e-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="7f30e-124">**Datovou sadu** také obsahuje dvě relace (jeden na základě **msdata:relationship** poznámky a druhý podle key ani keyref omezení) a různé omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="7f30e-125">Následující příklad ukazuje, relace a omezení.</span><span class="sxs-lookup"><span data-stu-id="7f30e-125">The following example shows the relations and constraints.</span></span>  
  
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
  
 <span data-ttu-id="7f30e-126">Pokud keyref omezení odkazování na vnořená tabulka obsahuje **msdata:IsNested = "true"** poznámky, **datovou sadu** vytvoří jeden vnořené relace, která je založena na omezení keyref a související omezení unique/key.</span><span class="sxs-lookup"><span data-stu-id="7f30e-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f30e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f30e-127">See Also</span></span>  
 [<span data-ttu-id="7f30e-128">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7f30e-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="7f30e-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7f30e-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
