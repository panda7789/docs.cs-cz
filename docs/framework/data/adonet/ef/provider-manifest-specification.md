---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 3d396f6ecfc0eb4a884e4af0d84ef65d18c5586c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033996"
---
# <a name="provider-manifest-specification"></a>Specifikace manifestu zprostředkovatele
Tato část popisuje, jak můžete zprostředkovatele úložiště dat podporují typy a funkce v úložišti.  
  
 Entita služby funguje nezávisle na poskytovatele úložiště konkrétní data, ale stále umožňuje poskytovatel dat explicitně definovat dotazy, modely a mapování interakci s základnímu úložišti dat. Bez abstraktní vrstvu může entita služby pouze cílená na konkrétní datové úložiště nebo poskytovatele dat služeb.  
  
 Typy, které podporuje zprostředkovatel přímo nebo nepřímo podporuje podkladové databáze. Tyto typy nejsou nutně typy přesné úložiště, ale poskytovatel se použije pro podporu typů [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Typy zprostředkovatele nebo úložiště jsou popsány v podmínkách Entity Data Model (EDM).  
  
 Parametry a návratovým typem pro funkce podporované v úložišti dat jsou určené v EDM podmínky.  
  
## <a name="requirements"></a>Požadavky  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a úložišti dat musí mít možnost předat data vpřed a zpět v známých typů bez ztráty dat nebo zkrácení.  
  
 Manifest zprostředkovatele musí být možné načíst pomocí nástrojů v době návrhu bez nutnosti otevřít připojení k úložišti.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je případ citlivé, ale nemusí být základnímu úložišti dat. Když artefakty EDM (názvy typu, například a identifikátory) jsou definovány a použít v manifestu, musíte použít [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] písmen. Pokud prvky úložiště dat, které mohou být velká a malá písmena v manifestu zprostředkovatele, musí být zachovány v manifestu zprostředkovatele, tento velká a malá písmena.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje manifest zprostředkovatele pro všechna data zprostředkovatele. Pokud se pokusíte použít poskytovatele, který nemá zprostředkovatele manifestu se [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], obdržíte chybu.  
  
 Následující tabulka popisuje druhy výjimek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] by výjimku při vzniknou výjimek prostřednictvím poskytovatele interakce:  
  
|Problém|Výjimka|  
|-----------|---------------|  
|Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.|ProviderIncompatibleException|  
|Chybějící manifest zprostředkovatele: zprostředkovatele vrátí `null` při pokusu o načtení manifest zprostředkovatele.|ProviderIncompatibleException|  
|Neplatný poskytovatel manifest: zprostředkovatel vrací neplatný kód XML při pokusu o načtení manifest zprostředkovatele.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scénáře  
 Poskytovatel by měl podporují následující scénáře:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Zápis zprostředkovatele s mapováním symetrický typu  
 Můžete napsat zprostředkovatele [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kde každý typ úložiště mapuje na jeden typ EDM, bez ohledu na směru mapování. Pro typ zprostředkovatele, který má velmi jednoduché mapování, která odpovídá typu EDM můžete použít symetrický řešení, protože systém typů je jednoduchá nebo odpovídá typů modelu EDM.  
  
 Můžete použít jednoduchost své domény a vytvoří manifest statické deklarativní poskytovatele.  
  
 Můžete napsat soubor XML, který má dvě části:  
  
- Seznam typů poskytovatelů vyjadřují "protějšek EDM" typ úložiště nebo funkce. Typy Store mají protějšek typů modelu EDM. Funkce Store mají odpovídající funkce EDM. Například varchar je typ serveru SQL Server, ale odpovídající typ EDM je řetězec.  
  
- Seznam funkcí podporovaných poskytovateli, ve kterém jsou parametry a návratovým typem vyjádřen v pojmech EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Zápis zprostředkovatele s mapováním asymetrického typu  
 Při psaní pro zprostředkovatele úložiště dat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], mapování pro některé typy mohou být odlišný od typu zprostředkovatele EDM mapování typů EDM zprostředkovatele. Například bez vazby modelu EDM PrimitiveTypeKind.String mohou být mapovány nvarchar(4000) na poskytovateli, zatímco nvarchar(4000) mapuje na EDM PrimitiveTypeKind.String(MaxLength=4000).  
  
 Můžete napsat soubor XML, který má dvě části:  
  
- Seznam typů poskytovatelů vyjádřen v pojmech EDM a definovat mapování pro oba směry: EDM poskytovatele a poskytovatele EDM.  
  
- Seznam funkcí podporovaných poskytovateli, ve kterém jsou parametry a návratovým typem vyjádřen v pojmech EDM.  
  
## <a name="provider-manifest-discoverability"></a>Zjistitelnost manifestu zprostředkovatele  
 Manifest je nepřímo používá několik typů součástí služby Entity (například nástroje nebo dotaz), ale informace přímo využíváno metadat prostřednictvím data ukládat metadata zavaděče.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Daný poskytovatel může však podporovat různých obchodech nebo různými verzemi stejného úložiště. Proto zprostředkovatele se musí hlásit různé manifestu pro každé podporované datové úložiště.  
  
