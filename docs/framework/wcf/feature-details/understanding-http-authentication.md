---
title: Princip ověřování HTTP
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: ebfb5920fcd5c1a8faac8780dc1c32c92f9f6255
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614813"
---
# <a name="understanding-http-authentication"></a>Princip ověřování HTTP
Ověřování je proces určit, jestli je klient oprávnění pro přístup k prostředku. Protokol HTTP podporuje ověřování jako způsob vyjednávání přístup k zabezpečené prostředku.  
  
 Počáteční žádosti od klientů je obvykle anonymní žádosti, neobsahuje informace o ověřování. Aplikace serveru HTTP můžete zakázat anonymní žádosti při označující, že ověřování je vyžadováno. Serverová aplikace odešle hlavičky WWW-ověřování k označení schémata podporované metody ověřování. Tento dokument popisuje více schémat ověřování protokolu HTTP a jejich podpora Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Schémata ověřování protokolu HTTP  
 Server můžete určit více schémat ověřování klienta lze vybírat. Následující tabulka popisuje některé z ověřovací schémata běžně nacházejí v aplikacích Windows.  
  
|Schéma ověřování|Popis|  
|---------------------------|-----------------|  
|Anonymní|Anonymní žádosti neobsahuje informace o ověřování. Jedná se o ekvivalent k poskytování všem uživatelům přístup k prostředku.|  
|Základní|Základní ověřování odešle řetězec s kódováním Base64, který obsahuje uživatelské jméno a heslo pro tohoto klienta. Ve formátu Base64 není formu šifrování a by měl být stejný jako odesílání uživatelské jméno a heslo ve formátu prostého textu. Pokud prostředek je potřeba chránit, důkladně zvážit možnost pomocí ověřovacího schématu než základní ověřování.|  
|ověřování algoritmem Digest|Ověřování hodnotou hash je schéma odpověď výzvy, která je určena k nahrazení základní ověřování. Server odešle řetězec náhodných dat s názvem *nonce* ke klientovi jako náročné. Klientovi jako odpověď vrátí hodnotu hash, která obsahuje uživatelské jméno, heslo a hodnota nonce, mezi Další informace. Složitost, kterou představuje tento exchange a dat hash to ztížit krádež a opakované použití přihlašovacích údajů uživatele v tomto schématu ověřování.<br /><br /> Ověřování algoritmem Digest vyžaduje použití účtů domény Windows. Algoritmus digest *sféry* je název domény Windows. Proto nelze použít server spuštěný v operačním systému, který nepodporuje domény Windows, jako jsou Windows XP Home Edition s ověřováním algoritmem Digest. Naopak pokud klienta běží na operačním systému, který nepodporuje domény Windows, účet domény musí být explicitně zadán během ověřování.|  
|NTLM|NT LAN Manager (NTLM) authentication je – výzva odezva schéma, které je securer variantou ověřování hodnotou hash. NTLM používá přihlašovací údaje Windows k transformaci dat challenge místo nekódovaného uživatelské jméno a heslo. Ověřování protokolem NTLM vyžaduje více výměn mezi klientem a serverem. Server a všechny použité proxy musí podporovat trvalé připojení pro úspěšné dokončení ověření.|  
|Vyjednávání|Vyjednávání automaticky vybere ověřování mezi protokolu Kerberos a ověřování protokolem NTLM, v závislosti na dostupnosti. Protokol Kerberos se používá, pokud je k dispozici. v opačném případě se pokusila NTLM. Ověřování protokolem Kerberos výrazně vylepšuje NTLM. Ověřování pomocí protokolu Kerberos je rychlejší než NTLM a umožňuje použití vzájemného ověření a delegování pověření na vzdálených počítačích.|  
|Windows Live ID|Základní služba Windows HTTP zahrnuje ověřování s použitím federovaného protokoly. Standardní přenosy HTTP ve službě WCF však nepodporují použití metody federované ověřování, jako je například Microsoft Windows Live ID. Podpora pro tuto funkci je momentálně dostupná prostřednictvím zabezpečení zpráv. Další informace najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Volba režimu ověřování  
 Při výběru potenciální schémat ověřování pro HTTP server, několik položek, které byste měli zvážit, patří:  
  
- Zvažte, zda prostředek, který je potřeba chránit. Použití ověřování pomocí protokolu HTTP vyžaduje přenáší další data a můžete omezte vzájemná funkční spolupráce s klienty. Povolit anonymní přístup k prostředkům, které není potřeba chránit.  
  
- Pokud prostředek je potřeba chránit, vezměte v úvahu které režimy ověřování poskytovat požadované úrovni zabezpečení. Základní ověřování je nejslabší schéma standardní ověřování zde popsané. Základní ověřování neposkytuje ochranu přihlašovacích údajů uživatele. Nejsilnější standardní ověřování je Negotiate ověřování, což vede k protokolu Kerberos.  
  
- Server nesmí prezentovat (hlavičky WWW-ověřování) žádné schéma, které není připraveno přijmout nebo který nezabezpečuje adekvátní chráněnému prostředku. Klienti jsou zdarma si vybrat mezi všechny ověřovací schémata prezentuje serveru. Některé klienty výchozí schéma slabé ověřování nebo první schéma ověřování v seznamu na serveru.  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)
- [Použití zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
