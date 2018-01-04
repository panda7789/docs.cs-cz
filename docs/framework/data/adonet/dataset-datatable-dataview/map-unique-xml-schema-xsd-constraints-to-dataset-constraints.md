---
title: "Mapování jedinečná omezení schématu XML (XSD) na omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5276697ebdc065965d970afc4ac2ef6be61c8f20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování jedinečná omezení schématu XML (XSD) na omezení datové sady
Ve schématu XML definition language (XSD) schématu **jedinečný** element určuje omezení jedinečnosti k elementu nebo atributu. Probíhá proces překladu schématu XML na relační schéma, jedinečné omezení zadaný na element nebo atribut ve schématu XML se mapuje na jedinečné omezení v <xref:System.Data.DataTable> do odpovídajícího <xref:System.Data.DataSet> generovanou.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **jedinečný** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**MSDATA:ConstraintName**|Pokud tento atribut je určen, jeho hodnota se používá jako název omezení. Jinak **název** atribut poskytuje hodnota název omezení.|  
|**MSDATA:PrimaryKey**|Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** element, jedinečné omezení je vytvořen s **IsPrimaryKey** vlastnost nastavena na hodnotu **true**.|  
  
 Následující příklad ukazuje schéma XML, který používá **jedinečný** elementu, který chcete zadat omezení jedinečnosti.  
  
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
  
 **Jedinečný** element ve schématu určuje, že pro všechny **zákazníci** instance elementy v dokumentu, hodnota **CustomerID** podřízený element musí být jedinečný. V sestavení **datovou sadu**, proces mapování čte toto schéma a generuje v následující tabulce:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapování také vytvoří jedinečné omezení na **CustomerID** sloupce, jak je znázorněno v následující **datovou sadu**. (Pro jednoduchost, jsou pouze relevantní vlastnosti zobrazené.)  
  
```  
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
  
 V **datovou sadu** , která je vytvořena **IsPrimaryKey** je nastavena na **False** pro jedinečné omezení. **Jedinečný** vlastnost sloupec znamená, že **CustomerID** hodnoty sloupců musí být jedinečné (ale může být odkaz s hodnotou null, podle specifikace **AllowDBNull** vlastnost sloupce).  
  
 Upravíte-li schéma a nastavit volitelné **msdata:PrimaryKey** atribut hodnotu **True**, jedinečné omezení je vytvořit v tabulce. **AllowDBNull** sloupce je nastavena na **False**a **IsPrimaryKey** vlastnost nastavit na omezení **True**, proto provedení **CustomerID** sloupec sloupcem primárního klíče.  
  
 Můžete zadat omezení unique u kombinaci elementy nebo atributy ve schématu XML. Následující příklad ukazuje, jak určit, že kombinaci **CustomerID** a **#companyname** hodnoty musí být jedinečné pro všechny **zákazníci** v žádné instanci podle přidáním další **xs:field** element ve schématu.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Toto je omezení, který je vytvořen v výsledná **datovou sadu**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Viz také  
 [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
