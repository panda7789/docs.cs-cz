---
title: Windows Communication Foundation – informace o ochraně osobních údajů
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 0b277728d2f2c224d5e45e3990ab2fd588bc81d3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318698"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation – informace o ochraně osobních údajů
Společnost Microsoft se zavazuje chránit ochranu osobních údajů koncových uživatelů. Když sestavíte aplikaci pomocí Windows Communication Foundation (WCF), verze 3,0, může vaše aplikace ovlivnit ochranu osobních údajů koncových uživatelů. Vaše aplikace může například explicitně shromažďovat kontaktní údaje uživatele nebo může vyžádat nebo odeslat informace prostřednictvím internetu na web. Pokud do své aplikace vložíte technologii Microsoftu, může mít tato technologie vlastní chování, které může mít vliv na ochranu osobních údajů. WCF neodesílá žádné informace společnosti Microsoft z vaší aplikace, pokud jste vy nebo koncový uživatel nezvolili odeslání na nás.  
  
## <a name="wcf-in-brief"></a>WCF v krátkém  
 Služba WCF je distribuovaná architektura pro zasílání zpráv pomocí .NET Framework Microsoftu, která vývojářům umožňuje vytvářet distribuované aplikace. Zprávy komunikující mezi dvěma aplikacemi obsahují záhlaví a informace o textu.  
  
 Záhlaví mohou obsahovat směrování zpráv, informace o zabezpečení, transakce a další informace v závislosti na službách, které aplikace používá. Zprávy jsou obvykle ve výchozím nastavení zašifrovány. Jedinou výjimkou je použití `BasicHttpBinding`, která byla navržena pro použití s nezabezpečenými staršími webovými službami. Jako návrhář aplikace zodpovídáte za finální návrh. Zprávy v těle protokolu SOAP obsahují data specifická pro aplikaci; Tato data, jako jsou osobní údaje definované aplikací, je ale možné zabezpečit pomocí funkcí šifrování a utajení WCF. V následujících částech jsou popsány funkce, které mohou mít vliv na ochranu osobních údajů.  
  
