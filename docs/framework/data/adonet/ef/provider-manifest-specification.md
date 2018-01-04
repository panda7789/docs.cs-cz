---
title: "Specifikace manifestu zprostředkovatele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3e80b5bb62cc785c220e2baeb773e6990c5fee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="provider-manifest-specification"></a>Specifikace manifestu zprostředkovatele
Tato část popisuje, jak můžete zprostředkovatele úložiště dat podporují typy a funkce v úložišti.  
  
 Entity služby funguje nezávisle na konkrétní data zprostředkovatele úložiště ještě stále umožňuje zprostředkovatele dat explicitně definujte, jak komunikovat s základní úložiště dat. modely, mapování a dotazů. Bez úroveň abstrakce Entity služby může být cílena na konkrétní data store nebo zprostředkovatele dat.  
  
 Typy, které zprostředkovatel podporuje přímo nebo nepřímo podporuje základní databáze. Tyto typy, nemusí nutně být typy přesný úložiště, ale typy používá zprostředkovatel pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Typy poskytovatele/úložiště jsou popsané v podmínkách Entity Data Model (EDM).  
  
 Parametr a návratové typy pro funkce nepodporuje úložiště dat jsou určené v podmínky EDM.  
  
## <a name="requirements"></a>Požadavky  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a úložiště dat musejí mít k předávání dat a zpět v známé typy bez ztráty dat nebo zkrácení.  
  
 Manifest zprostředkovatele musí být možné načíst pomocí nástrojů v době návrhu bez nutnosti otevřít připojení k úložišti.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je případ citlivé, ale nemusí být příslušné datové úložiště. Když artefakty EDM (identifikátory a názvy typů, např.) jsou definováni a použít v manifestu, musíte použít [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] písmen. Pokud datové úložiště prvky, které může být malá a velká písmena se zobrazí v manifestu zprostředkovatele, je třeba zachovat v manifestu zprostředkovatele, že velká a malá písmena.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje manifest zprostředkovatele pro všechny poskytovatele data. Pokud se pokusíte použít poskytovatele, který nemá zprostředkovatele manifestu s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobrazí se chyba.  
  
 Následující tabulka popisuje druhy výjimek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] by výjimku při výjimky jsou vyvolány prostřednictvím interakci poskytovatele:  
  
|Problém|Výjimka|  
|-----------|---------------|  
|Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.|ProviderIncompatibleException|  
|Chybí manifest zprostředkovatele: Zprostředkovatel vrátí `null` při pokusu o načtení manifestu zprostředkovatele.|ProviderIncompatibleException|  
|Manifest zprostředkovatele neplatný: Zprostředkovatel vrátí neplatný kód XML při pokusu o načtení manifestu zprostředkovatele.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scénáře  
 Zprostředkovatel musí podporují následující scénáře:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Zápis zprostředkovatele s mapováním symetrický typu  
 Můžete napsat poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kde každý typ úložiště mapuje jeden typ EDM, bez ohledu na to, že mapování směr. Pro typ zprostředkovatele, který má velmi jednoduché mapování, která odpovídá typu EDM můžete použít symetrický řešení, protože je jednoduchý systém typů nebo odpovídá typů EDM.  
  
 Můžete použít jednoduchost svoji doménu a vytvoření manifestu statické deklarativní zprostředkovatele.  
  
 Můžete zapsat soubor XML, který má dvě části:  
  
-   Seznam typů zprostředkovatele vyjádřené jako "protějšku EDM" typ úložiště nebo funkce. Typy úložiště mají protějšku typy EDM. Funkce úložiště mají odpovídající funkce EDM. Například varchar je typ systému SQL Server, ale odpovídající typ EDM je řetězec.  
  
-   Seznam funkcí podporovaných poskytovatelem, kde parametr a návratové typy jsou uvedeny v podmínkách EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Zápis zprostředkovatele s mapováním asymetrické typu  
 Při zápisu zprostředkovatele úložiště dat pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], typ EDM zprostředkovatele mapování pro některé typy se může lišit od mapování typu zprostředkovatele EDM. Například může bez vazby PrimitiveTypeKind.String EDM mapovat do nvarchar(4000) na zprostředkovateli při nvarchar(4000) mapuje EDM PrimitiveTypeKind.String(MaxLength=4000).  
  
 Můžete zapsat soubor XML, který má dvě části:  
  
-   Seznam typů zprostředkovatele vyjádřený v podmínkách EDM a definovat mapování pro obě směr: EDM zprostředkovatele a zprostředkovatele EDM.  
  
-   Seznam funkcí podporovaných poskytovatelem, kde parametr a návratové typy jsou uvedeny v podmínkách EDM.  
  
