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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f43f8b4f7bdaba3902168ee7a1c6b7f7a2f3d39c
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863140"
---
# <a name="automatic-proxy-detection"></a>Automatické rozpoznávání proxy serveru
Automatické rozpoznávání proxy serveru je proces, podle kterého je identifikován systému a použít má odesílat požadavky jménem klienta webového proxy serveru. Tato funkce je také označován jako Proxy Auto-Discovery WPAD (Web). Pokud je povoleno automatické rozpoznávání proxy serveru, systém se pokusí najít skript konfigurace proxy serveru, který je zodpovědný za vrácení sady proxy servery, které je možné pro daný požadavek. Pokud je nalezen skript konfigurace proxy serveru, skript stáhnout a spustit na místním počítači, když je získat informace o proxy serveru, datový proud požadavku nebo odpovědi pro žádosti, která používá zkompilován <xref:System.Net.WebProxy> instance.  
  
 Automatické rozpoznávání proxy serveru se provádí <xref:System.Net.WebProxy> třídy a můžete použít nastavení na úrovni žádosti, nastavení v konfiguračních souborech a nastavení zadaná v aplikaci Internet Explorer **místní sítě (LAN)** dialogové okno.  
  
> [!NOTE]
>  Můžete zobrazit aplikace Internet Explorer **nastavení místní sítě (LAN)** dialogové okno tak, že vyberete **nástroje** z hlavní nabídky v Internet Exploreru a pak vyberete **Možnosti Internetu**. V dalším kroku vyberte **připojení** kartu a klikněte na tlačítko **nastavení místní sítě**.  
  
 Pokud je povoleno automatické rozpoznávání proxy serveru, <xref:System.Net.WebProxy> třídy se pokusí najít skript konfigurace proxy serveru následujícím způsobem:  
  
1.  WinINet `InternetQueryOption` funkce se používá k vyhledání naposledy zjištěných aplikací Internet Explorer konfigurační skript proxy serveru.  
  
2.  Pokud skript není umístěn, <xref:System.Net.WebProxy> třída používá hostiteli konfigurace protokolu DHCP (Dynamic) a vyhledejte skript. DHCP server může reagovat pomocí umístění (název hostitele) skriptu nebo s úplnou adresu URL pro skript.  
  
3.  Pokud DHCP neidentifikuje WPAD hostitele, dotaz DNS na hostitele s WPAD jako jeho název nebo alias.  
  
4.  Pokud není označen hostitele a umístění skriptu konfigurace proxy serveru je určené nastavení místní sítě Internet Explorer nebo konfiguračního souboru, toto umístění se používá.  
  
> [!NOTE]
>  Aplikací spuštěných jako služby NT nebo v rámci technologie ASP.NET použijte nastavení aplikace Internet Explorer proxy serveru (Pokud je k dispozici) vyvolání uživatele. Tato nastavení nemusí být k dispozici pro všechny aplikace služby.  
  
 Proxy servery jsou nakonfigurovány na základě za připojení. Ikony připojení se položky v dialogovém okně síťové připojení a můžou být fyzické síťové zařízení (modem nebo karta Ethernet) nebo virtuální rozhraní (jako je například připojení k síti VPN systémem přes síťové zařízení). Když se profil změní (například bezdrátového připojení změny, které je povoleno přístupového bodu nebo síť VPN), je algoritmus zjišťování proxy serveru spusťte znovu.  
  
 Ve výchozím nastavení proxy aplikace Internet Explorer slouží ke zjišťování proxy serveru. Pokud vaše aplikace běží pod účtem neinteraktivním přístupu (bez pohodlný způsob, jak nakonfigurovat nastavení proxy aplikace Internet Explorer) nebo pokud chcete použít nastavení proxy serveru liší od nastavení aplikace Internet Explorer, je váš proxy server nakonfigurovat tak, že vytvoříte konfigurační soubor s [ \<defaultProxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) prvky definované.  
  
 Pro žádosti, které vytvoříte, můžete zakázat automatické rozpoznávání proxy serveru na úrovni žádost pomocí s hodnotou null <xref:System.Net.WebRequest.Proxy%2A> při zpracování požadavku, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Požadavky, které nemají proxy server používat proxy výchozí domény aplikace, která je k dispozici v <xref:System.Net.WebRequest.DefaultWebProxy%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [\<system.Net > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
