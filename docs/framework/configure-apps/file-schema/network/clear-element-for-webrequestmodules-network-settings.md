---
title: '&lt;Vymazat&gt; – Element pro webRequestModules (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: ccb9a19d4e6d79a84123014746b659a7168b2158
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607001"
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="798e0-102">&lt;Vymazat&gt; – Element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="798e0-102">&lt;clear&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="798e0-103">Odebere všechny registrované moduly webové žádosti z aplikace.</span><span class="sxs-lookup"><span data-stu-id="798e0-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="798e0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="798e0-104">\<configuration></span></span>  
<span data-ttu-id="798e0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="798e0-105">\<system.net></span></span>  
<span data-ttu-id="798e0-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="798e0-106">\<webRequestModules></span></span>  
<span data-ttu-id="798e0-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="798e0-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798e0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="798e0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="798e0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="798e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="798e0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="798e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="798e0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="798e0-111">Attributes</span></span>  
 <span data-ttu-id="798e0-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="798e0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="798e0-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="798e0-113">Child Elements</span></span>  
 <span data-ttu-id="798e0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="798e0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="798e0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="798e0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="798e0-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="798e0-116">**Element**</span></span>|<span data-ttu-id="798e0-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="798e0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="798e0-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="798e0-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="798e0-119">Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="798e0-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="798e0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="798e0-120">Remarks</span></span>  
 <span data-ttu-id="798e0-121">`clear` Element odebere všechny registrované webových požadavek modulů, které byly dříve definovány v konfiguračním souboru nebo na vyšší úrovni v hierarchii configuration.</span><span class="sxs-lookup"><span data-stu-id="798e0-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="798e0-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="798e0-122">Configuration Files</span></span>  
 <span data-ttu-id="798e0-123">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="798e0-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="798e0-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="798e0-124">Example</span></span>  
 <span data-ttu-id="798e0-125">V následujícím příkladu vymaže všechny moduly webové žádosti a pak zaregistruje webový modul požadavku pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="798e0-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="798e0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="798e0-126">See also</span></span>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="798e0-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="798e0-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
