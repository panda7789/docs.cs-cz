---
title: Útok DoS
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 55120430a9aaafe7d8bbf2b26f07806e4f1aa44a
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964427"
---
# <a name="denial-of-service"></a>Útok DoS
K odepření služby dojde v případě zahlcení systému takovým způsobem, že zprávy nelze zpracovat nebo jsou zpracovávány extrémně pomalu.  
  
## <a name="excess-memory-consumption"></a>Nadměrné využití paměti  
 K problému může dojít při čtení dokumentu XML s velkým počtem jedinečných místních názvů, oborů názvů nebo předpon. Pokud používáte třídu, která je odvozena z <xref:System.Xml.XmlReader>a voláte buď vlastnost <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> nebo <xref:System.Xml.XmlReader.NamespaceURI%2A> pro každou položku, vrácený řetězec je přidán do <xref:System.Xml.NameTable>. Kolekce, kterou uchovává <xref:System.Xml.NameTable>, se nikdy nezmenší a vytvoří virtuální "nevrácenou paměť obslužných rutin řetězce.  
  
 Zmírnění rizik zahrnuje:  
  
- Je odvozená od třídy <xref:System.Xml.NameTable> a vynutila maximální velikost kvóty. (Nemůžete zabránit použití <xref:System.Xml.NameTable> nebo přepnutí <xref:System.Xml.NameTable>, pokud je zaplněno.)  
  
- Vyhněte se použití uvedených vlastností a místo toho použijte metodu <xref:System.Xml.XmlReader.MoveToAttribute%2A> s metodou <xref:System.Xml.XmlReader.IsStartElement%2A>, pokud je to možné; Tyto metody nevrací řetězce, takže se vyhnete problému při přeplňování kolekce <xref:System.Xml.NameTable>.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Škodlivý klient posílá službě nadměrné požadavky na licence.  
 Pokud se v případě škodlivého klienta bombards služba s nadměrnými požadavky na licence, může to způsobit, že server bude používat nadměrné množství paměti.  
  
 Zmírnění: použijte následující vlastnosti třídy <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: řídí maximální počet časově vázaných `SecurityContextToken`s, které server ukládá do mezipaměti po `SPNego` nebo `SSL` vyjednávání.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: řídí dobu života `SecurityContextTokens`, na které server vystavuje problémy po `SPNego` nebo `SSL` vyjednávání. Server ukládá do mezipaměti `SecurityContextToken`s pro toto časové období.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: Určuje maximální počet zabezpečených konverzací, které jsou vytvořeny na serveru, ale pro které nebyly zpracovány žádné zprávy aplikace. Tato kvóta zabraňuje klientům v vytváření zabezpečených konverzací v rámci služby, což způsobuje, že služba udržuje stav pro každého klienta, ale nikdy je nepoužívá.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: Určuje maximální dobu, po kterou služba udržuje zabezpečenou konverzaci, aniž by přijímala zprávu aplikace od klienta pro konverzaci. Tato kvóta zabraňuje klientům v vytváření zabezpečených konverzací v rámci služby, což způsobuje, že služba udržuje stav pro každého klienta, ale nikdy je nepoužívá.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding nebo duální vlastní vazby vyžadují ověření klienta.  
 Ve výchozím nastavení má <xref:System.ServiceModel.WSDualHttpBinding> povolené zabezpečení. Je ale možné, že pokud je ověřování klientů zakázané, nastavením vlastnosti <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na <xref:System.ServiceModel.MessageCredentialType.None>, může uživatel se zlými úmysly způsobit útok na útok na službu třetí služby. Tato situace může nastat, protože škodlivý klient může nasměrovat službu tak, aby odesílala proud zpráv do třetí služby.  
  
 Pro zmírnění této nenastavte vlastnost na `None`. Pamatujte také na tuto možnost při vytváření vlastní vazby, která má vzorec duální zprávy.  
  
