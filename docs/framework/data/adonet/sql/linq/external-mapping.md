---
title: Externí mapování
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: ba5af75ae34b233354fec6e9074f3cc96d924c7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003054"
---
# <a name="external-mapping"></a>Externí mapování
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje *externí mapování*, což je proces, při kterém použijete samostatný soubor XML k určení mapování mezi datovým modelem databáze a objektového modelu. Mezi výhody použití externího mapovacího souboru patří následující:  
  
- Můžete zachovat kód mapování mimo kód aplikace. Tento přístup snižuje přehlednost kódu aplikace.  
  
- Soubor externího mapování můžete zacházet jako s konfiguračním souborem. Můžete například aktualizovat způsob, jakým se aplikace chová po odeslání binárních souborů, a to pouhým odchodem externího mapovacího souboru.  
  
## <a name="requirements"></a>Požadavky  
 Soubor mapování musí být soubor XML a soubor musí být ověřen proti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definice schématu (. XSD).  
  
 Platí následující pravidla:  
  
- Soubor mapování musí být soubor XML.  
  
- Soubor mapování XML musí být platný pro soubor definice schématu XML. Další informace najdete v tématu [Postup: ověření souborů dbml a externích mapování souborů](how-to-validate-dbml-and-external-mapping-files.md).  
  
- Externí mapování Přepisuje mapování na základě atributů. Jinými slovy, pokud použijete externí zdroj mapování k vytvoření <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje všechny atributy mapování, které jste vytvořili pro třídy. Toto chování je pravdivé bez ohledu na to, zda je třída obsažena v externím mapování souboru.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje hybridní použití dvou přístupů k mapování (na základě atributů a externích).  
  
## <a name="xml-schema-definition-file"></a>Soubor definice schématu XML  
 Externí mapování v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být platné pro následující definici schématu XML.  
  
 Rozliší tento soubor definice schématu ze souboru definice schématu, který se používá k ověření souboru DBML. Další informace naleznete v tématu [generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
> Uživatelé sady Visual Studio budou také tento soubor XSD v dialogovém okně schémat XML vyhledat jako "LinqToSqlMapping. xsd". Chcete-li tento soubor použít pro ověření externího mapovacího souboru správně, přečtěte si téma [How to: Validate a extern Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také:

- [Generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md)
- [Reference](reference.md)
- [Postupy: Generování objektového modelu jako externího souboru](how-to-generate-the-object-model-as-an-external-file.md)
