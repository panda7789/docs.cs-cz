---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 02faee9ad69bd75f4df608b9a4767560945c7bb3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767138"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="41709-102">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-102">Provider Manifest Specification</span></span>
<span data-ttu-id="41709-103">Tato část popisuje, jak můžete zprostředkovatele úložiště dat podporují typy a funkce v úložišti.</span><span class="sxs-lookup"><span data-stu-id="41709-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="41709-104">Entity služby funguje nezávisle na konkrétní data zprostředkovatele úložiště ještě stále umožňuje zprostředkovatele dat explicitně definujte, jak komunikovat s základní úložiště dat. modely, mapování a dotazů.</span><span class="sxs-lookup"><span data-stu-id="41709-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="41709-105">Bez úroveň abstrakce Entity služby může být cílena na konkrétní data store nebo zprostředkovatele dat.</span><span class="sxs-lookup"><span data-stu-id="41709-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="41709-106">Typy, které zprostředkovatel podporuje přímo nebo nepřímo podporuje základní databáze.</span><span class="sxs-lookup"><span data-stu-id="41709-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="41709-107">Tyto typy, nemusí nutně být typy přesný úložiště, ale typy používá zprostředkovatel pro podporu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41709-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="41709-108">Typy poskytovatele/úložiště jsou popsané v podmínkách Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="41709-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="41709-109">Parametr a návratové typy pro funkce nepodporuje úložiště dat jsou určené v podmínky EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41709-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41709-110">Requirements</span></span>  
 <span data-ttu-id="41709-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a úložiště dat musejí mít k předávání dat a zpět v známé typy bez ztráty dat nebo zkrácení.</span><span class="sxs-lookup"><span data-stu-id="41709-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="41709-112">Manifest zprostředkovatele musí být možné načíst pomocí nástrojů v době návrhu bez nutnosti otevřít připojení k úložišti.</span><span class="sxs-lookup"><span data-stu-id="41709-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="41709-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je případ citlivé, ale nemusí být příslušné datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="41709-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="41709-114">Když artefakty EDM (identifikátory a názvy typů, např.) jsou definováni a použít v manifestu, musíte použít [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] písmen.</span><span class="sxs-lookup"><span data-stu-id="41709-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="41709-115">Pokud datové úložiště prvky, které může být malá a velká písmena se zobrazí v manifestu zprostředkovatele, je třeba zachovat v manifestu zprostředkovatele, že velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="41709-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="41709-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje manifest zprostředkovatele pro všechny poskytovatele data.</span><span class="sxs-lookup"><span data-stu-id="41709-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="41709-117">Pokud se pokusíte použít poskytovatele, který nemá zprostředkovatele manifestu s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobrazí se chyba.</span><span class="sxs-lookup"><span data-stu-id="41709-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="41709-118">Následující tabulka popisuje druhy výjimek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] by výjimku při výjimky jsou vyvolány prostřednictvím interakci poskytovatele:</span><span class="sxs-lookup"><span data-stu-id="41709-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="41709-119">Problém</span><span class="sxs-lookup"><span data-stu-id="41709-119">Issue</span></span>|<span data-ttu-id="41709-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="41709-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="41709-121">Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="41709-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="41709-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="41709-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="41709-123">Chybí manifest zprostředkovatele: Zprostředkovatel vrátí `null` při pokusu o načtení manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="41709-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="41709-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="41709-125">Manifest zprostředkovatele neplatný: Zprostředkovatel vrátí neplatný kód XML při pokusu o načtení manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="41709-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="41709-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="41709-127">Scénáře</span><span class="sxs-lookup"><span data-stu-id="41709-127">Scenarios</span></span>  
 <span data-ttu-id="41709-128">Zprostředkovatel musí podporují následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="41709-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="41709-129">Zápis zprostředkovatele s mapováním symetrický typu</span><span class="sxs-lookup"><span data-stu-id="41709-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="41709-130">Můžete napsat poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kde každý typ úložiště mapuje jeden typ EDM, bez ohledu na to, že mapování směr.</span><span class="sxs-lookup"><span data-stu-id="41709-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="41709-131">Pro typ zprostředkovatele, který má velmi jednoduché mapování, která odpovídá typu EDM můžete použít symetrický řešení, protože je jednoduchý systém typů nebo odpovídá typů EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="41709-132">Můžete použít jednoduchost svoji doménu a vytvoření manifestu statické deklarativní zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="41709-133">Můžete zapsat soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="41709-133">You write an XML file that has two sections:</span></span>  
  