## <a name="provider-manifest-discoverability"></a>Vyhledání manifestu zprostředkovatele  
 Manifest nepřímo používá několik typů součásti v Entity služby (například nástroje nebo dotazu), ale informace přímo využít metadat prostřednictvím data ukládat zavaděč metadat.  
  
 ![dfb3d02b & č. 45; 7a8c & č. 45; 4d 51 & č. 45; ac5a & č. 45; a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Různých obchodů nebo různé verze stejného úložiště může však podporovat daného zprostředkovatele. Proto musí zprostředkovatele nahlásit různých manifestu pro každé podporované datové úložiště.  
  
### <a name="provider-manifest-token"></a>Token manifestu zprostředkovatele  
 Po otevření připojení úložišti dat zprostředkovatele můžete dotazovat informace, které vrátí správné manifestu. Toto nemusí být možné v offline scénářích, kde informace o připojení není k dispozici nebo pokud není možné se připojit k úložišti. Identifikovat manifest pomocí `ProviderManifestToken` atribut `Schema` element v souboru ssdl. Požadovaný formát není pro tento atribut; Zprostředkovatel zvolí minimální informace potřebné k identifikaci manifestu bez otevření připojení k úložišti.  
  
 Příklad:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programování manifestu zprostředkovatele  
 Poskytovatelé jsou odvozeny od <xref:System.Data.Common.DbXmlEnabledProviderManifest>, což umožňuje jejich zadejte jejich manifesty deklarativně. Následující obrázek znázorňuje hierarchie tříd zprostředkovatele:  
  
 ![Žádný](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Možnosti rozpoznání rozhraní API  
 Manifest zprostředkovatele je načíst zavaděčem ukládání metadat (StoreItemCollection), buď pomocí dat uložení připojení nebo tokenu manifestu zprostředkovatele.  
  
#### <a name="using-a-data-store-connection"></a>Pomocí připojení k úložišti dat  
 Při ukládání dat není k dispozici připojení, volejte DbProvderServices.GetProviderManifestToken vrátit token, který je předaný metodě GetProviderManifest, která vrátí hodnotu třída DbProviderManifest. Tato metoda provede delegaci pro poskytovatele implementace GetDbProviderManifestToken.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Pomocí tokenu manifestu zprostředkovatele  
 Offline scénář token vydán z reprezentace SSDL. SSDL umožňuje určit ProviderManifestToken (najdete v části [Element schématu (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222) informace). Například pokud připojení nelze otevřít, SSDL má token manifestu zprostředkovatele, která určuje informace o manifest.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schéma manifestu zprostředkovatele  
 Schéma definované pro každého zprostředkovatele informace obsahuje statický informace, které mají být využívány službou metadat:  
  
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
  
#### <a name="types-node"></a>Uzel typy  
 Uzel typy v manifestu zprostředkovatele, obsahuje informace o typech, které jsou nativně podporovány úložiště dat nebo prostřednictvím poskytovatele.  
  
##### <a name="type-node"></a>Typ uzlu  
 Každý typ uzlu definuje typ zprostředkovatele z hlediska EDM. Typ uzlu popisuje název typu zprostředkovatele, a informace týkající se typ modelu, který se mapuje na a omezující vlastnosti popisují mapování tohoto typu.  
  
 Chcete-li express tento typ informací v manifestu zprostředkovatele, musí každá deklarace TypeInformation definovat několik popis omezující vlastnosti pro každý typ:  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Název typu specifický pro zprostředkovatele dat|  
|Hodnota typu PrimitiveTypeKind|Hodnota typu PrimitiveTypeKind|Ano|není k dispozici|Název typu EDM|  
  
###### <a name="function-node"></a>Uzel – funkce  
 Jednotlivé funkce definuje jedinou funkci k dispozici prostřednictvím poskytovatele.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Identifikátor nebo název funkce|  
|Vlastnost ReturnType|String|Ne|Void|Návratový typ EDM funkce|  
|Aggregate|Boolean|Ne|False|Hodnota TRUE, pokud je funkce agregační funkce|  
|Předdefinované|Boolean|Ne|Hodnota TRUE|Hodnota TRUE, pokud je funkce integrovaná v úložišti dat.|  
|StoreFunctionName|String|Ne|\<Name >|Název funkce v úložišti dat.  Umožňuje pro úroveň přesměrování názvy funkcí.|  
|NiladicFunction|Boolean|Ne|False|Hodnota TRUE, pokud funkce nevyžaduje, parametry a je volána bez parametrů|  
|ParameterType<br /><br /> Sémantika|ParameterSemantics|Ne|AllowImplicit<br /><br /> Převod|Volba jak by se měl kanálu dotazu zabývat nahrazování parametru typu:<br /><br /> -ExactMatchOnly<br />-AllowImplicitPromotion<br />-AllowImplicitConversion|  
  
 **Parametry uzlu**  
  
 Jednotlivé funkce má kolekce jednoho či více uzlů parametr.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Název|String|Ano|není k dispozici|Identifikátor nebo název parametru.|  
|Typ|String|Ano|není k dispozici|Typ EDM parametru.|  
|Režim|Parametr<br /><br /> Směr|Ano|není k dispozici|Směr parametru:<br /><br /> -v<br />-out<br />-inout|  
  
##### <a name="namespace-attribute"></a>Atribut Namespace  
 Každý poskytovatel úložiště dat musí definovat v oboru názvů nebo skupině obory názvů pro informace definované v manifestu. Tento obor názvů lze v dotazech Entity SQL přeložit názvy funkcí a typy. Například: SQL Server. Tento obor názvů musí být odlišný od kanonický oboru názvů, EDM, definované Entity služby pro standardní funkce podporovaná dotazy Entity SQL.  
  
## <a name="see-also"></a>Viz také  
 [Zápis zprostředkovatele dat Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
