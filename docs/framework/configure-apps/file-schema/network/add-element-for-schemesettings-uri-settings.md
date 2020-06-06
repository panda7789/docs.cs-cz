---
title: <add> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087721"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ae18f-102">\<add> – element pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="ae18f-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ae18f-103">Přidá nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="ae18f-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="ae18f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae18f-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae18f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae18f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ae18f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae18f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae18f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae18f-107">Attributes</span></span>  
  
|<span data-ttu-id="ae18f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae18f-108">Attribute</span></span>|<span data-ttu-id="ae18f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ae18f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae18f-110">name</span><span class="sxs-lookup"><span data-stu-id="ae18f-110">name</span></span>|<span data-ttu-id="ae18f-111">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="ae18f-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="ae18f-112">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="ae18f-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="ae18f-113">{Název atributu} Přidělen</span><span class="sxs-lookup"><span data-stu-id="ae18f-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="ae18f-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ae18f-114">Value</span></span>|<span data-ttu-id="ae18f-115">Description</span><span class="sxs-lookup"><span data-stu-id="ae18f-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae18f-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="ae18f-116">genericUriParserOptions</span></span>|<span data-ttu-id="ae18f-117">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="ae18f-117">The parser options for this scheme.</span></span> <span data-ttu-id="ae18f-118">Jediná podporovaná hodnota je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="ae18f-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae18f-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae18f-119">Child Elements</span></span>  
 <span data-ttu-id="ae18f-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae18f-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae18f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae18f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ae18f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae18f-122">Element</span></span>|<span data-ttu-id="ae18f-123">Description</span><span class="sxs-lookup"><span data-stu-id="ae18f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae18f-124">\<schemeSettings>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="ae18f-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ae18f-125">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="ae18f-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae18f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae18f-126">Remarks</span></span>  
 <span data-ttu-id="ae18f-127">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="ae18f-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ae18f-128">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="ae18f-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ae18f-129">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="ae18f-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ae18f-130">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="ae18f-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ae18f-131">Výsledek předání škodlivou adresu URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktoru třídy má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ae18f-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ae18f-132">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="ae18f-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ae18f-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ae18f-133">Configuration Files</span></span>  
 <span data-ttu-id="ae18f-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ae18f-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae18f-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae18f-135">Example</span></span>  
 <span data-ttu-id="ae18f-136">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou pro podporu nekódovaných oddělovačů cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae18f-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae18f-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae18f-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="ae18f-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ae18f-138">Network Settings Schema</span></span>](index.md)
