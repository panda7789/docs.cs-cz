---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150932"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
Ve schématu můžete určit omezení klíče pro prvek nebo atribut pomocí **klíčového** prvku. Prvek nebo atribut, na kterém je zadáno omezení klíče, musí mít jedinečné hodnoty v libovolné instanci schématu a nemůže mít hodnoty null.  
  
 Omezení klíče je podobné jedinečnému omezení s tím rozdílem, že sloupec, ve kterém je definováno omezení klíče, nemůže mít nulové hodnoty.  
  
 Následující tabulka popisuje atributy **msdata,** které můžete zadat v **elementu klíče.**  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Pokud je tento atribut zadán, jeho hodnota se používá jako název omezení. V opačném případě atribut **name** poskytuje hodnotu názvu omezení.|  
|**msdata:Primární klíč**|Pokud `PrimaryKey="true"` je k dispozici, je vlastnost omezení **IsPrimaryKey** nastavena na **hodnotu true**, čímž se jedná o primární klíč. Vlastnost sloupec **AllowDBNull** je nastavena na **hodnotu false**, protože primární klíče nemohou mít hodnoty null.|  
  
 Při převodu schématu, ve kterém je zadáno omezení klíče, vytvoří proces mapování jedinečné omezení v tabulce s vlastností sloupce **AllowDBNull** nastavenou na **hodnotu false** pro každý sloupec v omezení. Vlastnost **IsPrimaryKey** jedinečného omezení je také nastavena `msdata:PrimaryKey="true"` na **hodnotu false,** pokud jste nezadali prvek **klíče.** Toto je totožné s jedinečným `PrimaryKey="true"`omezením ve schématu, ve kterém .  
  
 V následujícím příkladu schématu určuje prvek **klíče** omezení klíče pro prvek **CustomerID.**  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 Klíčový **key** prvek určuje, že hodnoty podřízeného prvku **CustomerID** prvku **Customers** musí mít jedinečné hodnoty a nemohou mít hodnoty null. Při překladu schématu jazyka definice schématu XML (XSD) vytvoří proces mapování následující tabulku:  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Mapování schématu XML také vytvoří **UniqueConstraint** na **CustomerID** sloupec, jak <xref:System.Data.DataSet>je znázorněno v následujícím . (Pro jednoduchost jsou zobrazeny pouze relevantní vlastnosti.)  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 V **dataset,** který je generován, **IsPrimaryKey** vlastnost **UniqueConstraint** je nastavena na **hodnotu true,** protože schéma určuje `msdata:PrimaryKey="true"` v **elementu klíče.**  
  
 Hodnota vlastnosti **ConstraintName** **vlastnosti UniqueConstraint** v **datové sadě** je hodnota atributu **msdata:ConstraintName** zadaného v elementu **klíče** ve schématu.  
  
## <a name="see-also"></a>Viz také

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
