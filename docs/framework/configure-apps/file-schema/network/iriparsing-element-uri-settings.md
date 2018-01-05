---
title: "&lt;iriParsing&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6cd69df9ccba39520cca26bb7042dc2932565336
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="03880-102">&lt;iriParsing&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="03880-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="03880-103">Určuje, zda analýza mezinárodní prostředků identifikátor (IRI) je použita k <xref:System.Uri> a zda má být použita IRI Analýza pravidla.</span><span class="sxs-lookup"><span data-stu-id="03880-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="03880-104">Schéma hierarchie</span><span class="sxs-lookup"><span data-stu-id="03880-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="03880-105">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="03880-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="03880-106">\<Identifikátor URI > elementu (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="03880-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="03880-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="03880-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="03880-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03880-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03880-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03880-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03880-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03880-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03880-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="03880-111">Attributes</span></span>  
  
|<span data-ttu-id="03880-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="03880-112">**Element**</span></span>|<span data-ttu-id="03880-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03880-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="03880-114">Určuje, zda je povoleno IRI analýza.</span><span class="sxs-lookup"><span data-stu-id="03880-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="03880-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="03880-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03880-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03880-116">Child Elements</span></span>  
 <span data-ttu-id="03880-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="03880-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03880-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03880-118">Parent Elements</span></span>  
  
|<span data-ttu-id="03880-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="03880-119">**Element**</span></span>|<span data-ttu-id="03880-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03880-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="03880-121">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="03880-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="03880-122">Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).</span><span class="sxs-lookup"><span data-stu-id="03880-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03880-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03880-123">Remarks</span></span>  
 <span data-ttu-id="03880-124">Existující <xref:System.Uri> třída rozšířilo v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="03880-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="03880-125">3.0 SP1 a 2.0 SP1 zajistit podporu pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="03880-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="03880-126">Aktuální uživatelé neuvidí žádné chování se liší od rozhraní .NET Framework 2.0, pokud konkrétně povolit IRI a IDN podporovat.</span><span class="sxs-lookup"><span data-stu-id="03880-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="03880-127">Tím se zajistí kompatibilitu aplikace s předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03880-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="03880-128">Povolení podpory pro IRI, je potřeba udělat následující dvě změny:</span><span class="sxs-lookup"><span data-stu-id="03880-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="03880-129">Přidejte následující řádek do souboru machine.config v adresáři rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="03880-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="03880-130">Zadejte, zda má být použita IRI Analýza pravidla.</span><span class="sxs-lookup"><span data-stu-id="03880-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="03880-131">To lze provést v souboru machine.config nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="03880-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="03880-132">Povolení analýza IRI (iriParsing, povoleno = `true`) provede normalizaci a znak kontrola podle nejnovější IRI pravidla v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="03880-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="03880-133">Výchozí hodnota je `false` a proveďte normalizaci a znak kontrolu podle RFC 2396 a RFC 3986 (pro literály IPv6).</span><span class="sxs-lookup"><span data-stu-id="03880-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="03880-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="03880-134">Configuration Files</span></span>  
 <span data-ttu-id="03880-135">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="03880-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03880-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="03880-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="03880-137">Popis</span><span class="sxs-lookup"><span data-stu-id="03880-137">Description</span></span>  
 <span data-ttu-id="03880-138">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy.</span><span class="sxs-lookup"><span data-stu-id="03880-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="03880-139">Kód</span><span class="sxs-lookup"><span data-stu-id="03880-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03880-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="03880-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="03880-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="03880-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
