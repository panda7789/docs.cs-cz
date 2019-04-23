---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108222"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
Ve schématu XML definice jazyk (XSD) schématu **jedinečný** prvek určuje omezení jedinečnosti pro elementu nebo atributu. Právě schématu XML se překládá na relační schéma, jedinečné omezení zadaný v elementu nebo atributu ve schématu XML se mapuje na jedinečné omezení v <xref:System.Data.DataTable> z odpovídajících <xref:System.Data.DataSet> , který je generován.  
  
 V následující tabulce jsou podrobněji popsány dále **msdata** atributy, které můžete zadat v **jedinečný** elementu.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Pokud tento atribut není zadán, jeho hodnota se používá jako název omezení. V opačném případě **název** atributu obsahuje hodnotu název omezení.|  
|**msdata:PrimaryKey**|Pokud `PrimaryKey="true"` je k dispozici v **jedinečný** elementu jedinečné omezení se vytvoří s **isprimarykey hodnotu** vlastnost nastavena na hodnotu **true**.|  
  
 Následující příklad ukazuje schématu XML, který používá **jedinečný** element zadat omezení jedinečnosti.  
  
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
  
 **Jedinečný** element ve schématu, která určuje pro všechny **zákazníkům** prvky v dokumentu instance, hodnota **CustomerID** podřízený element musí být jedinečný. V sestavení **datovou sadu**, proces mapování čte toto schéma a vygeneruje v následující tabulce:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapování také vytvoří jedinečné omezení na **CustomerID** sloupce, jak je znázorněno v následujícím **datovou sadu**. (Pro jednoduchost, pouze relevantní jsou zobrazeny vlastnosti.)  
  
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
  
 V **datovou sadu** , který je generován, **isprimarykey hodnotu** je nastavena na **False** pro jedinečné omezení. **Jedinečný** vlastnost sloupec znamená, že **CustomerID** hodnot sloupců musí být jedinečné (ale mohou být odkaz s hodnotou null, jak jsou určené **AllowDBNull** Vlastnosti sloupce).  
  
 Je-li upravit schéma a nastavit volitelný **msdata:PrimaryKey** atribut hodnotu **True**, jedinečné omezení se vytvoří v tabulce. **AllowDBNull** sloupce je nastavena na **False**a **isprimarykey hodnotu** vlastnost nastavit na omezení **True**a proto **CustomerID** sloupec sloupec primárního klíče.  
  
 Jedinečné omezení na kombinaci elementy nebo atributy můžete zadat ve schématu XML. Následující příklad ukazuje, jak určit, že kombinaci **CustomerID** a **CompanyName** hodnoty musí být jedinečné pro všechny **zákazníkům** v žádné instanci podle Přidání dalšího **xs:field** element ve schématu.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Toto je omezení, který je vytvořen ve výsledné **datovou sadu**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
