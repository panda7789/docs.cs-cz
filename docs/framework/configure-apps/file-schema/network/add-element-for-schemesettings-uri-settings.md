---
title: '&lt;Přidat&gt; Element pro schemeSettings (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd8033b07b29066633e5217645f3ee06937179da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="0bb5b-102">&lt;Přidat&gt; Element pro schemeSettings (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="0bb5b-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="0bb5b-103">Přidá nastavení schéma pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="0bb5b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0bb5b-104">\<configuration></span></span>  
<span data-ttu-id="0bb5b-105">\<identifikátor URI ></span><span class="sxs-lookup"><span data-stu-id="0bb5b-105">\<uri></span></span>  
<span data-ttu-id="0bb5b-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="0bb5b-106">\<schemeSettings></span></span>  
<span data-ttu-id="0bb5b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0bb5b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb5b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bb5b-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bb5b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0bb5b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0bb5b-110">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0bb5b-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bb5b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0bb5b-111">Attributes</span></span>  
  
|<span data-ttu-id="0bb5b-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="0bb5b-112">Attribute</span></span>|<span data-ttu-id="0bb5b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0bb5b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bb5b-114">name</span><span class="sxs-lookup"><span data-stu-id="0bb5b-114">name</span></span>|<span data-ttu-id="0bb5b-115">Název schématu, pro kterou platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="0bb5b-116">Podporované jsou pouze hodnoty name = "http" a name = "https".</span><span class="sxs-lookup"><span data-stu-id="0bb5b-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="0bb5b-117">{Atribut name} Atribut</span><span class="sxs-lookup"><span data-stu-id="0bb5b-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="0bb5b-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0bb5b-118">Value</span></span>|<span data-ttu-id="0bb5b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0bb5b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0bb5b-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="0bb5b-120">genericUriParserOptions</span></span>|<span data-ttu-id="0bb5b-121">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-121">The parser options for this scheme.</span></span> <span data-ttu-id="0bb5b-122">Jedinou podporovanou hodnotou je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="0bb5b-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bb5b-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0bb5b-123">Child Elements</span></span>  
 <span data-ttu-id="0bb5b-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="0bb5b-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bb5b-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0bb5b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0bb5b-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="0bb5b-126">Element</span></span>|<span data-ttu-id="0bb5b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="0bb5b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bb5b-128">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="0bb5b-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="0bb5b-129">Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb5b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bb5b-130">Remarks</span></span>  
 <span data-ttu-id="0bb5b-131">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třída zrušení – řídicí sekvence procent kódovaný cesta oddělovače před provedením cesta komprese.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0bb5b-132">Tato možnost byla implementovaná jako vhodný mechanismus zabezpečení před útoky takto:</span><span class="sxs-lookup"><span data-stu-id="0bb5b-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0bb5b-133">Pokud tento identifikátor URI předána dolů moduly není zpracování procent kódování znaků správně, to může způsobit vykonáván serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0bb5b-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0bb5b-134">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy první oddělovače zrušení – řídicí sekvence cestu a poté použije cesta komprese.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0bb5b-135">Výsledek předáním škodlivý adresu URL výše na <xref:System.Uri?displayProperty=nameWithType> třídy konstruktor má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="0bb5b-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0bb5b-136">Toto výchozí chování můžete upravit tak, aby není zrušení řídicí procenta kódovaného cesta oddělovače pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0bb5b-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0bb5b-137">Configuration Files</span></span>  
 <span data-ttu-id="0bb5b-138">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0bb5b-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb5b-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bb5b-139">Example</span></span>  
 <span data-ttu-id="0bb5b-140">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu není uvozovací znaky oddělovače kódováním procent cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="0bb5b-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bb5b-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bb5b-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="0bb5b-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0bb5b-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