## <a name="messaging"></a>Messaging  
 Každá zpráva WCF má hlavičku adresy, která určuje cíl zprávy a kam má odpověď jít.  
  
 Součást Address adresy koncového bodu je identifikátor URI (Uniform Resource Identifier), který identifikuje koncový bod. Adresa může být síťová nebo logická adresa. Adresa může obsahovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu. Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID) nebo kolekci identifikátorů GUID pro dočasné adresování, které slouží k nerozlišujeí jednotlivých adres. Každá zpráva obsahuje ID zprávy, která je identifikátorem GUID. Tato funkce se řídí referenčním standardem WS-Addressing.  
  
 Vrstva zasílání zpráv WCF nepíše žádné osobní údaje do místního počítače. Může však šířit osobní údaje na úrovni sítě, pokud vývojář služby vytvořil službu, která tyto informace zpřístupňuje (například pomocí názvu osoby v názvu koncového bodu nebo včetně osobních údajů na webu koncového bodu). Služba Description Language, ale nevyžaduje, aby klienti k přístupu ke WSDL používali https. Pokud vývojář spustí nástroj pro dodané [metadata (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) v rámci koncového bodu, který zveřejňuje osobní údaje, může také výstup tohoto nástroje obsahovat tyto informace a výstupní soubor je zapsán na místní pevný disk.  
  
## <a name="hosting"></a>Hostování  
 Funkce hostování v rámci WCF umožňuje aplikacím spouštět na vyžádání nebo povolit sdílení portů mezi několika aplikacemi. Aplikace WCF může být hostována ve službě Internetová informační služba (IIS), podobně jako ASP.NET.  
  
 Hostování nezveřejňuje žádné konkrétní informace v síti a neuchovává data v počítači.  
  
## <a name="message-security"></a>Zabezpečení zpráv  
 Zabezpečení WCF poskytuje možnosti zabezpečení pro aplikace zasílání zpráv. K dispozici jsou funkce zabezpečení zahrnující ověřování a autorizaci.  
  
 Ověřování se provádí předáním přihlašovacích údajů mezi klienty a službami. Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu, nebo prostřednictvím zabezpečení na úrovni zpráv SOAP, a to následujícím způsobem:  
  
- V zabezpečení zpráv SOAP se ověřování provádí prostřednictvím přihlašovacích údajů, jako jsou uživatelské jméno a hesla, certifikáty X. 509, lístky protokolu Kerberos a tokeny SAML, z nichž všechny můžou obsahovat osobní informace v závislosti na vystaviteli.  
  
- Pomocí zabezpečení přenosu se ověřování provádí pomocí tradičních mechanismů ověřování přenosu, jako jsou schémata ověřování HTTP (Basic, Digest, Negotiate, integrovaná autorizace Windows, NTLM, None a Anonymous), a ověřování pomocí formuláře.  
  
 Ověřování může mít za následek zabezpečenou relaci vytvořenou mezi komunikujícími koncovými body. Relace je identifikována identifikátorem GUID, který vydrží životnost relace zabezpečení. Následující tabulka ukazuje, co se zachová a kde.  
  
|Data|Úložiště|  
|----------|-------------|  
|Přihlašovací údaje pro prezentace, jako je uživatelské jméno, certifikáty X. 509, tokeny Kerberos a odkazy na přihlašovací údaje.|Standardní mechanismy správy přihlašovacích údajů systému Windows, jako je například úložiště certifikátů systému Windows.|  
|Informace o členství uživatele, například uživatelská jména a hesla.|ASP.NET poskytovatelé členství.|  
|Informace o identitě služby, která se používá k ověření služby pro klienty.|Adresa koncového bodu služby.|  
|Informace o volajícím.|Protokoly auditování.|  
  
## <a name="auditing"></a>Auditování  
 Auditování zaznamenává úspěšné a neúspěšné události ověřování a autorizace. Záznamy auditu obsahují následující data: identifikátor URI služby, identifikátor URI akce a identifikaci volajícího.  
  
 Auditování také zaznamenává, když správce změní konfiguraci protokolování zpráv (zapnutí nebo vypnutí), protože protokolování zpráv může protokolovat data specifická pro aplikaci v záhlavích a subjektech. V případě [!INCLUDE[wxp](../../../includes/wxp-md.md)] je záznam zaznamenán do protokolu událostí aplikace. U [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] se záznam zaznamená do protokolu událostí zabezpečení.  
  
## <a name="transactions"></a>Transakce  
 Funkce transakcí poskytuje transakční služby pro aplikaci WCF.  
  
 Hlavičky transakce použité v šíření transakce mohou obsahovat ID transakce nebo ID zařazení, což jsou identifikátory GUID.  
  
 Funkce Transactions používá správce transakcí služby Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) ke správě stavu transakce (součást systému Windows). Ve výchozím nastavení jsou komunikace mezi správci transakcí zašifrována. Správci transakcí mohou protokolovat odkazy koncových bodů, ID transakcí a ID zařazení v rámci jejich trvalého stavu. Doba života tohoto stavu je určena životností souboru protokolu správce transakcí. Služba MSDTC vlastní a udržuje tento protokol.  
  
 Funkce transakcí implementuje standardy pro transakce WS-koordinační a WS-Atomic.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace v rámci WCF poskytují přenos zpráv, když dojde k selhání přenosu nebo zprostředkovatelských prostředků. Poskytují právě jeden přenos zpráv, i když se podkladové přenosy odpojí (například připojení TCP v bezdrátové síti) nebo ztratí zprávu (proxy server HTTP, který vyřazuje odchozí nebo příchozí zpráva). Spolehlivé relace také obnovují pořadí zpráv (k tomu může dojít v případě směrování s více uživateli) a zachovává pořadí, ve kterém se zprávy poslaly.  
  
 Spolehlivé relace se implementují pomocí protokolu WS-ReliableMessaging (WS-RM). Přidávají hlavičky WS-RM, které obsahují informace o relacích, které slouží k identifikaci všech zpráv přidružených ke konkrétní spolehlivé relaci. Každá relace WS-RM má identifikátor, který je identifikátorem GUID.  
  
 V počítači koncového uživatele nejsou zachovány žádné osobní údaje.  
  
