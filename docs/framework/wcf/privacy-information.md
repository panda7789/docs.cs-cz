---
title: Windows Communication Foundation – informace o ochraně osobních údajů
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 9c2a8d89fc62f8e3e0ce17f13604a6ba05df1a6f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534434"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation – informace o ochraně osobních údajů
Společnost Microsoft se zavazuje chránit osobní údaje koncoví uživatelé. Při vytvoření aplikace využívající Windows Communication Foundation (WCF), verze 3.0, vaše aplikace může mít vliv na vaše koncové uživatele o ochraně osobních údajů. Například vaše aplikace explicitně shromažďovat informace o uživateli, nebo může požádat o nebo odeslat informace přes Internet k vašemu webovému serveru. Pokud vložíte technologie společnosti Microsoft ve vaší aplikaci, tato technologie může mít svůj vlastní chování, které můžou ovlivnit ochranu osobních údajů. WCF neodešle žádné informace o společnosti Microsoft z vaší aplikace Pokud vy nebo koncový uživatel se rozhodnete odeslat na nás.  
  
## <a name="wcf-in-brief"></a>Přehled WCF  
 WCF je distribuovaná architektura zasílání zpráv pomocí rozhraní Microsoft .NET Framework, která umožňuje vývojářům vytvářet distribuované aplikace. Komunikace mezi dvěma aplikacemi zprávy obsahují informace záhlaví a text.  
  
 Záhlaví může obsahovat směrování zpráv, informace o zabezpečení, transakce a déle v závislosti na služby používané aplikace. Ve výchozím nastavení jsou obvykle šifrované zprávy. Jedinou výjimkou je při použití `BasicHttpBinding`, která je navržená pro použití s nezabezpečené, starší verze webových služeb. Při návrhu aplikace zodpovídáte za konečný návrh. Zprávy v těle SOAP obsahují data specifická pro aplikaci; Tato data, jako je například osobní informace definované aplikací, ale můžete zabezpečit pomocí funkce šifrování nebo důvěrnosti WCF. Následující části popisují funkce, které mohou mít vliv na ochranu osobních údajů.  
  
