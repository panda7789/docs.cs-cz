---
title: "&lt;Odebrat&gt; Element pro webRequestModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
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
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 43f0d30f8c18c4755f31d0c851c773207bc15b78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="c5b39-102">&lt;Odebrat&gt; Element pro webRequestModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c5b39-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="c5b39-103">Odebere vlastní modul žádost webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5b39-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="c5b39-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c5b39-104">\<configuration></span></span>  
<span data-ttu-id="c5b39-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="c5b39-105">\<system.net></span></span>  
<span data-ttu-id="c5b39-106">\<webRequestModules – ></span><span class="sxs-lookup"><span data-stu-id="c5b39-106">\<webRequestModules></span></span>  
<span data-ttu-id="c5b39-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="c5b39-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b39-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5b39-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5b39-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5b39-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5b39-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5b39-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5b39-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5b39-111">Attributes</span></span>  
  
|<span data-ttu-id="c5b39-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="c5b39-112">**Attribute**</span></span>|<span data-ttu-id="c5b39-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c5b39-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="c5b39-114">Předpony identifikátoru URI pro tento webový modul požadavek zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="c5b39-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5b39-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5b39-115">Child Elements</span></span>  
 <span data-ttu-id="c5b39-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="c5b39-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5b39-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5b39-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c5b39-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="c5b39-118">**Element**</span></span>|<span data-ttu-id="c5b39-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c5b39-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c5b39-120">webRequestModules –</span><span class="sxs-lookup"><span data-stu-id="c5b39-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="c5b39-121">Určuje moduly sloužící k požadavku na informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="c5b39-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5b39-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5b39-122">Remarks</span></span>  
 <span data-ttu-id="c5b39-123">`remove` Element odebere registrovaný modul webové žádosti pro zadané předpony identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="c5b39-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="c5b39-124">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "http" nebo "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="c5b39-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c5b39-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c5b39-125">Configuration Files</span></span>  
 <span data-ttu-id="c5b39-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c5b39-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b39-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5b39-127">Example</span></span>  
 <span data-ttu-id="c5b39-128">Následující příklad odebere existující webový modul požadavku pro protokol HTTP a pak zaregistruje nový modul vlastní webové žádosti pro požadavky HTTP na www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c5b39-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5b39-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5b39-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="c5b39-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c5b39-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
