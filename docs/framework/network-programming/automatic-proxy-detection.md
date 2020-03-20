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
ms.openlocfilehash: 4c5bc9e0efb39032d388d141e8bccf3e520ebd45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180897"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="99580-102">Automatické rozpoznávání proxy serveru</span><span class="sxs-lookup"><span data-stu-id="99580-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="99580-103">Automatická detekce proxy serveru je proces, při kterém je systém identifikován webovým proxy serverem a používán k odesílání požadavků jménem klienta.</span><span class="sxs-lookup"><span data-stu-id="99580-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="99580-104">Tato funkce je také známá jako automatické zjišťování webového proxy serveru (WPAD).</span><span class="sxs-lookup"><span data-stu-id="99580-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="99580-105">Je-li povoleno automatické zjišťování proxy serveru, systém se pokusí vyhledat konfigurační skript proxy serveru, který je zodpovědný za vrácení sady proxy serverů, které lze použít pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="99580-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="99580-106">Pokud je nalezen konfigurační skript proxy, je skript stažen, zkompilován a spuštěn v místním počítači, když <xref:System.Net.WebProxy> jsou získány informace o serveru proxy, datový proud požadavku nebo odpověď pro požadavek, který používá instanci.</span><span class="sxs-lookup"><span data-stu-id="99580-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="99580-107">Automatické zjišťování proxy serveru <xref:System.Net.WebProxy> provádí třída a může využívat nastavení na úrovni požadavků, nastavení v konfiguračních souborech a nastavení určená pomocí dialogového okna Lan (Internet Explorer **Local Area Network).**</span><span class="sxs-lookup"><span data-stu-id="99580-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99580-108">Dialogové okno Nastavení místní sítě Internet Explorer **(LAN)** můžete zobrazit tak, že vyberete **nástroje** z hlavní nabídky aplikace Internet Explorer a potom vyberete **možnosti Internetu**.</span><span class="sxs-lookup"><span data-stu-id="99580-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="99580-109">Dále vyberte kartu **Připojení** a klepněte na **položku Nastavení místní sítě**.</span><span class="sxs-lookup"><span data-stu-id="99580-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="99580-110">Pokud je povolena automatická <xref:System.Net.WebProxy> detekce proxy serveru, třída se pokusí vyhledat skript konfigurace proxy takto:</span><span class="sxs-lookup"><span data-stu-id="99580-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="99580-111">Funkce WinINet `InternetQueryOption` se používá k vyhledání konfiguračního skriptu proxy, který aplikace Internet Explorer naposledy zjistila.</span><span class="sxs-lookup"><span data-stu-id="99580-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="99580-112">Pokud skript není nalezen, <xref:System.Net.WebProxy> třída používá k vyhledání skriptu protokol DHCP(DHCP).</span><span class="sxs-lookup"><span data-stu-id="99580-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="99580-113">Server DHCP může odpovědět buď umístěním (názvem hostitele) skriptu, nebo úplnou adresou URL skriptu.</span><span class="sxs-lookup"><span data-stu-id="99580-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="99580-114">Pokud server DHCP neidentifikuje hostitele WPAD, je služba DNS dotazována na hostitele s názvem nebo aliasem WPAD.</span><span class="sxs-lookup"><span data-stu-id="99580-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="99580-115">Pokud hostitel není identifikován a umístění konfiguračního skriptu proxy je určeno nastavením sítě LAN aplikace Internet Explorer nebo konfiguračním souborem, použije se toto umístění.</span><span class="sxs-lookup"><span data-stu-id="99580-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99580-116">Aplikace spuštěné jako služba NT nebo jako součást ASP.NET používají nastavení proxy serveru aplikace Internet Explorer (je-li k dispozici) vyvolávajícího uživatele.</span><span class="sxs-lookup"><span data-stu-id="99580-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="99580-117">Tato nastavení nemusí být k dispozici pro všechny aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="99580-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="99580-118">Proxy servery jsou konfigurovány na základě per-connectoid.</span><span class="sxs-lookup"><span data-stu-id="99580-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="99580-119">Connectoid je položka v dialogovém okně síťového připojení a může být fyzické síťové zařízení (modem nebo ethernetová karta) nebo virtuální rozhraní (například připojení VPN běžící přes síťové zařízení).</span><span class="sxs-lookup"><span data-stu-id="99580-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="99580-120">Při změně connectoid (například bezdrátové připojení změní přístupový bod nebo je povolena vpn), algoritmus detekce proxy je znovu spuštěn.</span><span class="sxs-lookup"><span data-stu-id="99580-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="99580-121">Ve výchozím nastavení se nastavení serveru proxy aplikace Internet Explorer používá k rozpoznání proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="99580-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="99580-122">Pokud je vaše aplikace spuštěna pod neinteraktivním účtem (bez vhodného způsobu konfigurace nastavení proxy serveru IE), nebo pokud chcete použít nastavení proxy serveru odlišné od nastavení iE, můžete nakonfigurovat proxy server vytvořením konfiguračního souboru s [ \<výchozím proxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvky definované.</span><span class="sxs-lookup"><span data-stu-id="99580-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="99580-123">U požadavků, které vytvoříte, můžete zakázat automatické zjišťování proxy <xref:System.Net.WebRequest.Proxy%2A> serveru na úrovni požadavku pomocí null s požadavkem, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="99580-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="99580-124">Požadavky, které nemají proxy server, používají výchozí proxy server domény <xref:System.Net.WebRequest.DefaultWebProxy%2A> aplikace, který je k dispozici ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="99580-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99580-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="99580-125">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="99580-126">\<system.Net> element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="99580-126">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