## <a name="auditing-event-log-can-be-filled"></a>Protokol událostí auditování může být vyplněn.  
 Pokud uživatel se zlými úmysly rozumí, že auditování je povolené, může útočník odeslat neplatné zprávy, které způsobí zápis záznamů auditu. Pokud se tento způsob vyplní protokolem auditu, systém auditování se nezdařil.  
  
 Pokud to chcete zmírnit, nastavte vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true` a použijte vlastnosti Prohlížeč událostí k řízení chování auditování. Další informace o použití Prohlížeč událostí k zobrazení a správě protokolů událostí najdete v tématu [Prohlížeč událostí](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)). Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>Neplatné implementace zásada IAuthorizationPolicy můžou způsobit, že služba přestane reagovat.  
 Volání metody <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> na vadnou implementaci rozhraní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> může způsobit, že služba přestane reagovat.  
  
 Zmírnění: Používejte jenom důvěryhodný kód. To znamená, že použijte pouze kód, který jste napsali a otestovali nebo který pochází od důvěryhodného poskytovatele. Nepovolujte, aby nedůvěryhodná rozšíření <xref:System.IdentityModel.Policy.IAuthorizationPolicy> mohla být do kódu zapojena bez náležité úvahy. To platí pro všechna rozšíření použitá v implementaci služby. WCF nerozlišuje mezi kódem aplikace a cizím kódem, který je napájený pomocí bodů rozšiřitelnosti.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Maximální velikost tokenu protokolu Kerberos může vyžadovat změnu velikosti.  
 Pokud klient patří do velkého počtu skupin (přibližně 900, i když se skutečný počet liší v závislosti na skupinách), může dojít k problému, když blok záhlaví zprávy překročí 64 kilobajtů. V takovém případě můžete zvýšit maximální velikost tokenu protokolu Kerberos. Je také možné, že budete muset zvětšit maximální velikost zprávy WCF, aby vyhovovala většímu tokenu Kerberos.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Výsledkem automatického zápisu je více certifikátů se stejným názvem subjektu pro počítač.  
 Automatický *zápis* je schopnost systému Windows Server 2003 automaticky registrovat uživatele a počítače pro certifikáty. Když je počítač v doméně s povolenou funkcí, vytvoří se automaticky certifikát X. 509 s zamýšleným účelem ověřování klienta a vloží se do úložiště osobních certifikátů místního počítače, kdykoli se do něj připojí nový počítač. sítě. Automatický zápis ale používá stejný název subjektu pro všechny certifikáty, které vytvoří v mezipaměti.  
  
 Dopadem je, že služby WCF se nemusí podařit otevřít v doménách s automatickým zápisem. K tomu dochází, protože výchozí kritéria vyhledávání pověření X. 509 mohou být nejednoznačná, protože existuje více certifikátů s plně kvalifikovaným názvem DNS (Domain Name System) počítače. Jeden certifikát pochází z automatického zápisu; druhým může být certifikát vydaný svým držitelem.  
  
 Pokud to chcete zmírnit, odkazujte na přesný certifikát, který chcete použít, pomocí přesnější vyhledávacího kritéria [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Použijte například možnost <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> a zadejte certifikát podle jeho jedinečného kryptografického otisku (hash).  
  
 Další informace o funkci automatického zápisu najdete v tématu [Automatický zápis certifikátů ve Windows serveru 2003](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc778954(v%3dws.10)).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Poslední z několika alternativních názvů subjektů používaných k autorizaci  
 Ve výjimečném případě, kdy certifikát X. 509 obsahuje více alternativních názvů subjektů a Vy autorizujete použití alternativního názvu subjektu, může autorizace selhat.  
  
## <a name="protect-configuration-files-with-acls"></a>Ochrana konfiguračních souborů pomocí seznamů ACL  
 Můžete zadat povinné a volitelné deklarace identity v kódu a konfiguračním souboru pro vydávané tokeny služby CardSpace. Výsledkem je, že se v `RequestSecurityToken` zprávy odesílané do služby tokenu zabezpečení generují odpovídající prvky. Útočník může změnit kód nebo konfiguraci, aby odstranil požadované nebo volitelné deklarace identity, a mohl tak získat token, který nepovoluje přístup k cílové službě.  
  
 Chcete-li zmírnit: vyžadovat přístup k počítači pro úpravu konfiguračního souboru. Pomocí seznamů řízení přístupu (ACL) souborů Zabezpečte konfigurační soubory. WCF vyžaduje, aby byl kód v adresáři aplikace nebo v globální mezipaměti sestavení (GAC) předtím, než bude moci takový kód načíst z konfigurace. K zabezpečení adresářů použijte seznamy ACL adresáře.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Dosáhlo se maximálního počtu zabezpečených relací pro službu.  
 Pokud se klient úspěšně ověřuje pomocí služby a ve službě se vytvoří zabezpečená relace, služba sleduje relaci, dokud ji klient nezruší nebo dokud relace nevyprší. Každá vytvořená relace se počítá s omezením maximálního počtu aktivních současných relací se službou. Po dosažení tohoto limitu se klienti, kteří se pokoušejí vytvořit novou relaci s touto službou, odmítnou, dokud jedna nebo víc aktivních relací nevyprší nebo neruší klient. Klient může mít několik relací se službou a každá z těchto relací se počítá směrem k limitu.  
  
> [!NOTE]
> Při použití stavových relací se předchozí odstavec netýká. Další informace o stavových relacích najdete v tématu [Postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Pokud to chcete zmírnit, nastavte limit maximálního počtu aktivních relací a maximální životnosti relace nastavením vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
