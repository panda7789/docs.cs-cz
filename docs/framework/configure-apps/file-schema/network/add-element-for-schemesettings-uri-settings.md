---
title: <add> – Element pro schemeSettings (nastavení Uri)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: e7606a1185d406384a926ca4dcb7c42586461574
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139929"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="093e0-102">\<Přidat > – Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="093e0-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="093e0-103">Přidá nastavení schéma pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="093e0-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="093e0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="093e0-104">\<configuration></span></span>  
<span data-ttu-id="093e0-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="093e0-105">\<uri></span></span>  
<span data-ttu-id="093e0-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="093e0-106">\<schemeSettings></span></span>  
<span data-ttu-id="093e0-107">\<add></span><span class="sxs-lookup"><span data-stu-id="093e0-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093e0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="093e0-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="093e0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="093e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="093e0-110">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="093e0-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="093e0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="093e0-111">Attributes</span></span>  
  
|<span data-ttu-id="093e0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="093e0-112">Attribute</span></span>|<span data-ttu-id="093e0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="093e0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="093e0-114">name</span><span class="sxs-lookup"><span data-stu-id="093e0-114">name</span></span>|<span data-ttu-id="093e0-115">Název schématu, pro kterou toto nastavení se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="093e0-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="093e0-116">Jenom pro podporované hodnoty jsou název = "http" a název = "https".</span><span class="sxs-lookup"><span data-stu-id="093e0-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="093e0-117">{Atribut name} Atribut</span><span class="sxs-lookup"><span data-stu-id="093e0-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="093e0-118">Value</span><span class="sxs-lookup"><span data-stu-id="093e0-118">Value</span></span>|<span data-ttu-id="093e0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="093e0-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="093e0-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="093e0-120">genericUriParserOptions</span></span>|<span data-ttu-id="093e0-121">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="093e0-121">The parser options for this scheme.</span></span> <span data-ttu-id="093e0-122">Jedinou podporovanou hodnotou je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="093e0-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="093e0-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="093e0-123">Child Elements</span></span>  
 <span data-ttu-id="093e0-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="093e0-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="093e0-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="093e0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="093e0-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="093e0-126">Element</span></span>|<span data-ttu-id="093e0-127">Popis</span><span class="sxs-lookup"><span data-stu-id="093e0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="093e0-128">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="093e0-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="093e0-129">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="093e0-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="093e0-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="093e0-130">Remarks</span></span>  
 <span data-ttu-id="093e0-131">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="093e0-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="093e0-132">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="093e0-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="093e0-133">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="093e0-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="093e0-134">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="093e0-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="093e0-135">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="093e0-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="093e0-136">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="093e0-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="093e0-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="093e0-137">Configuration Files</span></span>  
 <span data-ttu-id="093e0-138">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="093e0-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="093e0-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="093e0-139">Example</span></span>  
 <span data-ttu-id="093e0-140">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="093e0-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="093e0-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="093e0-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="093e0-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="093e0-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