## <a name="queued-channels"></a>Kanály zařazené do fronty  
 Fronty ukládají zprávy z odesílající aplikace jménem přijímající aplikace a později tyto zprávy předají do přijímající aplikace. Pomůžou zajistit přenos zpráv z odesílajících aplikací do přijímajících aplikací, když například přijímající aplikace je přechodný. Služba WCF poskytuje podporu pro řazení do fronty pomocí služby Microsoft řízení front zpráv (MSMQ) jako přenosu.  
  
 Funkce kanálů zařazených do fronty nepřidává do zprávy záhlaví. Místo toho vytvoří zprávu služby Řízení front zpráv s příslušným nastavením vlastností zprávy služby Řízení front zpráv a vyvolá metody služby Řízení front zpráv pro vložení zprávy do fronty služby Řízení front zpráv. Služba Řízení front zpráv je volitelná součást, která se dodává se systémem Windows.  
  
 Funkce kanálů ve frontě neuchovává žádné informace na počítači koncového uživatele, protože používá službu Řízení front zpráv jako infrastrukturu služby Řízení front zpráv.  
  
## <a name="com-integration"></a>Integrace COM+  
 Tato funkce zalomí existující funkce COM a COM+ a vytvoří služby, které jsou kompatibilní se službami WCF. Tato funkce nepoužívá konkrétní záhlaví a neuchovává data na počítači koncového uživatele.  
  
## <a name="com-service-moniker"></a>Moniker služby COM  
 To poskytuje nespravovaný obálku standardnímu klientovi WCF. Tato funkce nemá konkrétní záhlaví na lince ani neuchovává data v počítači.  
  
## <a name="peer-channel"></a>Rovnocenný kanál  
 Partnerský kanál umožňuje vývoj aplikací s více částmi pomocí WCF. Zasílání zpráv s více částmi probíhá v kontextu sítě. Sítě jsou označeny názvem, ke kterému se uzly můžou připojit. Každý uzel v partnerském kanálu vytvoří naslouchací proces TCP na portu zadaného uživatelem a naváže připojení k ostatním uzlům v síti, aby se zajistila odolnost. Pokud se chcete připojit k ostatním uzlům v síti, uzly také vyměňují data, včetně adresy naslouchacího procesu a IP adresy počítače, s dalšími uzly v síti. Zprávy odesílané do sítě mohou obsahovat informace o zabezpečení, které se týkají odesilatele, aby se zabránilo falšování a falšování zprávy.  
  
 V počítači koncového uživatele nejsou uloženy žádné osobní údaje.  
  
## <a name="it-professional-experience"></a>Uživatelské prostředí pro IT specialisty  
  
