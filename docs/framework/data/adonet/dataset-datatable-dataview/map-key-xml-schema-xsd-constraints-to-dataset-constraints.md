---
title: "Mapa klíč omezení schématu XML (XSD) k omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f5247d0ccfd2ceec641ff29d29b889a55c1a5e12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapa klíč omezení schématu XML (XSD) k omezení datové sady
Ve schématu, můžete určit klíče omezení na element nebo atribut, pomocí **klíč** elementu. Element nebo atribut, na kterém je zadán omezení klíče musí mít jedinečné hodnoty v žádné instanci schématu a nesmí obsahovat hodnoty null.  
  
 Omezení klíče je podobná jedinečné omezení, s tím rozdílem, že sloupec, na kterém je definovaný omezení klíče nesmí mít hodnotu null. hodnoty.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **klíč** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**MSDATA:ConstraintName**|Pokud tento atribut je určen, jeho hodnota se používá jako název omezení. Jinak **název** atribut poskytuje hodnota název omezení.|  
|**MSDATA:PrimaryKey**|Pokud `PrimaryKey="true"` je k dispozici, **IsPrimaryKey** omezení je nastavena na **true**, a tím primární klíč. **AllowDBNull** sloupce je nastavena na **false**, protože primární klíče nesmí mít hodnotu null. hodnoty.|  
  
 Převádění, ve kterém je omezení klíče zadané schéma, proces mapování vytvoří omezení unique u tabulky s **AllowDBNull** sloupce vlastnost nastavena na hodnotu **false** pro každý sloupec v omezení. **IsPrimaryKey** jedinečné omezení je také nastavena na **false** Pokud jste zadali `msdata:PrimaryKey="true"` na **klíč** elementu. Toto je stejný jako jedinečné omezení ve schématu, ve kterém `PrimaryKey="true"`.  
  
 V následujícím příkladu schématu **klíč** element určuje klíče omezení na **CustomerID** elementu.  
  
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
  
 **Klíč** element určuje, že hodnoty **CustomerID** podřízený element **zákazníci** element musí mít jedinečné hodnoty a nesmí obsahovat hodnoty null. V překladu schéma schématu XML definition language (XSD), proces mapování vytvoří v následující tabulce:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Mapování schémat XML také vytvoří **UniqueConstraint** na **CustomerID** sloupce, jak je znázorněno v následující <xref:System.Data.DataSet>. (Pro jednoduchost, jsou pouze relevantní vlastnosti zobrazené.)  
  
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
  
 V **datovou sadu** , která je vytvořena **IsPrimaryKey** vlastnost **UniqueConstraint** je nastaven na **true** protože schématu Určuje `msdata:PrimaryKey="true"` v **klíč** elementu.  
  
 Hodnota **ConstraintName** vlastnost **UniqueConstraint** v **datovou sadu** je hodnota **msdata:ConstraintName** Zadaný atribut v **klíč** element ve schématu.  
  
## <a name="see-also"></a>Viz také  
 [Omezení (XSD) schématu XML mapování k omezení datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generování datovou sadu vztahů ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