-   <span data-ttu-id="41709-134">Seznam typů zprostředkovatele vyjádřené jako "protějšku EDM" typ úložiště nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="41709-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="41709-135">Typy úložiště mají protějšku typy EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="41709-136">Funkce úložiště mají odpovídající funkce EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="41709-137">Například varchar je typ systému SQL Server, ale odpovídající typ EDM je řetězec.</span><span class="sxs-lookup"><span data-stu-id="41709-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
-   <span data-ttu-id="41709-138">Seznam funkcí podporovaných poskytovatelem, kde parametr a návratové typy jsou uvedeny v podmínkách EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="41709-139">Zápis zprostředkovatele s mapováním asymetrické typu</span><span class="sxs-lookup"><span data-stu-id="41709-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="41709-140">Při zápisu zprostředkovatele úložiště dat pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], typ EDM zprostředkovatele mapování pro některé typy se může lišit od mapování typu zprostředkovatele EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="41709-141">Například může bez vazby PrimitiveTypeKind.String EDM mapovat do nvarchar(4000) na zprostředkovateli při nvarchar(4000) mapuje EDM PrimitiveTypeKind.String(MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="41709-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="41709-142">Můžete zapsat soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="41709-142">You write an XML file that has two sections:</span></span>  
  
-   <span data-ttu-id="41709-143">Seznam typů zprostředkovatele vyjádřený v podmínkách EDM a definovat mapování pro obě směr: EDM zprostředkovatele a zprostředkovatele EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
-   <span data-ttu-id="41709-144">Seznam funkcí podporovaných poskytovatelem, kde parametr a návratové typy jsou uvedeny v podmínkách EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="41709-145">Vyhledání manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="41709-146">Manifest nepřímo používá několik typů součásti v Entity služby (například nástroje nebo dotazu), ale informace přímo využít metadat prostřednictvím data ukládat zavaděč metadat.</span><span class="sxs-lookup"><span data-stu-id="41709-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="41709-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="41709-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="41709-148">Různých obchodů nebo různé verze stejného úložiště může však podporovat daného zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="41709-149">Proto musí zprostředkovatele nahlásit různých manifestu pro každé podporované datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="41709-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="41709-150">Token manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="41709-151">Po otevření připojení úložišti dat zprostředkovatele můžete dotazovat informace, které vrátí správné manifestu.</span><span class="sxs-lookup"><span data-stu-id="41709-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="41709-152">Toto nemusí být možné v offline scénářích, kde informace o připojení není k dispozici nebo pokud není možné se připojit k úložišti.</span><span class="sxs-lookup"><span data-stu-id="41709-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="41709-153">Identifikovat manifest pomocí `ProviderManifestToken` atribut `Schema` element v souboru ssdl.</span><span class="sxs-lookup"><span data-stu-id="41709-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="41709-154">Požadovaný formát není pro tento atribut; Zprostředkovatel zvolí minimální informace potřebné k identifikaci manifestu bez otevření připojení k úložišti.</span><span class="sxs-lookup"><span data-stu-id="41709-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="41709-155">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41709-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="41709-156">Model programování manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="41709-157">Poskytovatelé jsou odvozeny od <xref:System.Data.Common.DbXmlEnabledProviderManifest>, což umožňuje jejich zadejte jejich manifesty deklarativně.</span><span class="sxs-lookup"><span data-stu-id="41709-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="41709-158">Následující obrázek znázorňuje hierarchie tříd zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="41709-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="41709-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="41709-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="41709-160">Možnosti rozpoznání rozhraní API</span><span class="sxs-lookup"><span data-stu-id="41709-160">Discoverability API</span></span>  
 <span data-ttu-id="41709-161">Manifest zprostředkovatele je načíst zavaděčem ukládání metadat (StoreItemCollection), buď pomocí dat uložení připojení nebo tokenu manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="41709-162">Pomocí připojení k úložišti dat</span><span class="sxs-lookup"><span data-stu-id="41709-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="41709-163">Při ukládání dat není k dispozici připojení, volejte DbProvderServices.GetProviderManifestToken vrátit token, který je předaný metodě GetProviderManifest, která vrátí hodnotu třída DbProviderManifest.</span><span class="sxs-lookup"><span data-stu-id="41709-163">When the data store connection is available, call DbProvderServices.GetProviderManifestToken to return the token that is passed to the GetProviderManifest method, which returns DbProviderManifest.</span></span> <span data-ttu-id="41709-164">Tato metoda provede delegaci pro poskytovatele implementace GetDbProviderManifestToken.</span><span class="sxs-lookup"><span data-stu-id="41709-164">This method delegates to the provider's implementation of GetDbProviderManifestToken.</span></span>  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="41709-165">Pomocí tokenu manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="41709-166">Offline scénář token vydán z reprezentace SSDL.</span><span class="sxs-lookup"><span data-stu-id="41709-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="41709-167">SSDL umožňuje určit ProviderManifestToken (najdete v části [Element schématu (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) informace).</span><span class="sxs-lookup"><span data-stu-id="41709-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) for more information).</span></span> <span data-ttu-id="41709-168">Například pokud připojení nelze otevřít, SSDL má token manifestu zprostředkovatele, která určuje informace o manifest.</span><span class="sxs-lookup"><span data-stu-id="41709-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="41709-169">Schéma manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="41709-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="41709-170">Schéma definované pro každého zprostředkovatele informace obsahuje statický informace, které mají být využívány službou metadat:</span><span class="sxs-lookup"><span data-stu-id="41709-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="41709-171">Uzel typy</span><span class="sxs-lookup"><span data-stu-id="41709-171">Types Node</span></span>  
 <span data-ttu-id="41709-172">Uzel typy v manifestu zprostředkovatele, obsahuje informace o typech, které jsou nativně podporovány úložiště dat nebo prostřednictvím poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="41709-173">Typ uzlu</span><span class="sxs-lookup"><span data-stu-id="41709-173">Type Node</span></span>  
 <span data-ttu-id="41709-174">Každý typ uzlu definuje typ zprostředkovatele z hlediska EDM.</span><span class="sxs-lookup"><span data-stu-id="41709-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="41709-175">Typ uzlu popisuje název typu zprostředkovatele, a informace týkající se typ modelu, který se mapuje na a omezující vlastnosti popisují mapování tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="41709-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="41709-176">Chcete-li express tento typ informací v manifestu zprostředkovatele, musí každá deklarace TypeInformation definovat několik popis omezující vlastnosti pro každý typ:</span><span class="sxs-lookup"><span data-stu-id="41709-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="41709-177">Název atributu</span><span class="sxs-lookup"><span data-stu-id="41709-177">Attribute Name</span></span>|<span data-ttu-id="41709-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="41709-178">Data Type</span></span>|<span data-ttu-id="41709-179">Požadováno</span><span class="sxs-lookup"><span data-stu-id="41709-179">Required</span></span>|<span data-ttu-id="41709-180">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="41709-180">Default Value</span></span>|<span data-ttu-id="41709-181">Popis</span><span class="sxs-lookup"><span data-stu-id="41709-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="41709-182">Název</span><span class="sxs-lookup"><span data-stu-id="41709-182">Name</span></span>|<span data-ttu-id="41709-183">String</span><span class="sxs-lookup"><span data-stu-id="41709-183">String</span></span>|<span data-ttu-id="41709-184">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-184">Yes</span></span>|<span data-ttu-id="41709-185">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-185">n/a</span></span>|<span data-ttu-id="41709-186">Název typu specifický pro zprostředkovatele dat</span><span class="sxs-lookup"><span data-stu-id="41709-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="41709-187">Hodnota typu PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="41709-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="41709-188">Hodnota typu PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="41709-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="41709-189">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-189">Yes</span></span>|<span data-ttu-id="41709-190">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-190">n/a</span></span>|<span data-ttu-id="41709-191">Název typu EDM</span><span class="sxs-lookup"><span data-stu-id="41709-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="41709-192">Uzel – funkce</span><span class="sxs-lookup"><span data-stu-id="41709-192">Function Node</span></span>  
 <span data-ttu-id="41709-193">Jednotlivé funkce definuje jedinou funkci k dispozici prostřednictvím poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="41709-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="41709-194">Název atributu</span><span class="sxs-lookup"><span data-stu-id="41709-194">Attribute Name</span></span>|<span data-ttu-id="41709-195">Datový typ</span><span class="sxs-lookup"><span data-stu-id="41709-195">Data Type</span></span>|<span data-ttu-id="41709-196">Požadováno</span><span class="sxs-lookup"><span data-stu-id="41709-196">Required</span></span>|<span data-ttu-id="41709-197">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="41709-197">Default Value</span></span>|<span data-ttu-id="41709-198">Popis</span><span class="sxs-lookup"><span data-stu-id="41709-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="41709-199">Název</span><span class="sxs-lookup"><span data-stu-id="41709-199">Name</span></span>|<span data-ttu-id="41709-200">String</span><span class="sxs-lookup"><span data-stu-id="41709-200">String</span></span>|<span data-ttu-id="41709-201">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-201">Yes</span></span>|<span data-ttu-id="41709-202">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-202">n/a</span></span>|<span data-ttu-id="41709-203">Identifikátor nebo název funkce</span><span class="sxs-lookup"><span data-stu-id="41709-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="41709-204">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="41709-204">ReturnType</span></span>|<span data-ttu-id="41709-205">String</span><span class="sxs-lookup"><span data-stu-id="41709-205">String</span></span>|<span data-ttu-id="41709-206">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-206">No</span></span>|<span data-ttu-id="41709-207">Void</span><span class="sxs-lookup"><span data-stu-id="41709-207">Void</span></span>|<span data-ttu-id="41709-208">Návratový typ EDM funkce</span><span class="sxs-lookup"><span data-stu-id="41709-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="41709-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="41709-209">Aggregate</span></span>|<span data-ttu-id="41709-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="41709-210">Boolean</span></span>|<span data-ttu-id="41709-211">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-211">No</span></span>|<span data-ttu-id="41709-212">False</span><span class="sxs-lookup"><span data-stu-id="41709-212">False</span></span>|<span data-ttu-id="41709-213">Hodnota TRUE, pokud je funkce agregační funkce</span><span class="sxs-lookup"><span data-stu-id="41709-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="41709-214">Předdefinované</span><span class="sxs-lookup"><span data-stu-id="41709-214">BuiltIn</span></span>|<span data-ttu-id="41709-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="41709-215">Boolean</span></span>|<span data-ttu-id="41709-216">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-216">No</span></span>|<span data-ttu-id="41709-217">Hodnota TRUE</span><span class="sxs-lookup"><span data-stu-id="41709-217">True</span></span>|<span data-ttu-id="41709-218">Hodnota TRUE, pokud je funkce integrovaná v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="41709-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="41709-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="41709-219">StoreFunctionName</span></span>|<span data-ttu-id="41709-220">String</span><span class="sxs-lookup"><span data-stu-id="41709-220">String</span></span>|<span data-ttu-id="41709-221">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-221">No</span></span>|<span data-ttu-id="41709-222">\<Name ></span><span class="sxs-lookup"><span data-stu-id="41709-222">\<Name></span></span>|<span data-ttu-id="41709-223">Název funkce v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="41709-223">Function Name in the data store.</span></span>  <span data-ttu-id="41709-224">Umožňuje pro úroveň přesměrování názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="41709-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="41709-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="41709-225">NiladicFunction</span></span>|<span data-ttu-id="41709-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="41709-226">Boolean</span></span>|<span data-ttu-id="41709-227">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-227">No</span></span>|<span data-ttu-id="41709-228">False</span><span class="sxs-lookup"><span data-stu-id="41709-228">False</span></span>|<span data-ttu-id="41709-229">Hodnota TRUE, pokud funkce nevyžaduje, parametry a je volána bez parametrů</span><span class="sxs-lookup"><span data-stu-id="41709-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="41709-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="41709-230">ParameterType</span></span><br /><br /> <span data-ttu-id="41709-231">Sémantika</span><span class="sxs-lookup"><span data-stu-id="41709-231">Semantics</span></span>|<span data-ttu-id="41709-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="41709-232">ParameterSemantics</span></span>|<span data-ttu-id="41709-233">Ne</span><span class="sxs-lookup"><span data-stu-id="41709-233">No</span></span>|<span data-ttu-id="41709-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="41709-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="41709-235">Převod</span><span class="sxs-lookup"><span data-stu-id="41709-235">Conversion</span></span>|<span data-ttu-id="41709-236">Volba jak by se měl kanálu dotazu zabývat nahrazování parametru typu:</span><span class="sxs-lookup"><span data-stu-id="41709-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="41709-237">-ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="41709-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="41709-238">-AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="41709-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="41709-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="41709-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="41709-240">**Parametry uzlu**</span><span class="sxs-lookup"><span data-stu-id="41709-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="41709-241">Jednotlivé funkce má kolekce jednoho či více uzlů parametr.</span><span class="sxs-lookup"><span data-stu-id="41709-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="41709-242">Název atributu</span><span class="sxs-lookup"><span data-stu-id="41709-242">Attribute Name</span></span>|<span data-ttu-id="41709-243">Datový typ</span><span class="sxs-lookup"><span data-stu-id="41709-243">Data Type</span></span>|<span data-ttu-id="41709-244">Požadováno</span><span class="sxs-lookup"><span data-stu-id="41709-244">Required</span></span>|<span data-ttu-id="41709-245">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="41709-245">Default Value</span></span>|<span data-ttu-id="41709-246">Popis</span><span class="sxs-lookup"><span data-stu-id="41709-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="41709-247">Název</span><span class="sxs-lookup"><span data-stu-id="41709-247">Name</span></span>|<span data-ttu-id="41709-248">String</span><span class="sxs-lookup"><span data-stu-id="41709-248">String</span></span>|<span data-ttu-id="41709-249">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-249">Yes</span></span>|<span data-ttu-id="41709-250">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-250">n/a</span></span>|<span data-ttu-id="41709-251">Identifikátor nebo název parametru.</span><span class="sxs-lookup"><span data-stu-id="41709-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="41709-252">Typ</span><span class="sxs-lookup"><span data-stu-id="41709-252">Type</span></span>|<span data-ttu-id="41709-253">String</span><span class="sxs-lookup"><span data-stu-id="41709-253">String</span></span>|<span data-ttu-id="41709-254">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-254">Yes</span></span>|<span data-ttu-id="41709-255">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-255">n/a</span></span>|<span data-ttu-id="41709-256">Typ EDM parametru.</span><span class="sxs-lookup"><span data-stu-id="41709-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="41709-257">Režim</span><span class="sxs-lookup"><span data-stu-id="41709-257">Mode</span></span>|<span data-ttu-id="41709-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="41709-258">Parameter</span></span><br /><br /> <span data-ttu-id="41709-259">Směr</span><span class="sxs-lookup"><span data-stu-id="41709-259">Direction</span></span>|<span data-ttu-id="41709-260">Ano</span><span class="sxs-lookup"><span data-stu-id="41709-260">Yes</span></span>|<span data-ttu-id="41709-261">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="41709-261">n/a</span></span>|<span data-ttu-id="41709-262">Směr parametru:</span><span class="sxs-lookup"><span data-stu-id="41709-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="41709-263">-v</span><span class="sxs-lookup"><span data-stu-id="41709-263">-   in</span></span><br /><span data-ttu-id="41709-264">-out</span><span class="sxs-lookup"><span data-stu-id="41709-264">-   out</span></span><br /><span data-ttu-id="41709-265">-inout</span><span class="sxs-lookup"><span data-stu-id="41709-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="41709-266">Atribut Namespace</span><span class="sxs-lookup"><span data-stu-id="41709-266">Namespace Attribute</span></span>  
 <span data-ttu-id="41709-267">Každý poskytovatel úložiště dat musí definovat v oboru názvů nebo skupině obory názvů pro informace definované v manifestu.</span><span class="sxs-lookup"><span data-stu-id="41709-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="41709-268">Tento obor názvů lze v dotazech Entity SQL přeložit názvy funkcí a typy.</span><span class="sxs-lookup"><span data-stu-id="41709-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="41709-269">Například: SQL Server.</span><span class="sxs-lookup"><span data-stu-id="41709-269">For instance: SqlServer.</span></span> <span data-ttu-id="41709-270">Tento obor názvů musí být odlišný od kanonický oboru názvů, EDM, definované Entity služby pro standardní funkce podporovaná dotazy Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="41709-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41709-271">Viz také</span><span class="sxs-lookup"><span data-stu-id="41709-271">See Also</span></span>  
 [<span data-ttu-id="41709-272">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="41709-272">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