## <a name="messaging"></a>Zasílání zpráv  
 Hlavička adresy, která určuje cíl zprávy má každá zpráva WCF a kde by měly patřit odpovědi.  
  
 Součást adresy adresy koncového bodu je identifikátor URI (Uniform Resource), který identifikuje koncový bod. Adresa může být síťové adresy nebo logické adresy. Adresa může obsahovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu. Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID), nebo kolekci identifikátorů GUID pro účely dočasné řešení umožňuje rozpoznat každou adresu. Každá zpráva obsahuje ID zprávy, které je identifikátor GUID. Tato funkce se řídí standardu WS-Addressing odkaz.  
  
 Vrstva zasílání zpráv WCF nezapisuje žádnými osobními údaji v místním počítači. Však to může-li vývojářem služeb vytvořil službu, která poskytuje tyto informace (například pomocí v názvu koncového bodu jméno uživatele, nebo se včetně osobních údajů na webu koncový bod šířit osobní informace na úrovni sítě Služby popis jazyka, ale nevyžaduje klientů na používání protokolu https pro přístup k rozhraní jazyka WSDL). Také pokud běží Vývojář [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro koncový bod, který zpřístupňuje osobní údaje, výstup nástroje můžou obsahovat tyto informace a je zapsaný do výstupního souboru místní disk.  
  
## <a name="hosting"></a>Hostování  
 Hostování funkcí ve službě WCF umožňuje aplikacím spustit na vyžádání nebo povolit sdílení portů mezi více aplikacemi. Aplikace WCF je možné hostovat v Internetové informační služby (IIS), podobně jako [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Hostování nevystavuje žádné konkrétní informace v síti a neudržuje data na počítači.  
  
## <a name="message-security"></a>Zabezpečení zpráv  
 Zabezpečení WCF zajišťuje bezpečnostní funkce pro zasílání zpráv aplikace. Poskytuje funkce zabezpečení zahrnují ověřování a autorizace.  
  
 Ověřování se provádí pomocí přihlašovacích údajů mezi klienty a služby. Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu nebo prostřednictvím protokolu SOAP zprávy zabezpečení na úrovni, následujícím způsobem:  
  
-   V zabezpečení zpráv SOAP provádí se ověření pomocí přihlašovacích údajů, jako je uživatelské jméno a hesla, certifikáty X.509, lístky protokolu Kerberos a tokeny SAML, které mohou obsahovat osobní informace, podle toho, že vystavitel.  
  
-   Pomocí zabezpečení přenosu, ověření se provádí pomocí tradičního přenosu ověřovací mechanismy, jako jsou schémata HTTP ověřování (Basic, Digest, Negotiate, integrované ověřování Windows, protokolu NTLM, None a anonymní) a ověření formuláře.  
  
 Ověřování může vést k zabezpečenou relaci mezi komunikujícími koncových bodů. Relace je identifikován identifikátor GUID, který trvá životnost relace zabezpečení. Následující tabulka uvádí, co se ukládají a kdekoli.  
  
|Data|Úložiště|  
|----------|-------------|  
|Prezentace pověření, jako je například uživatelské jméno, certifikáty X.509, tokenů Kerberos a odkazy na přihlašovací údaje.|Standardní Windows přihlašovacích údajů mechanismy správy, jako je úložiště certifikátů Windows.|  
|Členství informace o uživateli, jako jsou uživatelská jména a hesla.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] zprostředkovateli členství.|  
|Informace o identitě týkající se služby používá k ověření služby pro klienty.|Adresa koncového bodu služby.|  
|Informace o volajícím.|Protokoly auditování.|  
  
## <a name="auditing"></a>Auditování  
 Auditování zaznamenává úspěchy a chyby ověřování a autorizace událostí. Záznamy auditu obsahují následující data: identifikátor URI, identifikátor URI akce a identifikace volajícího.  
  
 Auditování také záznamy, pokud správce změní konfiguraci protokolování zpráv (ho na zapnutí a vypnutí funkce), protože protokolování zpráv může protokolovat data specifická pro aplikaci v záhlaví a obsah. Pro [!INCLUDE[wxp](../../../includes/wxp-md.md)], záznam se zaznamenají do protokolu událostí aplikace. Pro [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], záznam se zaznamenají do protokolu událostí zabezpečení.  
  
## <a name="transactions"></a>Transakce  
 Transakce funkce poskytuje transakční služeb k aplikaci WCF.  
  
 Záhlaví transakce používat při šíření transakcí může obsahovat ID transakce nebo zařazení ID, které jsou identifikátory GUID.  
  
 Transakce funkce používá správce transakcí Microsoft distribuované transakce koordinátor (MSDTC) (součást Windows) ke správě stavu transakce. Ve výchozím nastavení jsou zašifrovaná komunikace mezi správci transakcí. Správci transakcí může protokolovat Reference koncového bodu, ID transakce a zařazení ID jako součást svých trvalého stavu. Doba platnosti tohoto stavu se určuje podle doby života souboru protokolu správce transakcí. Služba MSDTC vlastní a spravuje tento protokol.  
  
 Transakce funkce implementuje standardů WS-koordinaci a protokolu WS-AtomicTransaction.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace ve službě WCF poskytují přenos zpráv při přenosu nebo zprostředkující selhání. Poskytují právě – jednou přenos zpráv, i v případě, že je základní přenos odpojí (například připojení protokolu TCP v bezdrátové síti) nebo ztratí zprávu (proxy server HTTP vyřadit odchozí nebo příchozí zprávy). Spolehlivé relace také obnovit zprávu změny pořadí (jak se může stát v případě více cest směrování), zachovávají pořadí, ve kterém byly odeslané zprávy.  
  
 Spolehlivé relace jsou implementovány pomocí protokolu WS-ReliableMessaging (WS-RM). Přidávají WS-RM hlavičky, které obsahují informace o relaci, která se používá k identifikaci všech zpráv přidružených k určité stabilní relace. Každá relace WS-RM má identifikátor, což je identifikátor GUID.  
  
 Žádné osobní informace se uchovávají v počítači koncového uživatele společnosti.  
  
## <a name="queued-channels"></a>Ve frontě kanálů  
 Fronty ukládání zpráv od odeslání aplikace jménem přijímající aplikace a později předávání těchto zpráv do přijímající aplikace. Pomáhají zajistit přenos zpráv z odeslání aplikace na přijímající aplikace po, například přijímající aplikace přechodné. WCF poskytuje podporu pro službu Řízení front s použitím Microsoft Message Queuing (MSMQ) jako přenosového mechanismu.  
  
 Funkce ve frontě kanálů nepřidá záhlaví zprávy. Místo toho vytvoří zprávy služby Řízení front zpráv se příslušné služby Řízení front zpráv sady zpráv vlastnosti a volá metody služby Řízení front zpráv vložit zprávu do fronty služby Řízení front zpráv. Služba Řízení front zpráv je volitelná součást, která se dodává s Windows.  
  
 Žádné informace se uchovávají v počítači koncového uživatele na funkcí ve frontě kanálů, protože ho používá jako infrastruktura zařazování služby Řízení front zpráv.  
  
## <a name="com-integration"></a>Integrace COM+  
 Tato funkce zabalí stávajících funkcí modelu COM a modelu COM + vytvářet služby, které jsou kompatibilní se službou WCF services. Tato funkce nebude používat konkrétní hlavičky a neuchovává data na koncového uživatele na počítači.  
  
## <a name="com-service-moniker"></a>Moniker služby modelu COM  
 To poskytuje nespravované obálky standardní klienta WCF. Tato funkce nemá žádné konkrétní hlavičky na lince ani nemá zachovat data v počítači.  
  
## <a name="peer-channel"></a>Rovnocenný kanál  
 Rovnocenný kanál umožňuje vývoj éře aplikací pomocí technologie WCF. Zasílání zpráv éře dochází v rámci sítě. Mřížky jsou označeny název, který se můžete zapojit do uzlů. Každý uzel v protokolu peer channel vytvoří naslouchací proces TCP na portu zadané uživatelem a naváže připojení k jiným uzlům v síti k zajištění odolnosti proti chybám. Připojení k ostatním uzlům v síti, uzly také exchange nějaká data, včetně adresy naslouchací proces a jeho IP adresy s jinými uzly síť. Zprávy odeslané kolem síť může obsahovat informace o zabezpečení, která se týkají odesílatele, aby se zabránilo falšování zprávu a manipulaci s.  
  
 Na počítači koncového uživatele nebudou uloženy žádné osobní informace.  
  
## <a name="it-professional-experience"></a>Profesionální IT prostředí  
  
### <a name="tracing"></a>Trasování  
 Funkce Diagnostika služby WCF infrastruktury protokoly zpráv, které procházejí přenos a modelu vrstvy služby a činnosti a události související se tyto zprávy. Tato funkce je ve výchozím nastavení vypnuté. Je povoleno, je používán konfigurační soubor aplikace a chování trasování může být upraveno pomocí poskytovatele služby WMI WCF v době běhu. Při povolení trasování infrastruktury vysílá diagnostickém trasování, která obsahuje zprávy, aktivity a zpracování událostí do nakonfigurovaného naslouchacích procesů. Formát a umístění výstupu se určují podle volby konfigurace naslouchacího procesu na správce, ale je obvykle formátovaného souboru XML. Správce zodpovídá za nastavení seznamu řízení přístupu (ACL) pro trasovací soubory. Zejména když jsou hostované pomocí aktivace systému Windows (WAS), Správce by měl Ujistěte se, že soubory nejsou obsluhovány z veřejné virtuální kořenový adresář Pokud, který není žádoucí.  
  
 Existují dva typy trasování: protokolování zpráv a Model služby diagnostické trasování, je popsáno v následující části. Každý typ je nakonfigurovaná prostřednictvím vlastní zdroj trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>. Obě tyto zdroje protokolování trasování zaznamenávat data, která je vůči aplikaci lokální.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zdroj trasování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správci protokolování zprávy tohoto toku prostřednictvím systému. Prostřednictvím konfigurace uživatel může rozhodnout protokolovat celé zprávy nebo pouze hlavičky zpráv, zda chcete protokolovat v modelu vrstvy přenosu a/nebo služba a jestli se mají zahrnout špatně vytvořené zprávy. Uživatel také může konfigurovat filtrování omezit zprávy, které jsou zaznamenány.  
  
 Protokolování zpráv je ve výchozím nastavení zakázána. Správce místního počítače zabránit zapnutí protokolování úrovni aplikace správce.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Protokolování zpráv zašifrovaně a je dešifrován  
 Zprávy jsou protokolovány, šifrované nebo dešifrovat, jak je popsáno v následující podmínky.  
  
 Protokolování přenosu  
 Protokoly zpráv přijatých a odeslaných na úrovni přenosu. Tyto zprávy obsahují všechny hlavičky a můžou šifrovat před odesláním na lince a při jejich obdržení.  
  
 Pokud se šifrují zprávy před odesláním na lince a při jejich přijetí, kterému jsou přihlášeni šifrovaná i. Výjimkou je, když protokol zabezpečení se používá (https): potom se protokolují, dešifrují před odesláním a po jejich obdržení i v případě, že jsou šifrovaná.  
  
 Služba protokolování  
 Zaznamenává zprávy příjem nebo odeslání na úrovni modelu služby po zpracování záhlaví kanálu, těsně před a po zadání uživatelského kódu.  
  
 Zprávy zaprotokolované na této úrovni se dešifrují i v případě, že by byly zabezpečená a šifrovaná.  
  
 Protokolování chybnou zprávu  
 Zaznamenává zprávy, které infrastruktura WCF nemůže pochopit a zpracovat.  
  
 Zprávy se zaznamenávají jako-se, to znamená, šifrují nebo ne  
  
 Zprávy jsou zaznamenány dešifrovaný nebo nezašifrované podobě, ve výchozím nastavení WCF odebere zabezpečení klíčů a potenciálně osobní údaje z zprávy před jejich protokolování. Tento oddíl popisuje, jaké informace se odebere a kdy. Správce počítače a nástroje pro nasazení aplikace musí provést určité akce konfigurace, chcete-li změnit výchozí chování pro přihlášení klíče a potenciálně osobní údaje.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informace, které jsou odebrány ze záhlaví zpráv při přihlašování bez dešifrovat/šifrování zprávy  
 Když zprávy se protokolují v dešifrovat/nešifrované podobě klíčů zabezpečení a potenciálně osobní údaje se odeberou ve výchozím nastavení ze záhlaví zpráv a zpráv předtím, než jsou protokolovány. Následující seznam uvádí, co WCF považuje za klíče a potenciálně osobní údaje.  
  
 Klíče, které jsou odebrány:  
  
 \- Xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 WSt:BinarySecret  
  
 WSt:Entropy  
  
 \- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:Nonce  
  
 Potenciálně osobní údaje, která byla odstraněna:  
  
 \- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- Pro xmlns:saml = "urn: oasis: názvy: tc: SAML:1.0:assertion" jsou odebrány položky tučným písmem (níže):  
  
 \<kontrolní výraz  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId = "[ID]"  
  
 Vystavitel = "[string]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<Podmínky NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 \<AudienceRestrictionCondition >  
  
 \<Audience>[uri]\</Audience>+  
  
 \</ AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition / > *  
  
 <\!--abstraktní základní typ  
  
 \<Podmínka / > *  
  
 -->  
  
 \</ Podmínky >?  
  
 \<Rady >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > *  
  
 \<Kontrolní výraz > [výrazu]\</Assertion > *  
  
 [jakýkoli] *  
  
 \</ Rady >?  
  
 <\!--Abstraktních základních typů  
  
 \<Příkaz / > *  
  
 \<SubjectStatement >  
  
 \<Předmět >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [jakýkoli]\</SubjectConfirmationData >?  
  
 \<ds:KeyInfo>...\</ds:KeyInfo>?  
  
 \</ SubjectConfirmation >?  
  
 \</ Předmět >  
  
 \</ SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod = "[identifikátor uri]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 [Subjektu]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind = "[QName]"  
  
 Umístění = "[identifikátor uri]"  
  
 Vytvoření vazby = "[identifikátor uri]"  
  
 />*  
  
 \</ AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Subjektu]  
  
 \<Atribut  
  
 AttributeName = "[string]"  
  
 AttributeNamespace = "[identifikátor uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</ Atribut > +  
  
 \</ AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Zdroj = "[identifikátor uri]"  
  
 Rozhodnutí = "[Povolit&#124;Odepřít&#124;neurčitý]"  
  
 >  
  
 [Subjektu]  
  
 \<Akce Namespace = "[identifikátor uri]" > [string]\</Action > +  
  
 \<Legitimace >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > +  
  
 \<Kontrolní výraz > [výrazu]\</Assertion > +  
  
 \</ Důkazy >?  
  
 \</ AuthorizationDecisionStatement > *  
  
 \</ Kontrolní výraz >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informace, které jsou odebrány z těla zprávy při přihlašování bez dešifrovat/šifrování zprávy  
 Jak je uvedeno výše, WCF odebere klíče a známé potenciálně osobními údaji ze záhlaví zpráv pro zprávy zaznamenané dříve dešifrovat/nezašifrované. Kromě toho WCF odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zabezpečení zprávy, které jsou zahrnuté v výměny klíčů.  
  
 Pro následující obory názvů:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (např. Pokud nejsou k dispozici žádná akce)  
  
 Pro tyto elementy textu, které zahrnují výměny klíčů odebraly informace:  
  
 WSt:RequestSecurityToken  
  
 WSt:RequestSecurityTokenResponse  
  
 WSt:RequestSecurityTokenResponseCollection  
  
 Informace o odebrán také pro každou z následujících akcí:  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Žádné informace se odebere z hlavičky specifické pro aplikace a Data těla  
 WCF nesleduje osobní údaje v záhlaví specifické pro aplikaci (například řetězce dotazu) a data subjektu (například číslo platební karty).  
  
 Při protokolování zpráv je na, může být osobní údaje v hlavičkách specifické pro aplikaci a informace o subjektu viditelné v protokolech. Nástroje pro nasazení aplikace znovu, zodpovídá za nastavení seznamu ACL u souborů konfigurace a protokolu. Si můžete také vypnout protokolování nechce uvidí tyto informace nebo mu může odfiltrovat tyto informace v souborech protokolů, až se protokoluje.  
  
