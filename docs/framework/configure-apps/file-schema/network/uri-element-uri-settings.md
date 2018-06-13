---
title: '&lt;Identifikátor URI&gt; – Element (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 05b2fb4255643f657f37012ec51a1b29ed68095d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742806"
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="b21d6-102">&lt;Identifikátor URI&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="b21d6-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="b21d6-103">Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).</span><span class="sxs-lookup"><span data-stu-id="b21d6-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="b21d6-104">Schéma hierarchie</span><span class="sxs-lookup"><span data-stu-id="b21d6-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="b21d6-105">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="b21d6-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="b21d6-106">\<identifikátor URI ></span><span class="sxs-lookup"><span data-stu-id="b21d6-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="b21d6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b21d6-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b21d6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b21d6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b21d6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b21d6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b21d6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b21d6-110">Attributes</span></span>  
 <span data-ttu-id="b21d6-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="b21d6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b21d6-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b21d6-112">Child Elements</span></span>  
  
|<span data-ttu-id="b21d6-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="b21d6-113">**Element**</span></span>|<span data-ttu-id="b21d6-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b21d6-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b21d6-115">IDN.</span><span class="sxs-lookup"><span data-stu-id="b21d6-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="b21d6-116">Určuje, pokud analýza mezinárodní název domény (IDN) se použijí pro názvy domén.</span><span class="sxs-lookup"><span data-stu-id="b21d6-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b21d6-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="b21d6-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="b21d6-118">Určuje, pokud analýza mezinárodní prostředků identifikátor (IRI) se použijí pro <xref:System.Uri> a zda má být použita IRI Analýza pravidla.</span><span class="sxs-lookup"><span data-stu-id="b21d6-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b21d6-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="b21d6-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="b21d6-120">Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.</span><span class="sxs-lookup"><span data-stu-id="b21d6-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b21d6-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b21d6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b21d6-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="b21d6-122">**Element**</span></span>|<span data-ttu-id="b21d6-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b21d6-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b21d6-124">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b21d6-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="b21d6-125">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b21d6-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b21d6-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b21d6-126">Remarks</span></span>  
 <span data-ttu-id="b21d6-127">`uri` Element obsahuje nastavení pro členy <xref:System.Uri> třídy používané třídy v <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b21d6-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="b21d6-128">Nastavení konfigurace podpory pro IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="b21d6-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b21d6-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="b21d6-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b21d6-130">Popis</span><span class="sxs-lookup"><span data-stu-id="b21d6-130">Description</span></span>  
 <span data-ttu-id="b21d6-131">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy.</span><span class="sxs-lookup"><span data-stu-id="b21d6-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="b21d6-132">V příkladu rovněž vymaže všechna nastavení schéma a pak přidává podporu pro není uvozovací znaky oddělovače kódováním procent cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="b21d6-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b21d6-133">Kód</span><span class="sxs-lookup"><span data-stu-id="b21d6-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b21d6-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b21d6-134">See Also</span></span>  
 [<span data-ttu-id="b21d6-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b21d6-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
