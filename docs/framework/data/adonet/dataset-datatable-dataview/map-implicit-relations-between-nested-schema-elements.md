---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150960"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapování implicitních relací mezi elementy ve vnořeném schématu
Schéma definice schématu XML (XSD) může mít složité typy vnořené uvnitř sebe. V tomto případě proces mapování použije výchozí mapování a <xref:System.Data.DataSet>vytvoří následující v :  
  
- Jedna tabulka pro každý z komplexních typů (nadřazený a podřízený).  
  
- Pokud v nadřazeném objektu neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče pro definici tabulky s názvem *Název_tabulky*_Id kde *název tablename* je název nadřazené tabulky.  
  
- Omezení primárního klíče v nadřazené tabulce identifikující další sloupec jako primární klíč (nastavením vlastnosti **IsPrimaryKey** na **hodnotu True).** Omezení se nazývá\# \# Omezení, kde je 1, 2, 3 a tak dále. Například výchozí název pro první omezení je Constraint1.  
  
- Omezení cizího klíče v podřízené tabulce identifikující další sloupec jako cizí klíč odkazující na primární klíč nadřazené tabulky. Omezení je pojmenováno *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *ChildTable* je název podřízené tabulky.  
  
- Datový vztah mezi nadřazenou a podřízenou tabulkou.  
  
 Následující příklad ukazuje schéma, kde **OrderDetail** je podřízený prvek **Order**.  
  
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
  
- **Objednávka** a **orderdetail** tabulka.  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Jedinečné omezení v tabulce **Objednávka.** Všimněte si, že **IsPrimaryKey** vlastnost je nastavena na **True**.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- Omezení cizího klíče v tabulce **OrderDetail.**  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail.** **Vnořené vlastnosti** pro tento vztah je nastavena na **True,** protože **Order** a **OrderDetail** prvky jsou vnořeny do schématu.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Viz také

- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Přehled ADO.NET](../ado-net-overview.md)
