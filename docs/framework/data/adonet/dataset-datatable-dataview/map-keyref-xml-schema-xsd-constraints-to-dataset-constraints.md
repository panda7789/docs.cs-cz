---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 4cc4cb530b7252f35469fd4bb43bf6da9c1a3e24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604026"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
**Keyref** element slouží k vytvoření vazeb mezi prvky v rámci dokumentu. Toto je podobný vztahu cizího klíče v relační databázi. Pokud schéma určuje **keyref** elementu, element je převeden při rušení mapování schématu odpovídající omezení cizího klíče na sloupce v tabulkách <xref:System.Data.DataSet>. Ve výchozím nastavení **keyref** element zároveň vytvoří relaci, se **ParentTable**, **tabulka**, **ParentColumn**a  **ChildColumn** vlastnosti zadané na vztah.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy můžete zadat v **keyref** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Pokud **ConstraintOnly = "true"** je zadaný na **keyref** element ve schématu, vytvoření omezení, ale žádný vztah se vytvoří. Pokud tento atribut není zadán (nebo je nastaven na **False**), omezení a vztahu se vytvoří v **datovou sadu**.|  
|**msdata:ConstraintName**|Pokud **ConstraintName** je zadán atribut, jeho hodnota se používá jako název omezení. V opačném případě **název** atribut **keyref** element ve schématu, poskytuje název omezení v **datovou sadu**.|  
|**msdata:UpdateRule**|Pokud **UpdateRule** je zadán atribut v **keyref** element ve schématu, její hodnota je přiřazená **UpdateRule** vlastnost omezení  **Datová sada**. V opačném případě **UpdateRule** je nastavena na **Cascade**.|  
|**msdata:DeleteRule**|Pokud **DeletRule** je zadán atribut v **keyref** element ve schématu, její hodnota je přiřazená **DeletRule** vlastnost omezení  **Datová sada**. V opačném případě **DeletRule** je nastavena na **Cascade**.|  
|**msdata:AcceptRejectRule**|Pokud **AcceptRejectRule** je zadán atribut v **keyref** element ve schématu, jeho hodnota přiřazena **AcceptRejectRule** vlastnost omezení  **Datová sada**. V opačném případě **AcceptRejectRule** je nastavena na **žádný**.|  
  
 Následující příklad obsahuje schéma, které se určuje **klíč** a **keyref** vztahy mezi **OrderNumber** podřízený prvek **pořadí**  elementu a **OrderNo** podřízený prvek **OrderDetail** elementu.  
  
 V tomto příkladu **OrderNumber** podřízený prvek **OrderDetail** element odkazuje na **OrderNo** klíče podřízený prvek **pořadí**elementu.  
  
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
  
 Proces mapování schématu XML definice jazyk (XSD) schématu vytvoří následující **datovou sadu** se dvěma tabulkami:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Kromě toho **datovou sadu** definuje následující omezení:  
  
- Omezení unique u **pořadí** tabulky.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Vztah mezi **pořadí** a **OrderDetail** tabulky. **Vnořené** je nastavena na **False** dva prvky nejsou vnořené ve schématu.  
  
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
  
- Omezení cizího klíče na **OrderDetail** tabulky.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
