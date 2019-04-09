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
ms.openlocfilehash: c6b3808a2d73070cc07b31eb0fca7ca9d6af8cdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200542"
---
# <a name="proxy-configuration"></a><span data-ttu-id="e6330-102">Konfigurace proxy serveru</span><span class="sxs-lookup"><span data-stu-id="e6330-102">Proxy Configuration</span></span>
<span data-ttu-id="e6330-103">Proxy server zpracovává požadavky klientů na prostředky.</span><span class="sxs-lookup"><span data-stu-id="e6330-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="e6330-104">Proxy server můžete vrátit požadovaný prostředek uloženou v mezipaměti nebo předání požadavku na server, ve kterém je prostředek umístěn.</span><span class="sxs-lookup"><span data-stu-id="e6330-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="e6330-105">Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="e6330-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="e6330-106">Proxy servery lze také omezit přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e6330-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="e6330-107">Adaptivní proxy servery</span><span class="sxs-lookup"><span data-stu-id="e6330-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="e6330-108">V rozhraní .NET Framework, existují proxy servery ve dvou variantách: Adaptivní a statická.</span><span class="sxs-lookup"><span data-stu-id="e6330-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="e6330-109">Adaptivní proxy upravit jejich nastavení, když se změní konfiguraci sítě.</span><span class="sxs-lookup"><span data-stu-id="e6330-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="e6330-110">Například pokud uživatel přenosný počítač spustí telefonického připojení k síti, adaptivní proxy by rozpozná tuto změnu, zjišťování a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e6330-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="e6330-111">Adaptivní proxy servery jsou nakonfigurovány pomocí konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="e6330-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="e6330-112">Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.</span><span class="sxs-lookup"><span data-stu-id="e6330-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="e6330-113">Změny v prostředí sítě může vyžadovat, že systém použít novou sadu proxy servery.</span><span class="sxs-lookup"><span data-stu-id="e6330-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="e6330-114">Pokud připojení k síti ocitne mimo provoz nebo nového připojení k síti je inicializována, systém musí vyhledat příslušný zdrojový konfigurační skript v novém prostředí a spusťte nový skript.</span><span class="sxs-lookup"><span data-stu-id="e6330-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="e6330-115">Můžete použít `usesystemdefault` atribut [ `<proxy>` ](../configure-apps/file-schema/network/proxy-element-network-settings.md) element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e6330-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="e6330-116">`usesystemdefault` Atribut ovládací prvky, jestli byste si měli přečíst nastavení statické proxy serveru (adresa proxy serveru, seznam obcházení a obejít v místní) z nastavení proxy aplikace Internet Explorer pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="e6330-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="e6330-117">Pokud tato hodnota nastavená na `true`, použije se nastavení statické proxy serveru z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e6330-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="e6330-118">Pokud je tato hodnota `false` nebo není nastavený, nastavení statické proxy serveru se dá nastavit v konfiguraci a přepíše nastavení proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e6330-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="e6330-119">Tato hodnota musí být také nastavena `false` nebo nebyla nastavena adaptivní proxy, aby byla povolená.</span><span class="sxs-lookup"><span data-stu-id="e6330-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="e6330-120">Následující příklad ukazuje konfiguraci typické adaptivní proxy.</span><span class="sxs-lookup"><span data-stu-id="e6330-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="e6330-121">Statické proxy servery</span><span class="sxs-lookup"><span data-stu-id="e6330-121">Static Proxies</span></span>  
 <span data-ttu-id="e6330-122">Statické proxy servery jsou obvykle explicitně nakonfigurovat aplikace, nebo při vyvolání konfigurační soubor aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="e6330-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="e6330-123">Statické proxy jsou užitečné v sítích, ve kterých topologie mění zřídka, jako je například stolní počítač připojený k podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="e6330-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="e6330-124">Několik možností, jak řídit, jak funguje statické proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e6330-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="e6330-125">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="e6330-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="e6330-126">Adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e6330-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="e6330-127">Určuje, zda by měl obejít proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="e6330-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="e6330-128">Určuje, zda by měl obejdou pro sadu adres proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e6330-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="e6330-129">V následující tabulce jsou uvedeny možnosti konfigurace pro statické proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e6330-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="e6330-130">Nastavení konfigurace, vlastnosti nebo atributu souboru</span><span class="sxs-lookup"><span data-stu-id="e6330-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="e6330-131">Popis</span><span class="sxs-lookup"><span data-stu-id="e6330-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` <span data-ttu-id="e6330-132">or</span><span class="sxs-lookup"><span data-stu-id="e6330-132">or</span></span> <xref:System.Net.WebProxy.Address>|<span data-ttu-id="e6330-133">Adresa proxy serveru používat.</span><span class="sxs-lookup"><span data-stu-id="e6330-133">The address of the proxy to use.</span></span>|  
|`bypassonlocal` <span data-ttu-id="e6330-134">or</span><span class="sxs-lookup"><span data-stu-id="e6330-134">or</span></span> <xref:System.Net.WebProxy.BypassProxyOnLocal>|<span data-ttu-id="e6330-135">Určuje, zda je pro místní adresy obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="e6330-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|`bypasslist` <span data-ttu-id="e6330-136">or</span><span class="sxs-lookup"><span data-stu-id="e6330-136">or</span></span> <xref:System.Net.WebProxy.BypassArrayList>|<span data-ttu-id="e6330-137">Popisuje sadu adresy, které obcházení proxy serveru pomocí regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="e6330-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="e6330-138">Určuje, zda nastavení statické proxy serveru (adresa proxy serveru, seznam obcházení a obejít na místních) byste si měli přečíst z nastavení proxy aplikace Internet Explorer pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="e6330-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="e6330-139">Pokud tato hodnota nastavená na `true`, pak budou použita nastavení statické proxy z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e6330-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="e6330-140">V rozhraní .NET Framework 2.0, pokud je tato hodnota nastavena na `true`, nastavení proxy aplikace Internet Explorer nejsou přepsána další nastavení proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e6330-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="e6330-141">V rozhraní .NET Framework 1.1 mohou být přepsány nastavení proxy aplikace Internet Explorer Další nastavení proxy v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e6330-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="e6330-142">Pokud je tato hodnota `false` nebo není nastavený, potom nastavení statické proxy serveru se dá nastavit v konfiguraci a přepíše nastavení proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e6330-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="e6330-143">Tato hodnota musí být také nastavena `false` nebo nebyla nastavena adaptivní proxy, aby byla povolená.</span><span class="sxs-lookup"><span data-stu-id="e6330-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="e6330-144">Následující příklad ukazuje konfiguraci typické statické proxy.</span><span class="sxs-lookup"><span data-stu-id="e6330-144">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6330-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6330-145">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="e6330-146">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="e6330-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
