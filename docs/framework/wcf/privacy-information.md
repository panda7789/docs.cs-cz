---
title: Windows Communication Foundation – informace o ochraně osobních údajů
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: e278b28e5c0015eeab549b04d3870dfa247a57ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808868"
---
# <a name="windows-communication-foundation-privacy-information"></a>Windows Communication Foundation – informace o ochraně osobních údajů
Společnost Microsoft se zavazuje chránit osobní údaje koncoví uživatelé. Když vytvoříte aplikaci pomocí Windows Communication Foundation (WCF), verze 3.0, vaše aplikace může mít vliv na vaši koncoví uživatelé o ochraně osobních údajů. Například aplikace může shromažďovat explicitně kontaktní informace o uživateli, nebo může požádat nebo poslat informace přes Internet na webové stránky. Pokud vložíte technologie společnosti Microsoft v aplikaci, že technologie může mít svůj vlastní chování, které by mohly ovlivnit ochranu osobních údajů. WCF neodesílá žádné informace společnosti Microsoft z vaší aplikace Pokud jste nebo koncový uživatel se rozhodnete odeslat do us.  
  
## <a name="wcf-in-brief"></a>WCF v Brief  
 WCF je architektura distribuované zasílání zpráv pomocí rozhraní Microsoft .NET Framework, která umožňuje vývojářům vytvářet distribuované aplikace. Přenášená mezi dvěma aplikacemi zprávy obsahují informace hlavičky a text.  
  
 Záhlaví může obsahovat směrování zpráv, informace o zabezpečení, transakce a další v závislosti na služby, které aplikace používá. Ve výchozím nastavení jsou obvykle šifrované zprávy. Jedinou výjimkou je při použití `BasicHttpBinding`, který byl navržený pro použití s webovými službami-zabezpečené, starší verze. Jako návrháře aplikací jste zodpovědní za konečný návrh. Zprávy v těle protokolu SOAP obsahovat data, specifické pro aplikaci; Tato data, jako je například osobní informace definované aplikací, ale lze zabezpečit pomocí funkce WCF šifrování nebo důvěrnosti. Následující části popisují funkce, které mohou mít vliv na ochranu osobních údajů.  
  
