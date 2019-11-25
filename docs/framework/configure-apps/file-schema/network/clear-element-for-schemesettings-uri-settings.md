---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087447"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="29739-102">\<Clear > element pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="29739-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="29739-103">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="29739-103">Clears all existing scheme settings.</span></span>  

<span data-ttu-id="29739-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="29739-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29739-105">&nbsp;&nbsp;[ **\<identifikátor uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="29739-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="29739-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="29739-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="29739-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="29739-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="29739-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29739-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29739-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29739-109">Attributes and Elements</span></span>  
 <span data-ttu-id="29739-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29739-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29739-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="29739-111">Attributes</span></span>  
 <span data-ttu-id="29739-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="29739-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29739-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29739-113">Child Elements</span></span>  
 <span data-ttu-id="29739-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="29739-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29739-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29739-115">Parent Elements</span></span>  
  
|<span data-ttu-id="29739-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="29739-116">Element</span></span>|<span data-ttu-id="29739-117">Popis</span><span class="sxs-lookup"><span data-stu-id="29739-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29739-118">\<element > schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="29739-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="29739-119">Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="29739-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29739-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29739-120">Remarks</span></span>  
 <span data-ttu-id="29739-121">Ve výchozím nastavení třída <xref:System.Uri?displayProperty=nameWithType> před spuštěním komprimace cesty vymění v procentech zakódovaných oddělovačů cest.</span><span class="sxs-lookup"><span data-stu-id="29739-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="29739-122">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="29739-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="29739-123">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="29739-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="29739-124">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třída nejprve zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="29739-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="29739-125">Výsledek předání škodlivých adres URL výše do konstruktoru <xref:System.Uri?displayProperty=nameWithType> třídy vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="29739-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="29739-126">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="29739-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="29739-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="29739-127">Configuration Files</span></span>  
 <span data-ttu-id="29739-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="29739-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29739-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="29739-129">Example</span></span>  
 <span data-ttu-id="29739-130">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri>, která vymaže všechna nastavení schématu a pak přidá podporu pro nekódované oddělovače cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="29739-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29739-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29739-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="29739-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="29739-132">Network Settings Schema</span></span>](index.md)
