---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: a9dca140588be26035b235109c48049ce01e9ce1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973889"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="82eef-102">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-102">Provider Manifest Specification</span></span>
<span data-ttu-id="82eef-103">Tato část popisuje, jak může zprostředkovatel úložiště dat podporovat typy a funkce v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="82eef-104">Služby entit pracují nezávisle na konkrétním poskytovateli úložiště dat. Zprostředkovatel dat však stále umožňuje poskytovateli dat explicitně definovat, jak modely, mapování a dotazy budou fungovat s podkladovým úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="82eef-105">Bez vrstvy abstrakce by mohly být služby entit cílené jenom na konkrétní úložiště dat nebo poskytovatele dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="82eef-106">Typy, které podporuje zprostředkovatel, jsou přímo nebo nepřímo podporovány podkladovou databází.</span><span class="sxs-lookup"><span data-stu-id="82eef-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="82eef-107">Tyto typy nejsou nutně v přesném typu úložiště, ale typy, které zprostředkovatel používá pro podporu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="82eef-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="82eef-108">Typy poskytovatel/úložiště jsou popsány v tématu model EDM (Entity Data Model) (EDM).</span><span class="sxs-lookup"><span data-stu-id="82eef-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="82eef-109">Parametry a návratové typy pro funkce podporované úložištěm dat jsou určené v rámci podmínek EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82eef-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82eef-110">Requirements</span></span>  
 <span data-ttu-id="82eef-111">Entity Framework a úložiště dat musí být schopné předat data zpátky a zpátky do známých typů, aniž by došlo ke ztrátě nebo zkracování dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="82eef-112">Manifest zprostředkovatele musí být spustitelný nástroji v době návrhu, aniž by bylo nutné otevřít připojení k úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="82eef-113">Entity Framework rozlišuje velká a malá písmena, ale příslušné úložiště dat nemusí být.</span><span class="sxs-lookup"><span data-stu-id="82eef-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="82eef-114">Pokud jsou v manifestu definovány a použity artefakty EDM (například identifikátory a názvy typů), musí používat rozlišování velkých a malých písmen Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="82eef-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="82eef-115">Pokud se v manifestu zprostředkovatele objeví prvky úložiště dat, které můžou rozlišovat velká a malá písmena, musí být toto pouzdro udržováno v manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="82eef-116">Entity Framework vyžaduje manifest zprostředkovatele pro všechny poskytovatele dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="82eef-117">Pokud se pokusíte použít poskytovatele, který nemá manifest zprostředkovatele s Entity Framework, zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="82eef-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="82eef-118">Následující tabulka popisuje typy výjimek, které Entity Framework by vyvolaly při výjimkách prostřednictvím interakce poskytovatele:</span><span class="sxs-lookup"><span data-stu-id="82eef-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="82eef-119">Problém</span><span class="sxs-lookup"><span data-stu-id="82eef-119">Issue</span></span>|<span data-ttu-id="82eef-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="82eef-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="82eef-121">Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="82eef-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="82eef-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="82eef-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="82eef-123">Chybějící manifest zprostředkovatele: Zprostředkovatel vrací `null` při pokusu o načtení manifestu poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="82eef-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="82eef-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="82eef-125">Neplatný manifest zprostředkovatele: zprostředkovatel při pokusu o načtení manifestu poskytovatele vrátí neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="82eef-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="82eef-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="82eef-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="82eef-127">Scénáře</span><span class="sxs-lookup"><span data-stu-id="82eef-127">Scenarios</span></span>  
 <span data-ttu-id="82eef-128">Poskytovatel by měl podporovat následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="82eef-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="82eef-129">Zápis zprostředkovatele pomocí mapování symetrického typu</span><span class="sxs-lookup"><span data-stu-id="82eef-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="82eef-130">Můžete napsat poskytovatele pro Entity Framework, kde se každý typ úložiště mapuje na jeden typ EDM bez ohledu na směr mapování.</span><span class="sxs-lookup"><span data-stu-id="82eef-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="82eef-131">Pro typ poskytovatele, který má velmi jednoduché mapování, které odpovídá typu EDM, můžete použít symetrické řešení, protože systém typů je jednoduchý nebo se shoduje s typy EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="82eef-132">Můžete použít jednoduchost své domény a vytvořit statický manifest deklarativního zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="82eef-133">Napíšete soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="82eef-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="82eef-134">Seznam typů zprostředkovatelů vyjádřených v souvislosti s typem "EDM protějšek" typu nebo funkce úložiště.</span><span class="sxs-lookup"><span data-stu-id="82eef-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="82eef-135">Typy úložiště mají protějšky typu EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="82eef-136">Funkce úložiště mají odpovídající funkce modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="82eef-137">Například varchar je typ SQL Server, ale odpovídající typ EDM je řetězec.</span><span class="sxs-lookup"><span data-stu-id="82eef-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="82eef-138">Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v terminologii EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="82eef-139">Zápis zprostředkovatele s mapováním asymetrického typu</span><span class="sxs-lookup"><span data-stu-id="82eef-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="82eef-140">Při psaní zprostředkovatele úložiště dat pro Entity Framework se mapování typu EDM-to-Provider u některých typů může lišit od mapování typu od poskytovatele k modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="82eef-141">Například nevázaný vlastnost PrimitiveTypeKind EDM. String se může namapovat na nvarchar (4000) na poskytovateli, zatímco nvarchar (4000) se mapuje na vlastnost PrimitiveTypeKind EDM. String (MaxLength = 4000).</span><span class="sxs-lookup"><span data-stu-id="82eef-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="82eef-142">Napíšete soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="82eef-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="82eef-143">Seznam typů zprostředkovatelů vyjádřených v terminologii EDM a definování mapování pro oba směry: EDM-to-Provider a Provider-to-EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="82eef-144">Seznam funkcí podporovaných poskytovatelem, kde jsou parametry a návratové typy vyjádřeny v terminologii EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="82eef-145">Zjistitelnost manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="82eef-146">Manifest se používá nepřímo několika typy komponent v entitních službách (například nástroje nebo dotaz), ale více přímo je využívá metadata prostřednictvím zavaděče metadat úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="82eef-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="82eef-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="82eef-148">Daný zprostředkovatel však může podporovat různá úložiště nebo různé verze stejného úložiště.</span><span class="sxs-lookup"><span data-stu-id="82eef-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="82eef-149">Proto musí zprostředkovatel nahlásit jiný manifest pro každé podporované úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="82eef-150">Token manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="82eef-151">Když je otevřeno připojení úložiště dat, může se zprostředkovatel dotazovat na informace, které vrátí správný manifest.</span><span class="sxs-lookup"><span data-stu-id="82eef-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="82eef-152">To nemusí být možné v offline scénářích, kde nejsou k dispozici informace o připojení nebo když není možné se připojit k úložišti.</span><span class="sxs-lookup"><span data-stu-id="82eef-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="82eef-153">Identifikujte manifest pomocí atributu `ProviderManifestToken` elementu `Schema` v souboru. ssdl.</span><span class="sxs-lookup"><span data-stu-id="82eef-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="82eef-154">Pro tento atribut není vyžadován žádný formát. poskytovatel zvolí minimální informace potřebné k identifikaci manifestu bez otevření připojení k úložišti.</span><span class="sxs-lookup"><span data-stu-id="82eef-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="82eef-155">Příklad:</span><span class="sxs-lookup"><span data-stu-id="82eef-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="82eef-156">Model programování manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="82eef-157">Zprostředkovatelé jsou odvozeni z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, což umožňuje jejich deklarativní určení jejich manifestů.</span><span class="sxs-lookup"><span data-stu-id="82eef-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="82eef-158">Následující ilustrace znázorňuje hierarchii tříd zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="82eef-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="82eef-159">![NTato](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="82eef-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="82eef-160">Rozhraní API pro zjišťování</span><span class="sxs-lookup"><span data-stu-id="82eef-160">Discoverability API</span></span>  
 <span data-ttu-id="82eef-161">Manifest zprostředkovatele je načten zavaděčem metadat úložiště (StoreItemCollection), a to buď pomocí připojení úložiště dat, nebo tokenu manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="82eef-162">Použití připojení úložiště dat</span><span class="sxs-lookup"><span data-stu-id="82eef-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="82eef-163">Když je k dispozici připojení úložiště dat, zavolejte <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> a vraťte token, který je předán metodě <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A>, která vrátí <xref:System.Data.Common.DbProviderManifest>.</span><span class="sxs-lookup"><span data-stu-id="82eef-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="82eef-164">Tato metoda se deleguje k implementaci `GetDbProviderManifestToken`poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="82eef-165">Použití tokenu manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="82eef-166">Pro offline scénář je token vydaný z reprezentace SSDL.</span><span class="sxs-lookup"><span data-stu-id="82eef-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="82eef-167">SSDL umožňuje zadat ProviderManifestToken (Další informace naleznete v tématu [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ).</span><span class="sxs-lookup"><span data-stu-id="82eef-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="82eef-168">Například pokud nelze připojení otevřít, má SSDL token manifestu, který určuje informace o manifestu.</span><span class="sxs-lookup"><span data-stu-id="82eef-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="82eef-169">Schéma manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="82eef-170">Schéma informací definovaných pro každého zprostředkovatele obsahuje statické informace, které musí metadata spotřebovat:</span><span class="sxs-lookup"><span data-stu-id="82eef-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="82eef-171">Uzel typů</span><span class="sxs-lookup"><span data-stu-id="82eef-171">Types Node</span></span>  
 <span data-ttu-id="82eef-172">Uzel typy v manifestu zprostředkovatele obsahuje informace o typech, které jsou nativně podporovány úložištěm dat nebo poskytovatelem.</span><span class="sxs-lookup"><span data-stu-id="82eef-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="82eef-173">Uzel typu</span><span class="sxs-lookup"><span data-stu-id="82eef-173">Type Node</span></span>  
 <span data-ttu-id="82eef-174">Každý uzel typu definuje typ poskytovatele z pohledu EDM.</span><span class="sxs-lookup"><span data-stu-id="82eef-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="82eef-175">Uzel typu popisuje název typu zprostředkovatele a informace týkající se typu modelu, ke kterému se mapuje, a omezující vlastnosti pro popis tohoto mapování typů.</span><span class="sxs-lookup"><span data-stu-id="82eef-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="82eef-176">Aby bylo možné vyjádřit tyto informace o typu v manifestu zprostředkovatele, musí každá deklarace TypeInformation definovat několik popisů omezujících vlastností pro každý typ:</span><span class="sxs-lookup"><span data-stu-id="82eef-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="82eef-177">Název atributu</span><span class="sxs-lookup"><span data-stu-id="82eef-177">Attribute Name</span></span>|<span data-ttu-id="82eef-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="82eef-178">Data Type</span></span>|<span data-ttu-id="82eef-179">Požadováno</span><span class="sxs-lookup"><span data-stu-id="82eef-179">Required</span></span>|<span data-ttu-id="82eef-180">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="82eef-180">Default Value</span></span>|<span data-ttu-id="82eef-181">Popis</span><span class="sxs-lookup"><span data-stu-id="82eef-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="82eef-182">Name</span><span class="sxs-lookup"><span data-stu-id="82eef-182">Name</span></span>|<span data-ttu-id="82eef-183">String</span><span class="sxs-lookup"><span data-stu-id="82eef-183">String</span></span>|<span data-ttu-id="82eef-184">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-184">Yes</span></span>|<span data-ttu-id="82eef-185">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-185">n/a</span></span>|<span data-ttu-id="82eef-186">Název specifického datového typu pro konkrétního poskytovatele</span><span class="sxs-lookup"><span data-stu-id="82eef-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="82eef-187">Vlastnost PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="82eef-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="82eef-188">Vlastnost PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="82eef-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="82eef-189">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-189">Yes</span></span>|<span data-ttu-id="82eef-190">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-190">n/a</span></span>|<span data-ttu-id="82eef-191">Název typu EDM</span><span class="sxs-lookup"><span data-stu-id="82eef-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="82eef-192">Uzel funkce</span><span class="sxs-lookup"><span data-stu-id="82eef-192">Function Node</span></span>  
 <span data-ttu-id="82eef-193">Každá funkce definuje jednu funkci dostupnou prostřednictvím poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="82eef-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="82eef-194">Název atributu</span><span class="sxs-lookup"><span data-stu-id="82eef-194">Attribute Name</span></span>|<span data-ttu-id="82eef-195">Datový typ</span><span class="sxs-lookup"><span data-stu-id="82eef-195">Data Type</span></span>|<span data-ttu-id="82eef-196">Požadováno</span><span class="sxs-lookup"><span data-stu-id="82eef-196">Required</span></span>|<span data-ttu-id="82eef-197">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="82eef-197">Default Value</span></span>|<span data-ttu-id="82eef-198">Popis</span><span class="sxs-lookup"><span data-stu-id="82eef-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="82eef-199">Name</span><span class="sxs-lookup"><span data-stu-id="82eef-199">Name</span></span>|<span data-ttu-id="82eef-200">String</span><span class="sxs-lookup"><span data-stu-id="82eef-200">String</span></span>|<span data-ttu-id="82eef-201">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-201">Yes</span></span>|<span data-ttu-id="82eef-202">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-202">n/a</span></span>|<span data-ttu-id="82eef-203">Identifikátor/název funkce</span><span class="sxs-lookup"><span data-stu-id="82eef-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="82eef-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="82eef-204">ReturnType</span></span>|<span data-ttu-id="82eef-205">String</span><span class="sxs-lookup"><span data-stu-id="82eef-205">String</span></span>|<span data-ttu-id="82eef-206">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-206">No</span></span>|<span data-ttu-id="82eef-207">Šekem</span><span class="sxs-lookup"><span data-stu-id="82eef-207">Void</span></span>|<span data-ttu-id="82eef-208">Návratový typ EDM funkce</span><span class="sxs-lookup"><span data-stu-id="82eef-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="82eef-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="82eef-209">Aggregate</span></span>|<span data-ttu-id="82eef-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="82eef-210">Boolean</span></span>|<span data-ttu-id="82eef-211">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-211">No</span></span>|<span data-ttu-id="82eef-212">False</span><span class="sxs-lookup"><span data-stu-id="82eef-212">False</span></span>|<span data-ttu-id="82eef-213">True, pokud je funkce agregační funkcí</span><span class="sxs-lookup"><span data-stu-id="82eef-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="82eef-214">Integrované</span><span class="sxs-lookup"><span data-stu-id="82eef-214">BuiltIn</span></span>|<span data-ttu-id="82eef-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="82eef-215">Boolean</span></span>|<span data-ttu-id="82eef-216">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-216">No</span></span>|<span data-ttu-id="82eef-217">Podmínka</span><span class="sxs-lookup"><span data-stu-id="82eef-217">True</span></span>|<span data-ttu-id="82eef-218">True, pokud je funkce integrovaná do úložiště dat</span><span class="sxs-lookup"><span data-stu-id="82eef-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="82eef-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="82eef-219">StoreFunctionName</span></span>|<span data-ttu-id="82eef-220">String</span><span class="sxs-lookup"><span data-stu-id="82eef-220">String</span></span>|<span data-ttu-id="82eef-221">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-221">No</span></span>|<span data-ttu-id="82eef-222">Název \<</span><span class="sxs-lookup"><span data-stu-id="82eef-222">\<Name></span></span>|<span data-ttu-id="82eef-223">Název funkce v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="82eef-223">Function Name in the data store.</span></span>  <span data-ttu-id="82eef-224">Umožňuje úroveň přesměrování názvů funkcí.</span><span class="sxs-lookup"><span data-stu-id="82eef-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="82eef-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="82eef-225">NiladicFunction</span></span>|<span data-ttu-id="82eef-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="82eef-226">Boolean</span></span>|<span data-ttu-id="82eef-227">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-227">No</span></span>|<span data-ttu-id="82eef-228">False</span><span class="sxs-lookup"><span data-stu-id="82eef-228">False</span></span>|<span data-ttu-id="82eef-229">True, pokud funkce nevyžaduje parametry a je volána bez parametrů</span><span class="sxs-lookup"><span data-stu-id="82eef-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="82eef-230">Zadanému ParameterType</span><span class="sxs-lookup"><span data-stu-id="82eef-230">ParameterType</span></span><br /><br /> <span data-ttu-id="82eef-231">Sémantiku</span><span class="sxs-lookup"><span data-stu-id="82eef-231">Semantics</span></span>|<span data-ttu-id="82eef-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="82eef-232">ParameterSemantics</span></span>|<span data-ttu-id="82eef-233">Ne</span><span class="sxs-lookup"><span data-stu-id="82eef-233">No</span></span>|<span data-ttu-id="82eef-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="82eef-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="82eef-235">Konverze</span><span class="sxs-lookup"><span data-stu-id="82eef-235">Conversion</span></span>|<span data-ttu-id="82eef-236">Volba způsobu, jakým by měl kanál dotazu pracovat s nahrazením typu parametru:</span><span class="sxs-lookup"><span data-stu-id="82eef-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="82eef-237">– ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="82eef-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="82eef-238">– AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="82eef-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="82eef-239">– AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="82eef-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="82eef-240">**Uzel parametrů**</span><span class="sxs-lookup"><span data-stu-id="82eef-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="82eef-241">Každá funkce má kolekci jednoho nebo více uzlů parametrů.</span><span class="sxs-lookup"><span data-stu-id="82eef-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="82eef-242">Název atributu</span><span class="sxs-lookup"><span data-stu-id="82eef-242">Attribute Name</span></span>|<span data-ttu-id="82eef-243">Datový typ</span><span class="sxs-lookup"><span data-stu-id="82eef-243">Data Type</span></span>|<span data-ttu-id="82eef-244">Požadováno</span><span class="sxs-lookup"><span data-stu-id="82eef-244">Required</span></span>|<span data-ttu-id="82eef-245">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="82eef-245">Default Value</span></span>|<span data-ttu-id="82eef-246">Popis</span><span class="sxs-lookup"><span data-stu-id="82eef-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="82eef-247">Name</span><span class="sxs-lookup"><span data-stu-id="82eef-247">Name</span></span>|<span data-ttu-id="82eef-248">String</span><span class="sxs-lookup"><span data-stu-id="82eef-248">String</span></span>|<span data-ttu-id="82eef-249">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-249">Yes</span></span>|<span data-ttu-id="82eef-250">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-250">n/a</span></span>|<span data-ttu-id="82eef-251">Identifikátor/název parametru.</span><span class="sxs-lookup"><span data-stu-id="82eef-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="82eef-252">Typ</span><span class="sxs-lookup"><span data-stu-id="82eef-252">Type</span></span>|<span data-ttu-id="82eef-253">String</span><span class="sxs-lookup"><span data-stu-id="82eef-253">String</span></span>|<span data-ttu-id="82eef-254">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-254">Yes</span></span>|<span data-ttu-id="82eef-255">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-255">n/a</span></span>|<span data-ttu-id="82eef-256">Typ typu EDM parametru.</span><span class="sxs-lookup"><span data-stu-id="82eef-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="82eef-257">Režim</span><span class="sxs-lookup"><span data-stu-id="82eef-257">Mode</span></span>|<span data-ttu-id="82eef-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="82eef-258">Parameter</span></span><br /><br /> <span data-ttu-id="82eef-259">Směr</span><span class="sxs-lookup"><span data-stu-id="82eef-259">Direction</span></span>|<span data-ttu-id="82eef-260">Ano</span><span class="sxs-lookup"><span data-stu-id="82eef-260">Yes</span></span>|<span data-ttu-id="82eef-261">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="82eef-261">n/a</span></span>|<span data-ttu-id="82eef-262">Směr parametru:</span><span class="sxs-lookup"><span data-stu-id="82eef-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="82eef-263">-in</span><span class="sxs-lookup"><span data-stu-id="82eef-263">-   in</span></span><br /><span data-ttu-id="82eef-264">-out</span><span class="sxs-lookup"><span data-stu-id="82eef-264">-   out</span></span><br /><span data-ttu-id="82eef-265">– InOut</span><span class="sxs-lookup"><span data-stu-id="82eef-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="82eef-266">Atribut namespace</span><span class="sxs-lookup"><span data-stu-id="82eef-266">Namespace Attribute</span></span>  
 <span data-ttu-id="82eef-267">Každý poskytovatel úložiště dat musí definovat obor názvů nebo skupinu oborů názvů pro informace definované v manifestu.</span><span class="sxs-lookup"><span data-stu-id="82eef-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="82eef-268">Tento obor názvů se dá použít v Entity SQLch dotazech k překladu názvů funkcí a typů.</span><span class="sxs-lookup"><span data-stu-id="82eef-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="82eef-269">Příklad: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="82eef-269">For instance: SqlServer.</span></span> <span data-ttu-id="82eef-270">Tento obor názvů musí být jiný než kanonický obor názvů (EDM) definovaný službou entity Services, aby se standardní funkce podporovaly pomocí Entity SQL dotazů.</span><span class="sxs-lookup"><span data-stu-id="82eef-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82eef-271">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82eef-271">See also</span></span>

- [<span data-ttu-id="82eef-272">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="82eef-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
