---
title: Rozšířená ochrana pro ověřování – přehled
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: 400bf7987b5fcd4ec75628d19a30739dd5f23b08
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964600"
---
# <a name="extended-protection-for-authentication-overview"></a>Rozšířená ochrana pro ověřování – přehled
Rozšířená ochrana pro ověřování pomáhá chránit před útoky typu MITM (man-in-the-middle), kdy útočník zachytí přihlašovací údaje klienta a předá je serveru.  
  
 Vezměte v úvahu scénář se třemi účastníky: klienta, server a útočník. Server má `https://server`URL, zatímco má útočník `https://attacker`adresu URL. Útočník získá klientovi přístup k útočníkovi, jako by se jednalo o server. Útočník pak odešle požadavek na server. Pokud se útočník pokusí získat přístup k zabezpečenému prostředku, server odpoví na útočníka pomocí hlavičky WWW-Authenticate. Útočník neobsahuje informace o ověřování, takže pošle záhlaví WWW-Authenticate na klienta. Klient pošle autorizační hlavičku a útočník odešle hlavičku na server a získá přístup k zabezpečeným prostředkům pomocí přihlašovacích údajů klienta.  
  
 V současné době se v případě, že se klientská aplikace sám ověřuje na serveru pomocí protokolu Kerberos, Digest nebo NTLM pomocí protokolu HTTPS, je nejprve vytvořen kanál TLS (Transport Level Security) a probíhá ověřování pomocí tohoto kanálu. Neexistuje ale žádná vazba mezi klíčem relace generovaným protokolem SSL (Secure Sockets Layer) (SSL) a klíčem relace, který se generuje při ověřování. Takže v předchozím scénáři platí, že pokud komunikace probíhá přes TLS (například kanál HTTPS), vytvoří se dva kanály SSL: jeden mezi klientem a útočníkem a druhý mezi útočníkem a serverem. Přihlašovací údaje klienta se odesílají z klienta na server nejdřív přes kanál SSL mezi klientem a útočníkem a potom přes kanál mezi útočníkem a serverem. Jakmile přihlašovací údaje klienta dosáhnou serveru, Server ověří přihlašovací údaje, aniž by zjistil, že kanál, přes který se tyto přihlašovací údaje poslal, byl útočníkem, a ne klientem.  
  
 Řešením je použít vnější kanál zabezpečený protokolem TLS a interní kanál ověřený klientem a předat token vazby kanálu (CBT) na server. CBT je vlastnost vnějšího kanálu zabezpečený protokolem TLS a používá se k navázání vnějšího kanálu ke konverzaci přes interní kanál ověřený klientem.  
  
 V předchozím scénáři se CBT kanálu TLS klienta na straně klienta slučuje s autorizačními informacemi, které se odesílají na server. Server s CBT porovnává CBT obsažený v informacích o ověřování klienta, které odpovídají kanálu pro útočníka klienta, k CBT připojenému k kanálu útočníka-Server. CBT je specifický pro cíl kanálu, takže se CBT klienta neshoduje s útočníkem-serverem CBT. To umožňuje serveru detekovat MITM útok a odmítnout žádost o ověření.  
  
 Strana klienta nevyžaduje žádné nastavení konfigurace. Po aktualizaci klienta, aby předal CBT serveru, to vždy udělá. Pokud byl server také aktualizován, lze jej nakonfigurovat tak, aby používal rozhraní CBT, nebo jej ignorovat. Pokud nebyla aktualizována, bude ignorována.  
  
 Server může mít následující úrovně ochrany:  
  
- Žádné Neprovádí se ověřování vazby kanálu. To je chování všech serverů, které nebyly aktualizovány.  
  
- Částečné. Všichni klienti, kteří byli aktualizováni, musí poskytovat informace o vazbě kanálu na server. Klienti, kteří nebyli aktualizováni, to nemusí dělat. Toto je mezilehlá možnost, která umožňuje kompatibilitu aplikací.  
  
- Kompletní. Všichni klienti musí poskytovat informace o vazbě kanálu. Server odmítne žádosti o ověření od klientů, kteří to nedělají.  
  
 Další informace najdete v ukázce CBT/rozšířené ochrany pro Win7.  
  
## <a name="see-also"></a>Viz také:

- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
