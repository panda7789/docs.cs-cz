---
title: Útok DoS
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: bc209d184ac330b112d17c34f0bf1c479a8b5f7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516158"
---
# <a name="denial-of-service"></a>Útok DoS
Útok DoS nastane, pokud je systém zahltil tak, že zprávy nelze zpracovat, nebo se zpracovávají velmi pomalu.  
  
## <a name="excess-memory-consumption"></a>Spotřeba nadbytek paměti  
 Při čtení dokumentu XML s velkým množstvím jedinečné místní názvy oborů názvů a předpony, může dojít k potížím. Pokud používáte třídu odvozenou z <xref:System.Xml.XmlReader>, a volání buď <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> nebo <xref:System.Xml.XmlReader.NamespaceURI%2A> pro každou položku, vrácený řetězec je přidána vlastnost <xref:System.Xml.NameTable>. Kolekce drží <xref:System.Xml.NameTable> nikdy zmenšena, vytváří se virtuální "nevracení paměti" popisovačů řetězec.  
  
 Zmírnění rizik patří:  
  
-   Odvozovat <xref:System.Xml.NameTable> třídy a vynucovat kvóta maximální velikosti. (Nelze zabránit používání <xref:System.Xml.NameTable> nebo přepněte <xref:System.Xml.NameTable> když je plný.)  
  
-   Vyhněte se použití vlastnosti uvedené a místo toho použít <xref:System.Xml.XmlReader.MoveToAttribute%2A> metodu s <xref:System.Xml.XmlReader.IsStartElement%2A> metoda povedou; tyto metody vracet řetězce a vyhněte se tím problém přeplnění <xref:System.Xml.NameTable> kolekce.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Škodlivý klient odešle nadměrné licenční požadavky na služby  
 Pokud klient se zlými úmysly bombards služby s nadměrným licenční požadavky, může to způsobit server určený využívala příliš mnoho paměti.  
  
 Omezení rizik: Použijte následující vlastnosti <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: Určuje maximální počet časově `SecurityContextToken`s, který ukládá do mezipaměti serveru po `SPNego` nebo `SSL` vyjednávání.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: Určuje životnost `SecurityContextTokens` , který server problémy následující `SPNego` nebo `SSL` vyjednávání. Server mezipaměti `SecurityContextToken`s pro tuto dobu.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: Určuje maximální počet zabezpečených konverzací, které jsou vytvořeny na serveru, ale pro které byly zpracovány žádné zprávy aplikace. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje služby pro uchování stavu pro klienta, ale nikdy je používají.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: Určuje maximální dobu službu zachová zabezpečené konverzace aktivní aniž by mu musela zprávy aplikace od klienta pro tuto konverzaci. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje služby pro uchování stavu pro klienta, ale nikdy je používají.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding nebo duální vlastních vazeb vyžadují ověření klienta  
 Ve výchozím nastavení <xref:System.ServiceModel.WSDualHttpBinding> povoleným zabezpečením. Je možné, ale, že pokud ověření klienta zakázal nastavení <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageCredentialType.None>, uživatel se zlými úmysly může způsobit, že útoku služby ve službě třetí. Tato situace může nastat, protože klient se zlými úmysly může směrovat služby umožňující odesílání zpráv do služby třetí.  
  
 Chcete-li tento problém zmírnit, nenastavujte vlastnost na `None`. Také mějte na paměti tuto možnost při vytváření vlastní vazby, který má vzor duální zprávy.  
  
