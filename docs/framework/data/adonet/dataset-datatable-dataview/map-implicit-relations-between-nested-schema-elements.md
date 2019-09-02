---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: e9ea85db98a577991e06e0239a0738a2ca5bada6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203478"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapování implicitních relací mezi elementy ve vnořeném schématu
Schéma jazyka XML Schema Definition Language (XSD) může mít vnořené typy vnořené uvnitř sebe. V tomto případě proces mapování použije výchozí mapování a vytvoří následující <xref:System.Data.DataSet>:  
  
- Jedna tabulka pro každý ze složitých typů (nadřazených a podřízených).  
  
- Pokud v nadřazeném prvku neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id, kde *TableName* je název nadřazené tabulky.  
  
- Omezení primárního klíče v nadřazené tabulce, které identifikuje další sloupec jako primární klíč (nastavením vlastnosti **IsPrimaryKey** na **hodnotu true**). Omezení je pojmenované jako omezení\# , \# kde je 1, 2, 3 atd. Výchozím názvem pro první omezení je například Constraint1.  
  
- Omezení cizího klíče v podřízené tabulce identifikující další sloupec jako cizí klíč odkazující na primární klíč nadřazené tabulky. Omezení je pojmenované *ParentTable_ChildTable* , kde *Parent* je název nadřazené tabulky a podřízená tabulka je název podřízené tabulky.  
  
- Vztah dat mezi nadřazenými a podřízenými tabulkami.  
  
 Následující příklad ukazuje schéma, kde **OrderDetail** je podřízeným prvkem **Order**.  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 Proces mapování schématu XML vytvoří v **datové sadě**následující:  
  
- **Objednávka** a tabulka **OrderDetail**  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Jedinečné omezení v tabulce **Order** . Všimněte si, že vlastnost **IsPrimaryKey** je nastavena na **hodnotu true**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- Omezení cizího klíče v tabulce **OrderDetail**  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail** . **Vnořená** vlastnost pro tento vztah je nastavena na **hodnotu true** , protože prvky **Order** a **OrderDetail** jsou vnořené ve schématu.  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
