---
title: "Automatické rozpoznávání serveru Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bbfdb16e284fcd266bcc8ebf41a197733e92ca23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="55faf-102">Automatické rozpoznávání serveru Proxy</span><span class="sxs-lookup"><span data-stu-id="55faf-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="55faf-103">Automatické rozpoznávání serveru proxy je proces, podle kterého je webový proxy server identifikovaný systému a používaný k odesílání žádostí jménem klienta.</span><span class="sxs-lookup"><span data-stu-id="55faf-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="55faf-104">Tato funkce je také označované jako Proxy Auto-Discovery WPAD (Web).</span><span class="sxs-lookup"><span data-stu-id="55faf-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="55faf-105">Pokud je povoleno automatické rozpoznávání serveru proxy, systém se pokusí najít skript konfigurace proxy serveru, která je odpovědná za vrácení sadu proxy servery, které lze použít pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="55faf-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="55faf-106">Pokud je nalezen skript konfigurace proxy serveru, skript stáhnout a spustit v místním počítači, když se získat informace o proxy serveru, datový proud požadavku nebo odpovědi pro požadavek, který používá zkompilovat <xref:System.Net.WebProxy> instance.</span><span class="sxs-lookup"><span data-stu-id="55faf-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="55faf-107">Provádí automatické rozpoznávání serveru proxy <xref:System.Net.WebProxy> třídy a můžete použít nastavení úrovni požadavků, nastavení v konfiguračních souborech a nastavení zadaná v aplikaci Internet Explorer **místní sítě (LAN)** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="55faf-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55faf-108">Můžete zobrazit v Internet Exploreru **nastavení místní sítě (LAN)** dialogové okno výběrem **nástroje** z hlavní nabídky aplikace Internet Explorer a pak vyberete **Možnosti Internetu**.</span><span class="sxs-lookup"><span data-stu-id="55faf-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="55faf-109">Potom vyberte **připojení** a klikněte na **nastavení místní sítě**.</span><span class="sxs-lookup"><span data-stu-id="55faf-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="55faf-110">Pokud je povoleno automatické rozpoznávání serveru proxy, <xref:System.Net.WebProxy> třída pokusí najít skript konfigurace proxy serveru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="55faf-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="55faf-111">WinINet `InternetQueryOption` funkce slouží k vyhledání naposledy zjištěných aplikací Internet Explorer skript konfigurace proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="55faf-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="55faf-112">Pokud skript není umístěný, <xref:System.Net.WebProxy> třída používá k vyhledání skriptu na hostiteli konfigurace protokolu DHCP (Dynamic).</span><span class="sxs-lookup"><span data-stu-id="55faf-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="55faf-113">DHCP server může odpovídat buď pomocí umístění (název hostitele), skriptu nebo s úplnou adresu URL pro skript.</span><span class="sxs-lookup"><span data-stu-id="55faf-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="55faf-114">Pokud hostitele WPAD není uvedeno, DHCP, DNS je dotazován na hostitele s WPAD jako jeho název nebo alias.</span><span class="sxs-lookup"><span data-stu-id="55faf-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="55faf-115">Pokud hostitel není identifikovat a umístění skript konfigurace proxy serveru je určený nastavení místní sítě Internet Explorer nebo konfiguračního souboru, se používá toto umístění.</span><span class="sxs-lookup"><span data-stu-id="55faf-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55faf-116">Aplikace běží jako služba NT nebo v rámci technologie ASP.NET použijte nastavení serveru proxy aplikace Internet Explorer (Pokud je k dispozici) volajícím uživatele.</span><span class="sxs-lookup"><span data-stu-id="55faf-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="55faf-117">Tato nastavení nemusí být dostupné pro všechny aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="55faf-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="55faf-118">Proxy servery jsou nakonfigurovány na základě ikony na připojení.</span><span class="sxs-lookup"><span data-stu-id="55faf-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="55faf-119">Ikony připojení je položku v dialogovém okně síťové připojení a může být fyzické síťové zařízení (modem nebo kartu Ethernet) nebo virtuální rozhraní (například připojení k síti VPN systémem přes síťové zařízení).</span><span class="sxs-lookup"><span data-stu-id="55faf-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="55faf-120">Když se změní ikony připojení (například bezdrátového připojení změny, které je povoleno přístupového bodu nebo síť VPN), je algoritmus detekce proxy spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="55faf-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="55faf-121">Ve výchozím nastavení proxy serveru aplikace Internet Explorer slouží ke zjišťování proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="55faf-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="55faf-122">Pokud vaše aplikace běží pod účtem neinteraktivní (bez pohodlný způsob, jak konfigurovat nastavení proxy serveru aplikace Internet Explorer), nebo pokud chcete použít nastavení proxy serveru liší od nastavení aplikace Internet Explorer, můžete nakonfigurovat proxy tak, že vytvoříte konfigurační soubor s [ \<defaultProxy – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy definované.</span><span class="sxs-lookup"><span data-stu-id="55faf-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="55faf-123">Pro požadavky, které vytvoříte, můžete zakázat automatické rozpoznávání serveru proxy na úrovni žádosti pomocí null <xref:System.Net.WebRequest.Proxy%2A> s žádostí, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="55faf-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="55faf-124">Použít proxy výchozí doménu aplikace, která je k dispozici v žádosti, které nemají žádný proxy server <xref:System.Net.WebRequest.DefaultWebProxy%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="55faf-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55faf-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="55faf-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="55faf-126">\<system.Net > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="55faf-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
