---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: e954fef455d0279a945c33f2014913fea9d63064
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699448"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="3f953-102">@no__t – element > 0clear pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="3f953-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="3f953-103">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="3f953-103">Clears all existing scheme settings.</span></span>  
  
[<span data-ttu-id="3f953-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="3f953-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3f953-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3f953-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="3f953-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3f953-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="3f953-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="3f953-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f953-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f953-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f953-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3f953-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f953-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3f953-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f953-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3f953-111">Attributes</span></span>  
 <span data-ttu-id="3f953-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f953-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f953-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3f953-113">Child Elements</span></span>  
 <span data-ttu-id="3f953-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f953-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f953-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3f953-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3f953-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f953-116">Element</span></span>|<span data-ttu-id="3f953-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3f953-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f953-118">@no__t – element > 1schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="3f953-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="3f953-119">Určuje, jak se bude pro konkrétní schémata analyzovat <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="3f953-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f953-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f953-120">Remarks</span></span>  
 <span data-ttu-id="3f953-121">Ve výchozím nastavení třídy <xref:System.Uri?displayProperty=nameWithType> zruší řídicí oddělovače% zakódovaných cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="3f953-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="3f953-122">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="3f953-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3f953-123">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="3f953-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="3f953-124">Z tohoto důvodu třída <xref:System.Uri?displayProperty=nameWithType> nejprve zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="3f953-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="3f953-125">Výsledek předání škodlivých adres URL výše do konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="3f953-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3f953-126">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="3f953-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3f953-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="3f953-127">Configuration Files</span></span>  
 <span data-ttu-id="3f953-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3f953-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f953-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f953-129">Example</span></span>  
 <span data-ttu-id="3f953-130">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri>, která vymaže všechna nastavení schématu, a potom přidá podporu pro nekódované oddělovače cest pro schéma HTTP v procentech.</span><span class="sxs-lookup"><span data-stu-id="3f953-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f953-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f953-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="3f953-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3f953-132">Network Settings Schema</span></span>](index.md)
