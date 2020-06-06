---
title: <uri> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697443"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="b2eb6-102">\<uri> – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="b2eb6-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="b2eb6-103">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="b2eb6-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="b2eb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2eb6-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2eb6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b2eb6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b2eb6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2eb6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b2eb6-107">Attributes</span></span>  
 <span data-ttu-id="b2eb6-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="b2eb6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2eb6-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b2eb6-109">Child Elements</span></span>  
  
|<span data-ttu-id="b2eb6-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b2eb6-110">**Element**</span></span>|<span data-ttu-id="b2eb6-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b2eb6-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2eb6-112">IDN</span><span class="sxs-lookup"><span data-stu-id="b2eb6-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="b2eb6-113">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="b2eb6-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b2eb6-114">iriParsing</span><span class="sxs-lookup"><span data-stu-id="b2eb6-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="b2eb6-115">Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b2eb6-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="b2eb6-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b2eb6-117">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2eb6-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b2eb6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b2eb6-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b2eb6-119">**Element**</span></span>|<span data-ttu-id="b2eb6-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b2eb6-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2eb6-121">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="b2eb6-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="b2eb6-122">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2eb6-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2eb6-123">Remarks</span></span>  
 <span data-ttu-id="b2eb6-124">`uri`Element obsahuje nastavení pro členy <xref:System.Uri> třídy používané třídami v <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="b2eb6-125">Nastavení konfigurují podporu pro IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2eb6-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2eb6-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b2eb6-127">Description</span><span class="sxs-lookup"><span data-stu-id="b2eb6-127">Description</span></span>  
 <span data-ttu-id="b2eb6-128">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> Třída používá pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="b2eb6-129">Tento příklad také vymaže všechna nastavení schématu a pak přidá podporu pro nekódované oddělovače cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2eb6-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b2eb6-130">Kód</span><span class="sxs-lookup"><span data-stu-id="b2eb6-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2eb6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2eb6-131">See also</span></span>

- [<span data-ttu-id="b2eb6-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b2eb6-132">Network Settings Schema</span></span>](index.md)
