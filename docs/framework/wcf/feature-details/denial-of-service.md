---
title: "Útok DoS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d5f67790abad5dcf6311de1817b4ea093e703d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="denial-of-service"></a>Útok DoS
Odmítnutí služby nastane, když je tak, že zprávy nelze zpracovat, nebo se zpracovávají velmi pomalu přetížena systému.  
  
## <a name="excess-memory-consumption"></a>Nadbytečné paměťové nároky  
 Při načítání dokumentu XML s velkým počtem jedinečné názvy místní, obory názvů a předpony, může dojít k potížím. Pokud používáte třídu odvozenou z <xref:System.Xml.XmlReader>, a buď zavoláte <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> nebo <xref:System.Xml.XmlReader.NamespaceURI%2A> vlastnosti pro každou položku, vrácený řetězec je přidat do <xref:System.Xml.NameTable>. Kolekce držené <xref:System.Xml.NameTable> nikdy zmenšena, vytváření virtuální "nevrácená paměť systému" řetězce popisovače.  
  
 Způsoby zmírnění patří:  
  
-   Odvozena od <xref:System.Xml.NameTable> třídy a vynutit kvóta maximální velikosti. (Nemůže zabránit používání <xref:System.Xml.NameTable> nebo přepnutí <xref:System.Xml.NameTable> když je plný.)  
  
-   Vyhněte se použití vlastností uvedených použijte raději <xref:System.Xml.XmlReader.MoveToAttribute%2A> metoda s <xref:System.Xml.XmlReader.IsStartElement%2A> metoda kde je to možné; tyto metody není vrátit řetězce a proto vyhnout problém přeplnění <xref:System.Xml.NameTable> kolekce.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Škodlivého klienta zasílá nadměrné licenční požadavky na služby  
 Pokud klient se zlými úmysly bombards služby s nadměrné licenční požadavky, může to způsobit server, aby používal příliš mnoho paměti.  
  
 Omezení rizik: Použijte následující vlastnosti <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: Určuje maximální počet ohraničenou čas `SecurityContextToken`s, který ukládá do mezipaměti serveru po `SPNego` nebo `SSL` vyjednávání.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: řídí životnost `SecurityContextTokens` , problémy server následující `SPNego` nebo `SSL` vyjednávání. Server mezipaměti `SecurityContextToken`s pro toto časové období.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: Určuje maximální počet zabezpečené konverzace, které se vytvoří na serveru, ale které byly zpracovány žádné zprávy aplikace. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje službu pro uchování stavu pro každého klienta, ale nikdy jejich používání.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: Určuje maximální dobu, po službu zachová zabezpečenou konverzaci aktivní bez přijetí zprávu aplikace od klienta pro konverzace. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje službu pro uchování stavu pro každého klienta, ale nikdy jejich používání.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>– WSDualHttpBinding nebo duální vlastní vazby vyžadují ověření klienta  
 Ve výchozím nastavení <xref:System.ServiceModel.WSDualHttpBinding> povoleným zabezpečením. Je možné, ale, že pokud ověření klienta zakázal nastavení <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageCredentialType.None>, uživatel se zlými úmysly může způsobit odepření služby útoku třetí služby. Tato situace může nastat, protože klient se zlými úmysly může směrovat službu pro odeslání zpráv do služby třetí datový proud s.  
  
 Toto riziko lze snížit, nenastavujte vlastnost na `None`. Být také to brát ohled při vytváření vlastní vazby, který má vzorce duální zpráv.  
  
