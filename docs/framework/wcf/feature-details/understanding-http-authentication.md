---
title: Princip ověřování HTTP
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: a31c9f96185364c59dca1ff26251a30f5d7a88bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595086"
---
# <a name="understanding-http-authentication"></a>Princip ověřování HTTP
Ověřování je proces identifikace, zda má klient nárok na přístup k prostředku. Protokol HTTP podporuje ověřování jako způsob vyjednávání přístupu k zabezpečenému prostředku.  
  
 Počáteční požadavek od klienta je obvykle anonymní požadavek, který neobsahuje informace o ověřování. Aplikace serveru HTTP můžou anonymní požadavek odepřít a zároveň indikuje, že se vyžaduje ověření. Serverová aplikace odesílá hlavičky pro ověřování WWW, aby označovala podporovaná schémata ověřování. Tento dokument popisuje několik schémat ověřování pro HTTP a popisuje jejich podporu v Windows Communication Foundation (WCF).  
  
## <a name="http-authentication-schemes"></a>Schémata ověřování HTTP  
 Server může určit několik schémat ověřování, ze kterých bude klient vybírat. Následující tabulka popisuje některé z schémat ověřování, které se běžně nacházejí v aplikacích pro Windows.  
  
|Schéma ověřování|Popis|  
|---------------------------|-----------------|  
|Anonymní|Anonymní požadavek neobsahuje žádné informace o ověřování. Jedná se o ekvivalent přidělení přístupu k prostředku všem všem.|  
|Basic|Základní ověřování pošle řetězec zakódovaný ve formátu base64, který obsahuje uživatelské jméno a heslo pro klienta. Base64 není forma šifrování a měla by být považována za stejnou jako odeslání uživatelského jména a hesla v nešifrovaném textu. Pokud je potřeba chránit prostředek, důrazně zvažte použití jiného schématu ověřování než základní ověřování.|  
|Otisk|Ověřování hodnotou hash je schéma reakce na výzvy, které má za cíl nahradit základní ověřování. Server odešle klientovi jako výzvu řetězec náhodných dat nazývaných hodnotu *nonce* . Klient odpoví hodnotou hash, která obsahuje uživatelské jméno, heslo a hodnotu nonce, a to i další informace. Složitost, kterou tento Exchange zavádí, a hash dat ztěžuje zneužití přihlašovacích údajů uživatele pomocí tohoto schématu ověřování a jejich opakované použití.<br /><br /> Ověřování hodnotou hash vyžaduje použití doménových účtů systému Windows. *Sféra* Digest je název domény systému Windows. Proto nemůžete použít server, který běží na operačním systému, který nepodporuje domény systému Windows, jako je například Windows XP Home Edition, s ověřováním hodnotou Digest. Naopak, pokud klient běží na operačním systému, který nepodporuje domény Windows, musí být při ověřování explicitně zadaný účet domény.|  
|NTLM|Ověřování NT LAN Manager (NTLM) je schéma reakce na výzvy, které je bezpečnostní variací ověřování hodnotou hash. Protokol NTLM používá přihlašovací údaje systému Windows k transformaci dat výzvy místo nekódovaného uživatelského jména a hesla. Ověřování protokolem NTLM vyžaduje více výměn mezi klientem a serverem. Server a všechny jeho použité proxy servery musí podporovat trvalá připojení, aby bylo možné úspěšně dokončit ověření.|  
|Negotiate|Vyjednání ověřování automaticky vybírá mezi protokolem Kerberos a ověřováním NTLM v závislosti na dostupnosti. Protokol Kerberos se používá, pokud je k dispozici. v opačném případě se pokusí NTLM. Ověřování protokolem Kerberos se na základě protokolu NTLM významně vylepšuje. Ověřování protokolem Kerberos je rychlejší než protokol NTLM a umožňuje použití vzájemného ověřování a delegování přihlašovacích údajů na vzdálené počítače.|  
|Windows Live ID|Základní služba Windows HTTP zahrnuje ověřování pomocí federovaných protokolů. Standardní přenosy HTTP ve službě WCF ale nepodporují použití schémat federovaného ověřování, jako je Microsoft Windows Live ID. Podpora pro tuto funkci je aktuálně k dispozici prostřednictvím použití zabezpečení zpráv. Další informace najdete v tématu [federace a vystavené tokeny](federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Výběr schématu ověřování  
 Při výběru možných schémat ověřování pro server HTTP je potřeba zvážit několik položek, které je třeba vzít v úvahu:  
  
- Zvažte, jestli je potřeba chránit prostředek. Použití ověřování protokolem HTTP vyžaduje přenos více dat a může omezit spolupráci s klienty. Povolí anonymní přístup k prostředkům, které není nutné chránit.  
  
- Pokud je potřeba chránit prostředek, zvažte, která schémata ověřování poskytují požadovanou úroveň zabezpečení. Nejslabší standardní schéma ověřování popsané tady je základní ověřování. Základní ověřování nechrání přihlašovací údaje uživatele. Nejsilnějším standardním schématem ověřování je ověřování Negotiate a výsledkem je protokol Kerberos.  
  
- Server by neměl být přítomen (v hlavičkách WWW-ověřování) jakékoli schéma, které není připraveno přijmout nebo které dostatečně nezabezpečuje chráněný prostředek. Klienti si mohou vybrat mezi libovolnými schématy ověřování, které server prezentuje. Někteří klienti mají ve výchozím nastavení slabší schéma ověřování nebo první schéma ověřování v seznamu serveru.  
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení přenosu](transport-security-overview.md)
- [Použití zosobnění se zabezpečením přenosu](using-impersonation-with-transport-security.md)
- [Delegace a zosobnění](delegation-and-impersonation-with-wcf.md)
