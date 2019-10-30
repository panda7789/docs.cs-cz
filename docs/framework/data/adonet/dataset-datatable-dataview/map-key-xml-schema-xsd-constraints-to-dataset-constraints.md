---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 670c07dd83e880b79c1ccf0c5af00d253b83f827
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040068"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
Ve schématu můžete zadat omezení klíče pro element nebo atribut pomocí elementu **Key** . Element nebo atribut, u kterého je zadáno omezení klíče, musí mít jedinečné hodnoty v libovolné instanci schématu a nesmí mít hodnoty null.  
  
 Omezení klíče je podobné omezení UNIQUE s tím rozdílem, že sloupec, na kterém je definováno omezení klíče, nemůže mít hodnoty null.  
  
 Následující tabulka popisuje atributy **msdata** , které lze zadat v elementu **Key** .  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata: Constraint**|Pokud je tento atribut zadán, použije se jako název omezení jeho hodnota. V opačném případě atribut **Name** poskytuje hodnotu názvu omezení.|  
|**msdata: PrimaryKey**|Pokud je k dispozici `PrimaryKey="true"`, vlastnost omezení **IsPrimaryKey** je nastavena na **hodnotu true**, čímž se nastaví jako primární klíč. Vlastnost **AllowDBNull** sloupce je nastavena na **hodnotu false**, protože primární klíče nemohou mít hodnoty null.|  
  
 Při převádění schématu, ve kterém je zadáno omezení klíče, proces mapování vytvoří v tabulce jedinečné omezení s vlastností **AllowDBNull** Column nastavenou na **hodnotu false** pro každý sloupec v omezení. Vlastnost **IsPrimaryKey** jedinečného omezení je také nastavena na **hodnotu false** , pokud jste nezadali `msdata:PrimaryKey="true"` u elementu **Key** . Toto je stejné jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.  
  
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
  
 **Klíčový** prvek určuje, že hodnoty podřízeného prvku **KódZákazníka** elementu **Customers** musí mít jedinečné hodnoty a nesmí mít hodnoty null. V rámci překladu schématu XML Schema Definition Language (XSD) vytvoří proces mapování následující tabulku:  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Mapování schématu XML také vytvoří **UniqueConstraint** ve sloupci **KódZákazníka** , jak je znázorněno na následujícím <xref:System.Data.DataSet>. (Pro jednoduchost se zobrazí pouze příslušné vlastnosti.)  
  
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
  
 V **datové sadě** , která je generována, vlastnost **IsPrimaryKey** třídy **UniqueConstraint** je nastavena na **hodnotu true** , protože schéma určuje `msdata:PrimaryKey="true"` v elementu **Key** .  
  
 Hodnota vlastnosti **Constraint** objektu **UniqueConstraint** v **datové sadě** je hodnota atributu **msdata: Constraint** uvedená v elementu **Key** ve schématu.  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
