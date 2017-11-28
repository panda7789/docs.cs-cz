---
title: "Zpřístupnění informací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1169aae0a2d2db6d020e87b1430e2dbdc1596117
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="information-disclosure"></a>Zpřístupnění informací
Zpřístupnění informací umožňuje útočníkovi získat cenné informace o systému. Proto vždy zvažte, které informace jsou odhalil a zda jej lze použít uživatelem se zlými úmysly. Následující informace o možných útoků zpřístupnění obsahuje seznam a jejich zmírnění pro každý.  
  
## <a name="message-security-and-http"></a>Zabezpečení zpráv a HTTP  
 Pokud používáte zabezpečení na úrovni zpráv přes přenosové vrstvy protokolu HTTP, mějte na paměti, že zabezpečení na úrovni zpráv nechrání hlavičky protokolu HTTP. Jediný způsob, jak chránit hlavičky protokolu HTTP je použití přenos HTTPS místo protokolu HTTP. Přenos HTTPS způsobí, že celé zprávy, včetně hlavičky protokolu HTTP k šifrování pomocí protokolu Secure Sockets Layer (SSL).  
  
## <a name="policy-information"></a>Informace o zásadách  
 Zachování zásady zabezpečení je důležité, zejména v federační scénáře, kde je v zásadách vystaven citlivé vydán token požadavky nebo informace o tokenu vystavitele. V těchto případech doporučujeme zabezpečit koncový bod zásad federované služby pro aby útočníci nemohli získat informace o službě, jako je typ deklarace identity se umístí vystavený token, nebo přesměrovat klienty na škodlivý tokenu vystavitelů. Například může útočník zjistit párů jméno a heslo uživatele změnou řetězu federovaného vztahu důvěryhodnosti ukončit v vystavitele, provést útok man-in-the-middle. Dále je doporučeno, federované klienti, kteří získat jejich vazby prostřednictvím načtení zásad ověřte, zda důvěřují vystavitele v řetězu získaných federovaný vztah důvěryhodnosti. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]federační scénáře, najdete v části [Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Výpisy paměti může odhalit informace o deklaraci identity  
 Pokud se aplikace nezdaří, přihlaste se soubory, jako jsou ty vyprodukované zotavení po havárii. Watson, může obsahovat informace o deklaraci identity. Tyto informace by neměl být exportovány do jinými entitami, jako je například týmy podpory; jinak informace o deklaraci identity, obsahující privátní data taky exportovat. Můžete zmírnit není poslat soubory protokolu na neznámý entity. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Systému Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Adresy koncových bodů  
 Adresy koncového bodu obsahuje informace potřebné ke komunikaci s koncovým bodem. Zabezpečení protokolu SOAP musí obsahovat adresu plně ve zprávách vyjednávání zabezpečení, které se vyměňují aby bylo možné vyjednávání symetrického klíče mezi klientem a serverem. Protože vyjednávání zabezpečení je spuštění procesu, hlavičky adresy nelze zašifrovat během tohoto procesu. Proto adresa nesmí obsahovat žádné důvěrných dat; jinak hodnota vede k útokům zpřístupnění informací.  
  
## <a name="certificates-transferred-unencrypted"></a>Certifikáty přenáší nezašifrovaná  
 Při použití certifikátu X.509. certifikát pro ověření klienta, certifikát se přenáší v nešifrované podobě, v hlavičce protokolu SOAP. Pamatujte na to jako potenciální zpřístupnění identifikovatelné osobní údaje (PII). Toto není problém pro `TransportWithMessageCredential` režimu, kde celé zprávy zašifrované pomocí zabezpečení na úrovni přenosu.  
  
## <a name="service-references"></a>Odkazy na službu  
 Odkaz na službu je odkaz na jinou službu. Služba může například předat odkazu na službu pro klienta v průběhu operace. Odkaz na službu se také používá s *důvěřovat identity ověřovatele*, interní součásti, které zajišťuje, aby identita cílový hlavní před odhalení informací, jako jsou data aplikace nebo přihlašovací údaje k cíli. Pokud identitu vzdáleného důvěryhodnosti nelze ověřit nebo není správný, odesílatel zkontrolujte, že se žádná data budou mít přístup, které by mohly ohrozit sám sebe, aplikace nebo uživatele.  
  
 Způsoby zmírnění zahrnují následující:  
  
-   Odkazy na službu, jsou považovány za důvěryhodné. Vezměte v potaz při každém přenosu instance služby odkaz zajistit, aby nebyly zaměněny.  
  
-   Některé aplikace může být činnost koncového uživatele, který umožňuje interaktivní navázání vztahu důvěryhodnosti na základě dat v referenčním a důvěryhodnosti data služby prokazuje vzdáleného hostitele. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Poskytuje rozšíření, které musí body pro taková zařízení, ale uživatel je implementována.  
  
## <a name="ntlm"></a>NTLM  
 Ve výchozím nastavení v prostředí domény systému Windows, ověřování systému Windows používá protokol Kerberos k ověřování a autorizaci uživatelů. Pokud z nějakého důvodu nelze použít protokol Kerberos, použije se jako zálohu NT LAN Manager (NTLM). Tuto funkci můžete zakázat nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false`. Problémy na vzít na vědomí při povolení protokolu NTLM patří:  
  
-   NTLM zpřístupní uživatelské jméno klienta. Pokud uživatelské jméno musí být důvěrné, nastavte `AllowNTLM` vlastnost vazby ke `false`.  
  
-   NTLM neumožňuje ověřování serveru. Klient nemůže proto zkontrolujte, že ho komunikuje s správné služby při použití jako ověřovací protokol NTLM.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Zadání pověření klienta nebo neplatná identita vynutí použití protokolu NTLM  
 Při vytváření klienta, zadání přihlašovacích údajů klienta bez názvu domény, nebo zadáte neplatný server identity, způsobí, že protokol NTLM namísto protokolu Kerberos použita (Pokud `AlllowNtlm` je nastavena na `true`). Protože protokol NTLM neprovádí ověřování serveru, může být odhalena potenciálně informace.  
  
 Například je možné zadat pověření klienta Windows bez názvu domény, jak je znázorněno v následujícím [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] kódu.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 Kód není uveden název domény, a proto se použije protokol NTLM.  
  
 Pokud je zadané doméně, ale neplatný hlavní název služby je zadán pomocí funkce identitu koncového bodu, se používá protokol NTLM. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak není zadaný koncový bod identity, najdete v části [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Viz také  
 [Aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zvýšení úrovně oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmítnutí služby](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Manipulaci](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
