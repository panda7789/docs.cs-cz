---
title: <add> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659543"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="abede-102">\<Přidat > element pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="abede-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="abede-103">Přidá nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="abede-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="abede-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="abede-104">\<configuration></span></span>  
<span data-ttu-id="abede-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="abede-105">\<uri></span></span>  
<span data-ttu-id="abede-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="abede-106">\<schemeSettings></span></span>  
<span data-ttu-id="abede-107">\<add></span><span class="sxs-lookup"><span data-stu-id="abede-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abede-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abede-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abede-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abede-109">Attributes and Elements</span></span>  
 <span data-ttu-id="abede-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abede-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abede-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="abede-111">Attributes</span></span>  
  
|<span data-ttu-id="abede-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="abede-112">Attribute</span></span>|<span data-ttu-id="abede-113">Popis</span><span class="sxs-lookup"><span data-stu-id="abede-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abede-114">name</span><span class="sxs-lookup"><span data-stu-id="abede-114">name</span></span>|<span data-ttu-id="abede-115">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="abede-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="abede-116">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="abede-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="abede-117">{Název atributu} Přidělen</span><span class="sxs-lookup"><span data-stu-id="abede-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="abede-118">Value</span><span class="sxs-lookup"><span data-stu-id="abede-118">Value</span></span>|<span data-ttu-id="abede-119">Popis</span><span class="sxs-lookup"><span data-stu-id="abede-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="abede-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="abede-120">genericUriParserOptions</span></span>|<span data-ttu-id="abede-121">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="abede-121">The parser options for this scheme.</span></span> <span data-ttu-id="abede-122">Jediná podporovaná hodnota je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="abede-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abede-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="abede-123">Child Elements</span></span>  
 <span data-ttu-id="abede-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="abede-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abede-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="abede-125">Parent Elements</span></span>  
  
|<span data-ttu-id="abede-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="abede-126">Element</span></span>|<span data-ttu-id="abede-127">Popis</span><span class="sxs-lookup"><span data-stu-id="abede-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abede-128">\<schemeSettings – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="abede-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="abede-129">Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="abede-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abede-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abede-130">Remarks</span></span>  
 <span data-ttu-id="abede-131">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="abede-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="abede-132">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="abede-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="abede-133">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="abede-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="abede-134">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="abede-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="abede-135">Výsledek předání škodlivou adresu URL výše konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="abede-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="abede-136">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="abede-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="abede-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="abede-137">Configuration Files</span></span>  
 <span data-ttu-id="abede-138">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="abede-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abede-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="abede-139">Example</span></span>  
 <span data-ttu-id="abede-140">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou pro podporu nekódovaných oddělovačů cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="abede-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="abede-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abede-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="abede-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="abede-142">Network Settings Schema</span></span>](index.md)
