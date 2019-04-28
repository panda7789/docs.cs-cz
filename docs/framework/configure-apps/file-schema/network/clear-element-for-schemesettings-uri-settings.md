---
title: <clear> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 132506dc15335b738fcdb026f4d31429bc45a228
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674685"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="a5ede-102">\<Vymazat > – Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="a5ede-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="a5ede-103">Vymaže všechna existující nastavení schéma.</span><span class="sxs-lookup"><span data-stu-id="a5ede-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="a5ede-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a5ede-104">\<configuration></span></span>  
<span data-ttu-id="a5ede-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="a5ede-105">\<uri></span></span>  
<span data-ttu-id="a5ede-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="a5ede-106">\<schemeSettings></span></span>  
<span data-ttu-id="a5ede-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="a5ede-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ede-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5ede-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5ede-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5ede-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a5ede-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5ede-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5ede-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5ede-111">Attributes</span></span>  
 <span data-ttu-id="a5ede-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5ede-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5ede-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5ede-113">Child Elements</span></span>  
 <span data-ttu-id="a5ede-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5ede-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5ede-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5ede-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a5ede-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5ede-116">Element</span></span>|<span data-ttu-id="a5ede-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a5ede-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5ede-118">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="a5ede-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="a5ede-119">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="a5ede-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5ede-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5ede-120">Remarks</span></span>  
 <span data-ttu-id="a5ede-121">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="a5ede-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="a5ede-122">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="a5ede-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a5ede-123">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a5ede-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="a5ede-124">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="a5ede-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="a5ede-125">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="a5ede-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a5ede-126">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="a5ede-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a5ede-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a5ede-127">Configuration Files</span></span>  
 <span data-ttu-id="a5ede-128">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a5ede-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ede-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ede-129">Example</span></span>  
 <span data-ttu-id="a5ede-130">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídu, která zruší všechny schéma nastavení a pak přidává podporu pro není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="a5ede-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5ede-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5ede-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="a5ede-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a5ede-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
