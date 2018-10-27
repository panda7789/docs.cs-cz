---
title: 'Základní komunikace: HTTP-HTTPS přenosové kanály'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 4c4a2537ae615943ffac299a8c8cd00c67094360
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50045402"
---
# <a name="core-communications-httphttps-transport-channels"></a>Základní komunikace: Přenosové kanály HTTP/HTTPS
Toto téma uvádí všechny výjimky generované Windows Communication Foundation (WCF), přenosové kanály HTTP/HTTPS.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Byla zadána úroveň zosobnění zadané. Ověřování algoritmem HTTP Digest podporuje pouze úroveň 'Zosobnění' při použití s explicitním pověřením.|  
|FramingContentTypeMismatch|Zadaný typ obsahu není podporována zadaná služba. Vazby klienta a služby se pravděpodobně neshodují.|  
|Hosting_SslSettingsMisconfigured|Nastavení (Secure Sockets Layer) pro zadanou službu neshodují Internetová informační služba.|  
|HttpAuthSchemeAndClientCert|Výroba naslouchací proces protokolu HTTPS byla nakonfigurována tak, aby vyžadovala certifikát klienta a zadané schéma ověřování. Však pouze jednu formu ověření klienta může vyžadovat najednou.|  
|HttpReceiveFailure|Během příjmu odpovědi protokolu HTTP na zadaný došlo k chybě. Vazba koncového bodu služby, nemusí být pomocí protokolu HTTP. Další možností je, že byl ji server ukončí kontext požadavku protokolu HTTP z důvodu vypnutí služby. Zobrazit další podrobnosti najdete v protokolech serveru.|  
|HttpRegistrationAccessDenied|Protokol HTTP nelze zaregistrovat zadanou adresu URL. Váš proces nemá přístupová práva k tomuto oboru názvů (viz [Namespace rezervace, registrace a směrování](/windows/desktop/http/namespace-reservations-registrations-and-routing) podrobnosti).|  
|HttpRegistrationAlreadyExists|Protokol HTTP nelze zaregistrovat zadanou adresu URL. Jiná aplikace již tuto adresu URL zaregistrovala přes HTTP. SYS.|  
|HttpRegistrationPortInUse|Protokol HTTP nelze zaregistrovat zadanou adresu URL, protože zadaný port TCP používán jinou aplikací.|  
|HttpSendFailure|Při vytváření požadavku protokolu HTTP na zadaný došlo k chybě. Ujistěte se, že příčinou není neshodou vazby zabezpečení. Také se ujistěte, že služba není nakonfigurována pro (Secure Sockets Layer).|  
|MessageXmlProtocolError|Došlo k potížím s XML, který byl přijat ze sítě. Viz vnitřní výjimka pro další podrobnosti.|  
|MissingContentType|Příjemce vrátil chybu, která označuje, že nebyl nalezen v požadavku na zadaný typ obsahu. Viz vnitřní výjimka pro další informace.|  
|ProxyAuthenticationLevelMismatch|Pověření pro ověření proxy serveru HTTP určilo požadavek vzájemného ověřování, který je přísnější než požadavek na ověření cílového serveru.|  
|ProxyImpersonationLevelMismatch|Pověření pro ověření proxy serveru HTTP určilo omezení úrovně zosobnění, který je přísnější než omezení ověření cílového serveru.|  
|SecureChannelFailure|Nelze vytvořit zabezpečený kanál pro Secure Socket Layer/Transport Layer Security s zadané oprávněním.|  
|TrustFailure|Nelze navázat vztah důvěryhodnosti pro Secure Socket Layer / Transport Layer Security zabezpečený kanál pomocí zadané oprávnění.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Nelze zadat adresou explicitní proxy serveru, jakož i UseDefaultWebProxy = true v elementu vaše HttpTransportBinding.|
