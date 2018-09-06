---
title: Zabezpečení zpráv ve WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 81d9acde3c8fab1860904074199066cca55c7186
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886182"
---
# <a name="message-security-in-wcf"></a>Zabezpečení zpráv ve WCF
Windows Communication Foundation (WCF) má dva hlavní režimy pro zajištění zabezpečení (`Transport` a `Message`) a třetí režimu (`TransportWithMessageCredential`), který kombinuje dvě. Toto téma popisuje zabezpečení zpráv a důvodů, proč ho použít.  
  
## <a name="what-is-message-security"></a>Co je zpráva Security?  
 Zabezpečení zpráv specifikaci WS-Security používá k zabezpečení zprávy. WS-Securityspecification popisuje vylepšení protokolu SOAP zprávy k zajištění důvěrnost, integritu a ověřování na úrovni zprávy protokolu SOAP (aniž byste museli transportní).  
  
 Stručně řečeno zabezpečení zprávy se liší od zabezpečení přenosu zapouzdřením zabezpečovací přihlašovací údaje a deklarací identity s každou zprávu a ochranu zprávy (podepisování nebo šifrování). Použití zabezpečení přímo na tuto zprávu tak, že upravíte jeho obsah umožňuje zabezpečené zpráva, která má být místním obsahující s ohledem na aspekty zabezpečení. To umožňuje několik scénářů, které nejsou možné při použití zabezpečení přenosu.  
  
## <a name="reasons-to-use-message-security"></a>Důvody pro použití zabezpečení zpráv  
 V zabezpečení na úrovni zpráv všechny informace o zabezpečení zapouzdřena ve zprávě. Zabezpečení zprávy pomocí zabezpečení na úrovni zpráv místo zabezpečení transportní vrstvy má následující výhody:  
  
-   Koncové zabezpečení. Zabezpečení přenosu, jako je například vrstvy SSL (Secure Sockets) zabezpečuje pouze zprávy, kdy je komunikace typu point-to-point. Pokud se zpráva směruje do jedné nebo více zprostředkovatelů SOAP (například router) před dosažením konečného příjemce, vlastní zprávě není chráněný, jakmile prostředník načtení z přenosu. Kromě toho informace o ověřování klienta je dostupná jenom pro první zprostředkovatel a musí být znovu předány ultimate příjemce out-of-band způsobem, v případě potřeby. To platí i v případě, že celý tras využívá zabezpečení SSL mezi jednotlivé segmenty směrování. Protože zabezpečení zpráv pracuje přímo s touto zprávou a zabezpečuje XML v ní, zůstane zabezpečení se zprávy bez ohledu na to, kolik zprostředkovatelů se využívá řada předtím, než dosáhne konečného příjemce. To umožňuje scénáře true zabezpečení začátku do konce.  
  
-   Vyšší flexibilita. Části zprávy, ne celou zprávu, může být podepsána nebo zašifrována. To znamená, že prostředníci části lze zobrazit na zprávy, které jsou určeny pro ně. Pokud odesílatel potřeba zviditelnit část informace ve zprávě dodavatelů ale chce mít jistotu, že se manipulovalo, lze pouze podepište ho ale ponechte bez šifrování. Podpis je část zprávy, můžete ověřit, že informace ve zprávě byla přijata Internet ultimate příjemce. Jeden scénář může být SOAP zprostředkovatele služby této zprávy trasy podle hodnotu záhlaví akce. Ve výchozím nastavení WCF, nešifruje hodnotu akce ale podepíše ho, pokud se používá zabezpečení zpráv. Proto tyto informace jsou k dispozici pro všech zprostředkovatelů, ale nikdo ho změnit.  
  
-   Podpora více přenosy. Odesílat zprávy o zabezpečené přes mnoho různých přenosy, jako jsou pojmenované kanály a protokol TCP, aniž byste museli spoléhat na protokol pro zabezpečení. Zabezpečení transportní vrstvy všechny informace o zabezpečení působí na jednoho konkrétního přenosového připojení a není k dispozici od samotného obsahu zprávy. Zabezpečení zpráv díky zprávu zabezpečení bez ohledu na to, jaký přenos použijete k přenosu zprávy a kontext zabezpečení je přímo vložena do zprávy.  
  
-   Podpora pro celou sadu přihlašovacích údajů a deklarací identity. Zabezpečení zpráv podle specifikace WS-Security, které poskytuje rozšiřitelný rámec přenášet libovolného typu deklarace identity uvnitř zprávy protokolu SOAP. Na rozdíl od zabezpečení přenosu není sadu ověřovacích mechanismů nebo deklarací identity, které můžete použít omezeno funkce přenosu. Zabezpečení zpráv WCF obsahuje více typů ověřování a deklarace identity přenosu a je možné rozšířit podporu dalších typů podle potřeby. Z těchto důvodů například, federované pověření scénář není možná bez zabezpečení zpráv. Další informace o federace scénáře WCF podporuje, najdete v části [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Porovnání zprávu a zabezpečení přenosu  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Výhody a nevýhody zabezpečení transportní vrstvy  
 Zabezpečení přenosu má následující výhody:  
  
-   Nevyžaduje, aby komunikujících stran koncepce XML úroveň zabezpečení. Zlepšíte tím vzájemná funkční spolupráce, například při použití protokolu HTTPS k zabezpečení komunikace.  
  
-   Obecně vylepšení výkonu.  
  
-   Hardwarové akcelerátory jsou k dispozici.  
  
-   Streamování je možné.  
  
 Zabezpečení přenosu má následující nevýhody:  
  
-   Směrování na směrování pouze.  
  
-   Množství dat a inextensible sadu přihlašovacích údajů.  
  
-   Přenos závislé.  
  
### <a name="disadvantages-of-message-level-security"></a>Nevýhody zabezpečení na úrovni zpráv  
 Zabezpečení zpráv má následující nevýhody:  
  
-   Výkon  
  
-   Nelze použít datový proud zprávy.  
  
-   Vyžaduje implementaci mechanismy zabezpečení na úrovni XML a podpora pro specifikaci WS-Security. To může mít vliv na interoperability.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices kapitola 3: implementace přenosu a zpráva vrstvy zabezpečení](https://go.microsoft.com/fwlink/?LinkId=88897)
