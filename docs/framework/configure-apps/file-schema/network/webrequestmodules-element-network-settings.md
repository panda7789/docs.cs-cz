---
title: '&lt;webRequestModules –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7454099d8af0f2d656296be55677c648cc0c36c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742689"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="94eaf-102">&lt;webRequestModules –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="94eaf-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="94eaf-103">Určuje moduly sloužící k požadavku na informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="94eaf-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="94eaf-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="94eaf-104">\<configuration></span></span>  
<span data-ttu-id="94eaf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="94eaf-105">\<system.net></span></span>  
<span data-ttu-id="94eaf-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="94eaf-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94eaf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94eaf-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94eaf-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94eaf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="94eaf-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94eaf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94eaf-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="94eaf-110">Attributes</span></span>  
 <span data-ttu-id="94eaf-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="94eaf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94eaf-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94eaf-112">Child Elements</span></span>  
  
|<span data-ttu-id="94eaf-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="94eaf-113">**Element**</span></span>|<span data-ttu-id="94eaf-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="94eaf-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94eaf-115">add</span><span class="sxs-lookup"><span data-stu-id="94eaf-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94eaf-116">Přidá vlastní modul žádost webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="94eaf-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="94eaf-117">Zrušte zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="94eaf-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94eaf-118">Odebere všechny registrované moduly žádost webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="94eaf-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="94eaf-119">remove</span><span class="sxs-lookup"><span data-stu-id="94eaf-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="94eaf-120">Odebere vlastní modul žádost webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="94eaf-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94eaf-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94eaf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="94eaf-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="94eaf-122">**Element**</span></span>|<span data-ttu-id="94eaf-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="94eaf-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="94eaf-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="94eaf-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="94eaf-125">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="94eaf-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94eaf-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94eaf-126">Remarks</span></span>  
 <span data-ttu-id="94eaf-127">`webRequestModules` Element zaregistruje následníků <xref:System.Net.WebRequest> třídy pro zpracování požadavků na informace na síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="94eaf-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="94eaf-128">Musí implementovat moduly webové žádosti <xref:System.Net.IWebRequestCreate> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="94eaf-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="94eaf-129">Rozhraní .NET Framework obsahuje webové žádosti modulů pro identifikátory URI, který začíná http://, https:// a file://.</span><span class="sxs-lookup"><span data-stu-id="94eaf-129">The .NET Framework includes Web request modules for URIs that begin with http://, https://, and file://.</span></span> <span data-ttu-id="94eaf-130">Můžete přepsat výchozí moduly pouze tak, že zaregistrujete vlastní modul v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="94eaf-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="94eaf-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="94eaf-131">Configuration Files</span></span>  
 <span data-ttu-id="94eaf-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="94eaf-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94eaf-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="94eaf-133">Example</span></span>  
 <span data-ttu-id="94eaf-134">Následující příklad zaregistruje výchozí modulu protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="94eaf-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="94eaf-135">Měli byste nahradit hodnoty verze a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="94eaf-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94eaf-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="94eaf-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="94eaf-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="94eaf-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
