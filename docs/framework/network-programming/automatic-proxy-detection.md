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
ms.openlocfilehash: d7d0dae2ffbec5e334057715cd1d8d44e52cec9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910468"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="b459e-102">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="b459e-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="b459e-103">Automatická detekce proxy je proces, kterým systém identifikuje webový proxy server a který slouží k odesílání žádostí jménem klienta.</span><span class="sxs-lookup"><span data-stu-id="b459e-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="b459e-104">Tato funkce se označuje taky jako automatické zjišťování webových proxy serverů (WPAD).</span><span class="sxs-lookup"><span data-stu-id="b459e-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="b459e-105">Pokud je povolená Automatická detekce proxy serveru, systém se pokusí vyhledat konfigurační skript proxy serveru, který je zodpovědný za vrácení sady proxy serverů, které se dají pro požadavek použít.</span><span class="sxs-lookup"><span data-stu-id="b459e-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="b459e-106">Pokud se skript konfigurace proxy serveru najde, skript se stáhne, zkompiluje a spustí v místním počítači, když se pro požadavek, který používá <xref:System.Net.WebProxy> instanci, získá informace o proxy serveru, datový proud požadavku nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="b459e-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="b459e-107">Automatickou detekci proxy provádí <xref:System.Net.WebProxy> třída a může využívat nastavení na úrovni požadavků, nastavení v konfiguračních souborech a nastavení určená pomocí dialogového okna místní sítě Internet Exploreru **(LAN)** .</span><span class="sxs-lookup"><span data-stu-id="b459e-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b459e-108">Dialogové okno **Nastavení místní sítě (LAN)** Internet Exploreru můžete zobrazit tak, že v hlavní nabídce aplikace Internet Explorer vyberete **nástroje** a pak vyberete **Možnosti Internetu**.</span><span class="sxs-lookup"><span data-stu-id="b459e-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="b459e-109">Potom vyberte kartu **připojení** a pak klikněte na **Nastavení místní sítě**.</span><span class="sxs-lookup"><span data-stu-id="b459e-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="b459e-110">Pokud je povolena automatická detekce proxy, třída <xref:System.Net.WebProxy> se pokusí vyhledat skript konfigurace proxy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b459e-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="b459e-111">Funkce WinInet `InternetQueryOption` slouží k vyhledání konfiguračního skriptu proxy serveru naposledy zjištěného aplikací Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b459e-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="b459e-112">Pokud skript není umístěný, <xref:System.Net.WebProxy> Třída pomocí protokolu DHCP (Dynamic Host Configuration Protocol) Tento skript vyhledá.</span><span class="sxs-lookup"><span data-stu-id="b459e-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="b459e-113">Server DHCP může reagovat buď s umístěním (názvem hostitele) skriptu, nebo s úplnou adresou URL pro tento skript.</span><span class="sxs-lookup"><span data-stu-id="b459e-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="b459e-114">Pokud server DHCP neidentifikuje hostitele WPAD, bude pro hostitele s protokolem WPAD jako jeho název nebo alias dotazován dotaz na server DNS.</span><span class="sxs-lookup"><span data-stu-id="b459e-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="b459e-115">Pokud hostitel není identifikovaný a umístění konfiguračního skriptu proxy serveru je zadáno pomocí nastavení aplikace Internet Explorer LAN nebo konfiguračního souboru, bude použito toto umístění.</span><span class="sxs-lookup"><span data-stu-id="b459e-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b459e-116">Aplikace spuštěné jako služba NT nebo jako součást ASP.NET používají nastavení aplikace Internet Explorer proxy server (Pokud je k dispozici) vyvolání uživatele.</span><span class="sxs-lookup"><span data-stu-id="b459e-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="b459e-117">Tato nastavení nemusí být k dispozici pro všechny aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="b459e-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="b459e-118">Proxy servery jsou nakonfigurovány podle connectoid.</span><span class="sxs-lookup"><span data-stu-id="b459e-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="b459e-119">Connectoid je položka v dialogovém okně připojení k síti a může to být fyzické síťové zařízení (modem nebo ethernetová karta) nebo virtuální rozhraní (například připojení VPN spuštěné přes síťové zařízení).</span><span class="sxs-lookup"><span data-stu-id="b459e-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="b459e-120">Pokud se connectoid změní (například bezdrátové připojení změní přístupový bod nebo je povolena síť VPN), algoritmus detekce proxy se spustí znovu.</span><span class="sxs-lookup"><span data-stu-id="b459e-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="b459e-121">Ve výchozím nastavení se k detekci proxy serveru používá nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="b459e-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="b459e-122">Pokud vaše aplikace běží pod neinteraktivním účtem (bez pohodlnýho způsobu konfigurace nastavení proxy serveru IE), nebo pokud chcete použít nastavení proxy serveru, které se liší od nastavení IE, můžete nakonfigurovat proxy tak, že vytvoříte konfigurační soubor s [ defaultProxy\<prvek > (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<elementy proxy > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) definovány.</span><span class="sxs-lookup"><span data-stu-id="b459e-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="b459e-123">U požadavků, které vytvoříte, můžete vypnout automatickou detekci proxy na úrovni žádosti pomocí hodnoty null <xref:System.Net.WebRequest.Proxy%2A> s vaším požadavkem, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b459e-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="b459e-124">Žádosti, které nemají proxy, používají výchozí proxy server domény, který je k dispozici ve <xref:System.Net.WebRequest.DefaultWebProxy%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b459e-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b459e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b459e-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="b459e-126">\<System .NET > – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b459e-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
