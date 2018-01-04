---
title: Konfigurace proxy serveru
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a><span data-ttu-id="eaf42-102">Konfigurace proxy serveru</span><span class="sxs-lookup"><span data-stu-id="eaf42-102">Proxy Configuration</span></span>
<span data-ttu-id="eaf42-103">Proxy server zpracovává požadavky na klienta pro prostředky.</span><span class="sxs-lookup"><span data-stu-id="eaf42-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="eaf42-104">Proxy server můžete vrátit požadovaný prostředek ze své mezipaměti nebo předat požadavek na server, kde je umístěn daný prostředek.</span><span class="sxs-lookup"><span data-stu-id="eaf42-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="eaf42-105">Proxy může zlepšit výkon sítě snížením počtu požadavky odeslané na vzdálených serverech.</span><span class="sxs-lookup"><span data-stu-id="eaf42-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="eaf42-106">Proxy lze také omezit přístup k prostředkům.</span><span class="sxs-lookup"><span data-stu-id="eaf42-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="eaf42-107">Adaptivní proxy</span><span class="sxs-lookup"><span data-stu-id="eaf42-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="eaf42-108">V rozhraní .NET Framework, proxy servery existují ve dvou variantách: Adaptivní a statické.</span><span class="sxs-lookup"><span data-stu-id="eaf42-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="eaf42-109">Adaptivní proxy úprava jejich nastavení, když se změny v konfiguraci sítě.</span><span class="sxs-lookup"><span data-stu-id="eaf42-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="eaf42-110">Například pokud uživatel přenosný počítač spustí telefonické připojení sítě, adaptivní proxy by rozpoznat tuto změnu, zjistit a spusťte nový skript pro konfiguraci a jeho nastavení, odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="eaf42-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="eaf42-111">Adaptivní proxy se nakonfiguroval konfigurační skript (viz [automatické zjišťování Proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="eaf42-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="eaf42-112">Tento skript generuje sadu protokoly aplikací a proxy serveru pro každý protokol.</span><span class="sxs-lookup"><span data-stu-id="eaf42-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="eaf42-113">Několik možností, jak řídit, jak je konfigurační skript spustit.</span><span class="sxs-lookup"><span data-stu-id="eaf42-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="eaf42-114">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="eaf42-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="eaf42-115">Jak často je konfigurační skript stáhnout a spustit.</span><span class="sxs-lookup"><span data-stu-id="eaf42-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="eaf42-116">Jak dlouho chcete čekat na skript, který chcete stáhnout.</span><span class="sxs-lookup"><span data-stu-id="eaf42-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="eaf42-117">Které přihlašovací údaje systému má použít pro přístup k proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="eaf42-118">Které přihlašovací údaje systému měli používat ke stažení konfigurační skript.</span><span class="sxs-lookup"><span data-stu-id="eaf42-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="eaf42-119">Změny v prostředí sítě můžou vyžadovat, že systém použít novou sadu serverů proxy.</span><span class="sxs-lookup"><span data-stu-id="eaf42-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="eaf42-120">Pokud připojení k síti ocitne mimo provoz nebo je inicializován nového připojení k síti, systém musí vyhledat příslušný zdroj konfigurační skript v nové verzi prostředí a spusťte nový skript.</span><span class="sxs-lookup"><span data-stu-id="eaf42-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="eaf42-121">V následující tabulce jsou uvedeny možnosti konfigurace pro adaptivní proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="eaf42-122">Atribut, vlastnost nebo konfigurace nastavení souboru</span><span class="sxs-lookup"><span data-stu-id="eaf42-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="eaf42-123">Popis</span><span class="sxs-lookup"><span data-stu-id="eaf42-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="eaf42-124">Uplynulý čas v sekundách mezi stahováním skriptu.</span><span class="sxs-lookup"><span data-stu-id="eaf42-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="eaf42-125">Doba čekání (v sekundách) pro skript, který chcete stáhnout.</span><span class="sxs-lookup"><span data-stu-id="eaf42-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="eaf42-126">`useDefaultCredentials`nebo<xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="eaf42-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="eaf42-127">Určuje, zda systém používá výchozí síťové přihlašovací údaje pro přístup k proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="eaf42-128">Určuje, zda systém použije výchozí přihlašovací údaje pro síť se stáhnout skript konfigurace.</span><span class="sxs-lookup"><span data-stu-id="eaf42-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="eaf42-129">Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="eaf42-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="eaf42-130">Pokud tato hodnota nastavena na hodnotu "true" a pak nastavení statické proxy z Internet Exploreru se použije.</span><span class="sxs-lookup"><span data-stu-id="eaf42-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="eaf42-131">Pokud je tato hodnota "false" nebo není sada, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="eaf42-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="eaf42-132">Tato hodnota musí také na hodnotu "false" nebo není nastavená adaptivní proxy, aby byl povolen.</span><span class="sxs-lookup"><span data-stu-id="eaf42-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="eaf42-133">Následující příklad ukazuje konfiguraci typické adaptivní proxy.</span><span class="sxs-lookup"><span data-stu-id="eaf42-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="eaf42-134">Statické proxy</span><span class="sxs-lookup"><span data-stu-id="eaf42-134">Static Proxies</span></span>  
 <span data-ttu-id="eaf42-135">Statické proxy jsou obvykle explicitně nakonfigurovaná aplikací, nebo při vyvolání konfiguračního souboru aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="eaf42-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="eaf42-136">Statické proxy jsou užitečné v sítích, ve kterých změny topologie zřídka, jako je například stolní počítač připojený k podnikové síti.</span><span class="sxs-lookup"><span data-stu-id="eaf42-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="eaf42-137">Několik možností, jak řídit, jak funguje statické proxy server.</span><span class="sxs-lookup"><span data-stu-id="eaf42-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="eaf42-138">Můžete zadat následující:</span><span class="sxs-lookup"><span data-stu-id="eaf42-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="eaf42-139">Adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="eaf42-140">Jestli by měl obejít proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="eaf42-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="eaf42-141">Jestli má u sadu adres název proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="eaf42-142">V následující tabulce jsou uvedeny možnosti konfigurace pro statické proxy server.</span><span class="sxs-lookup"><span data-stu-id="eaf42-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="eaf42-143">Atribut, vlastnost nebo konfigurace nastavení souboru</span><span class="sxs-lookup"><span data-stu-id="eaf42-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="eaf42-144">Popis</span><span class="sxs-lookup"><span data-stu-id="eaf42-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="eaf42-145">`proxyaddress`nebo<xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="eaf42-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="eaf42-146">Adresa proxy serveru používat.</span><span class="sxs-lookup"><span data-stu-id="eaf42-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="eaf42-147">`bypassonlocal`nebo<xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="eaf42-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="eaf42-148">Určuje, zda je vynechá proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="eaf42-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="eaf42-149">`bypasslist`nebo<xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="eaf42-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="eaf42-150">Popisuje sadu adres, které používat proxy server s použitím regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="eaf42-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="eaf42-151">Určuje, zda nastavení statické proxy (adresa proxy seznam obcházení a nepoužívat místního) byste si měli přečíst z nastavení proxy serveru aplikace Internet Explorer pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="eaf42-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="eaf42-152">Pokud tato hodnota nastavena na hodnotu "true" a pak nastavení statické proxy z Internet Exploreru se použije.</span><span class="sxs-lookup"><span data-stu-id="eaf42-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="eaf42-153">V rozhraní .NET Framework 2.0 když tato hodnota nastavena na hodnotu "PRAVDA", ostatní nastavení proxy serveru v konfiguračním souboru nejsou přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="eaf42-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="eaf42-154">V rozhraní .NET Framework 1.1 je možné přepsat nastavení proxy serveru aplikace Internet Explorer Další nastavení proxy serveru v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="eaf42-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="eaf42-155">Pokud je tato hodnota "false" nebo není sada, potom nastavení statické proxy může být zadaný v konfiguraci a přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="eaf42-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="eaf42-156">Tato hodnota musí také na hodnotu "false" nebo není nastavená adaptivní proxy, aby byl povolen.</span><span class="sxs-lookup"><span data-stu-id="eaf42-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="eaf42-157">Následující příklad ukazuje konfiguraci typické statické proxy.</span><span class="sxs-lookup"><span data-stu-id="eaf42-157">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eaf42-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaf42-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="eaf42-159">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="eaf42-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
