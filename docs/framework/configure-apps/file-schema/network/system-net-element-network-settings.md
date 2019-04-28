---
title: <system.Net> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: febea73ddbc45276f97835eb4af7ee0d0d68dda5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674334"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="845ca-102">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="845ca-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="845ca-103">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="845ca-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="845ca-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="845ca-104">\<configuration></span></span>  
<span data-ttu-id="845ca-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="845ca-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="845ca-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="845ca-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="845ca-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="845ca-107">Attributes and Elements</span></span>  
 <span data-ttu-id="845ca-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="845ca-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="845ca-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="845ca-109">Attributes</span></span>  
 <span data-ttu-id="845ca-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="845ca-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="845ca-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="845ca-111">Child Elements</span></span>  
  
|<span data-ttu-id="845ca-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="845ca-112">**Element**</span></span>|<span data-ttu-id="845ca-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="845ca-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="845ca-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="845ca-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="845ca-115">Určuje moduly používané k ověření požadavků na Internetu.</span><span class="sxs-lookup"><span data-stu-id="845ca-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="845ca-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="845ca-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="845ca-117">Určuje maximální počet připojení k hostiteli, který Internet.</span><span class="sxs-lookup"><span data-stu-id="845ca-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="845ca-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="845ca-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="845ca-119">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="845ca-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="845ca-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="845ca-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="845ca-121">Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="845ca-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="845ca-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="845ca-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="845ca-123">Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="845ca-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="845ca-124">settings</span><span class="sxs-lookup"><span data-stu-id="845ca-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="845ca-125">Nakonfiguruje možnosti základní sítě pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="845ca-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="845ca-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="845ca-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="845ca-127">Určuje moduly, které slouží k vyžádání informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="845ca-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="845ca-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="845ca-128">Parent Elements</span></span>  
  
|<span data-ttu-id="845ca-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="845ca-129">**Element**</span></span>|<span data-ttu-id="845ca-130">**Popis**</span><span class="sxs-lookup"><span data-stu-id="845ca-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="845ca-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="845ca-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="845ca-132">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="845ca-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="845ca-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="845ca-133">Remarks</span></span>  
 <span data-ttu-id="845ca-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="845ca-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="845ca-135">Nastavení konfigurace modulů ověřování, Správa připojení, nastavení pošty, proxy server a Internetu žádost moduly pro příjem informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="845ca-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="845ca-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="845ca-136">Example</span></span>  
 <span data-ttu-id="845ca-137">Následující příklad znázorňuje typickou konfiguraci používané <xref:System.Net> třídy.</span><span class="sxs-lookup"><span data-stu-id="845ca-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="845ca-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="845ca-138">See also</span></span>

- [<span data-ttu-id="845ca-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="845ca-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
