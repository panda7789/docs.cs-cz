---
title: "Mapování vztahy zadané pro vnořené prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 221e204c9eef5a861fbd6b85c1e23a0674c6aa4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapování vztahy zadané pro vnořené prvky
Schéma může zahrnovat **msdata:Relationship** poznámky k explicitnímu zadání mapování mezi dvěma prvky ve schématu. Dva prvky určené ve **msdata:Relationship** mohou být použity ve schématu, ale nemusí být. Proces mapování používá **msdata:Relationship** ve schématu vygenerovat primární klíč, cizí klíče relaci mezi dvěma sloupci.  
  
 Následující příklad ukazuje schéma XML, ve kterém **OrderDetail** element je podřízený prvek **pořadí**. **Msdata:Relationship** identifikuje tuto relaci nadřazený podřízený a určuje, že **OrderNumber** sloupec výsledná **pořadí** tabulky souvisí se **OrderNo** sloupec výsledná **OrderDetail** tabulky.  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 Proces mapování schématu XML vytvoří následující <xref:System.Data.DataSet>:  
  
-   **Pořadí** a **OrderDetail** tabulky.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** pro tento vztah je nastavena na **True** protože **pořadí** a **OrderDetail** vnořené prvky ve schématu .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapování nevytvoří žádné omezení.  
  
## <a name="see-also"></a>Viz také  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