## <a name="messaging"></a>Zasílání zpráv  
 Každá zpráva WCF má hlavičku adresy, která určuje cíl zprávy a kde se má zobrazit odpověď.  
  
 Komponenta adresy adresu koncového bodu je identifikátor URI (Uniform Resource) identifikující koncový bod. Adresa může být síťová adresa nebo logické adresy. Adresa může zahrnovat název počítače (název hostitele, plně kvalifikovaný název domény) a IP adresu. Adresa koncového bodu může obsahovat také globálně jedinečný identifikátor (GUID), nebo kolekce identifikátory GUID pro dočasné adresování použít pro každou adresu rozpoznat. Každá zpráva obsahuje ID zprávy, která je identifikátor GUID. Tato funkce se řídí odkaz standard adresování WS.  
  
 Vrstva zasílání zpráv WCF nelze zapsat žádné osobní údaje v místním počítači. Však ho může pokud vývojář service vytvoří služba, která zveřejňuje informace (například pomocí v název koncového bodu jméno uživatele, nebo se včetně osobních údajů v Web pro koncový bod rozšířit osobní informace na úrovni sítě Služby s popisem jazyka, ale které nevyžadují klienti používat protokol https pro přístup k schématu WSDL). Navíc pokud běží Vývojář [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro koncový bod, který zveřejňuje osobní údaje, výstup nástroje může obsahovat tyto informace a výstupní soubor je zapsán do místní pevný disk.  
  
## <a name="hosting"></a>Hostování  
 Hostování funkcí ve službě WCF umožňuje aplikacím můžete spustit na vyžádání nebo povolit sdílení portů mezi různými aplikacemi. Aplikace WCF může být hostovaný v Internetové informační služby (IIS), podobně jako [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Hostování nevystavuje žádné konkrétní informace v síti a není jej ponechat data v počítači.  
  
## <a name="message-security"></a>Zabezpečení zpráv  
 Zabezpečení WCF poskytuje funkce zabezpečení pro aplikace zasílání zpráv. Funkce zabezpečení poskytuje zahrnují ověřování a autorizace.  
  
 Ověřování se provádí pomocí předání přihlašovacích údajů mezi klienty a služby. Ověřování může být buď prostřednictvím zabezpečení na úrovni přenosu nebo prostřednictvím protokolu SOAP zprávy úroveň zabezpečení, následujícím způsobem:  
  
-   V zabezpečení zpráv protokolu SOAP provádí se ověření pomocí přihlašovacích údajů jako uživatelského jména a hesla, certifikáty X.509, lístky protokolu Kerberos a tokeny SAML, které mohou obsahovat osobní informace, v závislosti na vystavitele.  
  
-   Pomocí zabezpečení přenosu, ověření se provádí pomocí tradičního přenosu ověřovací mechanismy, které jako schémat ověřování protokolu HTTP (Basic, ověřování algoritmem Digest, Negotiate, integrované ověřování systému Windows, protokol NTLM, None a anonymní) a ověření formuláře.  
  
 Ověřování může způsobit v zabezpečené relaci mezi komunikuje koncových bodů. Relace je identifikována identifikátor GUID, který trvá po dobu životnosti relace zabezpečení. Následující tabulka uvádí, co se ukládají a kde.  
  
|Data|Úložiště|  
|----------|-------------|  
|Přihlašovací údaje prezentace, například uživatelské jméno, certifikáty X.509, tokeny pomocí protokolu Kerberos a odkazy na přihlašovací údaje.|Standardní Windows pověření správu mechanismy, jako je Windows úložiště certifikátů.|  
|Informace členství uživatele, například uživatelská jména a hesla.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] zprostředkovateli členství.|  
|Identity informace o službě, kterou používá k ověřování klientů.|Adresa koncového bodu služby.|  
|Informace o subjektu volajícím.|V protokolech auditování.|  
  
## <a name="auditing"></a>Auditování  
 Auditování zaznamenává úspěchy a chyby ověřování a autorizace událostí. Auditování záznamy obsahují následující data: služby URI, identifikátor URI akce a identifikace volajícího.  
  
 Auditování také záznamy, když správce upraví konfiguraci protokolování zpráv (ho na zapnutí a vypnutí funkce), protože protokolování zpráv může protokolovat data specifické pro aplikaci v záhlaví a obsah. Pro [!INCLUDE[wxp](../../../includes/wxp-md.md)], záznam se zaznamenají do protokolu událostí aplikace. Pro [!INCLUDE[wv](../../../includes/wv-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], záznam se zaznamenají do protokolu událostí zabezpečení.  
  
## <a name="transactions"></a>Transakce  
 Transakce funkce poskytuje transakční služby WCF aplikaci.  
  
 Záhlaví transakce používá v transakci šíření může obsahovat ID transakce nebo zařazení ID, které jsou identifikátory GUID.  
  
 Transakce funkce používá správce transakcí Microsoft Distributed Transaction Coordinator služba MSDTC () (součásti systému Windows) ke správě stav transakce. Ve výchozím nastavení jsou zašifrovaná komunikace mezi správci transakcí. Správci transakcí může odkazy na koncový bod, ID transakce a zařazení ID protokolu v rámci jejich trvalého stavu. Životnost tento stav je určen podle životnost soubor protokolu správce transakcí. Služba koordinátoru MS DTC vlastní a spravuje tento protokol.  
  
 Transakce funkce implementuje WS-koordinace a WS-Atomic Transactions standardy.  
  
## <a name="reliable-sessions"></a>Spolehlivé relace  
 Spolehlivé relace ve WCF poskytují přenos zpráv, když dojde k přenosu nebo zprostředkující selhání. Poskytují přesně-jednou přenosu zpráv i v případě, že základní přenos odpojí (například připojení protokolu TCP v bezdrátové síti) nebo zruší zprávu (proxy serveru HTTP vyřadit zprávu příchozí nebo odchozí). Spolehlivé relace také obnovit zprávy změna (jak může dojít v případě více cest směrování), zachování pořadí, ve které byly odeslány zprávy.  
  
 Spolehlivé relace se implementují pomocí protokolu WS-ReliableMessaging (WS-RM). Zvyšují WS-RM hlavičky, které obsahují informace o relace, které slouží k identifikaci všechny zprávy, které jsou spojené s konkrétní spolehlivé relace. Každá relace WS-RM má identifikátor, který je identifikátor GUID.  
  
 Žádné osobní informace se uchovávají v počítači uživatele end.  
  
## <a name="queued-channels"></a>Kanály zařazených do fronty  
 Fronty ukládat zprávy z odesílající aplikací jménem přijímající aplikace a později předávat tyto zprávy do přijímající aplikace. Mohou pomoci při má přijímající aplikace je třeba přechodný zajišťování přenos zpráv z odesílání na přijímací aplikace. WCF poskytuje podporu pro službu Řízení front pomocí Microsoft služby Řízení front zpráv (MSMQ) jako přenosového mechanismu.  
  
 Funkci ve frontě kanály nepřidá záhlaví zprávy. Místo toho se vytvoří zprávy služby Řízení front zpráv s příslušné služby Řízení front zpráv sady zpráv vlastnosti a volá metody služby Řízení front zpráv se umístí zprávy ve frontě služby Řízení front zpráv. Služba Řízení front zpráv je volitelná součást, která se dodává s verzí systému Windows.  
  
 Žádné informace se uchovávají na počítači koncového uživatele na funkcí ve frontě kanály, protože používá služby Řízení front zpráv jako front infrastruktury.  
  
## <a name="com-integration"></a>Integrace COM+  
 Tato funkce zabalí stávající funkce COM a modelu COM + k vytvoření služby, které jsou kompatibilní se službou WCF services. Tato funkce nepoužívá konkrétní hlavičky a neuchovává data na počítači koncového uživatele je.  
  
## <a name="com-service-moniker"></a>Monikeru služby COM  
 To zajišťuje nespravované obálku standardní klienta WCF. Tato funkce nemá konkrétní hlavičky v drátové síti ani nemá zachovat data na počítači.  
  
## <a name="peer-channel"></a>Rovnocenný kanál  
 Rovnocenného kanálu umožňuje vývoj více stran aplikací s použitím WCF. Více stran zasílání zpráv dojde v kontextu mřížku. Mřížek jsou identifikovány názvem, který se můžete zapojit do uzlů. Každý uzel v rovnocenného kanálu vytvoří naslouchací proces TCP na portu zadán uživatel a navázat připojení s ostatními uzly v mřížce zajistit odolnost proti chybám. Pokud chcete připojit k jiné uzly v mřížce, uzly také exchange některá data, včetně adres naslouchací proces a IP adres je počítač, se jiné uzly v mřížce. Zprávy odeslané kolem v mřížce může obsahovat informace o zabezpečení, která se týkají odesílatele, aby se zabránilo falšování identity zprávu a manipulaci.  
  
 Žádné osobní informace jsou uloženy na počítači uživatele end.  
  
## <a name="it-professional-experience"></a>Prostředí pro odborníky v oblasti IT  
  
### <a name="tracing"></a>Trasování  
 Diagnostické funkce infrastruktury WCF zaznamená zprávy, které předáte přenosu a vrstvy modelu služby a aktivity a události související se tyto zprávy. Tato funkce je ve výchozím nastavení vypnutý. Je povolené, pomocí konfiguračního souboru aplikace a chování trasování, může se mění pomocí zprostředkovatele rozhraní WCF WMI v době běhu. Když je povolené, vysílá infrastruktury trasování diagnostické trasování, která obsahuje zprávy, aktivity a zpracování události nakonfigurované naslouchací procesy. Formát a umístění výstupu určuje možnostmi konfigurace naslouchací proces správce, ale je obvykle formátovaný soubor XML. Správce je zodpovědný za nastavení seznamu řízení přístupu (ACL) pro trasovací soubory. Zejména při hostování podle aktivace systému Windows (WAS), správce Ujistěte se, že soubory nejsou zpracovat z veřejné virtuálního kořenového adresáře, pokud je, není žádoucí.  
  
 Existují dva typy trasování: protokolování zpráv a Model služby diagnostické trasování, popsané v následující části. Každý typ je konfigurovaný pomocí vlastní zdroj trasování: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> a <xref:System.ServiceModel>. Obě tyto zdroje protokolování trasování zachytit data, která je lokální vzhledem k aplikaci.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zdroj trasování zpráv (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umožňuje správcům zprávy protokolu s tokem prostřednictvím systému. Prostřednictvím konfigurace může uživatel rozhodnout protokolu celé zprávy nebo pouze hlavičky zpráv, zda se mají protokolovat v modelu vrstev přenosu nebo služby a zda mají být zahrnuty poškozených zpráv. Tento uživatel také může nakonfigurovat filtrování a omezit, které zprávy se zaznamenávají.  
  
 Ve výchozím nastavení je protokolování zpráv zakázaná. Zapnutí protokolování zpráv na úrovni aplikace správce můžete zabránit správce místního počítače.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Protokolování zpráv šifrovaná a dešifrovaným  
 Zprávy se protokolují, zašifrovaná nebo dešifrovat, jak je popsáno v následující podmínky.  
  
 Protokolování přenosu  
 Zaznamenává zprávy přijatých a odeslaných na úrovni přenosu. Tyto zprávy obsahují všechny hlavičky a může být šifrována před odesláním v drátové síti a pokud se přijímají.  
  
 Pokud jsou šifrované zprávy před odesláním v drátové síti a při příjmu, jsou zaznamenány šifrovaná i. Výjimkou je, pokud protokol zabezpečení používané (https): pak jsou zaznamenány dešifrovat před odesláním a po přijímání i v případě, že se šifrují v drátové síti.  
  
 Protokolování služby  
 Zaznamenává zprávy přijatých nebo odeslaných na úrovni modelu služby, po zpracování záhlaví kanálu došlo k, těsně před a po zadání uživatelského kódu.  
  
 Zprávy zaznamenané na této úrovni jsou dešifrovat i v případě, že by byly zabezpečená a šifrovaná v drátové síti.  
  
 Protokolování poškozených zpráv  
 Zaznamenává zprávy, které infrastrukturu WCF nemůže pochopit nebo zpracovat.  
  
 Zprávy se zaznamenávají jako-je, který je šifrovaná, nebo není  
  
 Zprávy se protokolují dešifrovaný nebo nezašifrované podobě, ve výchozím nastavení WCF odebere klíče zabezpečení a potenciálně osobní údaje z zprávy před jejich protokolování. Další části popisují, jaké informace se odebere a kdy. Správce počítače a nástroje pro nasazení aplikace musí provést určité akce konfigurace, chcete-li změnit výchozí chování do protokolu klíče a potenciálně osobní údaje.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informace o odebrat z hlavičky zpráv, pokud protokolování dešifrovat nebo bez šifrování zprávy  
 Když zprávy se protokolují v dešifrovat nezašifrované podobě zabezpečení klíčů a potenciálně osobní údaje jsou odebrány ve výchozím nastavení z hlavičky zpráv a obsah zpráv předtím, než jsou zaznamenány. V následujícím seznamu uvedeny, co WCF považuje za klíče a potenciálně osobní údaje.  
  
 Klíče, které jsou odebrány:  
  
 \- Xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 WSt:BinarySecret  
  
 WSt:Entropy  
  
 \- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:Nonce  
  
 Potenciálně osobní údaje, které byly odstraněny:  
  
 \- Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" a xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- Pro xmlns:saml = "urn: oasis: názvy: tc: SAML:1.0:assertion" položky tučným písmem (dole) jsou odebrány:  
  
 \<Kontrolní výraz  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId = "[ID]"  
  
 Vystavitel = "[řetězec]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<Podmínky neplatí před = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 \<AudienceRestrictionCondition >  
  
 \<Audience>[uri]\</Audience>+  
  
 \</ AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition / > *  
  
 <\!--abstraktní základní typ  
  
 \<Podmínka / > *  
  
 -->  
  
 \</ Podmínky >?  
  
 \<Rady, jak >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > *  
  
 \<Kontrolní výraz > [assertion]\</Assertion > *  
  
 [žádné] *  
  
 \</ Poradenství >?  
  
 <\!--Abstraktní základní typy  
  
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
  
 \<SubjectConfirmationData > [žádné]\</SubjectConfirmationData >?  
  
 \<ds:KeyInfo>...\</ds:KeyInfo>?  
  
 \</ SubjectConfirmation >?  
  
 \</ Předmět >  
  
 \</ SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod = "[uri]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 [Subjektu]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind = "[QName]"  
  
 Umístění = "[uri]"  
  
 Vazba = "[uri]"  
  
 />*  
  
 \</ AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Subjektu]  
  
 \<Atribut  
  
 AttributeName = "[řetězec]"  
  
 AttributeNamespace = "[uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</ Atribut > +  
  
 \</ AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Prostředek = "[uri]"  
  
 Rozhodnutí = "[Povolit&#124;Odepřít&#124;neurčitém]"  
  
 >  
  
 [Subjektu]  
  
 \<Akce Namespace = "[uri]" > [řetězec]\</Action > +  
  
 \<Důkaz >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > +  
  
 \<Kontrolní výraz > [assertion]\</Assertion > +  
  
 \</ Důkazy >?  
  
 \</ AuthorizationDecisionStatement > *  
  
 \</ Kontrolní výraz >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informace z těla zprávy odstraněny, až protokolování dešifrovat nebo bez šifrování zprávy  
 Jak se popisuje výš, WCF odebere klíče a známé potenciálně osobní informace ze záhlaví zprávy zprávy zaznamenané dešifrovat nebo bez šifrování. Kromě toho WCF odebere klíče a známé potenciálně osobní údaje z těla zprávy pro prvky těla a akce v následujícím seznamu, které popisují zabezpečení zprávy, které jsou zahrnuté v výměny klíčů.  
  
 Pro následující obory názvů:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" a xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (například pokud není k dispozici žádná akce)  
  
 Pro tyto elementy textu, které zahrnují výměny klíčů jsou odebrány informace:  
  
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
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Žádné informace se odebere z hlavičky specifické pro aplikace a Data textu  
 WCF nesleduje osobní informace hlavičky specifické pro aplikaci (například řetězce dotazu) nebo text data (například číslo platební karty).  
  
 Pokud protokolování zpráv je zapnutý, může být osobní údaje v hlavičkách konkrétní aplikace a tělo informace viditelné v protokolech. Nástroje pro nasazení aplikace znovu, zodpovídá za nastavení seznamy ACL v souborech konfigurace a protokolu. Si můžete také vypnout protokolování Pokud nechce tyto informace mají být zobrazeny, nebo mu může vyfiltrovat tyto informace ze souborů protokolu, po je protokolována.  
  
### <a name="service-model-tracing"></a>Služby modelu trasování  
 Zdroj trasování Model služby (<xref:System.ServiceModel>) umožňuje trasování aktivit a události související se zpracování zprávy. Tato funkce používá diagnostické funkce rozhraní .NET Framework z <xref:System.Diagnostics>. Stejně jako u <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> vlastnost, umístění a jeho seznamu ACL jsou uživatelsky konfigurovatelného pomocí konfigurační soubory aplikace rozhraní .NET Framework. Stejně jako u protokolování zpráv umístění souboru vždy nakonfigurované, pokud správce povolí trasování; Proto může správce nastavit seznam řízení přístupu.  
  
 Trasování obsahovat hlavičky zpráv, pokud zpráva je v oboru. Použít stejná pravidla pro skrytí potenciálně osobní údaje v záhlaví zpráv v předchozí části: odeberou se osobní informace, které už identifikované ve výchozím nastavení z hlavičky v trasování. Správce počítače a nástroje pro nasazení aplikace, musíte změnit konfiguraci chcete-li protokolu potenciálně osobní údaje. Osobní informace obsažené v hlavičkách specifické pro aplikaci je ale přihlášení trasování. Nástroje pro nasazení aplikace je zodpovědná za nastavení seznamy ACL v souborech konfigurace a trasování. Mu taky můžete vypnout trasování Pokud nechce tyto informace mají být zobrazeny, nebo mu můžete filtrovat tyto informace z trasování souborů po je protokolována.  
  
 Jako součást ServiceModel trasování, jedinečné ID (nazývané ID aktivit a obvykle identifikátor GUID) propojit různé aktivity společně jako zprávu prochází různých částí infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Vlastní trasování – moduly naslouchání  
 Pro obě zprávy protokolování a trasování naslouchací proces vlastního trasování je možné nakonfigurovat, které může poslat trasování a zprávy v drátové síti (například ke vzdálené databázi). Nástroje pro nasazení aplikace je zodpovědná za konfiguraci vlastní naslouchací procesy nebo uživatelům umožníte tak. Také je odpovědný žádné osobní údaje, které jsou zveřejněné ve vzdáleném umístění a správně použití seznamů řízení přístupu do tohoto umístění.  
  
### <a name="other-features-for-it-professionals"></a>Další funkce pro IT specialisty  
 WCF má poskytovatel rozhraní WMI, který zveřejňuje informace o konfiguraci infrastruktury WCF prostřednictvím rozhraní WMI (dodávané se systémem Windows). Ve výchozím nastavení je k dispozici správcům rozhraní WMI.  
  
 Konfigurace WCF používá mechanismus konfigurace rozhraní .NET Framework. Konfigurační soubory, které jsou uložené na počítači. Vývojář aplikace a správce vytvořit konfigurační soubory a seznamu ACL pro všechny požadavky na aplikace. Konfigurační soubor může obsahovat adresy koncových bodů a odkazy na certifikáty v úložišti certifikátů. Certifikáty slouží k poskytování data aplikací můžete nakonfigurovat různé vlastnosti funkce, které používá aplikaci.  
  
 WCF také používá funkci rozhraní .NET Framework proces výpisu voláním <xref:System.Environment.FailFast%2A> metoda.  
  
### <a name="it-pro-tools"></a>IT specialista nástroje  
 WCF také poskytuje následující IT odborníky v oblasti nástroje, které se dodávají v sadě Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Prohlížeč zobrazí WCF trasovací soubory. Prohlížeč zobrazí, ať informací obsažených v trasování.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Editor umožňuje uživatelům vytvářet a upravovat WCF konfigurační soubory. Editor zobrazuje, ať informace je obsažena v konfiguračních souborech. Pro stejnou úlohu můžete provést pomocí textového editoru.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Tento nástroj umožňuje uživatelům spravovat ServiceModel nainstaluje na počítač. Nástroj zobrazí stavové zprávy v okně konzoly, když běží a v procesu, se může zobrazovat informace o konfiguraci instalace WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe a WSATUI.dll  
 Tyto nástroje povolit Odborníci v oblasti IT provést konfiguraci podpory sítě umožňuje vzájemnou spolupráci WS-AtomicTransaction ve WCF. Nástroje pro zobrazení a povolit uživatelům změnit hodnoty nejčastěji používané WS-AtomicTransaction nastavení uložená v registru.  
  
## <a name="cross-cutting-features"></a>Mezi vyjímání funkce  
 Následující funkce jsou mezi vyjímání. To znamená mohou být komponovaná s žádným z předchozích funkcí.  
  
### <a name="service-framework"></a>Architektura služby  
 Záhlaví může obsahovat ID instance, což je identifikátor GUID, který přidruží zprávu instance třídy CLR.  
  
 Webové služby popis Language (WSDL) obsahuje definici portu. Každý z portů má adresu koncového bodu a vazbu, která představuje služby, které aplikace používá. Vystavení WSDL může být vypnuto pomocí konfigurace. Žádné informace se uchovávají v počítači.  
  
## <a name="see-also"></a>Viz také  
 [Windows Communication Foundation](http://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Zabezpečení](../../../docs/framework/wcf/feature-details/security.md)
