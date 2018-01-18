---
title: "Mapa implicitní vztahy mezi elementy vnořené schématu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 740d45c47f46c311ed703fa11ec86a9739930944
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapa implicitní vztahy mezi elementy vnořené schématu
Schématu schématu XML definition language (XSD) může mít komplexní typy vnořit do sebe navzájem. V takovém případě proces mapování použije výchozí mapování a vytvoří následující <xref:System.Data.DataSet>:  
  
-   Jedna tabulka pro každou komplexních typů (nadřazené a podřízené).  
  
-   Pokud na nadřazené neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id kde *TableName* je název nadřazené tabulce.  
  
-   Omezení primárního klíče v nadřazené tabulce identifikace další sloupec jako primární klíč (nastavením **IsPrimaryKey** vlastnost **True**). Omezení jmenuje omezení *#*  kde  *#*  je 1, 2, 3 a tak dále. Například výchozí název pro první omezení je Constraint1.  
  
-   Omezení cizího klíče na podřízenou tabulku identifikace další sloupec jako cizí klíč odkazující na primární klíč v nadřazené tabulce. Název omezení *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *tabulka* je název podřízené tabulky.  
  
-   Data vztah mezi nadřazenou a podřízenou tabulkou.  
  
 Následující příklad ukazuje schéma kde **OrderDetail** je podřízený prvek **pořadí**.  
  
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
  
-   Jedinečná omezení **pořadí** tabulky. Všimněte si, že **IsPrimaryKey** je nastavena na **True**.  
  
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
  
-   Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** pro tento vztah je nastavena na **True** protože **pořadí** a **OrderDetail** vnořené prvky ve schématu .  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
