---
title: Omezení schématu XML a relací
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 990ae2eef8d9fbd28472494c989ae9ecca34251d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119779"
---
# <a name="xml-schema-constraints-and-relationships"></a>Omezení schématu XML a relací
Ve schématu XML definice jazyk (XSD) schématu, můžete zadat omezení (jedinečný, klíče a omezení keyref) a vztahů (pomocí **msdata:Relationship** poznámky). Toto téma vysvětluje, jak se interpretují omezení a vztahů zadané ve schématu XML ke generování <xref:System.Data.DataSet>.  
  
 Obecně platí, ve schématu XML, můžete zadat **msdata:Relationship** anotace, pokud chcete vygenerovat pouze vztahy v **datovou sadu**. Další informace najdete v tématu [generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Zadat omezení (jedinečný, klíč a keyref) Pokud chcete generovat omezení **datovou sadu**. Všimněte si, že key ani keyref omezení se také používají ke generování relace, jak je popsáno dále v tomto tématu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generování vztahu z klíče a keyref omezení  
 Místo zadání **msdata:Relationship** poznámky, můžete zadat klíč a keyref omezení, které se používají během procesu mapování schématu XML ke generování nejen omezení, ale také relace v  **Datová sada**. Ale pokud zadáte `msdata:ConstraintOnly="true"` v **keyref** elementu, **datovou sadu** bude obsahovat pouze omezení a nebudou obsahovat relace.  
  
 Následující příklad ukazuje schématu XML, který zahrnuje **pořadí** a **OrderDetail** elementy, které nejsou vnořené. Schéma také určuje key ani keyref omezení.  
  
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
  
 **Datovou sadu** , který je generován během schématu XML, zahrnuje proces mapování **pořadí** a **OrderDetail** tabulky. Kromě toho **datovou sadu** zahrnuje relace a omezení. Následující příklad ukazuje tyto relace a omezení. Všimněte si, že schéma neurčuje **msdata:Relationship** anotaci; místo toho key ani keyref omezení slouží ke generování vztah.  
  
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
  
 V předchozím příkladu schématu **pořadí** a **OrderDetail** nejsou vnořené elementy. V následujícím příkladu schéma těchto elementů je vnořeno. Ale žádný **msdata:Relationship** je určena anotace; proto se předpokládá implicitní vztah. Další informace najdete v tématu [mapy implicitní vztahy mezi vnořené elementy schématu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Schéma také určuje key ani keyref omezení.  
  
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
  
 **Datovou sadu** vyplývající z procesu mapování schématu XML obsahuje dvě tabulky:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **Datovou sadu** také obsahuje dvě relace (jeden na základě **msdata:relationship** poznámky a druhý podle key ani keyref omezení) a různé omezení. Následující příklad ukazuje, relace a omezení.  
  
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
  
 Pokud keyref omezení odkazování na vnořená tabulka obsahuje **msdata:IsNested = "true"** poznámky, **datovou sadu** vytvoří jeden vnořené relace, která je založena na omezení keyref a související omezení unique/key.  
  
## <a name="see-also"></a>Viz také:

- [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
