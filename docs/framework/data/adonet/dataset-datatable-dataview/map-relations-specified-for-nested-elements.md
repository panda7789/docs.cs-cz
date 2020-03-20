---
title: Mapování relací zadaných pro vnořené elementy
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150893"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapování relací zadaných pro vnořené elementy
Schéma může obsahovat anotaci **msdata:Relationship** explicitně určit mapování mezi libovolnými dvěma prvky ve schématu. Dva prvky zadané v **msdata:Relationship** lze vnořit do schématu, ale nemusí být. Proces mapování používá **msdata:Relationship** ve schématu ke generování vztahu primárního klíče nebo cizího klíče mezi těmito dvěma sloupci.  
  
 Následující příklad ukazuje schéma XML, ve kterém **OrderDetail** element je podřízený prvek **Order**. **Msdata:Relationship** identifikuje tuto relaci nadřazený podřízený a určuje, že sloupec **OrderNumber** výsledné tabulky **Objednávka** souvisí se sloupcem **OrderNo** výsledné tabulky **OrderDetail.**  
  
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
  
 Proces mapování schématu XML vytvoří v <xref:System.Data.DataSet>:  
  
- **Objednávka** a **orderdetail** tabulka.  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail.** **Vnořené vlastnosti** pro tento vztah je nastavena na **True,** protože **Order** a **OrderDetail** prvky jsou vnořeny do schématu.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapování nevytváří žádná omezení.  
  
## <a name="see-also"></a>Viz také

- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Přehled ADO.NET](../ado-net-overview.md)
