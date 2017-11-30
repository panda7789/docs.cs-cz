---
title: "Základní komunikace: HTTP HTTPS přenosové kanály"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9fc16bb6bd512c424f2b3630f7bb6d0614bb067
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-httphttps-transport-channels"></a>Základní komunikace: Protokolu HTTP nebo HTTPS přenosové kanály
Toto téma uvádí všechny výjimky generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] přenosové kanály protokolu HTTP nebo HTTPS.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Úroveň zosobnění zadaný byla zadána. Ověřování hodnotou hash HTTP podporuje pouze úroveň 'Zosobnění' při použití s explicitní přihlašovací údaje.|  
|FramingContentTypeMismatch|Zadaná služba nepodporuje zadaný typ obsahu. Může být neshoda vazby klienta a služby.|  
|Hosting_SslSettingsMisconfigured|Nastavení protokolu SSL pro službu zadaný neodpovídají definicím služby IIS.|  
|HttpAuthSchemeAndClientCert|Objekt factory naslouchací proces HTTPS byla nakonfigurována tak, aby vyžadovala klientský certifikát a zadané schéma ověřování. Ale pouze jednu formu ověření klienta, může být nutná najednou.|  
|HttpReceiveFailure|Došlo k chybě při přijímání odpověď HTTP do zadané. Vazby koncového bodu služby, nemusí být pomocí protokolu HTTP. Další možností je, že kontext požadavku protokolu HTTP se ukončila serverem kvůli vypnutí služby. Zobrazit další podrobnosti v protokolech serveru.|  
|HttpRegistrationAccessDenied|HTTP nelze zaregistrovat zadanou adresu URL. Váš proces nemá přístupová práva na tento obor názvů (viz http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp podrobnosti).|  
|HttpRegistrationAlreadyExists|HTTP nelze zaregistrovat zadanou adresu URL. Jiná aplikace již zaregistrován tuto adresu URL s protokolem HTTP. SYS.|  
|HttpRegistrationPortInUse|HTTP nelze zaregistrovat zadanou adresu URL, protože je zadaný port TCP používá jiná aplikace.|  
|HttpSendFailure|Došlo k chybě při vytváření zadaný požadavek HTTP. Zkontrolujte, zda je příčinou není neshodou vazeb zabezpečení. Ujistěte se také, že služba není nakonfigurována pro Secure Sockets Layer.|  
|MessageXmlProtocolError|Vyskytl se problém se souborem XML, který jste získali od sítě. Viz vnitřní výjimka další podrobnosti.|  
|MissingContentType|Příjemce vrátila chybu, která znamená, že byla v požadavku na zadaný typ obsahu. Viz vnitřní výjimka Další informace.|  
|ProxyAuthenticationLevelMismatch|Zadat pověření pro ověření proxy serveru HTTP požadavek vzájemné ověřování, který je přísnější než požadavek na ověření cílového serveru.|  
|ProxyImpersonationLevelMismatch|Zadat pověření pro ověření proxy serveru HTTP úrovně omezení zosobnění, který je přísnější než omezení pro ověření cílového serveru.|  
|SecureChannelFailure|Nelze vytvořit zabezpečený kanál pro Secure Socket Layer/Transport Layer Security s zadaný autoritou.|  
|TrustFailure|Nelze navázat vztah důvěryhodnosti pro Secure Socket Layer / Transport Layer Security zabezpečený kanál s zadaný autoritou.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Nelze zadat adresou explicitní proxy serveru, jakož i UseDefaultWebProxy = true v vaší HttpTransportBinding elementu.|
