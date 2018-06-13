---
title: Zabezpečení zpráv ve WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 27f8354cf4d96f8da408cffa3cef42ab9609c76d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493888"
---
# <a name="message-security-in-wcf"></a>Zabezpečení zpráv ve WCF
Windows Communication Foundation (WCF) má dva hlavní režimy pro zajištění zabezpečení (`Transport` a `Message`) a třetí režim (`TransportWithMessageCredential`), kombinací obou. Toto téma popisuje zabezpečení zpráv a důvodů, proč ji používat.  
  
## <a name="what-is-message-security"></a>Co je zabezpečení zpráv?  
 Zabezpečení zpráv pomocí specifikace WS-zabezpečení zabezpečené zprávy. WS-Securityspecification popisuje vylepšení protokolu SOAP zprávy k zajištění důvěrnosti, integrity a ověřování na úrovni protokolu SOAP zprávy (namísto transportní).  
  
 Stručně řečeno zabezpečení zpráv se liší od zabezpečení přenosu zapouzdřením zabezpečovací přihlašovací údaje a deklarací identity s každou zprávu společně s ochranu zprávy (podepisování nebo šifrování). Použití zabezpečení přímo na zprávu změnou jeho obsah umožňuje zabezpečené zpráva, která má být samoobslužné obsahující s ohledem na aspekty zabezpečení. To umožňuje některé scénáře, které nejsou možné, pokud se používá zabezpečení přenosu.  
  
## <a name="reasons-to-use-message-security"></a>Důvody pro použití zabezpečení zpráv  
 V zabezpečení na úrovni zpráv všechny informace o zabezpečení je zapouzdřený ve zprávě. Zabezpečení zprávy se zabezpečením na úrovni zpráv místo zabezpečení na úrovni přenosu má následující výhody:  
  
-   Koncové zabezpečení. Zabezpečení přenosu, například vrstvy SSL (Secure Sockets) pouze zabezpečuje zprávy, když komunikace typu point-to-point. Pokud zpráva se směruje na jeden nebo více SOAP prostředníci (například router) dříve, než dorazila ultimate příjemce, samotné zprávy není chráněný, jakmile prostředník se čte z přenosu. Informace o ověřování klienta kromě toho je k dispozici pouze první zprostředkovatel a je třeba znovu přenést k příjemce ultimate způsobem out-of-band, v případě potřeby. To platí i v případě, že celá trasy, která používá zabezpečení SSL mezi jednotlivé směrování. Vzhledem k zabezpečení zpráv pracuje přímo s zprávu a zabezpečuje XML v něm, zůstává zabezpečení se zprávou bez ohledu na to, kolik prostředníci jsou související se situací, než dorazí ultimate příjemce. To umožňuje scénáři true-koncové zabezpečení.  
  
-   Vyšší flexibilita. Součástí zprávy, místo celé zprávy, může být podepsána nebo zašifrována. To znamená, že prostředníci můžete zobrazit části zprávy, které jsou určeny pro ně. Pokud odesílatel musí zpřístupněte součástí informace ve zprávě dodavatelů ale chce zajistit, že není manipulováno, je právě podepište ho ale ponechte bez šifrování. Vzhledem k tomu, že podpisu je součástí zprávy, ultimate příjemce může ověřit, že informace ve zprávě byla přijata Internet nedotčené. Jeden scénář pravděpodobně SOAP prostředník, služby směrování zprávy podle hodnota hlavičky akce. Ve výchozím nastavení WCF nešifruje hodnotu akce ale podepíše ho, pokud se používá k zabezpečení zpráv. Proto tyto informace jsou k dispozici pro všechny prostředníci, ale nikdo můžete ho změnit.  
  
-   Podpora pro více přenosy. Můžete odeslat zabezpečené zprávy přes mnoho různých přenosy, jako jsou pojmenované kanály a TCP, aniž byste museli spoléhat na protokol pro zabezpečení. Zabezpečení transportní vrstvy všechny informace o zabezpečení je omezená na jedno konkrétní přenosové spojení a není k dispozici z samotný obsah zprávy. Zabezpečení zpráv umožňuje zprávu zabezpečení bez ohledu na to, jaký přenos použijete k přenosu zprávy a kontext zabezpečení je přímo vložena do zprávy.  
  
-   Podpora pro celou sadu přihlašovacích údajů a deklarace identity. Specifikaci WS-zabezpečení, která poskytuje rozšiřitelný rámec přenášet libovolného typu deklarace identity uvnitř zprávu SOAP vychází zabezpečení zpráv. Na rozdíl od zabezpečení přenosu není omezený sadu mechanismy ověřování nebo deklarace identity, které můžete použít možnosti přenosu. Zabezpečení zpráv WCF obsahuje více typů ověřování a deklarace identity přenos a lze rozšířit na podporovat další typy podle potřeby. Z těchto důvodů například, scénáři federované přihlašovacích údajů není možné bez zabezpečení zpráv. Další informace o federační scénáře WCF podporuje, naleznete v části [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Jak porovnat zprávu a zabezpečení přenosu  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Výhody a nevýhody zabezpečení transportní vrstvy  
 Zabezpečení přenosu má následující výhody:  
  
-   Nevyžaduje, aby komunikuje strany rozumět koncepty XML úroveň zabezpečení. Vzájemná funkční spolupráce, tím lze vylepšit například když HTTPS se používá k zabezpečení komunikace.  
  
-   Obecně lepší výkon.  
  
-   Hardware akcelerátorů jsou k dispozici.  
  
-   Je možné streamování.  
  
 Zabezpečení přenosu má tyto nevýhody:  
  
-   Směrování na hop jenom.  
  
-   Omezené a inextensible sadu přihlašovacích údajů.  
  
-   Přenos závislé.  
  
### <a name="disadvantages-of-message-level-security"></a>Nevýhody zabezpečení na úrovni zpráv  
 Zabezpečení zpráv má tyto nevýhody:  
  
-   Výkon  
  
-   Nelze použít vysílání datového proudu zpráv.  
  
-   Vyžaduje implementace mechanismy zabezpečení na úrovni XML a podpory pro specifikaci WS-zabezpečení. Může to mít vliv interoperabilitu.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices kapitoly 3: implementace přenosu a zpráva vrstvy zabezpečení](http://go.microsoft.com/fwlink/?LinkId=88897)
