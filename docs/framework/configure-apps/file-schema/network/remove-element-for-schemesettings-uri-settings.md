---
title: <remove> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: f29ee86deaa150324b40f4fac12ead152553e50d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104972"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="00f14-102">\<Odebrat > – Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="00f14-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="00f14-103">Odstraní schéma nastavení pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="00f14-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="00f14-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="00f14-104">\<configuration></span></span>  
<span data-ttu-id="00f14-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="00f14-105">\<uri></span></span>  
<span data-ttu-id="00f14-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="00f14-106">\<schemeSettings></span></span>  
<span data-ttu-id="00f14-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="00f14-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f14-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00f14-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00f14-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00f14-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00f14-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00f14-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00f14-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="00f14-111">Attributes</span></span>  
  
|<span data-ttu-id="00f14-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="00f14-112">Attribute</span></span>|<span data-ttu-id="00f14-113">Popis</span><span class="sxs-lookup"><span data-stu-id="00f14-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00f14-114">name</span><span class="sxs-lookup"><span data-stu-id="00f14-114">name</span></span>|<span data-ttu-id="00f14-115">Název schématu, pro kterou toto nastavení se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="00f14-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="00f14-116">Jenom pro podporované hodnoty jsou název = "http" a název = "https".</span><span class="sxs-lookup"><span data-stu-id="00f14-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00f14-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00f14-117">Child Elements</span></span>  
 <span data-ttu-id="00f14-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="00f14-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00f14-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00f14-119">Parent Elements</span></span>  
  
|<span data-ttu-id="00f14-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="00f14-120">Element</span></span>|<span data-ttu-id="00f14-121">Popis</span><span class="sxs-lookup"><span data-stu-id="00f14-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00f14-122">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="00f14-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="00f14-123">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="00f14-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00f14-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00f14-124">Remarks</span></span>  
 <span data-ttu-id="00f14-125">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="00f14-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="00f14-126">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="00f14-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="00f14-127">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="00f14-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="00f14-128">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="00f14-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="00f14-129">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="00f14-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="00f14-130">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="00f14-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="00f14-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="00f14-131">Configuration Files</span></span>  
 <span data-ttu-id="00f14-132">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="00f14-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00f14-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="00f14-133">Example</span></span>  
 <span data-ttu-id="00f14-134">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídu, která odebere všechna nastavení schéma pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="00f14-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00f14-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00f14-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="00f14-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="00f14-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
