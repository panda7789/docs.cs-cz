---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150880"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
**Keyref** element umožňuje vytvořit propojení mezi prvky v rámci dokumentu. To je podobné vztahu cizího klíče v relační databázi. Pokud schéma určuje element **keyref,** prvek je převeden během procesu mapování schématu na odpovídající omezení cizího klíče na <xref:System.Data.DataSet>sloupce v tabulkách . Ve výchozím nastavení element **keyref** také generuje vztah s vlastnostmi **ParentTable**, **ChildTable**, **ParentColumn**a **ChildColumn** určenými pro relaci.  
  
 Následující tabulka popisuje **atributy msdata,** které můžete zadat v elementu **keyref.**  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:Pouze omezení**|Pokud **constraintOnly="true"** je zadán na **keyref** prvek ve schématu, je vytvořena omezení, ale je vytvořen žádný vztah. Pokud tento atribut není zadán (nebo je nastavenna **na False**), jsou v **dataset**vytvořeny omezení i vztah .|  
|**msdata:ConstraintName**|Pokud je zadán atribut **ConstraintName,** jeho hodnota se používá jako název omezení. V opačném případě atribut **name** elementu **keyref** ve schématu poskytuje název omezení v **dataset**.|  
|**msdata:Aktualizovatpravidlo**|Pokud je atribut **UpdateRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **UpdateRule** v **sadě DataSet**. V opačném případě je vlastnost **UpdateRule** nastavena na **možnost Kaskáda**.|  
|**msdata:Odstranitpravidlo**|Pokud je atribut **DeleteRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti **omezení DeleteRule** v **sadě DataSet**. V opačném případě je vlastnost **DeleteRule** nastavena na **možnost Kaskáda**.|  
|**msdata:AcceptRejectRule**|Pokud **acceptRejectRule** atribut je zadán v **keyref** element ve schématu, jeho hodnota je **přiřazena AcceptRejectRule** vlastnost omezení v **DataSet**. V opačném případě je vlastnost **AcceptRejectRule** nastavena na **položku None**.|  
  
 Následující příklad obsahuje schéma, které určuje vztahy **klíče** a **keyref** mezi podřízeným prvkem **OrderNumber** elementu **Order** a podřízeným prvkem **OrderNo** prvku **OrderDetail.**  
  
 V příkladu **ordernumber** podřízený prvek **OrderDetail** element odkazuje na **OrderNo** klíčový podřízený prvek **Order** element.  
  
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
  
 Proces mapování schématu schématu schématu schématu XML (XSD) vytváří následující **datovou sadu** se dvěma tabulkami:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Kromě toho **DataSet** definuje následující omezení:  
  
- Jedinečné omezení v tabulce **Objednávka.**  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail.** **Vnořené** Vlastnost je nastavena na **False,** protože dva prvky nejsou vnořeny do schématu.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- Omezení cizího klíče v tabulce **OrderDetail.**  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Viz také

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
