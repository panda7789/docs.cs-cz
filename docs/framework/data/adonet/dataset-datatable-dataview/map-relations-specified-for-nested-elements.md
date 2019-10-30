---
title: Mapování relací zadaných pro vnořené elementy
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 138fbbc3ccaa90096a15fa87544e5c29f66beb08
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040060"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapování relací zadaných pro vnořené elementy
Schéma může zahrnovat anotaci **msdata: Relationship** pro explicitní určení mapování mezi dvěma prvky ve schématu. Dva prvky určené v **msdata: vztah** může být vnořen ve schématu, ale nemusí být. Proces mapování používá **msdata: Relationship** ve schématu k vygenerování vztahu primárního klíče/cizího klíče mezi dvěma sloupci.  
  
 Následující příklad ukazuje schéma XML, ve kterém je element **OrderDetail** podřízeným prvkem **Order**. **Msdata: Relationship** identifikuje tuto relaci typu nadřazený-podřízený a určí, že sloupec **OrderNumber** výsledné tabulky **objednávky** souvisí se sloupcem **OrderNo** výsledné tabulky **OrderDetail** .  
  
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
  
 Proces mapování schématu XML vytvoří v <xref:System.Data.DataSet>následující:  
  
- **Objednávka** a tabulka **OrderDetail**  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail** . **Vnořená** vlastnost pro tento vztah je nastavena na **hodnotu true** , protože prvky **Order** a **OrderDetail** jsou vnořené ve schématu.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapování nevytváří žádná omezení.  
  
## <a name="see-also"></a>Viz také:

- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Přehled ADO.NET](../ado-net-overview.md)
