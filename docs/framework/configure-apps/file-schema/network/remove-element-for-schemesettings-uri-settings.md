---
title: <remove> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089153"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="fd1e0-102">\<remove> – element pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="fd1e0-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="fd1e0-103">Odebere nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="fd1e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd1e0-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd1e0-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fd1e0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd1e0-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd1e0-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="fd1e0-107">Attributes</span></span>  
  
|<span data-ttu-id="fd1e0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="fd1e0-108">Attribute</span></span>|<span data-ttu-id="fd1e0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fd1e0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd1e0-110">name</span><span class="sxs-lookup"><span data-stu-id="fd1e0-110">name</span></span>|<span data-ttu-id="fd1e0-111">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="fd1e0-112">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="fd1e0-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd1e0-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fd1e0-113">Child Elements</span></span>  
 <span data-ttu-id="fd1e0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="fd1e0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd1e0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fd1e0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fd1e0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd1e0-116">Element</span></span>|<span data-ttu-id="fd1e0-117">Description</span><span class="sxs-lookup"><span data-stu-id="fd1e0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd1e0-118">\<schemeSettings>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="fd1e0-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="fd1e0-119">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd1e0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd1e0-120">Remarks</span></span>  
 <span data-ttu-id="fd1e0-121">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="fd1e0-122">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="fd1e0-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="fd1e0-123">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="fd1e0-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="fd1e0-124">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="fd1e0-125">Výsledek předání škodlivou adresu URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktoru třídy má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="fd1e0-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="fd1e0-126">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fd1e0-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="fd1e0-127">Configuration Files</span></span>  
 <span data-ttu-id="fd1e0-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="fd1e0-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd1e0-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd1e0-129">Example</span></span>  
 <span data-ttu-id="fd1e0-130">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou, která odebere všechna nastavení schématu pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd1e0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd1e0-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="fd1e0-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fd1e0-132">Network Settings Schema</span></span>](index.md)
