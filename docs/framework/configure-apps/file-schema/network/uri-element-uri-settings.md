---
title: <Uri> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663968"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="c47fc-102">\<Identifikátor URI > – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="c47fc-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="c47fc-103">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="c47fc-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="c47fc-104">Hierarchie schématu</span><span class="sxs-lookup"><span data-stu-id="c47fc-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="c47fc-105">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c47fc-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="c47fc-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="c47fc-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="c47fc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c47fc-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c47fc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c47fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c47fc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c47fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c47fc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c47fc-110">Attributes</span></span>  
 <span data-ttu-id="c47fc-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c47fc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c47fc-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c47fc-112">Child Elements</span></span>  
  
|<span data-ttu-id="c47fc-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="c47fc-113">**Element**</span></span>|<span data-ttu-id="c47fc-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c47fc-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c47fc-115">IDN</span><span class="sxs-lookup"><span data-stu-id="c47fc-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="c47fc-116">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="c47fc-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="c47fc-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="c47fc-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="c47fc-118">Určuje, jestli se má použít <xref:System.Uri> analýza mezinárodní identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="c47fc-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="c47fc-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="c47fc-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="c47fc-120">Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="c47fc-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c47fc-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c47fc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c47fc-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="c47fc-122">**Element**</span></span>|<span data-ttu-id="c47fc-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c47fc-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c47fc-124">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="c47fc-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="c47fc-125">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="c47fc-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c47fc-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c47fc-126">Remarks</span></span>  
 <span data-ttu-id="c47fc-127">Element obsahuje nastavení pro členy <xref:System.Uri> třídy <xref:System.Net> používané třídami v oboru názvů. `uri`</span><span class="sxs-lookup"><span data-stu-id="c47fc-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="c47fc-128">Nastavení konfigurují podporu pro IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="c47fc-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c47fc-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="c47fc-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c47fc-130">Popis</span><span class="sxs-lookup"><span data-stu-id="c47fc-130">Description</span></span>  
 <span data-ttu-id="c47fc-131">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> třída používá pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="c47fc-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="c47fc-132">Tento příklad také vymaže všechna nastavení schématu a pak přidá podporu pro nekódované oddělovače cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="c47fc-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c47fc-133">Kód</span><span class="sxs-lookup"><span data-stu-id="c47fc-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c47fc-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c47fc-134">See also</span></span>

- [<span data-ttu-id="c47fc-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c47fc-135">Network Settings Schema</span></span>](index.md)
