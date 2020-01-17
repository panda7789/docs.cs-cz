---
title: Zabezpečení zpráv ve WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 32f6659f6ac744ab7af07c23e7e26ea1124d020c
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212074"
---
# <a name="message-security-in-wcf"></a>Zabezpečení zpráv ve WCF

Windows Communication Foundation (WCF) má dva hlavní režimy pro poskytování zabezpečení (`Transport` a `Message`) a třetí režim (`TransportWithMessageCredential`), který kombinuje tyto dvě. Toto téma popisuje zabezpečení zpráv a důvody jejich použití.

## <a name="what-is-message-security"></a>Co je zabezpečení zpráv?

Zabezpečení zpráv používá ke zabezpečování zpráv specifikaci WS-Security. Specifikace WS-Security popisuje vylepšení zasílání zpráv SOAP, aby se zajistila důvěrnost, integrita a ověřování na úrovni zprávy protokolu SOAP (místo úrovně Transport).

V krátkém případě se zabezpečení zpráv liší od zabezpečení přenosu tím, že zapouzdřuje zabezpečovací přihlašovací údaje a deklarace identity se všemi zprávami, a to prostřednictvím jakékoli ochrany zpráv (podepisování nebo šifrování). Použití zabezpečení přímo na zprávu změnou jejího obsahu umožňuje, aby zabezpečená zpráva obsahovala vlastní obsah v souvislosti s aspekty zabezpečení. To umožňuje některé scénáře, které nejsou možné při použití zabezpečení přenosu.

## <a name="reasons-to-use-message-security"></a>Důvody pro použití zabezpečení zpráv

V zabezpečení na úrovni zprávy jsou všechny informace o zabezpečení zapouzdřeny ve zprávě. Zabezpečení zprávy se zabezpečením na úrovni zpráv místo zabezpečení na úrovni přenosu má následující výhody:

- Komplexní zabezpečení. Zabezpečení přenosu, jako je například SSL (Secure Sockets Layer) (SSL), zabezpečuje pouze zprávy v případě, že komunikace je typu Point-to-Point. Pokud je zpráva směrována do jednoho nebo více zprostředkovatelů protokolu SOAP (například směrovače) předtím, než se dostane k konečnému přijímači, samotná zpráva není chráněna, jakmile ji zprostředkovatel přečte z tohoto propojení. Kromě toho jsou informace o ověřování klientů k dispozici pouze prvnímu zprostředkovateli a musí být v případě potřeby znovu přeneseny na konečného příjemce v nedostatku pásma. Platí to i v případě, že celá trasa používá zabezpečení SSL mezi jednotlivými segmenty směrování. Vzhledem k tomu, že zabezpečení zprávy funguje přímo se zprávou a zabezpečuje XML v něm, zabezpečení zůstává u zprávy bez ohledu na to, kolik zprostředkovatelů je zapojeno, než dosáhne konečného přijímače. To umožňuje skutečný scénář zabezpečení na konci.

- Vyšší flexibilita. Části zprávy místo celé zprávy mohou být podepsány nebo zašifrovány. To znamená, že prostředníci můžou zobrazit části zprávy, které jsou pro ně určené. Pokud odesílatel potřebuje, aby se informace ve zprávě viditelně zobrazovaly pro zprostředkovatele, ale chce se ujistit, že není manipulováno, může ho pouze podepsat, ale nechat ho nezašifrovaný. Vzhledem k tomu, že signatura je součástí zprávy, může konečný přijímač ověřit, zda informace ve zprávě byly přijaty beze změny. Jeden scénář může mít zprostředkující službu SOAP, která směruje zprávu podle hodnoty hlavičky Action. Ve výchozím nastavení služba WCF nešifruje hodnotu akce, ale podepíše ji, pokud se používá zabezpečení zprávy. Tyto informace jsou proto k dispozici všem zprostředkovatelům, ale nikdo je nemůže změnit.

- Podpora pro více přenosů. Můžete odesílat zabezpečené zprávy přes mnoho různých přenosů, jako jsou pojmenované kanály a TCP, aniž byste se museli spoléhat na zabezpečení protokolu. U zabezpečení na úrovni přenosu jsou všechny informace o zabezpečení vymezeny na jedno konkrétní přenosové připojení a nejsou dostupné přímo z samotného obsahu zprávy. Zabezpečení zpráv zajišťuje zabezpečenou zprávu bez ohledu na to, jaký přenos použijete k přenosu zprávy, a kontext zabezpečení je přímo vložen do zprávy.

- Podpora pro rozsáhlou sadu přihlašovacích údajů a deklarací identity. Zabezpečení zpráv je založeno na specifikaci WS-Security, která poskytuje rozšiřitelnou architekturu, která dokáže přenášet jakýkoli typ deklarace identity uvnitř zprávy protokolu SOAP. Na rozdíl od zabezpečení přenosu není sada mechanismů ověřování nebo deklarací identity, které můžete použít, omezené funkcemi přenosu. Zabezpečení zpráv WCF zahrnuje několik typů ověřování a přenos nároků a v případě potřeby je můžete rozšířit na podporu dalších typů. Z těchto důvodů je například možné, že se nejedná o scénář federovaných přihlašovacích údajů bez zabezpečení zpráv. Další informace o federačních scénářích, které podporuje WCF, najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).

## <a name="how-message-and-transport-security-compare"></a>Jak se porovnávají zabezpečení zpráv a přenosů

### <a name="pros-and-cons-of-transport-level-security"></a>Specialisté a nevýhody zabezpečení na úrovni přenosu

Zabezpečení přenosu má následující výhody:

- Nevyžaduje, aby komunikující strany rozuměly koncepcím zabezpečení na úrovni XML. To může zlepšit interoperabilitu, například při použití protokolu HTTPS k zabezpečení komunikace.

- Obecně Vylepšený výkon.

- Jsou k dispozici hardwarové akcelerátory.

- Streamování je možné.

 Zabezpečení přenosu má následující nevýhody:

- Pouze segment směrování na směrování.

- Omezená a nerozšiřitelná sada přihlašovacích údajů.

- Závislý na přenosu.

### <a name="disadvantages-of-message-level-security"></a>Nevýhody zabezpečení na úrovni zpráv

Zabezpečení zpráv má následující nevýhody:

- Výkon

- Nelze použít streamování zpráv.

- Vyžaduje implementaci mechanismů zabezpečení na úrovni XML a podporu specifikace WS-Security. To může mít vliv na interoperabilitu.

## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Vzory a postupy Microsoft, kapitola 3: implementace přenosu a zabezpečení vrstvy zpráv](https://docs.microsoft.com/previous-versions/msp-n-p/ff647370(v=pandp.10))
