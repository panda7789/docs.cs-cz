---
title: Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 6b847aba31aa75f7be3bd6a11b6bcb8231c06bc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040366"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady
Ve schématu XSD (XML Schema Definition Language) definuje **jedinečný** element omezení jedinečnosti pro element nebo atribut. V procesu překladu schématu XML do relačního schématu je jedinečné omezení zadané u elementu nebo atributu ve schématu XML mapováno na jedinečné omezení v <xref:System.Data.DataTable> v odpovídající <xref:System.Data.DataSet>, která je generována.  
  
 Následující tabulka popisuje atributy **msdata** , které lze zadat v **jedinečném** prvku.  
  
|Název atributu|Popis|  
|--------------------|-----------------|  
|**msdata: Constraint**|Pokud je tento atribut zadán, použije se jako název omezení jeho hodnota. V opačném případě atribut **Name** poskytuje hodnotu názvu omezení.|  
|**msdata: PrimaryKey**|Pokud je `PrimaryKey="true"` k dispozici v **jedinečném** prvku, je vytvořeno jedinečné omezení s vlastností **IsPrimaryKey** nastavenou na **hodnotu true**.|  
  
 Následující příklad ukazuje schéma XML, které používá **jedinečný** element k určení omezení jedinečnosti.  
  
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
  
 **Jedinečný** prvek ve schématu určuje, že pro všechny **zákazníky** v instanci dokumentu musí být hodnota podřízeného elementu **CustomerID** jedinečná. Při sestavování **datové sady**načte proces mapování toto schéma a vygeneruje následující tabulku:  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapování také vytvoří jedinečné omezení pro sloupec **KódZákazníka** , jak je znázorněno v následující **datové sadě**. (Pro jednoduchost se zobrazí pouze příslušné vlastnosti.)  
  
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
  
 V **datové sadě** , která je vygenerována, je vlastnost **IsPrimaryKey** pro jedinečné omezení nastavena na **hodnotu false** . Vlastnost **Unique** sloupce označuje, že hodnoty sloupce **KódZákazníka** musí být jedinečné (ale mohou být odkazem s hodnotou null, jak je určeno vlastností **AllowDBNull** sloupce).  
  
 Pokud schéma upravíte a nastavíte volitelnou hodnotu atributu **msdata: PrimaryKey** na hodnotu **true**, v tabulce se vytvoří jedinečné omezení. Vlastnost Column **AllowDBNull** je nastavena na **hodnotu false**a vlastnost **IsPrimaryKey** omezení je nastavena na **hodnotu true**, čímž se sloupec **KódZákazníka** nastaví jako sloupec primárního klíče.  
  
 Můžete zadat jedinečné omezení na kombinaci prvků nebo atributů ve schématu XML. Následující příklad ukazuje, jak určit, že kombinace hodnot **KódZákazníka** a **CompanyName** musí být jedinečná pro všechny **zákazníky** v jakékoli instanci přidáním jiného prvku **xs: Field** ve schématu.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Toto je omezení vytvořené ve výsledné **sadě dat**.  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Viz také:

- [Mapování omezení schématu XML (XSD) k omezením datové sady](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generování relací datové sady ze schématu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Přehled ADO.NET](../ado-net-overview.md)
