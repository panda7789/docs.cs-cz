---
title: <uri> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697443"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="b1a9a-102">\<element > identifikátoru URI (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="b1a9a-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="b1a9a-103">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="b1a9a-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="b1a9a-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="b1a9a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b1a9a-105">&nbsp;&nbsp; **\<uri >**</span><span class="sxs-lookup"><span data-stu-id="b1a9a-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a9a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1a9a-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1a9a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1a9a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b1a9a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1a9a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1a9a-109">Attributes</span></span>  
 <span data-ttu-id="b1a9a-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1a9a-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1a9a-111">Child Elements</span></span>  
  
|<span data-ttu-id="b1a9a-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1a9a-112">**Element**</span></span>|<span data-ttu-id="b1a9a-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1a9a-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1a9a-114">IDN</span><span class="sxs-lookup"><span data-stu-id="b1a9a-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="b1a9a-115">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="b1a9a-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b1a9a-116">iriParsing</span><span class="sxs-lookup"><span data-stu-id="b1a9a-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="b1a9a-117">Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b1a9a-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="b1a9a-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b1a9a-119">Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1a9a-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1a9a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b1a9a-121">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1a9a-121">**Element**</span></span>|<span data-ttu-id="b1a9a-122">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1a9a-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1a9a-123">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="b1a9a-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="b1a9a-124">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a9a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1a9a-125">Remarks</span></span>  
 <span data-ttu-id="b1a9a-126">Element `uri` obsahuje nastavení pro členy třídy <xref:System.Uri> používané třídami v oboru názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="b1a9a-127">Nastavení konfigurují podporu pro IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1a9a-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1a9a-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b1a9a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="b1a9a-129">Description</span></span>  
 <span data-ttu-id="b1a9a-130">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="b1a9a-131">Tento příklad také vymaže všechna nastavení schématu a pak přidá podporu pro nekódované oddělovače cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="b1a9a-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b1a9a-132">Kód</span><span class="sxs-lookup"><span data-stu-id="b1a9a-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1a9a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1a9a-133">See also</span></span>

- [<span data-ttu-id="b1a9a-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b1a9a-134">Network Settings Schema</span></span>](index.md)
