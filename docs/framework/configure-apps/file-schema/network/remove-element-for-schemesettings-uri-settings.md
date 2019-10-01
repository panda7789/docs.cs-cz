---
title: <remove> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 0dc8c6111157ba1f23d4a0449bee8f6626027e23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697850"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="a78d3-102">@no__t – element > 0remove pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="a78d3-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="a78d3-103">Odebere nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="a78d3-103">Removes a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="a78d3-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="a78d3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a78d3-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a78d3-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="a78d3-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a78d3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="a78d3-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="a78d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a78d3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a78d3-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a78d3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a78d3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a78d3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a78d3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a78d3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a78d3-111">Attributes</span></span>  
  
|<span data-ttu-id="a78d3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a78d3-112">Attribute</span></span>|<span data-ttu-id="a78d3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a78d3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a78d3-114">name</span><span class="sxs-lookup"><span data-stu-id="a78d3-114">name</span></span>|<span data-ttu-id="a78d3-115">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="a78d3-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="a78d3-116">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="a78d3-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a78d3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a78d3-117">Child Elements</span></span>  
 <span data-ttu-id="a78d3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a78d3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a78d3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a78d3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a78d3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a78d3-120">Element</span></span>|<span data-ttu-id="a78d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a78d3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a78d3-122">@no__t – element > 1schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="a78d3-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="a78d3-123">Určuje, jak se bude pro konkrétní schémata analyzovat <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="a78d3-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a78d3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a78d3-124">Remarks</span></span>  
 <span data-ttu-id="a78d3-125">Ve výchozím nastavení třídy <xref:System.Uri?displayProperty=nameWithType> zruší řídicí oddělovače% zakódovaných cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="a78d3-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="a78d3-126">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="a78d3-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a78d3-127">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="a78d3-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="a78d3-128">Z tohoto důvodu třída <xref:System.Uri?displayProperty=nameWithType> nejprve zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="a78d3-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="a78d3-129">Výsledek předání škodlivých adres URL výše do konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="a78d3-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a78d3-130">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="a78d3-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a78d3-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a78d3-131">Configuration Files</span></span>  
 <span data-ttu-id="a78d3-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a78d3-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a78d3-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="a78d3-133">Example</span></span>  
 <span data-ttu-id="a78d3-134">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri>, která odebere všechna nastavení schématu pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="a78d3-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a78d3-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a78d3-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="a78d3-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a78d3-136">Network Settings Schema</span></span>](index.md)