## <a name="auditing-event-log-can-be-filled"></a>Může být vyplněna auditování protokolu událostí  
 Pokud uživatel se zlými úmysly plně chápe, že je povoleno auditování, útočník odeslat neplatná zprávy, které způsobí položky auditu k zapsání. Pokud protokol auditu tímto způsobem, systém auditování selže.  
  
 Toto riziko lze nastavit <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true` a použití vlastností prohlížeče událostí můžete řídit chování auditování. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí prohlížeče událostí k zobrazení a správě protokolů událostí, najdete v tématu [Prohlížeč událostí](http://go.microsoft.com/fwlink/?LinkId=186123). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Neplatný implementace IAuthorizationPolicy může příčina služby zablokování  
 Volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodu vadný provádění <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní může způsobit, že služba přestane reagovat.  
  
 Omezení rizik: Použijte pouze důvěryhodný kód. To znamená, používají pouze kód, který jste vytvoření a otestování nebo která pochází z důvěryhodného zprostředkovatele. Nepovolit nedůvěryhodné rozšíření <xref:System.IdentityModel.Policy.IAuthorizationPolicy> zapojené do vašeho kódu bez termínu pozornost. To platí pro všechna rozšíření používat v implementaci služby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Zajistěte, aby nebyly žádné rozdíl mezi kódu aplikace a cizí kód, který je připojen pomocí body rozšiřitelnosti.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Token protokolu Kerberos maximální velikost může být nutné Změna velikosti  
 Pokud klient patří do velký počet skupin (přibližně 900, i když skutečný počet se liší v závislosti na skupiny), problému může dojít, pokud blok záhlaví zprávy překročí 64 kB. V takovém případě může zvýšit maximální velikost protokolu Kerberos tokenu, jak je popsáno v článek Microsoft Support "[ověřování protokolem Kerberos Internet Explorer nefunguje z důvodu nedostatek vyrovnávací paměti připojení do služby IIS](http://go.microsoft.com/fwlink/?LinkId=89176)." Také můžete potřebovat zvýšit maximální [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy velikost tak, aby dokázala pojmout větší token protokolu Kerberos.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Automatický zápis má za následek víc certifikátů se stejným názvem subjektu pro počítač  
 *Automatický zápis* je schopnost [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] pro automatický zápis uživatelů a počítačů pro certifikáty. Pokud je počítač v doméně s povolenou funkcí, je automaticky vytvořen a vložit do úložiště osobních certifikátů místního počítače vždy, když je nový počítač připojený k certifikátu X.509. certifikát s zamýšlený účel ověření klienta síť. Automatický zápis ale používá stejný název subjektu pro všechny certifikáty, které vytvoří v mezipaměti.  
  
 Dopad je, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se nemusí podařit otevřete v doménách s automatickým zápisem. K tomu dochází, protože kritéria hledání výchozí služby X.509 pověření pravděpodobně nejednoznačný, protože existuje více certifikátů pomocí počítače plně kvalifikovaný název systému DNS (Domain Name). Jeden certifikát pochází z automatického zápisu; druhý může být vystavený certifikát.  
  
 Toto riziko lze snížit odkazovat na přesný certifikát pomocí přesnější kritérium hledání na [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Například použít <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> možnost a určete certifikát, jeho jedinečné kryptografickým (hodnota hash).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]funkce automatického zápisu najdete v části [automatického zápisu certifikátů ve Windows serveru 2003](http://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Posledních několik názvů subjektu alternativní použít k ověřování  
 Ve výjimečných případu při certifikát X.509 obsahuje více názvů alternativní subjektu a autorizaci pomocí v alternativním názvu subjektu, autorizace se pravděpodobně nezdaří.  
  
## <a name="protect-configuration-files-with-acls"></a>Ochrana souborů konfigurace pomocí seznamů řízení přístupu  
 Povinné a nepovinné deklarací identity můžete zadat v souboru kódu a konfigurace [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vystavené tokeny. To vede k odpovídající elementy se vygenerované v `RequestSecurityToken` zprávy, které se odesílají do zabezpečení token služby. Útočník můžete upravit kód nebo konfiguraci, aby požadované nebo volitelné deklarace identity, potenciálně získávání služby tokenů zabezpečení vystavit token, který neumožňuje přístup ke službě cíl.  
  
 Zmírnění: vyžadují přístup k počítači a upravte konfigurační soubor. Řízení přístupu pomocí souboru seznamy ACL zabezpečit konfigurační soubory. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]vyžaduje, aby kódu v adresáři aplikace nebo v globální mezipaměti sestavení předtím, než bude možné takový kód, který má být načten z konfigurace. Seznamy ACL directory použijte k zabezpečení adresáře.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Bylo dosaženo maximálního počtu zabezpečených relací pro službu  
 Když klient úspěšně ověření služby a zabezpečené relace je vytvořených pomocí služby, uchovává informace o této relaci, dokud klient zruší ho nebo platnosti relace služby. Každý navázanou relaci započítává limit pro maximální počet aktivních souběžných relací se službou. Když je dosaženo tento limit, klienti, kteří se pokusí o vytvoření nové relace s touto službou odmítnuty až jeden nebo více aktivních relací vypršení platnosti nebo došlo ke zrušení klientem. Klient může mít více relací se službou a každé z nich těchto relací počty směrem k limit.  
  
> [!NOTE]
>  Při použití stavová relací nevztahuje předchozím odstavci. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Stavová relace, najdete v části [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Toto riziko lze nastavit tento limit pro maximální počet aktivních relací a maximální doba života pro relaci a nastavením <xref:System.ServiceModel.Channels.SecurityBindingElement> vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
