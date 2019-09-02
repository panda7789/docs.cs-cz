---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: d6fcdae77c2f2ac07ea5cd16baf07cd5de36d25b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203474"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
Ve schématu můžete zadat omezení klíče pro element nebo atribut pomocí elementu **Key** . Element nebo atribut, u kterého je zadáno omezení klíče, musí mít jedinečné hodnoty v libovolné instanci schématu a nesmí mít hodnoty null.  
  
 Omezení klíče je podobné omezení UNIQUE s tím rozdílem, že sloupec, na kterém je definováno omezení klíče, nemůže mít hodnoty null.  
  
 Následující tabulka popisuje atributy **msdata** , které lze zadat v elementu **Key** .  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Pokud je tento atribut zadán, použije se jako název omezení jeho hodnota. V opačném případě atribut **Name** poskytuje hodnotu názvu omezení.|  
|**msdata:PrimaryKey**|Pokud `PrimaryKey="true"` je k dispozici, vlastnost omezení **IsPrimaryKey** je nastavena na **hodnotu true**, takže ji vytvoří primární klíč. Vlastnost **AllowDBNull** sloupce je nastavena na **hodnotu false**, protože primární klíče nemohou mít hodnoty null.|  
  
 Při převádění schématu, ve kterém je zadáno omezení klíče, proces mapování vytvoří v tabulce jedinečné omezení s vlastností **AllowDBNull** Column nastavenou na **hodnotu false** pro každý sloupec v omezení. Vlastnost **IsPrimaryKey** jedinečného omezení je také nastavena na **hodnotu false** , pokud jste neurčili `msdata:PrimaryKey="true"` u elementu **Key** . Toto je stejné jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.  
  
 V následujícím příkladu schématu **klíč** elementu určuje omezení klíče u elementu **CustomerID** .  
  
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
  
 **Klíčový** prvek určuje, že hodnoty podřízeného prvku **KódZákazníka** elementu Customers musí mít jedinečné hodnoty a nesmí mít hodnoty null. V rámci překladu schématu XML Schema Definition Language (XSD) vytvoří proces mapování následující tabulku:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Mapování schématu XML také vytvoří **UniqueConstraint** ve sloupci **KódZákazníka** , jak je znázorněno v následujícím <xref:System.Data.DataSet>příkladu. (Pro jednoduchost se zobrazí pouze příslušné vlastnosti.)  
  
```  
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
  
 V **datové sadě** , která je generována, vlastnost **IsPrimaryKey** třídy **UniqueConstraint** je nastavena na **hodnotu true** , protože schéma `msdata:PrimaryKey="true"` určuje element **Key** .  
  
 Hodnota vlastnosti **Constraint** objektu **UniqueConstraint** v **datové sadě** je hodnota atributu **msdata: Constraint** uvedená v elementu **Key** ve schématu.  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
