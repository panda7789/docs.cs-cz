---
title: Mapa keyref omezení schématu XML (XSD) k omezení datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: a3a5033292db2b47e7a9811e36c0a4af016951fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758552"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapa keyref omezení schématu XML (XSD) k omezení datové sady
**Keyref** element umožňuje vytváření propojení mezi prvky dokumentu. Toto je podobná relace cizího klíče v relační databázi. Pokud schéma určuje **keyref** elementu, element je převést během procesu schéma mapování na odpovídající omezení cizího klíče u sloupců v tabulkách <xref:System.Data.DataSet>. Ve výchozím nastavení **keyref** element také vytváří vztah, se **ParentTable**, **tabulka**, **ParentColumn**a  **ChildColumn** na vztah byly zadány vlastnosti.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy můžete zadat v **keyref** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Pokud **ConstraintOnly = "true"** je zadaný na **keyref** element ve schématu omezení je vytvořen, ale je vytvořen žádný vztah. Pokud tento atribut nezadá (nebo je nastaven na **False**), omezení a vztah se vytvoří v **datovou sadu**.|  
|**msdata:ConstraintName**|Pokud **ConstraintName** zadán atribut, jeho hodnota se používá jako název omezení. Jinak **název** atribut **keyref** element ve schématu poskytuje název omezení v **datovou sadu**.|  
|**msdata:UpdateRule**|Pokud **UpdateRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **UpdateRule** vlastnost omezení  **Datová sada**. V opačném případě **UpdateRule** je nastavena na **Cascade**.|  
|**msdata:DeleteRule**|Pokud **DeletRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **DeletRule** vlastnost omezení  **Datová sada**. V opačném případě **DeletRule** je nastavena na **Cascade**.|  
|**msdata:AcceptRejectRule**|Pokud **AcceptRejectRule** atribut je uveden v **keyref** element ve schématu, jeho hodnota je přiřazen k **AcceptRejectRule** vlastnost omezení  **Datová sada**. V opačném případě **AcceptRejectRule** je nastavena na **žádné**.|  
  
 Následující příklad obsahuje schéma, které určuje **klíč** a **keyref** vztahy mezi **OrderNumber** podřízený element **pořadí**  elementu a **OrderNo** podřízený element **OrderDetail** element.  
  
 V příkladu **OrderNumber** podřízený element **OrderDetail** element odkazuje **OrderNo** klíče podřízený element **pořadí**elementu.  
  
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
  
 Proces mapování schématu XML definice jazyka (XSD) schématu vytváří následující **datovou sadu** s dvou tabulek:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Kromě toho **datovou sadu** definuje následující omezení:  
  
-   Jedinečná omezení **pořadí** tabulky.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** je nastavena na **False** nejsou vnořené dva elementy ve schématu.  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   Omezení cizího klíče na **OrderDetail** tabulky.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Viz také  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
