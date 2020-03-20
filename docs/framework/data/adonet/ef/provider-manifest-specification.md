---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 28bae8a6e249aa1fdab3c67759c8f8575cbdaa10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149723"
---
# <a name="provider-manifest-specification"></a>Specifikace manifestu zprostředkovatele
Tato část popisuje, jak zprostředkovatel úložiště dat může podporovat typy a funkce v úložišti dat.  
  
 Entity Services funguje nezávisle na konkrétním zprostředkovateli úložiště dat, ale stále umožňuje poskytovateli dat explicitně definovat, jak modely, mapování a dotazy spolupracují s podkladovým úložištěm dat. Bez vrstvy abstrakce entity služby by mohly být zaměřeny pouze na konkrétní úložiště dat nebo zprostředkovatele dat.  
  
 Typy, které podporuje zprostředkovatel jsou přímo nebo nepřímo podporovány podkladové databáze. Tyto typy nejsou nutně přesné typy úložiště, ale typy zprostředkovatel používá pro podporu entity framework. Typy zprostředkovatelů/obchodů jsou popsány v podmínkách datového modelu entity (EDM).  
  
 Parametry a návratové typy pro funkce podporované úložištěm dat jsou určeny v podmínkách EDM.  
  
## <a name="requirements"></a>Požadavky  
 Entity Framework a úložiště dat musí být schopen předávat data tam a zpět ve známých typů bez ztráty dat nebo zkrácení.  
  
 Manifest zprostředkovatele musí být zatěžovatelný nástroji v době návrhu bez nutnosti otevírat připojení k úložišti dat.  
  
 Entity Framework rozlišuje malá a velká písmena, ale základní úložiště dat nemusí být. Pokud jsou v manifestu definovány a používány artefakty EDM (například identifikátory a názvy typů), musí použít rozlišování velkých a malých písmen v rámci entit. Pokud prvky úložiště dat, které mohou být malá a velká písmena se zobrazí v manifestu zprostředkovatele, toto caseing musí být udržovány v manifestu zprostředkovatele.  
  
 Entity Framework vyžaduje manifest zprostředkovatele pro všechny zprostředkovatele dat. Pokud se pokusíte použít zprostředkovatele, který nemá manifest zprostředkovatele s entity framework, zobrazí se chyba.  
  
 Následující tabulka popisuje druhy výjimek, které by rozhraní entity vyvolalo, když dojde k výjimkám prostřednictvím interakce zprostředkovatele:  
  
|Problém|Výjimka|  
|-----------|---------------|  
|Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.|ZprostředkovatelNekompatibilníVýjimka|  
|Chybějící manifest zprostředkovatele: `null` zprostředkovatel vrátí při pokusu o načtení manifestu zprostředkovatele.|ZprostředkovatelNekompatibilníVýjimka|  
|Neplatný manifest zprostředkovatele: Zprostředkovatel vrátí neplatný xml při pokusu o načtení manifestu zprostředkovatele.|ZprostředkovatelNekompatibilníVýjimka|  
  
## <a name="scenarios"></a>Scénáře  
 Zprostředkovatel by měl podporovat následující scénáře:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Zápis zprostředkovatele s symetrickým mapováním typu  
 Můžete napsat zprostředkovatele pro entity framework, kde každý typ obchodu mapuje na jeden typ EDM, bez ohledu na směr mapování. Pro typ zprostředkovatele, který má velmi jednoduché mapování, které odpovídá typu EDM, můžete použít symetrické řešení, protože typ systému je jednoduchý nebo odpovídá typům EDM.  
  
 Můžete použít jednoduchost jejich domény a vytvořit statický deklarativní manifest zprostředkovatele.  
  
 Napíšete soubor XML, který má dva oddíly:  
  
- Seznam typů zprostředkovatelů vyjádřený jako "protějšek EDM" typu úložiště nebo funkce. Typy obchodů mají typy edm protějšků. Funkce úložiště mají odpovídající funkce EDM. Například varchar je typ serveru SQL Server, ale odpovídající typ EDM je řetězec.  
  
- Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v podmínkách EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Zápis zprostředkovatele s asymetrickým mapováním typu  
 Při zápisu zprostředkovatele úložiště dat pro entity framework, mapování typu EDM-to-provider pro některé typy se může lišit od mapování typu zprostředkovatele edm. Například neohraničené EDM PrimitiveTypeKind.String může mapovat na nvarchar(4000) na zprostředkovatele, zatímco nvarchar(4000) mapuje na EDM PrimitiveTypeKind.String(MaxLength = 4000).  
  
 Napíšete soubor XML, který má dva oddíly:  
  
- Seznam typů zprostředkovatelů vyjádřený v podmínkách EDM a definovat mapování pro oba směry: EDM-provider a provider-to-EDM.  
  
- Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v podmínkách EDM.  
  
## <a name="provider-manifest-discoverability"></a>Zjistitelnost manifestu zprostředkovatele  
 Manifest je používán nepřímo několika typy komponent ve službách entity (například nástroje nebo dotaz), ale více přímo využívají metadata pomocí zavaděče metadat úložiště dat.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Daný zprostředkovatel však může podporovat různé obchody nebo různé verze stejného úložiště. Zprostředkovatel proto musí hlásit jiný manifest pro každé podporované úložiště dat.  
  
