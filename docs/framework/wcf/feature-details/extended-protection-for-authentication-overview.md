---
title: Rozšířená ochrana pro ověřování – přehled
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5b4abd570f8bb40f2faa72f2debf2dee563d3a23
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526598"
---
# <a name="extended-protection-for-authentication-overview"></a>Rozšířená ochrana pro ověřování – přehled
Rozšířená ochrana ověřování pomáhá chránit před útoky (typu MITM) man-in-the-middle, při které útočník zachycuje přihlašovací údaje klienta a předává je na serveru.  
  
 Představte si třeba situaci s tři účastníky, kterými: klienta, server a útočník. Adresa URL má server `https://server`, že adresa URL má útočník `https://attacker`. Útočník triky klienta do přístup k útočník, jako kdyby byly na serveru. Útočník pak odešle požadavek na server. Pokud se útočník pokouší o přístup k zabezpečení prostředků, server odpoví útočníkovi s hlavičku WWW-Authenticate. Útočník nemá informace o ověřování, takže pošle hlavičku WWW-Authenticate ke klientovi. Klient odešle autorizační hlavičky pro útočníka a útočník hlavičku na server a získá přístup k zabezpečeným prostředkům pomocí přihlašovacích údajů klienta.  
  
 Když klientská aplikace ověří na serveru pomocí protokolu Kerberos, Digest nebo NTLM pomocí protokolu HTTPS, v současné době kanálu úroveň zabezpečení TLS (Transport) je prvním vytváření a ověřování probíhá pomocí tohoto kanálu. Neexistuje ale žádná vazba mezi vygenerované pomocí vrstvy SSL (Secure Sockets) klíč relace a klíče relace, který je generován během ověřování. Tak, v předchozím scénáři, pokud komunikace přes protokol TLS (např. kanál protokolu HTTPS), trvá míst existují dva kanály SSL vytvořili: jeden mezi klientem a útočník a jiné mezi útočník a serverem. Přihlašovací údaje klienta jsou odeslaných z klienta na server nejprve prostřednictvím kanálu SSL mezi klientem a útočník a potom prostřednictvím kanálu mezi útočník a serverem. Jakmile přihlašovací údaje klienta spojit se serverem, server ověřuje přihlašovací údaje bez detekuje, že kanál nad tím, které byly odeslány tyto přihlašovací údaje pochází ze útočník a ne klienta.  
  
 Řešením je použití vnějšího kanál TLS zabezpečené a ověření klienta vnitřního kanálu a předat kanálu vazby Token (CBT) na server. CBT je vlastnost kanálu vnější zabezpečené TLS a slouží k vytvoření vazby na vnější kanál ke konverzaci přes kanál vnitřní ověření klienta.  
  
 V předchozím scénáři CBT kanál TLS klienta útočník sloučeny s informace o ověření, která je odeslána na server. Porovná s ohledem na CBT server CBT obsažené v informace o ověřování klienta odpovídá klienta útočník kanál, CBT připojená ke kanálu útočník serveru. CBT je specifický pro určení nějaký kanál, takže útočník klienta CBT neodpovídá server útočník CBT. To umožňuje serveru zjistit útoky MITM a odmítnout žádosti o ověření.  
  
 Na straně klienta nevyžaduje, aby všechna nastavení konfigurace. Jakmile klient byl aktualizován CBT předat serveru, vždy provádí. Pokud na serveru se také aktualizovala, dá se použít CBT nebo ji ignorovat. Pokud ho ještě není aktualizovaný, ignoruje se.  
  
 Server může mít následující úrovně ochrany:  
  
-   Žádné Provede se žádné ověření vazby kanálu. Toto je chování ve všech serverech, které nebyly aktualizovány.  
  
-   Částečné. Všichni klienti, kteří se aktualizovaly musíte zadat informace o vazbě kanál na server. Klienti, kteří neprovedli aktualizaci není potřeba udělat. Toto je zprostředkující možnost, která umožňuje pro zajištění kompatibility aplikací.  
  
-   Úplná. Všichni klienti musí poskytnout informace o vazbě kanálu. Server odmítá žádosti o ověření z klientů, kteří tak.  
  
 Další informace najdete v ukázce Win7 CBT/Rozšířená ochrana.  
  
## <a name="see-also"></a>Viz také  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
