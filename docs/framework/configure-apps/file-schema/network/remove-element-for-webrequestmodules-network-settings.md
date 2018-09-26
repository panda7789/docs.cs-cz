---
title: '&lt;Odebrat&gt; – Element pro webRequestModules (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d0da0fd2edae4687ea80b4a23cc82a25ead9cb7b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112202"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="03376-102">&lt;Odebrat&gt; – Element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="03376-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="03376-103">Vlastní modul požadavku webového odstraní z aplikace.</span><span class="sxs-lookup"><span data-stu-id="03376-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="03376-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="03376-104">\<configuration></span></span>  
<span data-ttu-id="03376-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="03376-105">\<system.net></span></span>  
<span data-ttu-id="03376-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="03376-106">\<webRequestModules></span></span>  
<span data-ttu-id="03376-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="03376-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03376-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03376-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03376-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03376-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03376-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03376-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03376-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="03376-111">Attributes</span></span>  
  
|<span data-ttu-id="03376-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="03376-112">**Attribute**</span></span>|<span data-ttu-id="03376-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03376-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="03376-114">Předponu identifikátoru URI pro žádosti zpracovat tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="03376-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03376-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03376-115">Child Elements</span></span>  
 <span data-ttu-id="03376-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="03376-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03376-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03376-117">Parent Elements</span></span>  
  
|<span data-ttu-id="03376-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="03376-118">**Element**</span></span>|<span data-ttu-id="03376-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03376-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="03376-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="03376-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="03376-121">Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="03376-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03376-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03376-122">Remarks</span></span>  
 <span data-ttu-id="03376-123">`remove` Element odebere registrovaný modul požadavku webového pro zadaný identifikátor URI předponu.</span><span class="sxs-lookup"><span data-stu-id="03376-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="03376-124">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "http", nebo "`http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="03376-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "`http://www.contoso.com` ".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03376-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="03376-125">Configuration Files</span></span>  
 <span data-ttu-id="03376-126">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="03376-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03376-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="03376-127">Example</span></span>  
 <span data-ttu-id="03376-128">Následující příklad odebere existující webový modul požadavku pro protokol HTTP a pak zaregistruje nový modul vlastní webové žádosti pro požadavky HTTP na www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="03376-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03376-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="03376-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="03376-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="03376-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
