---
title: Automatické rozpoznávání proxy serveru
ms.date: 03/30/2017
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
ms.openlocfilehash: 3de9b67d687d23e9f31c3060f5af6ef90d45f217
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164759"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="a3665-102">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="a3665-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="a3665-103">Automatické rozpoznávání proxy serveru je proces, podle kterého je identifikován systému a použít má odesílat požadavky jménem klienta webového proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="a3665-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="a3665-104">Tato funkce je také označován jako Proxy Auto-Discovery WPAD (Web).</span><span class="sxs-lookup"><span data-stu-id="a3665-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="a3665-105">Pokud je povoleno automatické rozpoznávání proxy serveru, systém se pokusí najít skript konfigurace proxy serveru, který je zodpovědný za vrácení sady proxy servery, které je možné pro daný požadavek.</span><span class="sxs-lookup"><span data-stu-id="a3665-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="a3665-106">Pokud je nalezen skript konfigurace proxy serveru, skript stáhnout a spustit na místním počítači, když je získat informace o proxy serveru, datový proud požadavku nebo odpovědi pro žádosti, která používá zkompilován <xref:System.Net.WebProxy> instance.</span><span class="sxs-lookup"><span data-stu-id="a3665-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="a3665-107">Automatické rozpoznávání proxy serveru se provádí <xref:System.Net.WebProxy> třídy a můžete použít nastavení na úrovni žádosti, nastavení v konfiguračních souborech a nastavení zadaná v aplikaci Internet Explorer **místní sítě (LAN)** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a3665-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3665-108">Můžete zobrazit aplikace Internet Explorer **nastavení místní sítě (LAN)** dialogové okno tak, že vyberete **nástroje** z hlavní nabídky v Internet Exploreru a pak vyberete **Možnosti Internetu**.</span><span class="sxs-lookup"><span data-stu-id="a3665-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="a3665-109">V dalším kroku vyberte **připojení** kartu a klikněte na tlačítko **nastavení místní sítě**.</span><span class="sxs-lookup"><span data-stu-id="a3665-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="a3665-110">Pokud je povoleno automatické rozpoznávání proxy serveru, <xref:System.Net.WebProxy> třídy se pokusí najít skript konfigurace proxy serveru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a3665-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="a3665-111">WinINet `InternetQueryOption` funkce se používá k vyhledání naposledy zjištěných aplikací Internet Explorer konfigurační skript proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="a3665-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="a3665-112">Pokud skript není umístěn, <xref:System.Net.WebProxy> třída používá hostiteli konfigurace protokolu DHCP (Dynamic) a vyhledejte skript.</span><span class="sxs-lookup"><span data-stu-id="a3665-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="a3665-113">DHCP server může reagovat pomocí umístění (název hostitele) skriptu nebo s úplnou adresu URL pro skript.</span><span class="sxs-lookup"><span data-stu-id="a3665-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="a3665-114">Pokud DHCP neidentifikuje WPAD hostitele, dotaz DNS na hostitele s WPAD jako jeho název nebo alias.</span><span class="sxs-lookup"><span data-stu-id="a3665-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="a3665-115">Pokud není označen hostitele a umístění skriptu konfigurace proxy serveru je určené nastavení místní sítě Internet Explorer nebo konfiguračního souboru, toto umístění se používá.</span><span class="sxs-lookup"><span data-stu-id="a3665-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3665-116">Aplikací spuštěných jako služby NT nebo v rámci technologie ASP.NET použijte nastavení aplikace Internet Explorer proxy serveru (Pokud je k dispozici) vyvolání uživatele.</span><span class="sxs-lookup"><span data-stu-id="a3665-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="a3665-117">Tato nastavení nemusí být k dispozici pro všechny aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="a3665-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="a3665-118">Proxy servery jsou nakonfigurovány na základě za připojení.</span><span class="sxs-lookup"><span data-stu-id="a3665-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="a3665-119">Ikony připojení se položky v dialogovém okně síťové připojení a můžou být fyzické síťové zařízení (modem nebo karta Ethernet) nebo virtuální rozhraní (jako je například připojení k síti VPN systémem přes síťové zařízení).</span><span class="sxs-lookup"><span data-stu-id="a3665-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="a3665-120">Když se profil změní (například bezdrátového připojení změny, které je povoleno přístupového bodu nebo síť VPN), je algoritmus zjišťování proxy serveru spusťte znovu.</span><span class="sxs-lookup"><span data-stu-id="a3665-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="a3665-121">Ve výchozím nastavení proxy aplikace Internet Explorer slouží ke zjišťování proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="a3665-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="a3665-122">Pokud vaše aplikace běží pod účtem neinteraktivním přístupu (bez pohodlný způsob, jak nakonfigurovat nastavení proxy aplikace Internet Explorer) nebo pokud chcete použít nastavení proxy serveru liší od nastavení aplikace Internet Explorer, je váš proxy server nakonfigurovat tak, že vytvoříte konfigurační soubor s [ \<defaultProxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) prvky definované.</span><span class="sxs-lookup"><span data-stu-id="a3665-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="a3665-123">Pro žádosti, které vytvoříte, můžete zakázat automatické rozpoznávání proxy serveru na úrovni žádost pomocí s hodnotou null <xref:System.Net.WebRequest.Proxy%2A> při zpracování požadavku, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="a3665-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="a3665-124">Požadavky, které nemají proxy server používat proxy výchozí domény aplikace, která je k dispozici v <xref:System.Net.WebRequest.DefaultWebProxy%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3665-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3665-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3665-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="a3665-126">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a3665-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