## <a name="auditing-event-log-can-be-filled"></a>Můžou být vyplněné auditování protokolu událostí  
 Pokud uživatel se zlými úmysly rozumí, že je povolené auditování, že útočník odeslat neplatná zprávy, které způsobují auditu má být proveden zápis. Pokud je tímto způsobem protokolu auditu, selhání auditování systému.  
  
 Chcete-li tento problém zmírnit, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true` a použití vlastností v prohlížeči událostí pro řízení chování auditování. Další informace o používání v prohlížeči událostí k zobrazení a správě protokolů událostí, naleznete v tématu [Prohlížeč událostí](https://go.microsoft.com/fwlink/?LinkId=186123). Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Neplatný implementace může zásada IAuthorizationPolicy příčina služby. program přestane reagovat  
 Volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodu na chybný provádění <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní může způsobit, že služba přestane reagovat.  
  
 Omezení rizik: Použijte pouze pro důvěryhodného kódu. To znamená použít pouze kód, který slouží k vytvoření a otestování nebo, který pochází z důvěryhodného zprostředkovatele. Nejsou povoleny nedůvěryhodné rozšíření <xref:System.IdentityModel.Policy.IAuthorizationPolicy> zapojené do kódu bez náležité pozornost. To platí pro všechna rozšíření použitý v implementaci služby. WCF nepoužívá žádný rozdíl mezi kódu aplikace a cizí kód, který je připojen pomocí bodů rozšiřitelnosti.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Token protokolu Kerberos maximální velikost může být nutné změny velikosti  
 Pokud klient patří do velký počet skupin (přibližně 900, i když skutečný počet se liší v závislosti na skupiny), přesáhne 64 kB blok záhlaví zprávy může dojít k potížím. V takovém případě může zvýšit maximální velikost protokolu Kerberos tokenu, jak je popsáno v článek Microsoft Support "[ověřování protokolem Kerberos Internet Exploreru nefunguje kvůli nedostatek vyrovnávací paměti připojení do služby IIS](https://go.microsoft.com/fwlink/?LinkId=89176)." Budete také muset zvýšit maximální velikost zprávy WCF tak, aby vyhovovaly větší token protokolu Kerberos.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Automatický zápis za následek více certifikátů se stejným názvem předmětu pro počítač  
 *Automatický zápis* je schopnost [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] o automatickou registraci uživatelů a počítačů pro certifikáty. Když počítač je připojen k doméně s povolenou funkcí, certifikát X.509 s zamýšlený účel ověření klienta je automaticky vytvořen a vložit do úložiště osobních certifikátů místního počítače pokaždé, když se nový počítač připojen k síť. Automatický zápis však používá stejný název subjektu pro všechny certifikáty, které vytvoří v mezipaměti.  
  
 Se, že služby WCF se pravděpodobně nezdaří spustit v doménách s automatickým zápisem. K tomu dochází, protože výchozí služby X.509 přihlašovacích údajů kritéria hledání může být nejednoznačný, protože existuje více certifikátů s plně kvalifikovaným názvem systému DNS (Domain Name) počítači. Jeden certifikát pochází z automatického zápisu; druhý může být vystavený certifikát.  
  
 Chcete-li tento problém zmírnit, odkazovat na přesně certifikát pomocí přesnější kritérium hledání na [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Například použít <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> možnost a vyberte certifikát pro jeho jedinečné kryptografickým (hodnota hash).  
  
 Další informace o funkci automatického zápisu najdete v tématu [automatického zápisu certifikátů ve Windows serveru 2003](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Posledních několik názvů subjektu alternativní se používají pro autorizaci  
 Ve výjimečných případech, kdy certifikát X.509, který obsahuje několik názvů subjektu alternativní a autorizaci pomocí v alternativním názvu subjektu, může dojít k selhání autorizace.  
  
## <a name="protect-configuration-files-with-acls"></a>Chránit konfigurační soubory společně se seznamy ACL  
 Povinné a nepovinné deklarace identity můžete zadat v kódu a konfigurační soubory pro [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vydané tokeny. Výsledkem je odpovídající elementy probíhá emitovány v `RequestSecurityToken` zprávy odeslané bezpečnostní token služby. Útočník můžete upravit kódu nebo konfigurace odebrat požadované nebo nepovinné deklarace identity, potenciálně získávání služby tokenů zabezpečení k vydání tokenu, který neumožňuje přístup k cílové službě.  
  
 Zmírnit: Vyžadovat přístup k počítači a upravte konfigurační soubor. Řízení přístupu pomocí souboru seznamy ACL pro konfigurační soubory zabezpečení. WCF vyžaduje, aby kód v adresáři aplikace nebo v globální mezipaměti sestavení předtím, než bude možné takový kód, který se má načíst z konfigurace. Pro zabezpečení adresáře, použijte seznamy ACL adresáře.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Dosažen maximální počet zabezpečených relací pro službu  
 Po klienta úspěšně ověřen službou a vytvoření zabezpečené relace ve službě, službu uchovává informace o relaci, dokud ho ruší klienta nebo vypršení platnosti relace. Každý navázanou relaci počítat limit pro maximální počet aktivních souběžných relací se službou. Při dosažení tohoto limitu, klienti, kteří se pokusí vytvořit novou relaci s touto službou odmítají do jedné nebo víc aktivních relací vypršení platnosti nebo zrušení klientem. Klient může mít několik relací s využitím služby a jedna z těchto relací se počítá směrem k omezení.  
  
> [!NOTE]
>  Při použití stavové relací se nevztahuje předchozím odstavci. Další informace o relacích stavové najdete v tématu [jak: Vytvoření kontextu zabezpečení pro zabezpečenou relaci Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Toto riziko lze snížit nastavením limitu pro maximální počet aktivních relací a maximální doba života pro relaci <xref:System.ServiceModel.Channels.SecurityBindingElement> vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
## <a name="see-also"></a>Viz také:
- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
