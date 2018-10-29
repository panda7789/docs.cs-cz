---
title: '&lt;Přidat&gt; – Element pro schemeSettings (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 07bcaf470c68a4d400057b0fe19e96524b2859cb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205175"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="a4c3e-102">&lt;Přidat&gt; – Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="a4c3e-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="a4c3e-103">Přidá nastavení schéma pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="a4c3e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a4c3e-104">\<configuration></span></span>  
<span data-ttu-id="a4c3e-105">\<identifikátor URI ></span><span class="sxs-lookup"><span data-stu-id="a4c3e-105">\<uri></span></span>  
<span data-ttu-id="a4c3e-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="a4c3e-106">\<schemeSettings></span></span>  
<span data-ttu-id="a4c3e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="a4c3e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c3e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4c3e-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4c3e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4c3e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a4c3e-110">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4c3e-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4c3e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4c3e-111">Attributes</span></span>  
  
|<span data-ttu-id="a4c3e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a4c3e-112">Attribute</span></span>|<span data-ttu-id="a4c3e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c3e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4c3e-114">name</span><span class="sxs-lookup"><span data-stu-id="a4c3e-114">name</span></span>|<span data-ttu-id="a4c3e-115">Název schématu, pro kterou toto nastavení se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="a4c3e-116">Jenom pro podporované hodnoty jsou název = "http" a název = "https".</span><span class="sxs-lookup"><span data-stu-id="a4c3e-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="a4c3e-117">{Atribut name} Atribut</span><span class="sxs-lookup"><span data-stu-id="a4c3e-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="a4c3e-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a4c3e-118">Value</span></span>|<span data-ttu-id="a4c3e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c3e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4c3e-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="a4c3e-120">genericUriParserOptions</span></span>|<span data-ttu-id="a4c3e-121">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-121">The parser options for this scheme.</span></span> <span data-ttu-id="a4c3e-122">Jedinou podporovanou hodnotou je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="a4c3e-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4c3e-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4c3e-123">Child Elements</span></span>  
 <span data-ttu-id="a4c3e-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="a4c3e-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4c3e-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4c3e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a4c3e-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4c3e-126">Element</span></span>|<span data-ttu-id="a4c3e-127">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c3e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4c3e-128">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="a4c3e-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="a4c3e-129">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4c3e-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4c3e-130">Remarks</span></span>  
 <span data-ttu-id="a4c3e-131">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třídy řídících zrušení procent kódovaný oddělovače cesty před provedením komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="a4c3e-132">To bylo implementováno jako vhodný mechanismus zabezpečení před útoky, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="a4c3e-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a4c3e-133">Pokud tento identifikátor URI bude předána do modulů zpracování procent kódování znaků správně, může vést provedených na serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a4c3e-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="a4c3e-134">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy prvního oddělovače cesty zrušení – řídicí sekvence a poté použije komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="a4c3e-135">Výsledek předáním škodlivý adresa URL výše <xref:System.Uri?displayProperty=nameWithType> konstruktor za následek následující identifikátor URI třídy:</span><span class="sxs-lookup"><span data-stu-id="a4c3e-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="a4c3e-136">Toto výchozí chování lze upravit a není zrušení-oddělovačů řídicí sekvence procenta zakódované cesty pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a4c3e-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a4c3e-137">Configuration Files</span></span>  
 <span data-ttu-id="a4c3e-138">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a4c3e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4c3e-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4c3e-139">Example</span></span>  
 <span data-ttu-id="a4c3e-140">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu není uvozovací znaky oddělovače procentuálně zakódovaný cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="a4c3e-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4c3e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4c3e-141">See Also</span></span>  
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
- <xref:System.Uri?displayProperty=nameWithType>  
- [<span data-ttu-id="a4c3e-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a4c3e-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
