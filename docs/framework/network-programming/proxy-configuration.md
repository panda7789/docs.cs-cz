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
ms.openlocfilehash: 1fbfe25b90e810ff96924a2341582ff3f5ee5e5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047361"
---
# <a name="proxy-configuration"></a><span data-ttu-id="03518-102">Konfigurace proxy serveru</span><span class="sxs-lookup"><span data-stu-id="03518-102">Proxy Configuration</span></span>
<span data-ttu-id="03518-103">Proxy server zpracovává požadavky klientů na prostředky.</span><span class="sxs-lookup"><span data-stu-id="03518-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="03518-104">Proxy server může vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je prostředek umístěn.</span><span class="sxs-lookup"><span data-stu-id="03518-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="03518-105">Servery proxy mohou zvýšit výkon sítě snížením počtu požadavků odeslaných na vzdálené servery.</span><span class="sxs-lookup"><span data-stu-id="03518-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="03518-106">Proxy servery lze také omezit přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="03518-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="03518-107">Adaptivní proxy servery</span><span class="sxs-lookup"><span data-stu-id="03518-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="03518-108">V rozhraní .NET Framework jsou proxy servery ve dvou variantách: adaptivní a statické.</span><span class="sxs-lookup"><span data-stu-id="03518-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="03518-109">Adaptivní proxy servery upravují nastavení při změně konfigurace sítě.</span><span class="sxs-lookup"><span data-stu-id="03518-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="03518-110">Pokud například uživatel přenosného počítače spustí telefonické připojení k síti, adaptivní proxy server tuto změnu rozpozná, zjišťuje a spouští nový konfigurační skript a odpovídajícím způsobem upravuje jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="03518-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="03518-111">Adaptivní proxy servery jsou konfigurovány pomocí konfiguračního skriptu (viz [Automatická detekce proxy serveru).](automatic-proxy-detection.md)</span><span class="sxs-lookup"><span data-stu-id="03518-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="03518-112">Skript generuje sadu aplikačních protokolů a proxy server pro každý protokol.</span><span class="sxs-lookup"><span data-stu-id="03518-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="03518-113">Změny v síťovém prostředí mohou vyžadovat, aby systém používal novou sadu proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="03518-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="03518-114">Pokud dojde k vypnutí síťového připojení nebo inicializováno nové síťové připojení, musí systém v novém prostředí zjistit příslušný zdroj konfiguračního skriptu a spustit nový skript.</span><span class="sxs-lookup"><span data-stu-id="03518-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="03518-115">Atribut [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvku `usesystemdefault` můžete použít v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="03518-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="03518-116">Atribut `usesystemdefault` určuje, zda má být nastavení statického serveru proxy (adresa proxy, seznam obejití a obejití v místním) přečteno z nastavení serveru proxy aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="03518-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="03518-117">Pokud je tato `true`hodnota nastavena na hodnotu , bude použito statické nastavení proxy serveru z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="03518-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="03518-118">Pokud je `false` tato hodnota nastavena nebo není nastavena, lze v konfiguraci zadat nastavení statického serveru proxy a přepsat nastavení serveru proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="03518-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="03518-119">Tato hodnota musí být `false` také nastavena na nebo není nastavena pro adaptivní proxy servery, které mají být povoleny.</span><span class="sxs-lookup"><span data-stu-id="03518-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="03518-120">Následující příklad ukazuje typickou adaptivní konfiguraci proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="03518-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="03518-121">Statické proxy servery</span><span class="sxs-lookup"><span data-stu-id="03518-121">Static Proxies</span></span>  
 <span data-ttu-id="03518-122">Statické proxy servery jsou obvykle konfigurovány explicitně aplikací nebo při vyvolání konfiguračního souboru aplikací nebo systémem.</span><span class="sxs-lookup"><span data-stu-id="03518-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="03518-123">Statické proxy servery jsou užitečné v sítích, ve kterých se topologie mění zřídka, například v stolním počítači připojeném k podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="03518-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="03518-124">Několik možností řídí fungování statického proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="03518-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="03518-125">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="03518-125">You can specify the following:</span></span>  
  
- <span data-ttu-id="03518-126">Adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="03518-126">The address of the proxy.</span></span>  
  
- <span data-ttu-id="03518-127">Určuje, zda má být proxy server vynechán pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="03518-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="03518-128">Určuje, zda má být proxy server vynechán pro sadu adres.</span><span class="sxs-lookup"><span data-stu-id="03518-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="03518-129">V následující tabulce jsou uvedeny možnosti konfigurace statického proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="03518-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="03518-130">Nastavení atributu, vlastnosti nebo konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="03518-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="03518-131">Popis</span><span class="sxs-lookup"><span data-stu-id="03518-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="03518-132">`proxyaddress` nebo <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="03518-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="03518-133">Adresa proxy použít.</span><span class="sxs-lookup"><span data-stu-id="03518-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="03518-134">`bypassonlocal` nebo <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="03518-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="03518-135">Určuje, zda je proxy server vynechán pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="03518-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="03518-136">`bypasslist` nebo <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="03518-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="03518-137">Popisuje pomocí regulárních výrazů sadu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="03518-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="03518-138">Určuje, zda má být nastavení statického serveru proxy (adresa proxy, seznam obejití a obejití v místním) čteno z nastavení serveru proxy aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="03518-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="03518-139">Pokud je tato `true`hodnota nastavena na hodnotu , bude použito statické nastavení proxy serveru z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="03518-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="03518-140">V rozhraní .NET Framework 2.0, `true`pokud je tato hodnota nastavena na , nejsou nastavení serveru proxy aplikace Internet Explorer přepsána jinými nastaveními serveru proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="03518-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="03518-141">V rozhraní .NET Framework 1.1 lze přepsáno nastavení mno žláby proxy aplikace Internet Explorer jinými nastaveními serveru proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="03518-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="03518-142">Pokud je `false` tato hodnota nastavena nebo není nastavena, lze v konfiguraci zadat nastavení statického serveru proxy a přepsat nastavení serveru proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="03518-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="03518-143">Tato hodnota musí být `false` také nastavena na nebo není nastavena pro adaptivní proxy servery, které mají být povoleny.</span><span class="sxs-lookup"><span data-stu-id="03518-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="03518-144">Následující příklad ukazuje typickou statickou konfiguraci proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="03518-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03518-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="03518-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="03518-146">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="03518-146">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
