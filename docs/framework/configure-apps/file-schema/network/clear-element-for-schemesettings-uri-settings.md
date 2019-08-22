---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 51c669aff767948523172aa075677ad3fb6478a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664177"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ae76d-102">\<Clear – element > pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="ae76d-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ae76d-103">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="ae76d-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="ae76d-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ae76d-104">\<configuration></span></span>  
<span data-ttu-id="ae76d-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="ae76d-105">\<uri></span></span>  
<span data-ttu-id="ae76d-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="ae76d-106">\<schemeSettings></span></span>  
<span data-ttu-id="ae76d-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="ae76d-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae76d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae76d-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae76d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae76d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae76d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae76d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae76d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae76d-111">Attributes</span></span>  
 <span data-ttu-id="ae76d-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae76d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae76d-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae76d-113">Child Elements</span></span>  
 <span data-ttu-id="ae76d-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae76d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae76d-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae76d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ae76d-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae76d-116">Element</span></span>|<span data-ttu-id="ae76d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ae76d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae76d-118">\<schemeSettings – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="ae76d-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ae76d-119">Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="ae76d-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae76d-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae76d-120">Remarks</span></span>  
 <span data-ttu-id="ae76d-121">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="ae76d-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ae76d-122">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="ae76d-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ae76d-123">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="ae76d-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ae76d-124">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="ae76d-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ae76d-125">Výsledek předání škodlivou adresu URL výše konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="ae76d-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ae76d-126">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="ae76d-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ae76d-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ae76d-127">Configuration Files</span></span>  
 <span data-ttu-id="ae76d-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ae76d-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae76d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae76d-129">Example</span></span>  
 <span data-ttu-id="ae76d-130">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou, která vymaže všechna nastavení schématu, a potom přidá podporu pro nekódované oddělovače cest pro schéma HTTP v procentech.</span><span class="sxs-lookup"><span data-stu-id="ae76d-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae76d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae76d-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="ae76d-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ae76d-132">Network Settings Schema</span></span>](index.md)
