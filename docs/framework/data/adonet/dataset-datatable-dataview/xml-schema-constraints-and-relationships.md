---
title: "Omezení schématu XML a relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 219b8173fdbfd84719733edc2f900511f58967d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xml-schema-constraints-and-relationships"></a>Omezení schématu XML a relace
Ve schématu XML definition language (XSD) schématu, můžete zadat omezení (jedinečné, klíče a omezení keyref) a vztahů (pomocí **msdata:Relationship** poznámky). Toto téma vysvětluje, jak se interpretují omezení a vztahy zadaný v schéma XML pro generování <xref:System.Data.DataSet>.  
  
 Obecně platí, v schéma XML, můžete zadat **msdata:Relationship** anotace, pokud chcete generovat pouze vztahy v **datovou sadu**. Další informace najdete v tématu [generování vztahů datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Zadejte omezení (jedinečné, klíč a keyref) Pokud chcete generovat omezení **datovou sadu**. Všimněte si, že klíč a keyref omezení se také používají ke generování relace, jak je popsáno dále v tomto tématu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generování vztahu z klíče a keyref omezení  
 Místo zadání **msdata:Relationship** poznámky, můžete zadat klíč a keyref omezení, které se používají během procesu mapování schématu XML k vygenerování pouze omezení, ale také relace v  **Datová sada**. Ale pokud zadáte `msdata:ConstraintOnly="true"` v **keyref** elementu, **datovou sadu** bude obsahovat pouze omezení a nebude obsahovat relace.  
  
 Následující příklad ukazuje schéma XML, který zahrnuje **pořadí** a **OrderDetail** prvky, které nejsou vnořené. Schéma také Určuje klíč a keyref omezení.  
  
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
  
 **Datovou sadu** , je generován během schématu XML, zahrnuje proces mapování **pořadí** a **OrderDetail** tabulky. Kromě toho **datovou sadu** obsahuje vztahy a omezení. Následující příklad ukazuje tyto vztahy a omezení. Všimněte si, že schéma neurčuje **msdata:Relationship** anotaci; místo toho se omezení klíč a keyref používají ke generování vztah.  
  
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
  
 V předchozím příkladu schématu **pořadí** a **OrderDetail** nejsou vnořené prvky. V následujícím příkladu schématu jsou vnořeny těchto elementů. Však žádné **msdata:Relationship** poznámky je zadán; proto se předpokládá implicitní vztah. Další informace najdete v tématu [mapy implicitní vztahy mezi vnořené prvky schématu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Schéma také Určuje klíč a keyref omezení.  
  
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
  
 **Datovou sadu** vyplývající z proces mapování schématu XML obsahuje dvě tabulky:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **Datovou sadu** také zahrnuje dvě relace (jeden na základě **msdata:relationship** poznámky a dalších omezení klíče a keyref podle) a různé omezení. Následující příklad ukazuje, vztahy a omezení.  
  
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
  
 Pokud obsahuje keyref omezení, která odkazuje na vnořené tabulky **msdata:IsNested = "true"** poznámky, **datovou sadu** vytvoří jeden vnořené vztah, který je založen na omezení keyref a související omezení unique nebo key.  
  
## <a name="see-also"></a>Viz také  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
