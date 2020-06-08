---
title: Automatické rozpoznávání proxy serveru
description: Přečtěte si o automatickém zjišťování proxy serveru, kde systém identifikuje webovou proxy server a používá ho k posílání požadavků jménem klienta.
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
ms.openlocfilehash: dbd5d7fa671ae5ec3b7dc00205f0c9d8381bb3ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502691"
---
# <a name="automatic-proxy-detection"></a>Automatické rozpoznávání proxy serveru
Automatická detekce proxy je proces, kterým systém identifikuje webový proxy server a který slouží k odesílání žádostí jménem klienta. Tato funkce se označuje taky jako automatické zjišťování webových proxy serverů (WPAD). Pokud je povolená Automatická detekce proxy serveru, systém se pokusí vyhledat konfigurační skript proxy serveru, který je zodpovědný za vrácení sady proxy serverů, které se dají pro požadavek použít. Pokud se skript konfigurace proxy serveru najde, skript se stáhne, zkompiluje a spustí v místním počítači, když se pro požadavek, který používá instanci, získá informace o proxy serveru, datový proud požadavku nebo odpověď <xref:System.Net.WebProxy> .  
  
 Automatickou detekci proxy provádí <xref:System.Net.WebProxy> Třída a může využívat nastavení na úrovni požadavků, nastavení v konfiguračních souborech a nastavení určená pomocí dialogového okna místní sítě Internet Exploreru **(LAN)** .  
  
> [!NOTE]
> Dialogové okno **Nastavení místní sítě (LAN)** Internet Exploreru můžete zobrazit tak, že v hlavní nabídce aplikace Internet Explorer vyberete **nástroje** a pak vyberete **Možnosti Internetu**. Potom vyberte kartu **připojení** a pak klikněte na **Nastavení místní sítě**.  
  
 Pokud je povolena automatická detekce proxy, <xref:System.Net.WebProxy> Třída se pokusí vyhledat skript konfigurace proxy následujícím způsobem:  
  
1. Funkce WinINet `InternetQueryOption` slouží k vyhledání konfiguračního skriptu proxy serveru naposledy zjištěného aplikací Internet Explorer.  
  
2. Pokud skript není umístěný, <xref:System.Net.WebProxy> Třída pomocí protokolu DHCP (Dynamic Host Configuration Protocol) Tento skript vyhledá. Server DHCP může reagovat buď s umístěním (názvem hostitele) skriptu, nebo s úplnou adresou URL pro tento skript.  
  
3. Pokud server DHCP neidentifikuje hostitele WPAD, bude pro hostitele s protokolem WPAD jako jeho název nebo alias dotazován dotaz na server DNS.  
  
4. Pokud hostitel není identifikovaný a umístění konfiguračního skriptu proxy serveru je zadáno pomocí nastavení aplikace Internet Explorer LAN nebo konfiguračního souboru, bude použito toto umístění.  
  
> [!NOTE]
> Aplikace spuštěné jako služba NT nebo jako součást ASP.NET používají nastavení aplikace Internet Explorer proxy server (Pokud je k dispozici) vyvolání uživatele. Tato nastavení nemusí být k dispozici pro všechny aplikace služby.  
  
 Proxy servery jsou nakonfigurovány podle connectoid. Connectoid je položka v dialogovém okně připojení k síti a může to být fyzické síťové zařízení (modem nebo ethernetová karta) nebo virtuální rozhraní (například připojení VPN spuštěné přes síťové zařízení). Pokud se connectoid změní (například bezdrátové připojení změní přístupový bod nebo je povolena síť VPN), algoritmus detekce proxy se spustí znovu.  
  
 Ve výchozím nastavení se k detekci proxy serveru používá nastavení proxy serveru aplikace Internet Explorer. Pokud vaše aplikace běží pod neinteraktivním účtem (bez pohodlnýho způsobu konfigurace nastavení proxy serveru IE), nebo pokud chcete použít nastavení proxy serveru, které se liší od nastavení IE, můžete nakonfigurovat proxy vytvořením konfiguračního souboru pomocí [ \<defaultProxy> elementu (nastavení sítě)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) a [ \<proxy> elementu (nastavení sítě)](../configure-apps/file-schema/network/proxy-element-network-settings.md) definovaných prvků.  
  
 U požadavků, které vytvoříte, můžete vypnout automatickou detekci proxy na úrovni žádosti pomocí hodnoty null <xref:System.Net.WebRequest.Proxy%2A> s vaším požadavkem, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Žádosti, které nemají proxy, používají výchozí proxy server domény, který je k dispozici ve <xref:System.Net.WebRequest.DefaultWebProxy%2A> Vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [\<system.Net>– Element (nastavení sítě)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
