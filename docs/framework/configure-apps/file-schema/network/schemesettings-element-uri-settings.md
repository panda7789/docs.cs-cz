---
title: <schemeSettings> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 46012b15d41422fb3357e57438e320136809ef41
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664013"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="eea8a-102">\<schemeSettings – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="eea8a-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="eea8a-103">Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="eea8a-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="eea8a-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="eea8a-104">\<configuration></span></span>  
<span data-ttu-id="eea8a-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="eea8a-105">\<uri></span></span>  
<span data-ttu-id="eea8a-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="eea8a-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea8a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eea8a-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eea8a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eea8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eea8a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eea8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eea8a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="eea8a-110">Attributes</span></span>  
 <span data-ttu-id="eea8a-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="eea8a-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eea8a-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eea8a-112">Child Elements</span></span>  
  
|<span data-ttu-id="eea8a-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="eea8a-113">**Element**</span></span>|<span data-ttu-id="eea8a-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eea8a-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eea8a-115">add</span><span class="sxs-lookup"><span data-stu-id="eea8a-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="eea8a-116">Přidá nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="eea8a-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="eea8a-117">jejich</span><span class="sxs-lookup"><span data-stu-id="eea8a-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="eea8a-118">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="eea8a-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="eea8a-119">remove</span><span class="sxs-lookup"><span data-stu-id="eea8a-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="eea8a-120">Odebere nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="eea8a-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eea8a-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eea8a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eea8a-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="eea8a-122">**Element**</span></span>|<span data-ttu-id="eea8a-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eea8a-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eea8a-124">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="eea8a-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="eea8a-125">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="eea8a-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eea8a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eea8a-126">Remarks</span></span>  
 <span data-ttu-id="eea8a-127">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="eea8a-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="eea8a-128">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="eea8a-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="eea8a-129">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="eea8a-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="eea8a-130">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="eea8a-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="eea8a-131">Výsledek předání škodlivou adresu URL výše konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="eea8a-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="eea8a-132">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="eea8a-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eea8a-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="eea8a-133">Configuration Files</span></span>  
 <span data-ttu-id="eea8a-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="eea8a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eea8a-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="eea8a-135">Example</span></span>  
 <span data-ttu-id="eea8a-136">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou pro podporu nekódovaných oddělovačů cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="eea8a-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="eea8a-137">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="eea8a-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="eea8a-138">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="eea8a-138">Namespace</span></span>|<span data-ttu-id="eea8a-139">Systém</span><span class="sxs-lookup"><span data-stu-id="eea8a-139">System</span></span>|  
|<span data-ttu-id="eea8a-140">Název schématu</span><span class="sxs-lookup"><span data-stu-id="eea8a-140">Schema Name</span></span>||  
|<span data-ttu-id="eea8a-141">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="eea8a-141">Validation File</span></span>||  
|<span data-ttu-id="eea8a-142">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="eea8a-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="eea8a-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eea8a-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="eea8a-144">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="eea8a-144">Network Settings Schema</span></span>](index.md)
