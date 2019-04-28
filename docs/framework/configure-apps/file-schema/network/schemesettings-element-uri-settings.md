---
title: <schemeSettings> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 8dc505d8a9de4e8939372af61b23652551c36530
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705009"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="770d1-102">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="770d1-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="770d1-103">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="770d1-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="770d1-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="770d1-104">\<configuration></span></span>  
<span data-ttu-id="770d1-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="770d1-105">\<uri></span></span>  
<span data-ttu-id="770d1-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="770d1-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770d1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="770d1-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="770d1-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="770d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="770d1-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="770d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="770d1-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="770d1-110">Attributes</span></span>  
 <span data-ttu-id="770d1-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="770d1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="770d1-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="770d1-112">Child Elements</span></span>  
  
|<span data-ttu-id="770d1-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="770d1-113">**Element**</span></span>|<span data-ttu-id="770d1-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="770d1-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="770d1-115">add</span><span class="sxs-lookup"><span data-stu-id="770d1-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="770d1-116">Přidá nastavení schéma pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="770d1-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="770d1-117">clear</span><span class="sxs-lookup"><span data-stu-id="770d1-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="770d1-118">Vymaže všechna existující nastavení schéma.</span><span class="sxs-lookup"><span data-stu-id="770d1-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="770d1-119">remove</span><span class="sxs-lookup"><span data-stu-id="770d1-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="770d1-120">Odstraní schéma nastavení pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="770d1-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="770d1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="770d1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="770d1-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="770d1-122">**Element**</span></span>|<span data-ttu-id="770d1-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="770d1-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="770d1-124">uri</span><span class="sxs-lookup"><span data-stu-id="770d1-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="770d1-125">Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="770d1-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="770d1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="770d1-126">Remarks</span></span>  
 <span data-ttu-id="770d1-127">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="770d1-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="770d1-128">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="770d1-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="770d1-129">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="770d1-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="770d1-130">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="770d1-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="770d1-131">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="770d1-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="770d1-132">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="770d1-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="770d1-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="770d1-133">Configuration Files</span></span>  
 <span data-ttu-id="770d1-134">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="770d1-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="770d1-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="770d1-135">Example</span></span>  
 <span data-ttu-id="770d1-136">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="770d1-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="770d1-137">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="770d1-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="770d1-138">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="770d1-138">Namespace</span></span>|<span data-ttu-id="770d1-139">Systém</span><span class="sxs-lookup"><span data-stu-id="770d1-139">System</span></span>|  
|<span data-ttu-id="770d1-140">Název schématu</span><span class="sxs-lookup"><span data-stu-id="770d1-140">Schema Name</span></span>||  
|<span data-ttu-id="770d1-141">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="770d1-141">Validation File</span></span>||  
|<span data-ttu-id="770d1-142">Může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="770d1-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="770d1-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="770d1-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="770d1-144">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="770d1-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
