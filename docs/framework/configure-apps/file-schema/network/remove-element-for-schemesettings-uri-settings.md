---
title: <remove> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089153"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="75296-102">\<odebrat element > pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="75296-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="75296-103">Odebere nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="75296-103">Removes a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="75296-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="75296-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75296-105">&nbsp;&nbsp;[ **\<identifikátor uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="75296-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="75296-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="75296-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="75296-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="75296-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75296-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75296-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75296-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="75296-109">Attributes and Elements</span></span>  
 <span data-ttu-id="75296-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="75296-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75296-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="75296-111">Attributes</span></span>  
  
|<span data-ttu-id="75296-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="75296-112">Attribute</span></span>|<span data-ttu-id="75296-113">Popis</span><span class="sxs-lookup"><span data-stu-id="75296-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75296-114">name</span><span class="sxs-lookup"><span data-stu-id="75296-114">name</span></span>|<span data-ttu-id="75296-115">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="75296-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="75296-116">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="75296-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75296-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="75296-117">Child Elements</span></span>  
 <span data-ttu-id="75296-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="75296-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75296-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="75296-119">Parent Elements</span></span>  
  
|<span data-ttu-id="75296-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="75296-120">Element</span></span>|<span data-ttu-id="75296-121">Popis</span><span class="sxs-lookup"><span data-stu-id="75296-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75296-122">\<element > schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="75296-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="75296-123">Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="75296-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75296-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75296-124">Remarks</span></span>  
 <span data-ttu-id="75296-125">Ve výchozím nastavení třída <xref:System.Uri?displayProperty=nameWithType> před spuštěním komprimace cesty vymění v procentech zakódovaných oddělovačů cest.</span><span class="sxs-lookup"><span data-stu-id="75296-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="75296-126">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="75296-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="75296-127">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="75296-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="75296-128">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třída nejprve zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="75296-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="75296-129">Výsledek předání škodlivých adres URL výše do konstruktoru <xref:System.Uri?displayProperty=nameWithType> třídy vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="75296-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="75296-130">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="75296-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="75296-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="75296-131">Configuration Files</span></span>  
 <span data-ttu-id="75296-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="75296-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75296-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="75296-133">Example</span></span>  
 <span data-ttu-id="75296-134">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri>, která odebere všechna nastavení schématu pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="75296-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75296-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75296-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="75296-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="75296-136">Network Settings Schema</span></span>](index.md)
