---
title: Specifikace manifestu zprostředkovatele
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 0f3eaa73a26c3f8519e1c168ab2e2968ed4ab28d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641167"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="c1d38-102">Specifikace manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-102">Provider Manifest Specification</span></span>
<span data-ttu-id="c1d38-103">Tato část popisuje, jak můžete zprostředkovatele úložiště dat podporují typy a funkce v úložišti.</span><span class="sxs-lookup"><span data-stu-id="c1d38-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="c1d38-104">Entita služby funguje nezávisle na poskytovatele úložiště konkrétní data, ale stále umožňuje poskytovatel dat explicitně definovat dotazy, modely a mapování interakci s základnímu úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="c1d38-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="c1d38-105">Bez abstraktní vrstvu může entita služby pouze cílená na konkrétní datové úložiště nebo poskytovatele dat služeb.</span><span class="sxs-lookup"><span data-stu-id="c1d38-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="c1d38-106">Typy, které podporuje zprostředkovatel přímo nebo nepřímo podporuje podkladové databáze.</span><span class="sxs-lookup"><span data-stu-id="c1d38-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="c1d38-107">Tyto typy nejsou nutně typy přesné úložiště, ale poskytovatel se použije pro podporu typů [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c1d38-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="c1d38-108">Typy zprostředkovatele nebo úložiště jsou popsány v podmínkách Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="c1d38-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="c1d38-109">Parametry a návratovým typem pro funkce podporované v úložišti dat jsou určené v EDM podmínky.</span><span class="sxs-lookup"><span data-stu-id="c1d38-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1d38-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1d38-110">Requirements</span></span>  
 <span data-ttu-id="c1d38-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a úložišti dat musí mít možnost předat data vpřed a zpět v známých typů bez ztráty dat nebo zkrácení.</span><span class="sxs-lookup"><span data-stu-id="c1d38-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="c1d38-112">Manifest zprostředkovatele musí být možné načíst pomocí nástrojů v době návrhu bez nutnosti otevřít připojení k úložišti.</span><span class="sxs-lookup"><span data-stu-id="c1d38-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="c1d38-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Je případ citlivé, ale nemusí být základnímu úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="c1d38-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="c1d38-114">Když artefakty EDM (názvy typu, například a identifikátory) jsou definovány a použít v manifestu, musíte použít [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] písmen.</span><span class="sxs-lookup"><span data-stu-id="c1d38-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="c1d38-115">Pokud prvky úložiště dat, které mohou být velká a malá písmena v manifestu zprostředkovatele, musí být zachovány v manifestu zprostředkovatele, tento velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="c1d38-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="c1d38-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Vyžaduje manifest zprostředkovatele pro všechna data zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="c1d38-117">Pokud se pokusíte použít poskytovatele, který nemá zprostředkovatele manifestu se [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], obdržíte chybu.</span><span class="sxs-lookup"><span data-stu-id="c1d38-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="c1d38-118">Následující tabulka popisuje druhy výjimek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] by výjimku při vzniknou výjimek prostřednictvím poskytovatele interakce:</span><span class="sxs-lookup"><span data-stu-id="c1d38-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="c1d38-119">Problém</span><span class="sxs-lookup"><span data-stu-id="c1d38-119">Issue</span></span>|<span data-ttu-id="c1d38-120">Výjimka</span><span class="sxs-lookup"><span data-stu-id="c1d38-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="c1d38-121">Zprostředkovatel nepodporuje GetProviderManifest v DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="c1d38-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="c1d38-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="c1d38-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="c1d38-123">Chybějící manifest zprostředkovatele: zprostředkovatele vrátí `null` při pokusu o načtení manifest zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="c1d38-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="c1d38-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="c1d38-125">Neplatný poskytovatel manifest: zprostředkovatel vrací neplatný kód XML při pokusu o načtení manifest zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="c1d38-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="c1d38-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="c1d38-127">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c1d38-127">Scenarios</span></span>  
 <span data-ttu-id="c1d38-128">Poskytovatel by měl podporují následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="c1d38-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="c1d38-129">Zápis zprostředkovatele s mapováním symetrický typu</span><span class="sxs-lookup"><span data-stu-id="c1d38-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="c1d38-130">Můžete napsat zprostředkovatele [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kde každý typ úložiště mapuje na jeden typ EDM, bez ohledu na směru mapování.</span><span class="sxs-lookup"><span data-stu-id="c1d38-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="c1d38-131">Pro typ zprostředkovatele, který má velmi jednoduché mapování, která odpovídá typu EDM můžete použít symetrický řešení, protože systém typů je jednoduchá nebo odpovídá typů modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="c1d38-132">Můžete použít jednoduchost své domény a vytvoří manifest statické deklarativní poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="c1d38-133">Můžete napsat soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="c1d38-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="c1d38-134">Seznam typů poskytovatelů vyjadřují "protějšek EDM" typ úložiště nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="c1d38-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="c1d38-135">Typy Store mají protějšek typů modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="c1d38-136">Funkce Store mají odpovídající funkce EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="c1d38-137">Například varchar je typ serveru SQL Server, ale odpovídající typ EDM je řetězec.</span><span class="sxs-lookup"><span data-stu-id="c1d38-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="c1d38-138">Seznam funkcí podporovaných poskytovateli, ve kterém jsou parametry a návratovým typem vyjádřen v pojmech EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="c1d38-139">Zápis zprostředkovatele s mapováním asymetrického typu</span><span class="sxs-lookup"><span data-stu-id="c1d38-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="c1d38-140">Při psaní pro zprostředkovatele úložiště dat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], mapování pro některé typy mohou být odlišný od typu zprostředkovatele EDM mapování typů EDM zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="c1d38-141">Například bez vazby modelu EDM PrimitiveTypeKind.String mohou být mapovány nvarchar(4000) na poskytovateli, zatímco nvarchar(4000) mapuje na EDM PrimitiveTypeKind.String(MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="c1d38-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="c1d38-142">Můžete napsat soubor XML, který má dvě části:</span><span class="sxs-lookup"><span data-stu-id="c1d38-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="c1d38-143">Seznam typů poskytovatelů vyjádřen v pojmech EDM a definovat mapování pro oba směry: EDM poskytovatele a poskytovatele EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="c1d38-144">Seznam funkcí podporovaných poskytovateli, ve kterém jsou parametry a návratovým typem vyjádřen v pojmech EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="c1d38-145">Zjistitelnost manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="c1d38-146">Manifest je nepřímo používá několik typů součástí služby Entity (například nástroje nebo dotaz), ale informace přímo využíváno metadat prostřednictvím data ukládat metadata zavaděče.</span><span class="sxs-lookup"><span data-stu-id="c1d38-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="c1d38-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="c1d38-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="c1d38-148">Daný poskytovatel může však podporovat různých obchodech nebo různými verzemi stejného úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1d38-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="c1d38-149">Proto zprostředkovatele se musí hlásit různé manifestu pro každé podporované datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1d38-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="c1d38-150">Token manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="c1d38-151">Po otevření připojení úložiště dat zprostředkovatele můžete dotazovat na informace se vraťte správný manifest.</span><span class="sxs-lookup"><span data-stu-id="c1d38-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="c1d38-152">To nemusí být možné v případě offline scénářů, kde není k dispozici informace o připojení nebo když není možné se připojit k úložišti.</span><span class="sxs-lookup"><span data-stu-id="c1d38-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="c1d38-153">Identifikovat manifestu pomocí `ProviderManifestToken` atribut `Schema` element v souboru ssdl.</span><span class="sxs-lookup"><span data-stu-id="c1d38-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="c1d38-154">Neexistuje žádné požadovaný formát pro tento atribut; Zprostředkovatel zvolí minimální informace potřebné k identifikaci manifest bez nutnosti otevřít připojení k úložišti.</span><span class="sxs-lookup"><span data-stu-id="c1d38-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="c1d38-155">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c1d38-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="c1d38-156">Programovací Model manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="c1d38-157">Poskytovatelé jsou odvozeny z <xref:System.Data.Common.DbXmlEnabledProviderManifest>, který umožňuje zadat svých manifestech deklarativně.</span><span class="sxs-lookup"><span data-stu-id="c1d38-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="c1d38-158">Následující obrázek znázorňuje hierarchii tříd zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="c1d38-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="c1d38-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="c1d38-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="c1d38-160">Zjistitelnost rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c1d38-160">Discoverability API</span></span>  
 <span data-ttu-id="c1d38-161">Manifest zprostředkovatele je načten zavaděč Store Metadata (StoreItemCollection), s použitím dat uložit připojení nebo token manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="c1d38-162">Data Store připojení</span><span class="sxs-lookup"><span data-stu-id="c1d38-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="c1d38-163">Při ukládání dat je k dispozici připojení, volejte DbProvderServices.GetProviderManifestToken vrátí token, který se předá metodě GetProviderManifest, které vrací DbProviderManifest.</span><span class="sxs-lookup"><span data-stu-id="c1d38-163">When the data store connection is available, call DbProvderServices.GetProviderManifestToken to return the token that is passed to the GetProviderManifest method, which returns DbProviderManifest.</span></span> <span data-ttu-id="c1d38-164">Tato metoda deleguje se do poskytovatele provádění GetDbProviderManifestToken.</span><span class="sxs-lookup"><span data-stu-id="c1d38-164">This method delegates to the provider's implementation of GetDbProviderManifestToken.</span></span>  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="c1d38-165">Pomocí tokenu manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="c1d38-166">Token scénáři offline, je odebrána ze souborů SSDL reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c1d38-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="c1d38-167">SSDL můžete zadat ProviderManifestToken (viz [Element schématu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) Další informace).</span><span class="sxs-lookup"><span data-stu-id="c1d38-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="c1d38-168">Například pokud připojení nelze otevřít, SSDL má token manifestu zprostředkovatele, který určuje informace o manifestu.</span><span class="sxs-lookup"><span data-stu-id="c1d38-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="c1d38-169">Schéma manifestu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c1d38-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="c1d38-170">Schéma informace definované pro každý poskytovatel obsahuje statické informace, které mají být využívány službou metadat:</span><span class="sxs-lookup"><span data-stu-id="c1d38-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="c1d38-171">Typy uzlů</span><span class="sxs-lookup"><span data-stu-id="c1d38-171">Types Node</span></span>  
 <span data-ttu-id="c1d38-172">Typy uzlů v manifestu zprostředkovatele, obsahuje informace o typech, které jsou nativně podporovány v úložišti dat nebo prostřednictvím poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="c1d38-173">Typ uzlu</span><span class="sxs-lookup"><span data-stu-id="c1d38-173">Type Node</span></span>  
 <span data-ttu-id="c1d38-174">Každý typ uzlu definuje typ zprostředkovatele z hlediska modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="c1d38-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="c1d38-175">Uzel typu popisuje název poskytovatele typu a informace týkající se typ modelu, který je namapován na a omezující vlastnosti k popisu mapování typu.</span><span class="sxs-lookup"><span data-stu-id="c1d38-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="c1d38-176">Aby bylo možné tento typ informací v manifestu zprostředkovatele, express, každý TypeInformation prohlášení musí definovat několik popisů omezující vlastnost pro každý typ:</span><span class="sxs-lookup"><span data-stu-id="c1d38-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="c1d38-177">Název atributu</span><span class="sxs-lookup"><span data-stu-id="c1d38-177">Attribute Name</span></span>|<span data-ttu-id="c1d38-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c1d38-178">Data Type</span></span>|<span data-ttu-id="c1d38-179">Požadováno</span><span class="sxs-lookup"><span data-stu-id="c1d38-179">Required</span></span>|<span data-ttu-id="c1d38-180">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1d38-180">Default Value</span></span>|<span data-ttu-id="c1d38-181">Popis</span><span class="sxs-lookup"><span data-stu-id="c1d38-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="c1d38-182">Name</span><span class="sxs-lookup"><span data-stu-id="c1d38-182">Name</span></span>|<span data-ttu-id="c1d38-183">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-183">String</span></span>|<span data-ttu-id="c1d38-184">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-184">Yes</span></span>|<span data-ttu-id="c1d38-185">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-185">n/a</span></span>|<span data-ttu-id="c1d38-186">Název typu specifickým pro zprostředkovatele dat</span><span class="sxs-lookup"><span data-stu-id="c1d38-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="c1d38-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="c1d38-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="c1d38-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="c1d38-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="c1d38-189">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-189">Yes</span></span>|<span data-ttu-id="c1d38-190">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-190">n/a</span></span>|<span data-ttu-id="c1d38-191">Název typu EDM</span><span class="sxs-lookup"><span data-stu-id="c1d38-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="c1d38-192">Uzel – funkce</span><span class="sxs-lookup"><span data-stu-id="c1d38-192">Function Node</span></span>  
 <span data-ttu-id="c1d38-193">Každá funkce definuje jedinou funkci k dispozici prostřednictvím poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c1d38-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="c1d38-194">Název atributu</span><span class="sxs-lookup"><span data-stu-id="c1d38-194">Attribute Name</span></span>|<span data-ttu-id="c1d38-195">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c1d38-195">Data Type</span></span>|<span data-ttu-id="c1d38-196">Požadováno</span><span class="sxs-lookup"><span data-stu-id="c1d38-196">Required</span></span>|<span data-ttu-id="c1d38-197">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1d38-197">Default Value</span></span>|<span data-ttu-id="c1d38-198">Popis</span><span class="sxs-lookup"><span data-stu-id="c1d38-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="c1d38-199">Name</span><span class="sxs-lookup"><span data-stu-id="c1d38-199">Name</span></span>|<span data-ttu-id="c1d38-200">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-200">String</span></span>|<span data-ttu-id="c1d38-201">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-201">Yes</span></span>|<span data-ttu-id="c1d38-202">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-202">n/a</span></span>|<span data-ttu-id="c1d38-203">Identifikátor nebo název funkce</span><span class="sxs-lookup"><span data-stu-id="c1d38-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="c1d38-204">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="c1d38-204">ReturnType</span></span>|<span data-ttu-id="c1d38-205">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-205">String</span></span>|<span data-ttu-id="c1d38-206">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-206">No</span></span>|<span data-ttu-id="c1d38-207">Typ void</span><span class="sxs-lookup"><span data-stu-id="c1d38-207">Void</span></span>|<span data-ttu-id="c1d38-208">Návratový typ funkce EDM</span><span class="sxs-lookup"><span data-stu-id="c1d38-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="c1d38-209">Aggregate</span><span class="sxs-lookup"><span data-stu-id="c1d38-209">Aggregate</span></span>|<span data-ttu-id="c1d38-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="c1d38-210">Boolean</span></span>|<span data-ttu-id="c1d38-211">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-211">No</span></span>|<span data-ttu-id="c1d38-212">False</span><span class="sxs-lookup"><span data-stu-id="c1d38-212">False</span></span>|<span data-ttu-id="c1d38-213">Hodnota TRUE, pokud funkce je agregační funkce</span><span class="sxs-lookup"><span data-stu-id="c1d38-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="c1d38-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="c1d38-214">BuiltIn</span></span>|<span data-ttu-id="c1d38-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="c1d38-215">Boolean</span></span>|<span data-ttu-id="c1d38-216">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-216">No</span></span>|<span data-ttu-id="c1d38-217">Pravda</span><span class="sxs-lookup"><span data-stu-id="c1d38-217">True</span></span>|<span data-ttu-id="c1d38-218">Hodnota TRUE, pokud funkce je integrovaná do úložiště dat</span><span class="sxs-lookup"><span data-stu-id="c1d38-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="c1d38-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="c1d38-219">StoreFunctionName</span></span>|<span data-ttu-id="c1d38-220">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-220">String</span></span>|<span data-ttu-id="c1d38-221">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-221">No</span></span>|<span data-ttu-id="c1d38-222">\<Název ></span><span class="sxs-lookup"><span data-stu-id="c1d38-222">\<Name></span></span>|<span data-ttu-id="c1d38-223">Název funkce v úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="c1d38-223">Function Name in the data store.</span></span>  <span data-ttu-id="c1d38-224">Umožňuje úroveň přesměrování názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="c1d38-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="c1d38-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="c1d38-225">NiladicFunction</span></span>|<span data-ttu-id="c1d38-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="c1d38-226">Boolean</span></span>|<span data-ttu-id="c1d38-227">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-227">No</span></span>|<span data-ttu-id="c1d38-228">False</span><span class="sxs-lookup"><span data-stu-id="c1d38-228">False</span></span>|<span data-ttu-id="c1d38-229">Hodnota TRUE v případě, že funkce nevyžaduje parametrů a je volána bez parametrů</span><span class="sxs-lookup"><span data-stu-id="c1d38-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="c1d38-230">Zda položka ParameterType</span><span class="sxs-lookup"><span data-stu-id="c1d38-230">ParameterType</span></span><br /><br /> <span data-ttu-id="c1d38-231">Sémantika</span><span class="sxs-lookup"><span data-stu-id="c1d38-231">Semantics</span></span>|<span data-ttu-id="c1d38-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="c1d38-232">ParameterSemantics</span></span>|<span data-ttu-id="c1d38-233">Ne</span><span class="sxs-lookup"><span data-stu-id="c1d38-233">No</span></span>|<span data-ttu-id="c1d38-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="c1d38-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="c1d38-235">Konverze</span><span class="sxs-lookup"><span data-stu-id="c1d38-235">Conversion</span></span>|<span data-ttu-id="c1d38-236">Výběr jak kanálu dotazu by měl řešit nahrazení typ parametru:</span><span class="sxs-lookup"><span data-stu-id="c1d38-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="c1d38-237">-ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="c1d38-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="c1d38-238">-AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="c1d38-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="c1d38-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="c1d38-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="c1d38-240">**Parametry uzlu**</span><span class="sxs-lookup"><span data-stu-id="c1d38-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="c1d38-241">Každá funkce má kolekce jednoho nebo více uzlů parametrů.</span><span class="sxs-lookup"><span data-stu-id="c1d38-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="c1d38-242">Název atributu</span><span class="sxs-lookup"><span data-stu-id="c1d38-242">Attribute Name</span></span>|<span data-ttu-id="c1d38-243">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c1d38-243">Data Type</span></span>|<span data-ttu-id="c1d38-244">Požadováno</span><span class="sxs-lookup"><span data-stu-id="c1d38-244">Required</span></span>|<span data-ttu-id="c1d38-245">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="c1d38-245">Default Value</span></span>|<span data-ttu-id="c1d38-246">Popis</span><span class="sxs-lookup"><span data-stu-id="c1d38-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="c1d38-247">Name</span><span class="sxs-lookup"><span data-stu-id="c1d38-247">Name</span></span>|<span data-ttu-id="c1d38-248">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-248">String</span></span>|<span data-ttu-id="c1d38-249">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-249">Yes</span></span>|<span data-ttu-id="c1d38-250">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-250">n/a</span></span>|<span data-ttu-id="c1d38-251">Identifikátor nebo název parametru.</span><span class="sxs-lookup"><span data-stu-id="c1d38-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="c1d38-252">Type</span><span class="sxs-lookup"><span data-stu-id="c1d38-252">Type</span></span>|<span data-ttu-id="c1d38-253">String</span><span class="sxs-lookup"><span data-stu-id="c1d38-253">String</span></span>|<span data-ttu-id="c1d38-254">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-254">Yes</span></span>|<span data-ttu-id="c1d38-255">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-255">n/a</span></span>|<span data-ttu-id="c1d38-256">Typ EDM parametru.</span><span class="sxs-lookup"><span data-stu-id="c1d38-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="c1d38-257">Režim</span><span class="sxs-lookup"><span data-stu-id="c1d38-257">Mode</span></span>|<span data-ttu-id="c1d38-258">Parametr</span><span class="sxs-lookup"><span data-stu-id="c1d38-258">Parameter</span></span><br /><br /> <span data-ttu-id="c1d38-259">Směr</span><span class="sxs-lookup"><span data-stu-id="c1d38-259">Direction</span></span>|<span data-ttu-id="c1d38-260">Ano</span><span class="sxs-lookup"><span data-stu-id="c1d38-260">Yes</span></span>|<span data-ttu-id="c1d38-261">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c1d38-261">n/a</span></span>|<span data-ttu-id="c1d38-262">Směr parametru:</span><span class="sxs-lookup"><span data-stu-id="c1d38-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="c1d38-263">-v</span><span class="sxs-lookup"><span data-stu-id="c1d38-263">-   in</span></span><br /><span data-ttu-id="c1d38-264">-out</span><span class="sxs-lookup"><span data-stu-id="c1d38-264">-   out</span></span><br /><span data-ttu-id="c1d38-265">– vstup</span><span class="sxs-lookup"><span data-stu-id="c1d38-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="c1d38-266">Atribut Namespace</span><span class="sxs-lookup"><span data-stu-id="c1d38-266">Namespace Attribute</span></span>  
 <span data-ttu-id="c1d38-267">Každý poskytovatel úložiště dat musí definovat obor názvů nebo skupiny oborů názvů informace definované v manifestu.</span><span class="sxs-lookup"><span data-stu-id="c1d38-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="c1d38-268">Tento obor názvů lze použít v dotazech Entity SQL k překladu názvů funkcí a typů.</span><span class="sxs-lookup"><span data-stu-id="c1d38-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="c1d38-269">Příklad: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="c1d38-269">For instance: SqlServer.</span></span> <span data-ttu-id="c1d38-270">Tento obor názvů musí být odlišný od canonical obor názvů, EDM, určené služby Entity pro standardní funkce to, že dotazy Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="c1d38-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d38-271">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1d38-271">See also</span></span>

- [<span data-ttu-id="c1d38-272">Zápis zprostředkovatele dat Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c1d38-272">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