### <a name="tracing"></a>Trasování  
 Funkce diagnostiky infrastruktury WCF protokoluje zprávy, které procházejí prostřednictvím vrstev přenosu a modelu služby, a aktivit a událostí přidružených k těmto zprávám. Tato funkce je ve výchozím nastavení vypnutá. Je povolená pomocí konfiguračního souboru aplikace a chování trasování se dá v době běhu upravit pomocí zprostředkovatele WMI WCF. Pokud je tato možnost povolena, trasovací infrastruktura vygeneruje diagnostické trasování, které obsahuje zprávy, aktivity a zpracování událostí pro nakonfigurované naslouchací procesy. Formát a umístění výstupu jsou určeny volbami konfigurace naslouchacího procesu správce, ale obvykle se jedná o soubor ve formátu XML. Správce zodpovídá za nastavení seznamu řízení přístupu (ACL) na trasovacích souborech. Zejména pokud je hostovaný systémem Windows Activation System (WAS), správce by měl zajistit, aby soubory nebyly obsluhovány z veřejného virtuálního kořenového adresáře, pokud to není žádoucí.  
  
 Existují dva typy trasování: protokolování zpráv a trasování diagnostiky modelu služby, které jsou popsány v následující části. Každý typ je nakonfigurován pomocí vlastního zdroje trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>. Oba tyto zdroje trasování protokolování zachytí data, která jsou místní pro aplikaci.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Zdroj trasování protokolování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správci Protokolovat zprávy, které procházejí systémem. Uživatel může prostřednictvím konfigurace zaprotokolovat pouze celé zprávy nebo hlavičky zpráv, zda se mají protokolovat na vrstvy přenosu nebo modelu služby a zda mají být zahrnuty poškozené zprávy. Uživatel taky může nakonfigurovat filtrování, aby se omezilo protokolování zpráv.  
  
 Ve výchozím nastavení je protokolování zpráv zakázané. Správce místního počítače může zabránit tomu, aby správce na úrovni aplikace zapnul protokolování zpráv.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Šifrované a dešifrované protokolování zpráv  
 Zprávy jsou protokolovány, šifrovány nebo dešifrovány, jak je popsáno v následujících výrazech.  
  
 Protokolování přenosu  
 Protokoluje přijaté a odesílané zprávy na úrovni přenosu. Tyto zprávy obsahují všechny hlavičky a můžou být před odesláním na kabel a při přijímání zašifrované.  
  
 Pokud jsou zprávy před odesláním na síťový kabel zašifrované a jsou přijímány, zašifrují se i do protokolu. Výjimkou je případ, kdy se používá protokol zabezpečení (https): před odesláním a po přijetí, i když jsou zašifrovány na lince, se zaprotokolují dešifrování.  
  
 Protokolování služby  
 Protokoluje zprávy přijaté nebo odeslané na úrovni modelu služby, poté, co došlo ke zpracování hlaviček kanálu, těsně před a po zadání uživatelského kódu.  
  
 Zprávy, které jsou protokolovány na této úrovni, jsou dešifrovány, i když byly zabezpečeny a šifrovány na lince.  
  
 Poškozené protokolování zpráv  
 Protokoluje zprávy, které infrastruktura WCF nedokáže pochopit nebo zpracovat.  
  
 Zprávy jsou protokolovány tak, jak jsou, jsou zašifrovány nebo nikoli.  
  
 Pokud jsou zprávy protokolovány v dešifrovaném nebo nešifrovaném tvaru, služba WCF ve výchozím nastavení odstraní klíče zabezpečení a potenciálně osobní informace ze zpráv předtím, než je přihlásí. V dalších oddílech jsou popsány informace, které jsou odebrány a kdy. Správce počítače a nástroj pro nasazení aplikace musí provést určité konfigurační akce a změnit výchozí chování na klíče protokolu a potenciálně osobní údaje.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informace odebrané z hlaviček zpráv při protokolování dešifrovaných/nešifrovaných zpráv  
 Pokud jsou zprávy protokolovány v dešifrovaném/nešifrovaném tvaru, jsou klíče zabezpečení a potenciálně osobní informace ve výchozím nastavení odebrány z záhlaví zpráv a těla zprávy před jejich zápisem do protokolu. Následující seznam uvádí, co WCF považuje klíče a potenciálně osobní údaje.  
  
 Odebrané klíče:  
  
 \- pro xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst: BinarySecret  
  
 wst: entropie  
  
 \- pro xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse: heslo  
  
 wsse: nonce  
  
 Potenciálně odstraněné osobní informace:  
  
 \- pro xmlns: wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns: wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse: username  
  
 wsse:BinarySecurityToken  
  
 \- pro xmlns: SAML = "urn: Oasis: names: TC: SAML: 1.0: assertion" položky tučným písmem (níže) jsou odebrány:  
  
 @no__t – 0Assertion  
  
 MajorVersion = "1"  
  
 Podverze = "1"  
  
 AssertionId = "[ID]"  
  
 Vystavitel = "[řetězec]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<Conditions NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 @no__t – 0AudienceRestrictionCondition >  
  
 \<Audience > [URI] \</cílová skupina > +  
  
 \</AudienceRestrictionCondition > *  
  
 @no__t – 0DoNotCacheCondition/> *  
  
 < @ no__t-1--abstraktní základní typ  
  
 @no__t – 0Condition/> *  
  
 -->  
  
 @no__t – 0/podmínky >?  
  
 @no__t – 0Advice >  
  
 \<AssertionIDReference > [ID] \</AssertionIDReference > *  
  
 \<Assertion > [kontrolní výraz] \</kontrolní výraz > *  
  
 [any] *  
  
 \< > Rady?  
  
 < @ no__t-1--abstraktní základní typy  
  
 @no__t – 0Statement/> *  
  
 @no__t – 0SubjectStatement >  
  
 @no__t – 0Subject >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 @no__t – 0SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyUri] \</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [any] \</SubjectConfirmationData >?  
  
 \<ds: KeyInfo >... \</DS: KeyInfo >?  
  
 \</SubjectConfirmation >?  
  
 \</> předmětu  
  
 \</SubjectStatement > *  
  
 -->  
  
 @no__t – 0AuthenticationStatement  
  
 AuthenticationMethod = "[identifikátor URI]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 Závislosti  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < elementů AuthorityBinding  
  
 AuthorityKind = "[QName]"  
  
 Location = "[URI]"  
  
 Binding = "[URI]"  
  
 />*  
  
 \</AuthenticationStatement > *  
  
 @no__t – 0AttributeStatement >  
  
 Závislosti  
  
 @no__t – 0Attribute  
  
 AttributeName = "[řetězec]"  
  
 AttributeNamespace = "[identifikátor URI]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</atribut > +  
  
 \</AttributeStatement > *  
  
 @no__t – 0AuthorizationDecisionStatement  
  
 Prostředek = "[identifikátor URI]"  
  
 Rozhodnutí = "[Povolit&#124;odmítnutí&#124;neurčitelné]"  
  
 >  
  
 Závislosti  
  
 \<Action obor názvů = "[URI]" > [String] \</Action > +  
  
 @no__t – 0Evidence >  
  
 \<AssertionIDReference > [ID] \</AssertionIDReference > +  
  
 \<Assertion > [kontrolní výraz] \</kontrolní výraz > +  
  
 \</> legitimace?  
  
 \</AuthorizationDecisionStatement > *  
  
 \</kontrolní výraz >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informace odebrané z těla zprávy při protokolování dešifrovaných/nešifrovaných zpráv  
 Jak je popsáno výše, WCF odebere klíče a známé potenciálně osobní informace z hlaviček zpráv pro protokolované/nešifrované zprávy protokolu. Kromě toho WCF odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zprávy o zabezpečení zapojené do výměny klíčů.  
  
 Pro následující obory názvů:  
  
 xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (například, pokud není k dispozici žádná akce)  
  
 Odeberou se informace pro tyto prvky těla, které zahrnují výměnu klíčů:  
  
 wst: RequestSecurityToken  
  
 wst: RequestSecurityTokenResponse  
  
 wst: třída RequestSecurityTokenResponseCollection  
  
 Odeberou se taky informace pro každou z těchto akcí:  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Z hlaviček specifických pro aplikaci a dat těla nejsou odebrány žádné informace  
 WCF nesleduje osobní údaje v hlavičkách specifických pro aplikace (například řetězce dotazů) nebo data základního textu (například číslo platební karty).  
  
 Když je zapnuté protokolování zpráv, můžou se v protokolech zobrazovat osobní informace v záhlavích specifických pro jednotlivé aplikace a informace o textu. Znovu, nástroj pro nasazení aplikace zodpovídá za nastavení seznamů ACL pro konfigurační soubory a soubory protokolů. Může také vypnout protokolování, pokud nechce, aby tyto informace byly viditelné, nebo může tyto informace odfiltrovat od souborů protokolu po jejich zaprotokolování.  
  