### <a name="provider-manifest-token"></a>Token manifestu zprostředkovatele  
 Při otevření připojení úložiště dat zprostředkovatel může dotaz na informace vrátit správný manifest. To nemusí být možné v offline scénářích, kde nejsou k dispozici informace o připojení nebo pokud není možné se připojit k úložišti. Identifikujte `ProviderManifestToken` manifest `Schema` pomocí atributu prvku v souboru .ssdl. Pro tento atribut není vyžadován žádný formát. poskytovatel zvolí minimální informace potřebné k identifikaci manifestu bez otevření připojení k úložišti.  
  
 Například:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Programovací model manifestu zprostředkovatele  
 Zprostředkovatelé <xref:System.Data.Common.DbXmlEnabledProviderManifest>odvozují z , který jim umožňuje deklarativně specifikovat své manifesty. Následující obrázek znázorňuje hierarchii tříd zprostředkovatele:  
  
 ![Žádné](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Rozhraní API pro zjišťování  
 Manifest zprostředkovatele je načten zavaděč metadat úložiště (StoreItemCollection), buď pomocí připojení úložiště dat nebo token manifestu zprostředkovatele.  
  
#### <a name="using-a-data-store-connection"></a>Použití připojení úložiště dat  
 Pokud je k dispozici připojení <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> úložiště dat, volání vrátit <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> token, <xref:System.Data.Common.DbProviderManifest>který je předán metodě, která vrátí . Tato metoda deleguje implementaci `GetDbProviderManifestToken`zprostředkovatele .  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Použití tokenu manifestu zprostředkovatele  
 Pro offline scénář je token vyzvednut z reprezentace SSDL. SSDL umožňuje zadat ProviderManifestToken (viz [Prvek schématu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) pro další informace). Například pokud nelze otevřít připojení, SSDL má token manifestu zprostředkovatele, který určuje informace o manifestu.  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schéma manifestu zprostředkovatele  
 Schéma informací definovaných pro každého zprostředkovatele obsahuje statické informace, které mají být spotřebovány metadaty:  
  
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
  
#### <a name="types-node"></a>Uzel typů  
 Typ uzlu v manifestu zprostředkovatele obsahuje informace o Types, které jsou podporovány nativně úložiště dat nebo prostřednictvím zprostředkovatele.  
  
##### <a name="type-node"></a>Typový uzel  
 Každý uzel Typu definuje typ zprostředkovatele z hlediska EDM. Uzel Typ popisuje název typu zprostředkovatele a informace související s typem modelu, na který se mapuje, a omezující mise popisující mapování typu.  
  
 Chcete-li vyjádřit tento typ informace v manifestu zprostředkovatele, každý TypeInformation prohlášení musí definovat několik omezující tak pro každý Typ:  
  
|Název atributu|Typ dat|Požaduje se|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name (Název)|Řetězec|Ano|neuvedeno|Název datového typu specifického pro zprostředkovatele|  
|PrimitiveTypeKind|PrimitiveTypeKind|Ano|neuvedeno|Název typu EDM|  
  
###### <a name="function-node"></a>Uzel funkce  
 Každá funkce definuje jednu funkci, která je k dispozici prostřednictvím zprostředkovatele.  
  
|Název atributu|Typ dat|Požaduje se|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name (Název)|Řetězec|Ano|neuvedeno|Identifikátor/název funkce|  
|Returntype|Řetězec|Ne|Void|Návratový typ funkce EDM|  
|Agregace|Logická hodnota|Ne|False|True, pokud je funkce agregační funkce|  
|Builtin|Logická hodnota|Ne|True|True, pokud je funkce integrována do úložiště dat|  
|StoreFunctionName|Řetězec|Ne|\<Název>|Název funkce v úložišti dat.  Umožňuje úroveň přesměrování názvů funkcí.|  
|NiladicFunkce|Logická hodnota|Ne|False|True, pokud funkce nevyžaduje parametry a je volána bez parametrů|  
|ParametrType<br /><br /> Sémantika|ParametrYSématika|Ne|AllowImplicit<br /><br /> Převod|Volba způsobu, jakým by měl kanál dotazů zacházat s nahrazením typu parametru:<br /><br /> - ExactMatchOnly<br />- AllowImplicitiPromotion<br />- AllowImplicitConversion|  
  
 **Uzel parametry**  
  
 Každá funkce má kolekci jednoho nebo více uzlů parametru.  
  
|Název atributu|Typ dat|Požaduje se|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name (Název)|Řetězec|Ano|neuvedeno|Identifikátor/název parametru.|  
|Typ|Řetězec|Ano|neuvedeno|Typ EDM parametru.|  
|Mode|Parametr<br /><br /> Směr|Ano|neuvedeno|Směr parametru:<br /><br /> - v<br />- ven<br />- inout|  
  
##### <a name="namespace-attribute"></a>Atribut Oboru názvů  
 Každý zprostředkovatel úložiště dat musí definovat obor názvů nebo skupinu oborů názvů pro informace definované v manifestu. Tento obor názvů lze použít v dotazech entity SQL k překladu názvů funkcí a typů. Například: SqlServer. Tento obor názvů se musí lišit od kanonického oboru názvů EDM definovaného službou Entity Services pro standardní funkce podporované dotazy SQL entity.  
  
## <a name="see-also"></a>Viz také

- [Zápis zprostředkovatele dat Entity Framework](writing-an-ef-data-provider.md)
