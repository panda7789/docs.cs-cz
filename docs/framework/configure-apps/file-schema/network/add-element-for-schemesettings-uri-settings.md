---
title: <add> – element pro schemeSettings (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: efd52557ea8b617a39e685ff8ad69bab01322a7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699597"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="02bc9-102">@no__t – element > 0add pro schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="02bc9-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="02bc9-103">Přidá nastavení schématu pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="02bc9-103">Adds a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="02bc9-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="02bc9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="02bc9-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="02bc9-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="02bc9-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="02bc9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="02bc9-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="02bc9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02bc9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02bc9-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02bc9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02bc9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="02bc9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02bc9-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02bc9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="02bc9-111">Attributes</span></span>  
  
|<span data-ttu-id="02bc9-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="02bc9-112">Attribute</span></span>|<span data-ttu-id="02bc9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="02bc9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02bc9-114">name</span><span class="sxs-lookup"><span data-stu-id="02bc9-114">name</span></span>|<span data-ttu-id="02bc9-115">Název schématu, pro který platí toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="02bc9-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="02bc9-116">Jediné podporované hodnoty jsou Name = "http" a Name = "https".</span><span class="sxs-lookup"><span data-stu-id="02bc9-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="02bc9-117">{Název atributu} Přidělen</span><span class="sxs-lookup"><span data-stu-id="02bc9-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="02bc9-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="02bc9-118">Value</span></span>|<span data-ttu-id="02bc9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="02bc9-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02bc9-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="02bc9-120">genericUriParserOptions</span></span>|<span data-ttu-id="02bc9-121">Možnosti analyzátoru pro toto schéma.</span><span class="sxs-lookup"><span data-stu-id="02bc9-121">The parser options for this scheme.</span></span> <span data-ttu-id="02bc9-122">Jediná podporovaná hodnota je genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="02bc9-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02bc9-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02bc9-123">Child Elements</span></span>  
 <span data-ttu-id="02bc9-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="02bc9-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02bc9-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02bc9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="02bc9-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="02bc9-126">Element</span></span>|<span data-ttu-id="02bc9-127">Popis</span><span class="sxs-lookup"><span data-stu-id="02bc9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02bc9-128">@no__t – element > 1schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="02bc9-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="02bc9-129">Určuje, jak se bude pro konkrétní schémata analyzovat <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="02bc9-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02bc9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02bc9-130">Remarks</span></span>  
 <span data-ttu-id="02bc9-131">Ve výchozím nastavení třídy <xref:System.Uri?displayProperty=nameWithType> zruší řídicí oddělovače% zakódovaných cest před spuštěním komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="02bc9-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="02bc9-132">Tato akce byla implementována jako bezpečnostní mechanismus proti útokům, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="02bc9-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="02bc9-133">Pokud se tento identifikátor URI předává do modulů, které nezpracovávají procento nesprávně kódovaných znaků, může to mít za následek provedení následujícího příkazu serveru:</span><span class="sxs-lookup"><span data-stu-id="02bc9-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="02bc9-134">Z tohoto důvodu třída <xref:System.Uri?displayProperty=nameWithType> nejprve zruší oddělovače cest a pak použije kompresi cesty.</span><span class="sxs-lookup"><span data-stu-id="02bc9-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="02bc9-135">Výsledek předání škodlivých adres URL výše do konstruktoru třídy <xref:System.Uri?displayProperty=nameWithType> vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="02bc9-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="02bc9-136">Toto výchozí chování lze upravit tak, aby nezrušilo řídicí znaky v procentech kódovaných cest, a to pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="02bc9-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="02bc9-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="02bc9-137">Configuration Files</span></span>  
 <span data-ttu-id="02bc9-138">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="02bc9-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bc9-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="02bc9-139">Example</span></span>  
 <span data-ttu-id="02bc9-140">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu nekódovaných oddělovačů cest pro schéma HTTP v procentech.</span><span class="sxs-lookup"><span data-stu-id="02bc9-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02bc9-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02bc9-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="02bc9-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="02bc9-142">Network Settings Schema</span></span>](index.md)
