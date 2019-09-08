---
title: Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: b5ffe69886b08903feab4373b1cd5c5244b3b3b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784509"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady
Element **keyref** umožňuje vytvořit propojení mezi prvky v rámci dokumentu. To se podobá relaci cizího klíče v relační databázi. Pokud schéma určuje element **keyref** , je element převeden během procesu mapování schématu na odpovídající omezení cizího klíče pro sloupce v tabulkách <xref:System.Data.DataSet>. Ve výchozím nastavení element **keyref** také generuje relaci s vlastnostmi **nadřazené tabulky**, **podřízenosti**, **ParentColumn**a **ChildColumn** , které jsou zadány v relaci.  
  
 Následující tabulka popisuje atributy **msdata** , které lze zadat v elementu **keyref** .  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Pokud je v elementu **keyref** ve schématu zadán parametr **ConstraintOnly = "true"** , je vytvořeno omezení, ale není vytvořena žádná relace. Pokud tento atribut není zadán (nebo je nastaven na **hodnotu false**), je omezení i vztah vytvořen v **datové sadě**.|  
|**msdata:ConstraintName**|Pokud je zadán atribut **Constraint** , použije se jako název omezení jeho hodnota. Jinak atribut **Name** elementu **keyref** ve schématu poskytuje název omezení v **datové sadě**.|  
|**msdata:UpdateRule**|Pokud je atribut **UpdateRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **UpdateRule** v **datové sadě**. V opačném případě je vlastnost **UpdateRule** nastavena na hodnotu **Cascade**.|  
|**msdata:DeleteRule**|Pokud je atribut **DeleteRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **DeleteRule** v **datové sadě**. V opačném případě je vlastnost **DeleteRule** nastavena na hodnotu **Cascade**.|  
|**msdata:AcceptRejectRule**|Pokud je atribut **AcceptRejectRule** zadán v elementu **keyref** ve schématu, je jeho hodnota přiřazena vlastnosti omezení **AcceptRejectRule** v **datové sadě**. V opačném případě je vlastnost **AcceptRejectRule** nastavena na **hodnotu None**.|  
  
 Následující příklad obsahuje schéma, které určuje vztahy **Key** a **keyref** mezi podřízeným prvkem **OrderNumber** elementu **Order** a podřízeným prvkem **OrderNo** **OrderDetail** objekt.  
  
 V příkladu podřízený element **OrderNumber** elementu **OrderDetail** odkazuje na podřízený element Key elementu **OrderNo** elementu **Order** .  
  
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
  
 Proces mapování schématu XSD (XML Schema Definition Language) vytvoří následující **datovou sadu** se dvěma tabulkami:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Kromě toho **datová sada** definuje následující omezení:  
  
- Jedinečné omezení v tabulce **Order** .  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Vztah mezi tabulkami **Order** a **OrderDetail** . **Vnořená** vlastnost je nastavena na **hodnotu false** , protože tyto dva prvky nejsou vnořené ve schématu.  
  
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
  
- Omezení cizího klíče v tabulce **OrderDetail**  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
