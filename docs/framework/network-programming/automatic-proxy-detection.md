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
# <a name="automatic-proxy-detection"></a>Automatické rozpoznávání proxy serveru
Automatická detekce proxy serveru je proces, při kterém je systém identifikován webovým proxy serverem a používán k odesílání požadavků jménem klienta. Tato funkce je také známá jako automatické zjišťování webového proxy serveru (WPAD). Je-li povoleno automatické zjišťování proxy serveru, systém se pokusí vyhledat konfigurační skript proxy serveru, který je zodpovědný za vrácení sady proxy serverů, které lze použít pro požadavek. Pokud je nalezen konfigurační skript proxy, je skript stažen, zkompilován a spuštěn v místním počítači, když <xref:System.Net.WebProxy> jsou získány informace o serveru proxy, datový proud požadavku nebo odpověď pro požadavek, který používá instanci.  
  
 Automatické zjišťování proxy serveru <xref:System.Net.WebProxy> provádí třída a může využívat nastavení na úrovni požadavků, nastavení v konfiguračních souborech a nastavení určená pomocí dialogového okna Lan (Internet Explorer **Local Area Network).**  
  
> [!NOTE]
> Dialogové okno Nastavení místní sítě Internet Explorer **(LAN)** můžete zobrazit tak, že vyberete **nástroje** z hlavní nabídky aplikace Internet Explorer a potom vyberete **možnosti Internetu**. Dále vyberte kartu **Připojení** a klepněte na **položku Nastavení místní sítě**.  
  
 Pokud je povolena automatická <xref:System.Net.WebProxy> detekce proxy serveru, třída se pokusí vyhledat skript konfigurace proxy takto:  
  
1. Funkce WinINet `InternetQueryOption` se používá k vyhledání konfiguračního skriptu proxy, který aplikace Internet Explorer naposledy zjistila.  
  
2. Pokud skript není nalezen, <xref:System.Net.WebProxy> třída používá k vyhledání skriptu protokol DHCP(DHCP). Server DHCP může odpovědět buď umístěním (názvem hostitele) skriptu, nebo úplnou adresou URL skriptu.  
  
3. Pokud server DHCP neidentifikuje hostitele WPAD, je služba DNS dotazována na hostitele s názvem nebo aliasem WPAD.  
  
4. Pokud hostitel není identifikován a umístění konfiguračního skriptu proxy je určeno nastavením sítě LAN aplikace Internet Explorer nebo konfiguračním souborem, použije se toto umístění.  
  
> [!NOTE]
> Aplikace spuštěné jako služba NT nebo jako součást ASP.NET používají nastavení proxy serveru aplikace Internet Explorer (je-li k dispozici) vyvolávajícího uživatele. Tato nastavení nemusí být k dispozici pro všechny aplikace služby.  
  
 Proxy servery jsou konfigurovány na základě per-connectoid. Connectoid je položka v dialogovém okně síťového připojení a může být fyzické síťové zařízení (modem nebo ethernetová karta) nebo virtuální rozhraní (například připojení VPN běžící přes síťové zařízení). Při změně connectoid (například bezdrátové připojení změní přístupový bod nebo je povolena vpn), algoritmus detekce proxy je znovu spuštěn.  
  
 Ve výchozím nastavení se nastavení serveru proxy aplikace Internet Explorer používá k rozpoznání proxy serveru. Pokud je vaše aplikace spuštěna pod neinteraktivním účtem (bez vhodného způsobu konfigurace nastavení proxy serveru IE), nebo pokud chcete použít nastavení proxy serveru odlišné od nastavení iE, můžete nakonfigurovat proxy server vytvořením konfiguračního souboru s [ \<výchozím proxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy> Element (Nastavení sítě)](../configure-apps/file-schema/network/proxy-element-network-settings.md) prvky definované.  
  
 U požadavků, které vytvoříte, můžete zakázat automatické zjišťování proxy <xref:System.Net.WebRequest.Proxy%2A> serveru na úrovni požadavku pomocí null s požadavkem, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Požadavky, které nemají proxy server, používají výchozí proxy server domény <xref:System.Net.WebRequest.DefaultWebProxy%2A> aplikace, který je k dispozici ve vlastnosti.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net> element (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
