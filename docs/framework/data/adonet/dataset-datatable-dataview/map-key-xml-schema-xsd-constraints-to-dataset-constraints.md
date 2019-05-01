---
title: Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 46a980f06198c6f06bb13824c65cfb5309eec154
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034226"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování klíčových omezení schématu XML (XSD) k omezením datové sady
Ve schématu, můžete určit klíče omezení na element nebo atribut, pomocí **klíč** elementu. Element nebo atribut, na kterém je zadáno klíčové omezení musí mít jedinečné hodnoty v žádné instanci schéma a nemůže mít hodnotu null.  
  
 Omezení klíče je podobná omezení unique, s tím rozdílem, že sloupec, na kterém je definována omezení klíče nesmí obsahovat hodnoty null.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **klíč** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Pokud tento atribut není zadán, jeho hodnota se používá jako název omezení. V opačném případě **název** atributu obsahuje hodnotu název omezení.|  
|**msdata:PrimaryKey**|Pokud `PrimaryKey="true"` je k dispozici, **isprimarykey hodnotu** omezení je nastavena na **true**, díky čemuž je primární klíč. **AllowDBNull** sloupce je nastavena na **false**, protože primární klíče nemůže mít hodnotu null.|  
  
 Při převodu schématu, ve které je zadáno klíčových omezení, proces mapování vytvoří omezení unique u tabulky se **AllowDBNull** sloupce nastavenou na **false** pro každý sloupec v omezení. **Isprimarykey hodnotu** jedinečné omezení je také nastavena na **false** mít uvedeno `msdata:PrimaryKey="true"` na **klíč** elementu. To je stejný jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.  
  
 V následujícím příkladu schématu **klíč** prvek určuje klíče omezení na **CustomerID** elementu.  
  
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
  
 **Klíč** element určuje, že hodnoty **CustomerID** podřízený prvek **zákazníkům** element musí mít jedinečné hodnoty a nemůže mít hodnotu null. Při překladu jazyk (XSD) schématu definice schématu XML, proces mapování vytvoří v následující tabulce:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Také vytvoří mapování schématu XML **UniqueConstraint** na **CustomerID** sloupce, jak je znázorněno v následujícím <xref:System.Data.DataSet>. (Pro jednoduchost, pouze relevantní jsou zobrazeny vlastnosti.)  
  
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
  
 V **datovou sadu** , který je generován, **isprimarykey hodnotu** vlastnost **UniqueConstraint** je nastavena na **true** protože schématu Určuje `msdata:PrimaryKey="true"` v **klíč** elementu.  
  
 Hodnota **ConstraintName** vlastnost **UniqueConstraint** v **datovou sadu** je hodnota **msdata:ConstraintName** zadaný v atributu **klíč** element ve schématu.  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
