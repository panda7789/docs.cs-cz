---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150841"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
V definičním jazyce xml schématu (XSD) **jedinečný** prvek určuje omezení jedinečnosti prvku nebo atributu. V procesu překladu schématu XML do relačního schématu je jedinečné omezení zadané pro prvek nebo atribut ve schématu XML mapováno na jedinečné omezení v <xref:System.Data.DataTable> odpovídajícím, <xref:System.Data.DataSet> který je generován.  
  
 Následující tabulka popisuje atributy **msdata,** které můžete zadat v **jedinečném** prvku.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Pokud je tento atribut zadán, jeho hodnota se používá jako název omezení. V opačném případě atribut **name** poskytuje hodnotu názvu omezení.|  
|**msdata:Primární klíč**|Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** prvek, je vytvořen jedinečný omezení s **IsPrimaryKey** vlastnost nastavena na **hodnotu true**.|  
  
 Následující příklad ukazuje schéma XML, které používá **jedinečný** prvek k určení omezení jedinečnosti.  
  
```xml  
<xs:schema id="SampleDataSet"
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 **Jedinečný** prvek ve schématu určuje, že pro všechny **prvky Customers** v instanci dokumentu musí být hodnota podřízeného prvku **CustomerID** jedinečná. Při vytváření **dataset**, proces mapování přečte toto schéma a generuje následující tabulku:  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapování také vytvoří jedinečné omezení ve **sloupci CustomerID,** jak je znázorněno v následujícím **datovém souboru**. (Pro jednoduchost jsou zobrazeny pouze relevantní vlastnosti.)  
  
```text  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID
      IsPrimaryKey: False  
```  
  
 V **dataset,** který je generován, **IsPrimaryKey** vlastnost je nastavena na **False** pro jedinečné omezení. **Jedinečná** vlastnost ve sloupci označuje, že hodnoty sloupce **CustomerID** musí být jedinečné (ale mohou se jednat o nulový odkaz, jak je určeno vlastností **AllowDBNull** sloupce).  
  
 Pokud změníte schéma a nastavíte volitelnou hodnotu atributu **msdata:PrimaryKey** na **hodnotu True**, vytvoří se v tabulce jedinečné omezení. Vlastnost sloupec **AllowDBNull** je nastavena na **hodnotu False**a vlastnost **IsPrimaryKey** nastaveného omezení na **hodnotu True**, čímž se sloupec **CustomerID** stává sloupcem primárního klíče.  
  
 Ve schématu XML můžete určit jedinečné omezení kombinace prvků nebo atributů. Následující příklad ukazuje, jak určit, že kombinace **CustomerID** a **CompanyName** hodnoty musí být jedinečný pro všechny **zákazníky** v každém případě přidáním další **xs:field** element ve schématu.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 Toto je omezení, které je vytvořeno ve výsledné **datové sadě**.  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Viz také

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