### <a name="service-model-tracing"></a>Služby modelu trasování  
 Zdroj trasování Service Model (<xref:System.ServiceModel>) umožňuje trasování aktivity a události související se zpracování zpráv. Tato funkce používá diagnostické funkce rozhraní .NET Framework z <xref:System.Diagnostics>. Stejně jako u <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> vlastnost, umístění a jeho seznamu ACL se uživatelem konfigurovatelné pomocí konfiguračních souborů aplikace rozhraní .NET Framework. Stejně jako u protokolování zpráv umístění souboru vždy nakonfigurované, pokud správce povolí trasování; Proto správce ovládací prvky seznamu ACL.  
  
 Trasování neobsahovala záhlaví zpráv, když je zpráva v oboru. Platí stejná pravidla pro skrytí potenciálně osobní údaje v záhlaví zpráv v předchozí části: Odebereme osobní údaje dříve identifikovat ve výchozím nastavení ze záhlaví ve trasování. Správce počítače a nástroje pro nasazení aplikace, musíte změnit konfiguraci protokolování potenciálně osobní údaje. Osobní informace obsažené v konkrétní aplikaci záhlaví je však přihlášen trasování. Nástroje pro nasazení aplikace je zodpovědná za nastavení seznamu ACL u souborů konfigurace a trasování. Má také vypnout trasování nechce uvidí tyto informace nebo mu můžete filtrovat tyto informace ze souborů trasování po je zaznamenána.  
  
 Jako součást ServiceModel trasování, jedinečné identifikátory (označované jako ID aktivit a obvykle GUID) propojit různé aktivity jako zpráva prochází různých součástí infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Naslouchací procesy vlastního trasování  
 Pro obě zprávy protokolování a trasování naslouchací proces vlastního trasování je možné nakonfigurovat, který můžete poslat trasování a zpráv na lince (například vzdálená databáze). Nástroje pro nasazení aplikace je zodpovědná za konfiguraci vlastní naslouchacích procesů nebo umožnění uživatelům Uděláte to tak. Je také zodpovídá za žádné osobní údaje, které jsou zveřejněné ve vzdáleném umístění a správně do tohoto umístění seznamy ACL.  
  
