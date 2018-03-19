---
title: "&lt;Odebrat&gt; Element pro webRequestModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 391e5f2a7d9d8076ba9e9a3057e3d8899e2ce672
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="fa5cc-102">&lt;Odebrat&gt; Element pro webRequestModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fa5cc-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="fa5cc-103">Odebere vlastní modul žádost webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="fa5cc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fa5cc-104">\<configuration></span></span>  
<span data-ttu-id="fa5cc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fa5cc-105">\<system.net></span></span>  
<span data-ttu-id="fa5cc-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="fa5cc-106">\<webRequestModules></span></span>  
<span data-ttu-id="fa5cc-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="fa5cc-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa5cc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa5cc-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa5cc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa5cc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fa5cc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa5cc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa5cc-111">Attributes</span></span>  
  
|<span data-ttu-id="fa5cc-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="fa5cc-112">**Attribute**</span></span>|<span data-ttu-id="fa5cc-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="fa5cc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="fa5cc-114">Předpony identifikátoru URI pro tento webový modul požadavek zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa5cc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fa5cc-115">Child Elements</span></span>  
 <span data-ttu-id="fa5cc-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="fa5cc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa5cc-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fa5cc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fa5cc-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="fa5cc-118">**Element**</span></span>|<span data-ttu-id="fa5cc-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="fa5cc-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fa5cc-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="fa5cc-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="fa5cc-121">Určuje moduly sloužící k požadavku na informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa5cc-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa5cc-122">Remarks</span></span>  
 <span data-ttu-id="fa5cc-123">`remove` Element odebere registrovaný modul webové žádosti pro zadané předpony identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="fa5cc-124">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "http", nebo "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="fa5cc-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fa5cc-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="fa5cc-125">Configuration Files</span></span>  
 <span data-ttu-id="fa5cc-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fa5cc-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa5cc-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa5cc-127">Example</span></span>  
 <span data-ttu-id="fa5cc-128">Následující příklad odebere existující webový modul požadavku pro protokol HTTP a pak zaregistruje nový modul vlastní webové žádosti pro požadavky HTTP na www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="fa5cc-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa5cc-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa5cc-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="fa5cc-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fa5cc-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
