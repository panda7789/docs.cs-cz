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
# <a name="xml-schema-constraints-and-relationships"></a>Omezení schématu XML a relací
Ve schématu jazyka definice schématu XML (XSD) můžete určit omezení (jedinečná omezení, omezení klíče a klíčenky) a vztahy (pomocí anotace **msdata:Relationship).** Toto téma vysvětluje, jak jsou interpretována omezení a vztahy zadané ve <xref:System.Data.DataSet>schématu XML pro generování .  
  
 Obecně platí, že ve schématu XML zadáte poznámku **msdata:Relationship,** pokud chcete generovat pouze relace v **datové sadě**. Další informace naleznete [v tématu Generování vztahů sady dat ze schématu XML (XSD).](generating-dataset-relations-from-xml-schema-xsd.md) Omezení (jedinečný, klíč a keyref) zadáte, pokud chcete generovat omezení v **datové sadě**. Všimněte si, že omezení klíče a keyref se také používají ke generování vztahů, jak je vysvětleno dále v tomto tématu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generování relace z omezení klíče a klíčové reference  
 Namísto určení anotace **msdata:Relationship** můžete zadat omezení klíče a klíče, která se používají během procesu mapování schématu XML ke generování nejen omezení, ale také vztahu v **datové sadě**. Pokud však `msdata:ConstraintOnly="true"` zadáte v elementu **keyref,** **dataset** bude obsahovat pouze omezení a nebude zahrnovat vztah.  
  
 Následující příklad ukazuje schéma XML, které obsahuje prvky **Order** a **OrderDetail,** které nejsou vnořené. Schéma také určuje omezení klíče a klíče.  
  
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
  
 Sada **dat,** která je generována během procesu mapování schématu XML, zahrnuje tabulky **Order** a **OrderDetail.** Kromě toho **DataSet** obsahuje vztahy a omezení. Následující příklad ukazuje tyto vztahy a omezení. Všimněte si, že schéma neurčuje anotaci **msdata:Relationship;** místo toho klíč a keyref omezení se používají ke generování vztahu.  
  
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
  
 V předchozím příkladu schématu nejsou vnořené prvky **Order** a **OrderDetail.** V následujícím příkladu schématu jsou tyto prvky vnořeny. Není však zadána žádná anotace **msdata:Relationship;** proto se předpokládá implicitní vztah. Další informace naleznete v [tématu Mapa implicitních vztahů mezi vnořené prvky schématu](map-implicit-relations-between-nested-schema-elements.md). Schéma také určuje omezení klíče a klíče.  
  
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
  
 Sada **dat,** která je výsledkem procesu mapování schématu XML, obsahuje dvě tabulky:  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** také obsahuje dvě relace (jeden na základě anotace **msdata:vztah** a druhý na základě omezení klíče a keyref) a různá omezení. Následující příklad ukazuje vztahy a omezení.  
  
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
  
 Pokud omezení keyref odkazující na vnořenou tabulku obsahuje anotaci **msdata:IsNested="true",** **dataset** vytvoří jednu vnořenou relaci, která je založena na omezení keyref a souvisejícím jedinečném omezení/klíči.  
  
## <a name="see-also"></a>Viz také

- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
