---
title: "&lt;schemeSettings&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4cf1d2013a51985f9d7772ac0ef86e5dbb120be9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltschemesettingsgt-element-uri-settings"></a><span data-ttu-id="69628-102">&lt;schemeSettings&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="69628-102">&lt;schemeSettings&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="69628-103">Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.</span><span class="sxs-lookup"><span data-stu-id="69628-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="69628-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="69628-104">\<configuration></span></span>  
<span data-ttu-id="69628-105">\<identifikátor URI ></span><span class="sxs-lookup"><span data-stu-id="69628-105">\<uri></span></span>  
<span data-ttu-id="69628-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="69628-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69628-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69628-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69628-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69628-108">Attributes and Elements</span></span>  
 <span data-ttu-id="69628-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69628-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69628-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="69628-110">Attributes</span></span>  
 <span data-ttu-id="69628-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="69628-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69628-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69628-112">Child Elements</span></span>  
  
|<span data-ttu-id="69628-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="69628-113">**Element**</span></span>|<span data-ttu-id="69628-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="69628-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69628-115">Přidat</span><span class="sxs-lookup"><span data-stu-id="69628-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="69628-116">Přidá nastavení schéma pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="69628-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="69628-117">Vymazat</span><span class="sxs-lookup"><span data-stu-id="69628-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="69628-118">Vymaže všechna existující nastavení schéma.</span><span class="sxs-lookup"><span data-stu-id="69628-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="69628-119">odebrat</span><span class="sxs-lookup"><span data-stu-id="69628-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="69628-120">Odebere schéma nastavení pro název schématu.</span><span class="sxs-lookup"><span data-stu-id="69628-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69628-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69628-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69628-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="69628-122">**Element**</span></span>|<span data-ttu-id="69628-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="69628-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69628-124">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="69628-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="69628-125">Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).</span><span class="sxs-lookup"><span data-stu-id="69628-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69628-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69628-126">Remarks</span></span>  
 <span data-ttu-id="69628-127">Ve výchozím nastavení <xref:System.Uri?displayProperty=nameWithType> třída zrušení – řídicí sekvence procent kódovaný cesta oddělovače před provedením cesta komprese.</span><span class="sxs-lookup"><span data-stu-id="69628-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="69628-128">Tato možnost byla implementovaná jako vhodný mechanismus zabezpečení před útoky takto:</span><span class="sxs-lookup"><span data-stu-id="69628-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="69628-129">Pokud tento identifikátor URI předána dolů moduly není zpracování procent kódování znaků správně, to může způsobit vykonáván serveru následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="69628-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="69628-130">Z tohoto důvodu <xref:System.Uri?displayProperty=nameWithType> třídy první oddělovače zrušení – řídicí sekvence cestu a poté použije cesta komprese.</span><span class="sxs-lookup"><span data-stu-id="69628-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="69628-131">Výsledek předáním škodlivý adresu URL výše na <xref:System.Uri?displayProperty=nameWithType> třídy konstruktor má za následek následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="69628-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="69628-132">Toto výchozí chování můžete upravit tak, aby není zrušení řídicí procenta kódovaného cesta oddělovače pomocí možnosti konfigurace schemeSettings pro konkrétní schéma.</span><span class="sxs-lookup"><span data-stu-id="69628-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="69628-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="69628-133">Configuration Files</span></span>  
 <span data-ttu-id="69628-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="69628-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69628-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="69628-135">Example</span></span>  
 <span data-ttu-id="69628-136">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu není uvozovací znaky oddělovače kódováním procent cestu pro schéma protokolu http.</span><span class="sxs-lookup"><span data-stu-id="69628-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="69628-137">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="69628-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="69628-138">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="69628-138">Namespace</span></span>|<span data-ttu-id="69628-139">Systém</span><span class="sxs-lookup"><span data-stu-id="69628-139">System</span></span>|  
|<span data-ttu-id="69628-140">Název schématu</span><span class="sxs-lookup"><span data-stu-id="69628-140">Schema Name</span></span>||  
|<span data-ttu-id="69628-141">Ověření souboru</span><span class="sxs-lookup"><span data-stu-id="69628-141">Validation File</span></span>||  
|<span data-ttu-id="69628-142">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="69628-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="69628-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="69628-143">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="69628-144">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="69628-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