### <a name="service-model-tracing"></a>Trasování modelu služby  
 Zdroj trasování modelu služby (<xref:System.ServiceModel>) umožňuje sledovat aktivity a události související se zpracováním zprávy. Tato funkce používá diagnostické funkce .NET Framework z <xref:System.Diagnostics>. Stejně jako u vlastnosti <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> je umístění a jeho seznam ACL uživatelsky konfigurovatelné pomocí konfiguračních souborů aplikace .NET Framework. Stejně jako u protokolování zpráv je umístění souboru vždy nakonfigurované, když správce povolí trasování; Proto správce řídí seznam ACL.  
  
 Pokud je zpráva v oboru, trasování obsahují záhlaví zpráv. Stejná pravidla pro skrývání potenciálně osobních údajů v hlavičkách zpráv v předchozí části platí: osobní údaje, které byly dříve identifikovány, jsou ve výchozím nastavení odebrány z hlaviček v trasování. Aby bylo možné protokolovat potenciálně osobní údaje, musí konfigurace správce počítače i nástroj pro nasazení aplikace upravit. Osobní údaje obsažené v hlavičkách specifických pro aplikace jsou však zaznamenávány do trasování. Nástroj pro nasazení aplikace zodpovídá za nastavení seznamů ACL pro konfigurační a trasovací soubory. Může také vypnout trasování, pokud nechce, aby tyto informace byly viditelné, nebo může vyfiltrovat tyto informace z trasovacích souborů po jejich zaprotokolování.  
  
 V rámci trasování ServiceModel (označované jako ID aktivit a obvykle identifikátor GUID) propojuje různé aktivity společně jako zprávu mezi různými částmi infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Vlastní naslouchací procesy trasování  
 Pro protokolování a trasování zpráv je možné nakonfigurovat vlastní naslouchací proces trasování, který může odesílat trasování a zprávy na lince (například do vzdálené databáze). Nástroj pro nasazení aplikací zodpovídá za konfiguraci vlastních naslouchacího procesu nebo k tomu, aby je uživatelé mohli použít. Zodpovídá taky za všechny osobní údaje vystavené ve vzdáleném umístění a pro správné použití seznamů ACL do tohoto umístění.  
  