### <a name="provider-manifest-token"></a>Token manifestu zprostředkovatele  
 Po otevření připojení úložiště dat zprostředkovatele můžete dotazovat na informace se vraťte správný manifest. To nemusí být možné v případě offline scénářů, kde není k dispozici informace o připojení nebo když není možné se připojit k úložišti. Identifikovat manifestu pomocí `ProviderManifestToken` atribut `Schema` element v souboru ssdl. Neexistuje žádné požadovaný formát pro tento atribut; Zprostředkovatel zvolí minimální informace potřebné k identifikaci manifest bez nutnosti otevřít připojení k úložišti.  
  
 Příklad:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Programovací Model manifestu zprostředkovatele  
 Poskytovatelé jsou odvozeny z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, který umožňuje zadat svých manifestech deklarativně. Následující obrázek znázorňuje hierarchii tříd zprostředkovatele:  
  
 ![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Zjistitelnost rozhraní API  
 Manifest zprostředkovatele je načten zavaděč Store Metadata (StoreItemCollection), s použitím dat uložit připojení nebo token manifestu zprostředkovatele.  
  
#### <a name="using-a-data-store-connection"></a>Data Store připojení  
 Při ukládání dat je k dispozici připojení, volejte DbProvderServices.GetProviderManifestToken vrátí token, který se předá metodě GetProviderManifest, které vrací DbProviderManifest. Tato metoda deleguje se do poskytovatele provádění GetDbProviderManifestToken.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Pomocí tokenu manifestu zprostředkovatele  
 Token scénáři offline, je odebrána ze souborů SSDL reprezentace. SSDL můžete zadat ProviderManifestToken (viz [Element schématu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) Další informace). Například pokud připojení nelze otevřít, SSDL má token manifestu zprostředkovatele, který určuje informace o manifestu.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schéma manifestu zprostředkovatele  
 Schéma informace definované pro každý poskytovatel obsahuje statické informace, které mají být využívány službou metadat:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a>Typy uzlů  
 Typy uzlů v manifestu zprostředkovatele, obsahuje informace o typech, které jsou nativně podporovány v úložišti dat nebo prostřednictvím poskytovatele.  
  
##### <a name="type-node"></a>Typ uzlu  
 Každý typ uzlu definuje typ zprostředkovatele z hlediska modelu EDM. Uzel typu popisuje název poskytovatele typu a informace týkající se typ modelu, který je namapován na a omezující vlastnosti k popisu mapování typu.  
  
 Aby bylo možné tento typ informací v manifestu zprostředkovatele, express, každý TypeInformation prohlášení musí definovat několik popisů omezující vlastnost pro každý typ:  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Název typu specifickým pro zprostředkovatele dat|  
|PrimitiveTypeKind|PrimitiveTypeKind|Ano|není k dispozici|Název typu EDM|  
  
###### <a name="function-node"></a>Uzel – funkce  
 Každá funkce definuje jedinou funkci k dispozici prostřednictvím poskytovatele.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Identifikátor nebo název funkce|  
|Vlastnost ReturnType|String|Ne|Typ void|Návratový typ funkce EDM|  
|Aggregate|Boolean|Ne|False|Hodnota TRUE, pokud funkce je agregační funkce|  
|BuiltIn|Boolean|Ne|Pravda|Hodnota TRUE, pokud funkce je integrovaná do úložiště dat|  
|StoreFunctionName|String|Ne|\<Název >|Název funkce v úložišti dat.  Umožňuje úroveň přesměrování názvy funkcí.|  
|NiladicFunction|Boolean|Ne|False|Hodnota TRUE v případě, že funkce nevyžaduje parametrů a je volána bez parametrů|  
|Zda položka ParameterType<br /><br /> Sémantika|ParameterSemantics|Ne|AllowImplicit<br /><br /> Konverze|Výběr jak kanálu dotazu by měl řešit nahrazení typ parametru:<br /><br /> -ExactMatchOnly<br />-AllowImplicitPromotion<br />-AllowImplicitConversion|  
  
 **Parametry uzlu**  
  
 Každá funkce má kolekce jednoho nebo více uzlů parametrů.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Identifikátor nebo název parametru.|  
|Type|String|Ano|není k dispozici|Typ EDM parametru.|  
|Režim|Parametr<br /><br /> Směr|Ano|není k dispozici|Směr parametru:<br /><br /> -v<br />-out<br />– vstup|  
  
##### <a name="namespace-attribute"></a>Atribut Namespace  
 Každý poskytovatel úložiště dat musí definovat obor názvů nebo skupiny oborů názvů informace definované v manifestu. Tento obor názvů lze použít v dotazech Entity SQL k překladu názvů funkcí a typů. Příklad: SqlServer. Tento obor názvů musí být odlišný od canonical obor názvů, EDM, určené služby Entity pro standardní funkce to, že dotazy Entity SQL.  
  
## <a name="see-also"></a>Viz také:

- [Zápis zprostředkovatele dat Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
