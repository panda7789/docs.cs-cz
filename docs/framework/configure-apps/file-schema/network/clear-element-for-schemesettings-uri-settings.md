---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087447"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="528fa-102">\<clear> – element pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="528fa-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="528fa-103">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="528fa-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="528fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="528fa-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="528fa-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="528fa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="528fa-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="528fa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="528fa-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="528fa-107">Attributes</span></span>  
 <span data-ttu-id="528fa-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="528fa-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="528fa-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="528fa-109">Child Elements</span></span>  
 <span data-ttu-id="528fa-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="528fa-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="528fa-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="528fa-111">Parent Elements</span></span>  
  
|<span data-ttu-id="528fa-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="528fa-112">Element</span></span>|<span data-ttu-id="528fa-113">Description</span><span class="sxs-lookup"><span data-stu-id="528fa-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="528fa-114">\<schemeSettings>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="528fa-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="528fa-115">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="528fa-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528fa-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="528fa-116">Remarks</span></span>  
 <span data-ttu-id="528fa-117">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="528fa-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="528fa-118">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="528fa-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="528fa-119">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="528fa-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="528fa-120">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="528fa-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="528fa-121">Výsledek předání škodlivou adresu URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktoru třídy má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="528fa-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="528fa-122">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="528fa-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="528fa-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="528fa-123">Configuration Files</span></span>  
 <span data-ttu-id="528fa-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="528fa-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="528fa-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="528fa-125">Example</span></span>  
 <span data-ttu-id="528fa-126">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou, která vymaže všechna nastavení schématu, a potom přidá podporu pro nekódované oddělovače cest pro schéma HTTP v procentech.</span><span class="sxs-lookup"><span data-stu-id="528fa-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="528fa-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="528fa-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="528fa-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="528fa-128">Network Settings Schema</span></span>](index.md)
