---
title: Automatické rozpoznávání serveru Proxy
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acb14d8785a01d98d56233b8eb942f9bc4675f63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="automatic-proxy-detection"></a>Automatické rozpoznávání serveru Proxy
Automatické rozpoznávání serveru proxy je proces, podle kterého je webový proxy server identifikovaný systému a používaný k odesílání žádostí jménem klienta. Tato funkce je také označované jako Proxy Auto-Discovery WPAD (Web). Pokud je povoleno automatické rozpoznávání serveru proxy, systém se pokusí najít skript konfigurace proxy serveru, která je odpovědná za vrácení sadu proxy servery, které lze použít pro požadavek. Pokud je nalezen skript konfigurace proxy serveru, skript stáhnout a spustit v místním počítači, když se získat informace o proxy serveru, datový proud požadavku nebo odpovědi pro požadavek, který používá zkompilovat <xref:System.Net.WebProxy> instance.  
  
 Provádí automatické rozpoznávání serveru proxy <xref:System.Net.WebProxy> třídy a můžete použít nastavení úrovni požadavků, nastavení v konfiguračních souborech a nastavení zadaná v aplikaci Internet Explorer **místní sítě (LAN)** dialogové okno.  
  
> [!NOTE]
>  Můžete zobrazit v Internet Exploreru **nastavení místní sítě (LAN)** dialogové okno výběrem **nástroje** z hlavní nabídky aplikace Internet Explorer a pak vyberete **Možnosti Internetu**. Potom vyberte **připojení** a klikněte na **nastavení místní sítě**.  
  
 Pokud je povoleno automatické rozpoznávání serveru proxy, <xref:System.Net.WebProxy> třída pokusí najít skript konfigurace proxy serveru následujícím způsobem:  
  
1.  WinINet `InternetQueryOption` funkce slouží k vyhledání naposledy zjištěných aplikací Internet Explorer skript konfigurace proxy serveru.  
  
2.  Pokud skript není umístěný, <xref:System.Net.WebProxy> třída používá k vyhledání skriptu na hostiteli konfigurace protokolu DHCP (Dynamic). DHCP server může odpovídat buď pomocí umístění (název hostitele), skriptu nebo s úplnou adresu URL pro skript.  
  
3.  Pokud hostitele WPAD není uvedeno, DHCP, DNS je dotazován na hostitele s WPAD jako jeho název nebo alias.  
  
4.  Pokud hostitel není identifikovat a umístění skript konfigurace proxy serveru je určený nastavení místní sítě Internet Explorer nebo konfiguračního souboru, se používá toto umístění.  
  
> [!NOTE]
>  Aplikace běží jako služba NT nebo v rámci technologie ASP.NET použijte nastavení serveru proxy aplikace Internet Explorer (Pokud je k dispozici) volajícím uživatele. Tato nastavení nemusí být dostupné pro všechny aplikace služby.  
  
 Proxy servery jsou nakonfigurovány na základě ikony na připojení. Ikony připojení je položku v dialogovém okně síťové připojení a může být fyzické síťové zařízení (modem nebo kartu Ethernet) nebo virtuální rozhraní (například připojení k síti VPN systémem přes síťové zařízení). Když se změní ikony připojení (například bezdrátového připojení změny, které je povoleno přístupového bodu nebo síť VPN), je algoritmus detekce proxy spusťte znovu.  
  
 Ve výchozím nastavení proxy serveru aplikace Internet Explorer slouží ke zjišťování proxy serveru. Pokud vaše aplikace běží pod účtem neinteraktivní (bez pohodlný způsob, jak konfigurovat nastavení proxy serveru aplikace Internet Explorer), nebo pokud chcete použít nastavení proxy serveru liší od nastavení aplikace Internet Explorer, můžete nakonfigurovat proxy tak, že vytvoříte konfigurační soubor s [ \<defaultProxy – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elementy definované.  
  
 Pro požadavky, které vytvoříte, můžete zakázat automatické rozpoznávání serveru proxy na úrovni žádosti pomocí null <xref:System.Net.WebRequest.Proxy%2A> s žádostí, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Použít proxy výchozí doménu aplikace, která je k dispozici v žádosti, které nemají žádný proxy server <xref:System.Net.WebRequest.DefaultWebProxy%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [\<system.Net > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
