---
title: '&lt;Vymazat&gt; – Element pro schemeSettings (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 043ce78283c42d2cf42851e13919bf71a77b28b4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196671"
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="349b0-102">&lt;Vymazat&gt; – Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="349b0-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="349b0-103">Vymaže všechna existující nastavení schéma.</span><span class="sxs-lookup"><span data-stu-id="349b0-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="349b0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="349b0-104">\<configuration></span></span>  
<span data-ttu-id="349b0-105">\<identifikátor URI ></span><span class="sxs-lookup"><span data-stu-id="349b0-105">\<uri></span></span>  
<span data-ttu-id="349b0-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="349b0-106">\<schemeSettings></span></span>  
<span data-ttu-id="349b0-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="349b0-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349b0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="349b0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="349b0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="349b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="349b0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="349b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="349b0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="349b0-111">Attributes</span></span>  
 <span data-ttu-id="349b0-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="349b0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="349b0-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="349b0-113">Child Elements</span></span>  
 <span data-ttu-id="349b0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="349b0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="349b0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="349b0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="349b0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="349b0-116">Element</span></span>|<span data-ttu-id="349b0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="349b0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="349b0-118">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="349b0-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="349b0-119">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="349b0-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="349b0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="349b0-120">Remarks</span></span>  
 <span data-ttu-id="349b0-121">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="349b0-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="349b0-122">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="349b0-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="349b0-123">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="349b0-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="349b0-124">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="349b0-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="349b0-125">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="349b0-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="349b0-126">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="349b0-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="349b0-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="349b0-127">Configuration Files</span></span>  
 <span data-ttu-id="349b0-128">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="349b0-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="349b0-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="349b0-129">Example</span></span>  
 <span data-ttu-id="349b0-130">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídu, která zruší všechny schéma nastavení a pak přidává podporu pro není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="349b0-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="349b0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="349b0-131">See Also</span></span>  
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
- <xref:System.Uri?displayProperty=nameWithType>  
- [<span data-ttu-id="349b0-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="349b0-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