### <a name="other-features-for-it-professionals"></a>Další funkce pro odborníky v oblasti IT  
 WCF má poskytovatele rozhraní WMI, který zpřístupňuje informace o konfiguraci infrastruktury WCF prostřednictvím rozhraní WMI (dodávané se systémem Windows). Ve výchozím nastavení je rozhraní WMI k dispozici správcům.  
  
 Konfigurace WCF používá mechanismus konfigurace .NET Framework. Konfigurační soubory jsou uloženy v počítači. Vývojář aplikací a správce vytvoří konfigurační soubory a seznam řízení přístupu pro jednotlivé požadavky aplikace. Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů. Certifikáty lze použít k poskytnutí dat aplikací pro konfiguraci různých vlastností funkcí používaných aplikací.  
  
 WCF také používá funkci výpisu paměti procesu .NET Framework voláním metody <xref:System.Environment.FailFast%2A>.  
  
### <a name="it-pro-tools"></a>Nástroje pro IT specialisty  
 WCF nabízí také následující profesionální nástroje, které dodávají Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer. exe  
 Prohlížeč zobrazí trasovací soubory WCF. Prohlížeč zobrazuje všechny informace, které jsou obsaženy v trasováních.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor. exe  
 Editor umožňuje uživateli vytvářet a upravovat konfigurační soubory služby WCF. Editor zobrazuje informace, které jsou obsaženy v konfiguračních souborech. Stejný úkol lze provést pomocí textového editoru.  
  
#### <a name="servicemodel_reg"></a>ServiceModel_Reg  
 Tento nástroj umožňuje uživateli spravovat na počítači instalaci ServiceModel. Nástroj zobrazí stavové zprávy v okně konzoly při spuštění a v procesu se může zobrazit informace o konfiguraci instalace služby WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig. exe a WSATUI. dll  
 Tyto nástroje umožňují odborníkům v oblasti IT konfigurovat interoperabilní podporu sítě WS-AtomicTransaction ve službě WCF. Nástroje se zobrazí a umožní uživateli změnit hodnoty nejčastěji používaných nastavení WS-AtomicTransaction uložených v registru.  
  
## <a name="cross-cutting-features"></a>Funkce pro různé vyprůřezování  
 Následující funkce jsou křížově vykrájené. To znamená, že mohou být tvořeny kteroukoli z výše uvedených funkcí.  
  
### <a name="service-framework"></a>Architektura služby  
 Hlavičky mohou obsahovat ID instance, což je identifikátor GUID, který přidruží zprávu s instancí třídy CLR.  
  
 Jazyk WSDL (Web Services Description Language) obsahuje definici portu. Každý port má adresu koncového bodu a vazbu, která představuje služby používané aplikací. Vystavení kódu WSDL může být vypnuto pomocí konfigurace. V počítači nejsou uchovány žádné informace.  
  
## <a name="see-also"></a>Viz také:

- [Windows Communication Foundation](index.md)
- [Zabezpečení](./feature-details/security.md)
