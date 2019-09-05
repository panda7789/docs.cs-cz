---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 6b924f484e6635760d08d0eba9fb9436bdd8bc88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248590"
---
# <a name="provider-manifest-specification"></a>Specifikace manifestu zprostředkovatele
Tato část popisuje, jak může zprostředkovatel úložiště dat podporovat typy a funkce v úložišti dat.  
  
 Služby entit pracují nezávisle na konkrétním poskytovateli úložiště dat. Zprostředkovatel dat však stále umožňuje poskytovateli dat explicitně definovat, jak modely, mapování a dotazy budou fungovat s podkladovým úložištěm dat. Bez vrstvy abstrakce by mohly být služby entit cílené jenom na konkrétní úložiště dat nebo poskytovatele dat.  
  
 Typy, které podporuje zprostředkovatel, jsou přímo nebo nepřímo podporovány podkladovou databází. Tyto typy nejsou nutně v přesném typu úložiště, ale typy, které poskytovatel používá pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Typy poskytovatel/úložiště jsou popsány v tématu model EDM (Entity Data Model) (EDM).  
  
 Parametry a návratové typy pro funkce podporované úložištěm dat jsou určené v rámci podmínek EDM.  
  
## <a name="requirements"></a>Požadavky  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] A úložiště dat musí být schopné předat data zpátky a zpátky do známých typů bez ztráty dat nebo zkrácení.  
  
 Manifest zprostředkovatele musí být spustitelný nástroji v době návrhu, aniž by bylo nutné otevřít připojení k úložišti dat.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Rozlišuje velká a malá písmena, ale příslušné úložiště dat nemusí být. Pokud jsou v manifestu definovány a použity artefakty EDM (například identifikátory a názvy typů), musí používat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] rozlišování velkých a malých písmen. Pokud se v manifestu zprostředkovatele objeví prvky úložiště dat, které můžou rozlišovat velká a malá písmena, musí být toto pouzdro udržováno v manifestu zprostředkovatele.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje manifest zprostředkovatele pro všechny poskytovatele dat. Pokud se pokusíte použít poskytovatele, který nemá manifest zprostředkovatele s rozhraním [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobrazí se chyba.  
  
 Následující tabulka popisuje typy výjimek, které [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] by byly vyvolány při výskytu výjimek prostřednictvím interakce poskytovatele:  
  
|Problém|Výjimka|  
|-----------|---------------|  
|Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.|ProviderIncompatibleException|  
|Chybějící manifest zprostředkovatele: poskytovatel se vrátí `null` při pokusu o načtení manifestu poskytovatele.|ProviderIncompatibleException|  
|Neplatný manifest zprostředkovatele: zprostředkovatel při pokusu o načtení manifestu poskytovatele vrátí neplatný kód XML.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Scénáře  
 Poskytovatel by měl podporovat následující scénáře:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Zápis zprostředkovatele pomocí mapování symetrického typu  
 Můžete napsat poskytovatele pro, kde se [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] každý typ úložiště mapuje na jeden typ EDM bez ohledu na směr mapování. Pro typ poskytovatele, který má velmi jednoduché mapování, které odpovídá typu EDM, můžete použít symetrické řešení, protože systém typů je jednoduchý nebo se shoduje s typy EDM.  
  
 Můžete použít jednoduchost své domény a vytvořit statický manifest deklarativního zprostředkovatele.  
  
 Napíšete soubor XML, který má dvě části:  
  
- Seznam typů zprostředkovatelů vyjádřených v souvislosti s typem "EDM protějšek" typu nebo funkce úložiště. Typy úložiště mají protějšky typu EDM. Funkce úložiště mají odpovídající funkce modelu EDM. Například varchar je typ SQL Server, ale odpovídající typ EDM je řetězec.  
  
- Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v terminologii EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Zápis zprostředkovatele s mapováním asymetrického typu  
 Při psaní zprostředkovatele úložiště dat pro je [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]možné mapování typu EDM-to-Provider pro některé typy lišit od mapování typu od poskytovatele k modelu EDM. Například nevázaný vlastnost PrimitiveTypeKind EDM. String se může namapovat na nvarchar (4000) na poskytovateli, zatímco nvarchar (4000) se mapuje na vlastnost PrimitiveTypeKind EDM. String (MaxLength = 4000).  
  
 Napíšete soubor XML, který má dvě části:  
  
- Seznam typů zprostředkovatelů vyjádřených v terminologii EDM a definování mapování pro oba směry: EDM-to-Provider a Provider-to-EDM.  
  
- Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v terminologii EDM.  
  
## <a name="provider-manifest-discoverability"></a>Zjistitelnost manifestu zprostředkovatele  
 Manifest se používá nepřímo několika typy komponent v entitních službách (například nástroje nebo dotaz), ale více přímo je využívá metadata prostřednictvím zavaděče metadat úložiště dat.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Daný zprostředkovatel však může podporovat různá úložiště nebo různé verze stejného úložiště. Proto musí zprostředkovatel nahlásit jiný manifest pro každé podporované úložiště dat.  
  
### <a name="provider-manifest-token"></a>Token manifestu zprostředkovatele  
 Když je otevřeno připojení úložiště dat, může se zprostředkovatel dotazovat na informace, které vrátí správný manifest. To nemusí být možné v offline scénářích, kde nejsou k dispozici informace o připojení nebo když není možné se připojit k úložišti. Identifikujte manifest pomocí `ProviderManifestToken` atributu `Schema` elementu v souboru. ssdl. Pro tento atribut není vyžadován žádný formát. poskytovatel zvolí minimální informace potřebné k identifikaci manifestu bez otevření připojení k úložišti.  
  
 Příklad:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Model programování manifestu zprostředkovatele  
 Zprostředkovatelé jsou <xref:System.Data.Common.DbXmlEnabledProviderManifest>odvozeni z, což umožňuje jejich deklarativní určení jejich manifestů. Následující ilustrace znázorňuje hierarchii tříd zprostředkovatele:  
  
 ![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Rozhraní API pro zjišťování  
 Manifest zprostředkovatele je načten zavaděčem metadat úložiště (StoreItemCollection), a to buď pomocí připojení úložiště dat, nebo tokenu manifestu zprostředkovatele.  
  
#### <a name="using-a-data-store-connection"></a>Použití připojení úložiště dat  
 Když je k dispozici připojení úložiště dat, <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> zavolejte na vrácení tokenu, který je předán <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> metodě, která vrací <xref:System.Data.Common.DbProviderManifest>. Tato metoda se deleguje k implementaci `GetDbProviderManifestToken`poskytovatele.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Použití tokenu manifestu zprostředkovatele  
 Pro offline scénář je token vydaný z reprezentace SSDL. SSDL umožňuje zadat ProviderManifestToken (Další informace naleznete v tématu [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ). Například pokud nelze připojení otevřít, má SSDL token manifestu, který určuje informace o manifestu.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Schéma manifestu zprostředkovatele  
 Schéma informací definovaných pro každého zprostředkovatele obsahuje statické informace, které musí metadata spotřebovat:  
  
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
 Uzel typy v manifestu zprostředkovatele obsahuje informace o typech, které jsou nativně podporovány úložištěm dat nebo poskytovatelem.  
  
##### <a name="type-node"></a>Uzel typu  
 Každý uzel typu definuje typ poskytovatele z pohledu EDM. Uzel typu popisuje název typu zprostředkovatele a informace týkající se typu modelu, ke kterému se mapuje, a omezující vlastnosti pro popis tohoto mapování typů.  
  
 Aby bylo možné vyjádřit tyto informace o typu v manifestu zprostředkovatele, musí každá deklarace TypeInformation definovat několik popisů omezujících vlastností pro každý typ:  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name|String|Ano|není k dispozici|Název specifického datového typu pro konkrétního poskytovatele|  
|PrimitiveTypeKind|PrimitiveTypeKind|Ano|není k dispozici|Název typu EDM|  
  
###### <a name="function-node"></a>Uzel funkce  
 Každá funkce definuje jednu funkci dostupnou prostřednictvím poskytovatele.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name|String|Ano|není k dispozici|Identifikátor/název funkce|  
|ReturnType|String|Ne|Šekem|Návratový typ EDM funkce|  
|Aggregate|Boolean|Ne|False|True, pokud je funkce agregační funkcí|  
|Integrované|Boolean|Ne|Pravda|True, pokud je funkce integrovaná do úložiště dat|  
|StoreFunctionName|String|Ne|\<Název >|Název funkce v úložišti dat.  Umožňuje úroveň přesměrování názvů funkcí.|  
|NiladicFunction|Boolean|Ne|False|True, pokud funkce nevyžaduje parametry a je volána bez parametrů|  
|Zadanému ParameterType<br /><br /> Sémantiku|ParameterSemantics|Ne|AllowImplicit<br /><br /> Konverze|Volba způsobu, jakým by měl kanál dotazu pracovat s nahrazením typu parametru:<br /><br /> – ExactMatchOnly<br />– AllowImplicitPromotion<br />– AllowImplicitConversion|  
  
 **Uzel parametrů**  
  
 Každá funkce má kolekci jednoho nebo více uzlů parametrů.  
  
|Název atributu|Datový typ|Požadováno|Výchozí hodnota|Popis|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Name|String|Ano|není k dispozici|Identifikátor/název parametru.|  
|type|String|Ano|není k dispozici|Typ typu EDM parametru.|  
|Režim|Parametr<br /><br /> Směr|Ano|není k dispozici|Směr parametru:<br /><br /> -in<br />-out<br />– InOut|  
  
##### <a name="namespace-attribute"></a>Atribut namespace  
 Každý poskytovatel úložiště dat musí definovat obor názvů nebo skupinu oborů názvů pro informace definované v manifestu. Tento obor názvů se dá použít v Entity SQLch dotazech k překladu názvů funkcí a typů. Příklad: SqlServer. Tento obor názvů musí být jiný než kanonický obor názvů (EDM) definovaný službou entity Services, aby se standardní funkce podporovaly pomocí Entity SQL dotazů.  
  
## <a name="see-also"></a>Viz také:

- [Zápis zprostředkovatele dat Entity Framework](writing-an-ef-data-provider.md)
