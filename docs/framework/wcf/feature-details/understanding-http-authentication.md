---
title: "Princip ověřování HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8e1c299e58f83807689f71ded2dec569e6c70015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-http-authentication"></a>Princip ověřování HTTP
Ověřování je proces identifikace, zda je vhodné pro přístup k prostředkům klienta. Protokol HTTP podporuje ověřování jako způsob vyjednávání přístup k zabezpečení prostředků.  
  
 Počáteční žádosti z klienta je obvykle požadavek anonymní, neobsahující žádné informace o ověřování. Aplikace serveru HTTP můžete odepřít, že je vyžadován anonymní požadavek při označující, že ověřování. Aplikace serveru odešle hlavičky WWW-ověřování k označení schémat podporované ověřování. Tento dokument popisuje několik schémat ověřování pro protokol HTTP a popisuje jejich podpora v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="http-authentication-schemes"></a>Schémat ověřování protokolu HTTP  
 Server můžete určit více schémat ověřování pro klienta lze vybírat. Následující tabulka popisuje některé schémat ověřování, které jsou běžně součástí aplikací systému Windows.  
  
|Schéma ověřování|Popis|  
|---------------------------|-----------------|  
|Anonymní|Žádost o anonymní neobsahuje žádné informace o ověřování. Jde o ekvivalent udělení všem uživatelům přístup k danému prostředku.|  
|Základní|Základní ověřování odešle řetězec s kódováním Base64, obsahující uživatelské jméno a heslo pro klienta. Base64 není šifrování a by se měly zvažovat stejná jako odesílání uživatelské jméno a heslo ve formátu prostého textu. Pokud prostředek je potřeba chránit, důrazně zvažte použití příslušné schéma ověřování než základní ověřování.|  
|Ověřování algoritmem Digest|Ověřování hodnotou hash je výzvy a odezvy schématu, která má nahradit základní ověřování. Server odešle řetězec náhodná data názvem *hodnotu nonce* klientovi jako výzvu. Klient odpoví hodnotu hash, která obsahuje uživatelské jméno, heslo a hodnotu nonce mezi Další informace. Složitost, kterou představuje tento exchange a dat, výpočtu hodnoty hash je obtížné více ukrást a opakovaně používat přihlašovací údaje uživatele se toto schéma ověřování.<br /><br /> Ověřování algoritmem Digest vyžaduje použití účtů domény Windows. Daný výtah *sféry* je název domény systému Windows. Proto nelze použít server běžící na operační systém, který nepodporuje domény systému Windows, například Windows XP Home Edition s ověřování hodnotou hash. Naopak pokud klient se spouští na operační systém, který nepodporuje doménách systému Windows, účet domény musí být explicitně zadaná během ověřování.|  
|NTLM|NT LAN Manager (NTLM) authentication je schéma výzvy a odezvy, který je securer varianta ověřování hodnotou hash. NTLM používá přihlašovací údaje systému Windows pro transformaci dat výzvy místo nekódovaného uživatelské jméno a heslo. Ověřování protokolem NTLM vyžaduje víc výměn mezi klientem a serverem. Server a všechny použité proxy musí podporovat trvalé připojení k úspěšnému provedení ověřování.|  
|Vyjednávání|Vyjednávání ověřování automaticky vybere mezi protokolu Kerberos a ověřování NTLM, v závislosti na dostupnosti. Protokol Kerberos se používá, pokud je k dispozici. v opačném případě se pokus o protokolu NTLM. Ověřování protokolem Kerberos se výrazně zvyšuje na protokol NTLM. Ověřování protokolem Kerberos se rychleji než pomocí protokolu NTLM a umožňuje použití vzájemného ověření a delegování pověření na vzdálených počítačích.|  
|Windows Live ID|Základní služba Windows HTTP zahrnuje ověřování pomocí protokolů federované. Přenosy, ale standardního protokolu HTTP v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepodporují použití schémat federovaného ověřování, jako je například Microsoft Windows Live ID. Podpora pro tuto funkci je aktuálně k dispozici prostřednictvím zabezpečení zpráv. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Výběr příslušné schéma ověřování  
 Když vyberete potenciální schémat ověřování pro HTTP server, několik položek vzít v úvahu, patří:  
  
-   Zvažte, zda prostředek je potřeba chránit. Pomocí ověřování protokolu HTTP vyžaduje přenáší další data a můžete omezit interoperability s klienty. Povolí anonymní přístup k prostředkům, které nemusí být chráněny.  
  
-   Pokud prostředek je potřeba chránit, zvažte, které schémat ověřování, zadejte požadované úrovni zabezpečení. Schéma nejslabších standardní ověřování tady popisovaných je základní ověřování. Základní ověřování nechrání přihlašovacích údajů uživatele. Nejsilnější standardní ověřování je Negotiate ověřování, což je protokol Kerberos.  
  
-   Server by neměl k dispozici (v hlavičky WWW-ověřování) žádné schéma, které není připraven přijímat nebo který nezabezpečuje adekvátní k chráněnému prostředku. Klienti mohou zvolit žádné ze serveru představuje schémat ověřování. Některé klienty výchozí schéma slabé ověřování nebo první schéma ověřování v seznamu serveru.  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Použití zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
