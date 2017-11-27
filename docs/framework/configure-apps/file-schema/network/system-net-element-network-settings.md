---
title: "&lt;system.Net&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d2eb903b8a84410aa08504c12e78a016d2368923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="7ca0d-102">&lt;system.Net&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7ca0d-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="7ca0d-103">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="7ca0d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7ca0d-104">\<configuration></span></span>  
<span data-ttu-id="7ca0d-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="7ca0d-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca0d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ca0d-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ca0d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ca0d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7ca0d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ca0d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ca0d-109">Attributes</span></span>  
 <span data-ttu-id="7ca0d-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="7ca0d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ca0d-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ca0d-111">Child Elements</span></span>  
  
|<span data-ttu-id="7ca0d-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="7ca0d-112">**Element**</span></span>|<span data-ttu-id="7ca0d-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7ca0d-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7ca0d-114">authenticationModules –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="7ca0d-115">Určuje moduly používané k ověřování žádostí o Internetu.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="7ca0d-116">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="7ca0d-117">Určuje maximální počet připojení Internetu hostitele.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="7ca0d-118">defaultProxy –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="7ca0d-119">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="7ca0d-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="7ca0d-120">mailSettings –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="7ca0d-121">Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="7ca0d-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="7ca0d-122">requestCaching –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="7ca0d-123">Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="7ca0d-124">nastavení</span><span class="sxs-lookup"><span data-stu-id="7ca0d-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="7ca0d-125">Nakonfiguruje základní síťové možnosti pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="7ca0d-126">webRequestModules –</span><span class="sxs-lookup"><span data-stu-id="7ca0d-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="7ca0d-127">Určuje moduly, které slouží k vyžádání informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ca0d-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ca0d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7ca0d-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="7ca0d-129">**Element**</span></span>|<span data-ttu-id="7ca0d-130">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7ca0d-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7ca0d-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7ca0d-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="7ca0d-132">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ca0d-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ca0d-133">Remarks</span></span>  
 <span data-ttu-id="7ca0d-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="7ca0d-135">Nastavení konfigurace ověřovací moduly, správu připojení, nastavení e-mailu, proxy serveru a moduly požadavek Internetu pro příjem informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ca0d-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ca0d-136">Example</span></span>  
 <span data-ttu-id="7ca0d-137">Následující příklad ukazuje obvyklá konfigurace používané <xref:System.Net> třídy.</span><span class="sxs-lookup"><span data-stu-id="7ca0d-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ca0d-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ca0d-138">See Also</span></span>  
 [<span data-ttu-id="7ca0d-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7ca0d-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
