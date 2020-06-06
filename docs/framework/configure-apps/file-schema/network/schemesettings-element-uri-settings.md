---
title: <schemeSettings> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154644"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="3d6a1-102">\<schemeSettings> – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="3d6a1-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="3d6a1-103">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="3d6a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d6a1-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d6a1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3d6a1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3d6a1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d6a1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3d6a1-107">Attributes</span></span>  
 <span data-ttu-id="3d6a1-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3d6a1-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d6a1-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6a1-109">Child Elements</span></span>  
  
|<span data-ttu-id="3d6a1-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="3d6a1-110">**Element**</span></span>|<span data-ttu-id="3d6a1-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3d6a1-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3d6a1-112">add</span><span class="sxs-lookup"><span data-stu-id="3d6a1-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="3d6a1-113">Přidá nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="3d6a1-114">jejich</span><span class="sxs-lookup"><span data-stu-id="3d6a1-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="3d6a1-115">Vymaže všechna existující nastavení schématu.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="3d6a1-116">odebrány</span><span class="sxs-lookup"><span data-stu-id="3d6a1-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="3d6a1-117">Odebere nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d6a1-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3d6a1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3d6a1-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="3d6a1-119">**Element**</span></span>|<span data-ttu-id="3d6a1-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3d6a1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3d6a1-121">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="3d6a1-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="3d6a1-122">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="3d6a1-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d6a1-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d6a1-123">Remarks</span></span>  
 <span data-ttu-id="3d6a1-124">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy zruší počet znaků zakódovaných oddělovači cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="3d6a1-125">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="3d6a1-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3d6a1-126">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="3d6a1-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="3d6a1-127">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> Třída First zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="3d6a1-128">Výsledek předání škodlivou adresu URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktoru třídy má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="3d6a1-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3d6a1-129">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3d6a1-130">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="3d6a1-130">Configuration Files</span></span>  
 <span data-ttu-id="3d6a1-131">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3d6a1-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6a1-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d6a1-132">Example</span></span>  
 <span data-ttu-id="3d6a1-133">Následující příklad ukazuje konfiguraci použitou <xref:System.Uri> třídou pro podporu nekódovaných oddělovačů cest v procentech pro schéma HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d6a1-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="3d6a1-134">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="3d6a1-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="3d6a1-135">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3d6a1-135">Namespace</span></span>|<span data-ttu-id="3d6a1-136">Systém</span><span class="sxs-lookup"><span data-stu-id="3d6a1-136">System</span></span>|  
|<span data-ttu-id="3d6a1-137">Název schématu</span><span class="sxs-lookup"><span data-stu-id="3d6a1-137">Schema Name</span></span>||  
|<span data-ttu-id="3d6a1-138">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="3d6a1-138">Validation File</span></span>||  
|<span data-ttu-id="3d6a1-139">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="3d6a1-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="3d6a1-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d6a1-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="3d6a1-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3d6a1-141">Network Settings Schema</span></span>](index.md)
