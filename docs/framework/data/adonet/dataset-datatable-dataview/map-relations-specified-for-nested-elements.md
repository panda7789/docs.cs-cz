---
title: Mapování relací zadaných pro vnořené elementy
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 9772f077991c758be65bbb44b9474f1ad341371f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203142"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapování relací zadaných pro vnořené elementy
Schéma může obsahovat **msdata:Relationship** poznámky k explicitnímu zadání mapování mezi dva prvky ve schématu. Dva prvky určené ve **msdata:Relationship** může být vnořena ve schématu, ale nemusí být. Proces mapování využívá **msdata:Relationship** ve schématu pro generování primární klíč nebo relace cizího klíče mezi dvěma sloupci.  
  
 Následující příklad ukazuje schématu XML, ve kterém **OrderDetail** prvek je podřízený prvek **pořadí**. **Msdata:Relationship** identifikuje tento vztah nadřízenosti a podřízenosti a určuje, že **OrderNumber** sloupec výsledné **pořadí** tabulka má vztah k **OrderNo** sloupec výsledné **OrderDetail** tabulky.  
  
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
  
-   Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** pro tento vztah je nastavena na **True** vzhledem k tomu, **pořadí** a **OrderDetail** elementů je vnořeno ve schématu .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapování nevytvoří žádná omezení.  
  
## <a name="see-also"></a>Viz také:

- [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
