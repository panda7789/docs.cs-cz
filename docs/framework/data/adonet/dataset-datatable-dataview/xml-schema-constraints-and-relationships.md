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
# <a name="xml-schema-constraints-and-relationships"></a>Omezení schématu XML a relací
Ve schématu XSD (XML Schema Definition Language) můžete určit omezení (jedinečné omezení, klíč a možnost keyref) a vztahy (pomocí poznámky **msdata: Relationship** ). Toto téma vysvětluje, jak jsou interpretována omezení a vztahy, které jsou zadány ve schématu <xref:System.Data.DataSet>XML pro generování.  
  
 Obecně platí, že ve schématu XML zadáte anotaci **msdata: Relationship** , pokud chcete generovat pouze relace v **datové sadě**. Další informace najdete v tématu [generování vztahů datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md). Určete omezení (jedinečné, klíč, a keyref), pokud chcete generovat omezení v **datové sadě**. Všimněte si, že omezení Key a keyref se také používají ke generování vztahů, jak je vysvětleno dále v tomto tématu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generování vztahu z omezení klíče a elementu keyref  
 Namísto zadání poznámky **msdata: Relationship** můžete zadat omezení Key a keyref, která se používají během procesu mapování schématu XML pro generování nejen omezení, ale i vztahu v **datové sadě**. Pokud však zadáte `msdata:ConstraintOnly="true"` v elementu **keyref** , **datová sada** bude obsahovat pouze omezení a nebude obsahovat vztah.  
  
 Následující příklad ukazuje schéma XML, které obsahuje prvky **Order** a **OrderDetail** , které nejsou vnořené. Schéma také určuje omezení Key a keyref.  
  
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
  
 **Datová sada** , která je generována během procesu mapování schématu XML, zahrnuje tabulky **Order** a **OrderDetail** . Kromě toho **datová sada** zahrnuje vztahy a omezení. Následující příklad ukazuje tyto vztahy a omezení. Všimněte si, že schéma neurčuje anotaci **msdata: Relationship** ; místo toho se k vygenerování vztahu použijí omezení Key a keyref.  
  
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
  
 V předchozím příkladu schématu nejsou prvky **Order** a **OrderDetail** vnořené. V následujícím příkladu schématu jsou tyto prvky vnořené. Nicméně není zadána žádná **msdata: Poznámka vztahu** ; Proto se předpokládá implicitní vztah. Další informace najdete v tématu [mapování implicitních vztahů mezi prvky vnořeného schématu](map-implicit-relations-between-nested-schema-elements.md). Schéma také určuje omezení Key a keyref.  
  
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
  
 **Datová sada** výsledná z procesu mapování schématu XML zahrnuje dvě tabulky:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **Datová sada** obsahuje také dvě relace (jedna na základě poznámky **msdata: Relationship** a druhá v závislosti na omezeních Key a keyref) a v různých omezeních. Následující příklad ukazuje vztahy a omezení.  
  
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
  
 Pokud omezení elementu keyref odkazující na vnořenou tabulku obsahuje anotaci **msdata: Nested = "true"** , **datová sada** vytvoří jednu vnořenou relaci, která je založena na omezení elementu keyref a souvisejícím jedinečném omezení/klíče.  
  
## <a name="see-also"></a>Viz také:

- [Odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
