---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: a4d4df8c214efb955f8f9d6678aaf8d56de71ebc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256653"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="97d88-102">\<iriParsing > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="97d88-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="97d88-103">Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="97d88-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="97d88-104">Schema Hierarchy</span><span class="sxs-lookup"><span data-stu-id="97d88-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="97d88-105">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="97d88-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="97d88-106">\<Identifikátor URI > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="97d88-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="97d88-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="97d88-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="97d88-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97d88-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97d88-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97d88-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97d88-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97d88-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97d88-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="97d88-111">Attributes</span></span>  
  
|<span data-ttu-id="97d88-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="97d88-112">**Element**</span></span>|<span data-ttu-id="97d88-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="97d88-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="97d88-114">Určuje, zda je povolena analýza IRI.</span><span class="sxs-lookup"><span data-stu-id="97d88-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="97d88-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="97d88-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97d88-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97d88-116">Child Elements</span></span>  
 <span data-ttu-id="97d88-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="97d88-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97d88-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97d88-118">Parent Elements</span></span>  
  
|<span data-ttu-id="97d88-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="97d88-119">**Element**</span></span>|<span data-ttu-id="97d88-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="97d88-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97d88-121">uri</span><span class="sxs-lookup"><span data-stu-id="97d88-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="97d88-122">Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="97d88-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97d88-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97d88-123">Remarks</span></span>  
 <span data-ttu-id="97d88-124">Existující <xref:System.Uri> bylo rozšířeno třídy v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="97d88-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="97d88-125">3.0 SP1 a 2.0 SP1 pro poskytnutí podpory pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="97d88-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="97d88-126">Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud výslovně povolit IRI a IDN podporovat.</span><span class="sxs-lookup"><span data-stu-id="97d88-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="97d88-127">Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97d88-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="97d88-128">Povolení podpory pro IRI, jsou požadovány následující dvě změny:</span><span class="sxs-lookup"><span data-stu-id="97d88-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="97d88-129">Přidejte následující řádek do souboru machine.config, v adresáři rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="97d88-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="97d88-130">Určete, zda má být použita IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="97d88-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="97d88-131">To můžete udělat v souboru machine.config nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="97d88-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="97d88-132">Povolení analýza IRI (iriParsing, povoleno = `true`) provede normalizaci a znak kontroly podle nejnovějších IRI pravidla v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="97d88-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="97d88-133">Výchozí hodnota je `false` a proveďte normalizace a znak kontroly podle RFC 2396 a RFC 3986 (pro literály IPv6).</span><span class="sxs-lookup"><span data-stu-id="97d88-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="97d88-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="97d88-134">Configuration Files</span></span>  
 <span data-ttu-id="97d88-135">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="97d88-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97d88-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="97d88-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97d88-137">Popis</span><span class="sxs-lookup"><span data-stu-id="97d88-137">Description</span></span>  
 <span data-ttu-id="97d88-138">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.</span><span class="sxs-lookup"><span data-stu-id="97d88-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="97d88-139">Kód</span><span class="sxs-lookup"><span data-stu-id="97d88-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97d88-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97d88-140">See also</span></span>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="97d88-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="97d88-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