### <a name="other-features-for-it-professionals"></a>Další funkce pro IT specialisty  
 WCF se zprostředkovatel rozhraní WMI, který poskytuje informace o konfiguraci infrastruktury WCF přes rozhraní WMI (dodávané s Windows). Ve výchozím nastavení je k dispozici správcům rozhraní WMI.  
  
 Konfigurace WCF používá mechanismus konfigurace rozhraní .NET Framework. Konfigurační soubory se ukládají na počítači. Správce a vývojáře aplikací vytvořte konfigurační soubory a seznamu ACL pro každou podle požadavků vaší aplikace. Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů. Certifikáty slouží k poskytnutí dat aplikace nakonfigurovat různé vlastnosti objektu funkcí používaných v rámci aplikace.  
  
 WCF také používá funkce rozhraní .NET Framework procesu s výpisem paměti pomocí volání <xref:System.Environment.FailFast%2A> metody.  
  
### <a name="it-pro-tools"></a>IT profesionálních nástrojů  
 WCF také obsahuje následující IT professional nástroje, které se dodávají v sadě Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Prohlížeč zobrazí soubory trasování WCF. Prohlížeč zobrazí libovolné informace je součástí trasování.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Editor umožňuje uživateli vytvoření a úprava konfiguračních souborů WCF. Editor hlásí libovolné informace je obsažen v konfiguračních souborech. Stejné úlohy můžete provést pomocí textového editoru.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Tento nástroj umožňuje uživateli spravovat ServiceModel nainstaluje na počítač. Nástroj zobrazí stavové zprávy v okně konzoly, když se spustí a v procesu, mohou zobrazit informace o konfiguraci instalace WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe a WSATUI.dll  
 Tyto nástroje umožňují Odborníci v oblasti IT provést konfiguraci podpory sítě interoperabilní WS-AtomicTransaction ve službě WCF. Nástroje pro zobrazení a povolit uživateli měnit hodnoty nejčastěji používaná nastavení WS-AtomicTransaction uložené v registru.  
  
## <a name="cross-cutting-features"></a>Společné funkce  
 Společné spadají následující funkce. To znamená mohou být složené s některým z předchozích funkcí.  
  
### <a name="service-framework"></a>Architektura služby  
 Záhlaví může obsahovat ID instance, což je identifikátor GUID, která přidružuje zprávu instance třídy CLR.  
  
 Na webové služby WSDL (Description Language) obsahuje definici portu. Každý z portů má adresu koncového bodu a vazbu, která představuje služby používané aplikace. Vystavení WSDL můžete vypnout pomocí konfigurace. Žádné informace se uchovávají v počítači.  
  
## <a name="see-also"></a>Viz také  
 [Windows Communication Foundation](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Zabezpečení](../../../docs/framework/wcf/feature-details/security.md)
