---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 73cd8a83021934de3b8e3bf494a4f59dd32e183c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192781"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapování implicitních relací mezi elementy ve vnořeném schématu
Jazyk (XSD) schématu definice schématu XML může mít složité typy vnořené do jiné. V takovém případě proces mapování použije výchozí mapování a vytvoří v následující <xref:System.Data.DataSet>:  
  
-   Jednu tabulku pro každý z komplexních typů (nadřazené a podřízené).  
  
-   Pokud neexistuje žádné omezení unique u nadřazené, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id kde *TableName* je název nadřazené tabulky.  
  
-   Omezení primárního klíče na identifikaci další sloupec jako primární klíč nadřazené tabulky (nastavením **isprimarykey hodnotu** vlastnost **True**). Omezení jmenuje omezení\# kde \# je 1, 2, 3 a tak dále. Například výchozí název pro první omezení je Constraint1.  
  
-   Omezení cizího klíče v podřízené tabulce, určení dalších sloupců jako cizí klíč odkazující na primární klíč nadřazené tabulky. Název omezení *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *tabulka* je název podřízené tabulky.  
  
-   Datová relace mezi nadřazenými a podřízenými tabulkami.  
  
 Následující příklad ukazuje schématu kde **OrderDetail** je podřízený prvek **pořadí**.  
  
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
  
 Proces mapování schématu XML vytvoří následující **datovou sadu**:  
  
-   **Pořadí** a **OrderDetail** tabulky.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Omezení unique u **pořadí** tabulky. Všimněte si, že **isprimarykey hodnotu** je nastavena na **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Omezení cizího klíče na **OrderDetail** tabulky.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** pro tento vztah je nastavena na **True** vzhledem k tomu, **pořadí** a **OrderDetail** elementů je vnořeno ve schématu .  
  
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
  
## <a name="see-also"></a>Viz také  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
