---
title: Konfigurace proxy serveru
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6cf25d3d7dcde963f06729794716b75dffdb64ae
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207362"
---
# <a name="proxy-configuration"></a><span data-ttu-id="9da13-102">Konfigurace proxy serveru</span><span class="sxs-lookup"><span data-stu-id="9da13-102">Proxy Configuration</span></span>
<span data-ttu-id="9da13-103">Proxy server zpracovává požadavky na klienta pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="9da13-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="9da13-104">Proxy server můžete vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je umístěn daný prostředek.</span><span class="sxs-lookup"><span data-stu-id="9da13-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="9da13-105">Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="9da13-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="9da13-106">Proxy lze také omezit přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="9da13-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="9da13-107">Adaptivní proxy</span><span class="sxs-lookup"><span data-stu-id="9da13-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="9da13-108">V rozhraní .NET Framework, proxy servery existují ve dvou variantách: Adaptivní a statické.</span><span class="sxs-lookup"><span data-stu-id="9da13-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="9da13-109">Adaptivní proxy úprava jejich nastavení, když se změny v konfiguraci sítě.</span><span class="sxs-lookup"><span data-stu-id="9da13-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="9da13-110">Například pokud uživatel přenosný počítač spustí telefonické připojení sítě, adaptivní proxy by rozpoznat tuto změnu, zjistit a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9da13-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="9da13-111">Adaptivní proxy se nakonfiguroval konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="9da13-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="9da13-112">Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.</span><span class="sxs-lookup"><span data-stu-id="9da13-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="9da13-113">Změny v prostředí sítě můžou vyžadovat, že systém použít novou sadu serverů proxy.</span><span class="sxs-lookup"><span data-stu-id="9da13-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="9da13-114">Pokud připojení k síti ocitne mimo provoz nebo je inicializován nového připojení k síti, systém musí vyhledat příslušný zdroj konfigurační skript v nové verzi prostředí a spusťte nový skript.</span><span class="sxs-lookup"><span data-stu-id="9da13-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="9da13-115">Můžete použít `usesystemdefault` atribut [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9da13-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="9da13-116">`usesystemdefault` Atribut ovládací prvky, zda nastavení statické proxy (adresa proxy serveru, seznam obcházení a nepoužívat v místní) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9da13-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="9da13-117">Pokud tato hodnota nastavena na `true`, použije se nastavení statické proxy serveru z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="9da13-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="9da13-118">Pokud je tato hodnota `false` nebo není nastavený, nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9da13-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="9da13-119">Tato hodnota musí být také nastaven na `false` nebo není nastaveno adaptivní proxy, aby byl povolen.</span><span class="sxs-lookup"><span data-stu-id="9da13-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="9da13-120">Následující příklad ukazuje konfiguraci typické adaptivní proxy.</span><span class="sxs-lookup"><span data-stu-id="9da13-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="9da13-121">Statické proxy</span><span class="sxs-lookup"><span data-stu-id="9da13-121">Static Proxies</span></span>  
 <span data-ttu-id="9da13-122">Statické proxy jsou obvykle explicitně nakonfigurovaná aplikací, nebo při vyvolání konfiguračního souboru aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="9da13-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="9da13-123">Statické proxy jsou užitečné v sítích, ve kterých změny topologie zřídka, jako je například stolní počítač připojený k podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="9da13-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="9da13-124">Několik možností, jak řídit, jak funguje statické proxy server.</span><span class="sxs-lookup"><span data-stu-id="9da13-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="9da13-125">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="9da13-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="9da13-126">Adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="9da13-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="9da13-127">Jestli by měl obejít proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="9da13-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="9da13-128">Jestli má u sadu adres název proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="9da13-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="9da13-129">V následující tabulce jsou uvedeny možnosti konfigurace pro statické proxy server.</span><span class="sxs-lookup"><span data-stu-id="9da13-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="9da13-130">Atribut, vlastnost nebo konfigurace nastavení souboru</span><span class="sxs-lookup"><span data-stu-id="9da13-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="9da13-131">Popis</span><span class="sxs-lookup"><span data-stu-id="9da13-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="9da13-132">`proxyaddress` Nebo <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="9da13-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="9da13-133">Adresa proxy serveru používat.</span><span class="sxs-lookup"><span data-stu-id="9da13-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="9da13-134">`bypassonlocal` Nebo <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="9da13-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="9da13-135">Určuje, zda je vynechá proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="9da13-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="9da13-136">`bypasslist` Nebo <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="9da13-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="9da13-137">Popisuje sadu adres, které používat proxy server s použitím regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="9da13-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="9da13-138">Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9da13-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="9da13-139">Pokud tato hodnota nastavena na `true`, pak se použije nastavení statické proxy serveru z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="9da13-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="9da13-140">V rozhraní .NET Framework 2.0, pokud je tato hodnota nastavena na `true`, ostatní nastavení proxy serveru v konfiguračním souboru nejsou přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9da13-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="9da13-141">V rozhraní .NET Framework 1.1 je možné přepsat nastavení proxy serveru aplikace Internet Explorer Další nastavení proxy serveru v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9da13-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="9da13-142">Pokud je tato hodnota `false` nebo není nastavený, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9da13-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="9da13-143">Tato hodnota musí být také nastaven na `false` nebo není nastaveno adaptivní proxy, aby byl povolen.</span><span class="sxs-lookup"><span data-stu-id="9da13-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="9da13-144">Následující příklad ukazuje konfiguraci typické statické proxy.</span><span class="sxs-lookup"><span data-stu-id="9da13-144">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9da13-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="9da13-145">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="9da13-146">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="9da13-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
