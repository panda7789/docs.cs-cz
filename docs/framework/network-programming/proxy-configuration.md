---
title: Konfigurace proxy serveru
description: Přečtěte si, jak nakonfigurovat adaptivní a statické proxy servery. Konfigurace proxy řídí způsob, jakým proxy server zpracovává požadavky klienta na prostředky.
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
ms.openlocfilehash: d1c8b69223ab470d505d9f8007bc01b29fdc66b8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502207"
---
# <a name="proxy-configuration"></a><span data-ttu-id="b75ce-104">Konfigurace proxy serveru</span><span class="sxs-lookup"><span data-stu-id="b75ce-104">Proxy Configuration</span></span>
<span data-ttu-id="b75ce-105">Proxy server zpracovává požadavky klienta na prostředky.</span><span class="sxs-lookup"><span data-stu-id="b75ce-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="b75ce-106">Proxy může vrátit požadovaný prostředek ze své mezipaměti nebo odeslat požadavek na server, kde se nachází prostředek.</span><span class="sxs-lookup"><span data-stu-id="b75ce-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="b75ce-107">Proxy mohou zlepšit výkon sítě snížením počtu požadavků odesílaných na vzdálené servery.</span><span class="sxs-lookup"><span data-stu-id="b75ce-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="b75ce-108">Proxy servery je také možné použít k omezení přístupu k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="b75ce-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="b75ce-109">Adaptivní proxy</span><span class="sxs-lookup"><span data-stu-id="b75ce-109">Adaptive Proxies</span></span>  
 <span data-ttu-id="b75ce-110">V .NET Framework jsou proxy servery součástí dvou variant: adaptivní a statické.</span><span class="sxs-lookup"><span data-stu-id="b75ce-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="b75ce-111">Adaptivní proxy servery upravují jejich nastavení při změně konfigurace sítě.</span><span class="sxs-lookup"><span data-stu-id="b75ce-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="b75ce-112">Pokud třeba uživatel přenosného počítače spustí telefonické připojení k síti, adaptivní proxy tuto změnu rozpozná, zjistí a spustí nový konfigurační skript a patřičně upraví jeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="b75ce-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="b75ce-113">Adaptivní proxy servery jsou nakonfigurovány pomocí konfiguračního skriptu (viz [Automatická detekce proxy serveru](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="b75ce-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="b75ce-114">Skript vygeneruje sadu aplikačních protokolů a proxy pro každý protokol.</span><span class="sxs-lookup"><span data-stu-id="b75ce-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="b75ce-115">Změny v síťovém prostředí můžou vyžadovat, aby systém používal novou sadu proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="b75ce-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="b75ce-116">Pokud dojde k výpadku síťového připojení nebo k inicializaci nového síťového připojení, musí systém zjistit příslušný zdroj konfiguračního skriptu v novém prostředí a spustit nový skript.</span><span class="sxs-lookup"><span data-stu-id="b75ce-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="b75ce-117">Můžete použít `usesystemdefault` atribut [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvku v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="b75ce-118">`usesystemdefault`Atribut určuje, zda má být nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti) čteno z nastavení proxy serveru aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="b75ce-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="b75ce-119">Pokud je tato hodnota nastavená na `true` , použijí se nastavení statického proxy serveru z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="b75ce-120">Pokud tato hodnota není `false` nastavená, může být nastavení statického proxy serveru zadáno v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b75ce-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="b75ce-121">Tato hodnota musí být také nastavená na `false` nebo není nastavená pro adaptivní proxy servery, které se mají povolit.</span><span class="sxs-lookup"><span data-stu-id="b75ce-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="b75ce-122">Následující příklad ukazuje typickou konfiguraci adaptivního proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="b75ce-123">Statické proxy servery</span><span class="sxs-lookup"><span data-stu-id="b75ce-123">Static Proxies</span></span>  
 <span data-ttu-id="b75ce-124">Statické proxy servery jsou obvykle konfigurovány explicitně aplikací nebo při vyvolání konfiguračního souboru aplikací nebo systémem.</span><span class="sxs-lookup"><span data-stu-id="b75ce-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="b75ce-125">Statické proxy servery jsou užitečné v sítích, ve kterých se topologie mění zřídka, jako je stolní počítač připojený k podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="b75ce-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="b75ce-126">Několik možností řídí fungování statického proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="b75ce-127">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="b75ce-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="b75ce-128">Adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="b75ce-129">Určuje, zda má být proxy server pro místní adresy obejít.</span><span class="sxs-lookup"><span data-stu-id="b75ce-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="b75ce-130">Určuje, zda má být proxy server pro sadu adres vynechán.</span><span class="sxs-lookup"><span data-stu-id="b75ce-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="b75ce-131">V následující tabulce jsou uvedeny možnosti konfigurace pro statický proxy server.</span><span class="sxs-lookup"><span data-stu-id="b75ce-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="b75ce-132">Nastavení atributu, vlastnosti nebo konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b75ce-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="b75ce-133">Description</span><span class="sxs-lookup"><span data-stu-id="b75ce-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="b75ce-134">`proxyaddress` nebo <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="b75ce-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="b75ce-135">Adresa proxy serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="b75ce-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="b75ce-136">`bypassonlocal` nebo <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="b75ce-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="b75ce-137">Určuje, jestli se proxy server pro místní adresy nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b75ce-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="b75ce-138">`bypasslist` nebo <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="b75ce-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="b75ce-139">Popisuje, s regulárními výrazy, sada adres, které obcházejí proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="b75ce-140">Určuje, jestli se má pro uživatele přečíst nastavení statického proxy serveru (adresa proxy serveru, seznam obcházení a obejití v místní síti).</span><span class="sxs-lookup"><span data-stu-id="b75ce-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="b75ce-141">Pokud je tato hodnota nastavená na `true` , použijí se nastavení statického proxy serveru z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="b75ce-142">V .NET Framework 2,0 Pokud je tato hodnota nastavena na `true` , nastavení proxy serveru aplikace Internet Explorer nejsou přepsána jinými nastaveními proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="b75ce-143">V .NET Framework 1,1 lze nastavení proxy serveru aplikace Internet Explorer přepsat jinými nastaveními proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="b75ce-144">Pokud tato hodnota není `false` nastavená, můžete v konfiguraci zadat nastavení statického proxy serveru a přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b75ce-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="b75ce-145">Tato hodnota musí být také nastavená na `false` nebo není nastavená pro adaptivní proxy servery, které se mají povolit.</span><span class="sxs-lookup"><span data-stu-id="b75ce-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="b75ce-146">Následující příklad ukazuje typickou konfiguraci statického proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b75ce-146">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b75ce-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b75ce-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="b75ce-148">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="b75ce-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
