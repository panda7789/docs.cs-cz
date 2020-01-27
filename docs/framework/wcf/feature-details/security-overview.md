---
title: Přehled zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 1e551572fa6d94e9fd1170eb7e3b258f2e8fb926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728891"
---
# <a name="windows-communication-foundation-security-overview"></a>Přehled zabezpečení Windows Communication Foundation
Windows Communication Foundation (WCF) je distribuovaná programovací platforma založená na zprávách SOAP a zabezpečení zpráv mezi klienty a službami je nezbytné pro ochranu dat. WCF poskytuje všestrannou a interoperabilní platformu pro výměnu zabezpečených zpráv na základě stávající bezpečnostní infrastruktury a uznávaných standardů zabezpečení pro zprávy SOAP.  
  
> [!NOTE]
> Komplexní průvodce zabezpečením služby WCF najdete v tématu [pokyny pro zabezpečení WCF](https://archive.codeplex.com/?p=WCFSecurity).  
  
 WCF používá koncepty, které jsou známé, pokud jste vytvořili zabezpečené a distribuované aplikace se stávajícími technologiemi, jako je například HTTPS, integrované zabezpečení systému Windows nebo uživatelská jména a hesla pro ověřování uživatelů. Služba WCF není integrována pouze se stávajícími bezpečnostními infrastrukturami, ale také rozšiřuje distribuované zabezpečení nad doménami pouze Windows pomocí zabezpečených zpráv SOAP. Zvažte technologii WCF implementaci stávajících mechanismů zabezpečení s významnou výhodou použití protokolu SOAP jako protokolu spolu s existujícími protokoly. Například přihlašovací údaje, které identifikují klienta nebo službu, například uživatelské jméno a heslo nebo certifikáty X. 509, mají interoperabilní profily SOAP založené na XML. Pomocí těchto profilů se zprávy vyměňují bezpečně tím, že využívají otevřené specifikace, jako jsou digitální podpisy XML a šifrování XML. Seznam specifikací najdete v tématu [protokoly webových služeb podporované vazbami interoperability poskytovanými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Další paralelní je model COM (Component Object Model) na platformě Windows, který umožňuje zabezpečené distribuované aplikace. Model COM má komplexní bezpečnostní mechanismus, při kterém je možné mezi komponentami přesměrovat kontext zabezpečení. Tento mechanismus vynutil integritu, důvěrnost a ověřování. Model COM ale nepovoluje pro různé platformy zabezpečená zasílání zpráv, jako je WCF. Pomocí WCF můžete sestavovat služby a klienty, které jsou z domén Windows přes Internet. Interoperabilní zprávy služby WCF jsou nezbytné pro vytváření dynamických, podnikových služeb, které vám pomohou se zachováním zabezpečení vašich informací.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Výhody zabezpečení Windows Communication Foundation  
 WCF je distribuovaná programovací platforma založená na zprávách SOAP. Pomocí WCF můžete vytvářet aplikace, které fungují jako služby a klienti služeb, vytvářet a zpracovávat zprávy z neomezeného počtu jiných služeb a klientů. V takové distribuované aplikaci můžou zprávy procházet z uzlu do uzlu, přes brány firewall, na Internet a prostřednictvím řady dodavatelů SOAP. To přináší nejrůznější hrozby zabezpečení zpráv. Následující příklady ilustrují některé běžné hrozby, které může zabezpečení WCF při výměně zpráv mezi entitami pomáhat zmírnit:  
  
- Sledování síťového provozu pro získání citlivých informací. Například v případě online bankovnictví klient požaduje přenos finančních prostředků z jednoho účtu na jiný. Uživatel se zlými úmysly zachycuje zprávu a má číslo účtu a heslo, později provede přenos prostředků z ohroženého účtu.  
  
- Neautorizovaných entit fungujících jako služby bez vědomí klienta. V tomto scénáři uživatel se zlými úmysly funguje jako online služba a zachycuje zprávy od klienta za účelem získání citlivých informací. Pak neautorizovaným pomocí odcizených dat přenáší prostředky z ohroženého účtu. Tento útok je známý taky *útokem na útok phishing*.  
  
- Změna zpráv, aby se získal jiný výsledek než volající zamýšlený. Například změna čísla účtu, na který je vklad vytvořen, umožňuje prostředkům přejít na neautorizovaný účet.  
  
- V hackerech se přehrávají, ve kterých se v důsledku rušivého hackera přehrává stejná nákupní objednávka. Online knihkupectví například obdrží stovky objednávek a zasílá je zákazníkům, kteří je neobjednali.  
  
- Neschopnost služby ověřit klienta. V takovém případě se služba nemůže ujistit, že příslušná osoba provedla transakci.  
  
 V části Souhrn přenosů zabezpečení poskytuje následující záruky:  
  
- Ověřování koncového bodu služby (respondent).  
  
- Ověřování objektu zabezpečení klienta (iniciátor).  
  
- Integrita zprávy.  
  
- Důvěrnost zpráv.  
  
- Zjišťování opětovného přehrání.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integrace se stávajícími bezpečnostními infrastrukturami  
 Nasazení webových služeb často obsahují existující řešení zabezpečení, například SSL (Secure Sockets Layer) (SSL) nebo protokol Kerberos. Některé využívají infrastrukturu zabezpečení, která již byla nasazena, například domény systému Windows pomocí služby Active Directory. Při vyhodnocování a současném přijímání nových technologií je často potřeba tyto technologie integrovat.  
  
 Zabezpečení WCF se integruje s existujícími modely zabezpečení přenosů a může využít stávající infrastrukturu pro novější modely zabezpečení přenosu založené na zabezpečení zpráv SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integrace s existujícími modely ověřování  
 Důležitou součástí jakéhokoli modelu zabezpečení komunikace je schopnost identifikovat a ověřovat entity v komunikaci. Tyto entity v komunikaci využívají "digitální identity" nebo přihlašovací údaje, aby se ověřily pomocí komunikujících partnerských uzlů. V případě vývoje distribuovaných komunikačních platforem byly implementovány různé ověřování přihlašovacích údajů a související modely zabezpečení. Například na internetu je použití uživatelského jména a hesla k identifikaci uživatelů běžné. V intranetu je běžné použití řadiče domény Kerberos k zálohování ověřování uživatelů a služeb. V některých scénářích, například mezi dvěma obchodními partnery, se certifikáty dají použít k vzájemnému ověření partnerů.  
  
 Proto je v celém světě webových služeb, kde může být stejná služba vystavena interním zákazníkům společnosti i externím partnerům nebo zákazníkům v Internetu, je důležité, aby infrastruktura poskytovala integraci s těmito stávajícími zabezpečeními. modely ověřování. Zabezpečení WCF podporuje širokou škálu typů přihlašovacích údajů (modelů ověřování), včetně:  
  
- Anonymní volající.  
  
- Uživatelské jméno klienta přihlašovací údaje.  
  
- Přihlašovací údaje klienta certifikátu.  
  
- Windows (protokol Kerberos a NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy a interoperabilita  
 V celém světě s velkými existujícími nasazeními je homogenita zřídka. Distribuované výpočetní a komunikační platformy musí spolupracovat s nabídkou různých výrobců. Stejně tak musí být zabezpečení také vzájemně ovladatelné.  
  
 Aby bylo možné zapnout interoperabilní systémy zabezpečení, společnosti, které jsou aktivní v oboru webových služeb, jsou vytvořeny řadou standardů. Konkrétně o zabezpečení bylo navrženo několik významných standardů: WS-Security: SOAP Message Security (přijatý OASIS standardy Standards a dříve označované jako WS-Security), WS-Trust, WS-SecureConversation a WS-SecurityPolicy.  
  
 WCF podporuje širokou škálu scénářů interoperability. <xref:System.ServiceModel.BasicHttpBinding> třídy cílí na základní profil zabezpečení (BSP) a <xref:System.ServiceModel.WSHttpBinding>á Třída cílí na nejnovější standardy zabezpečení, jako je WS-Security 1,1 a WS-SecureConversation. Díky dodržování těchto standardů může zabezpečení WCF spolupracovat a integrovat s webovými službami hostovanými v operačních systémech a platformách jiných než Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Oblasti funkčnosti zabezpečení WCF  
 Zabezpečení WCF je rozdělené do tří funkčních oblastí: přenos zabezpečení, řízení přístupu a auditování. Následující části stručně popisují tyto oblasti a poskytují odkazy na Další informace.  
  
### <a name="transfer-security"></a>Přenos zabezpečení  
 Přenos zabezpečení zahrnuje tři hlavní funkce zabezpečení: integrita, důvěrnost a ověřování. *Integrita* je schopnost zjistit, zda byla zpráva úmyslně poškozena. *Důvěrné* je schopnost uchovávat zprávu, kterou nemůže číst nikdo jiný než zamýšlený příjemce; toho je dosaženo prostřednictvím kryptografie. *Ověřování* je schopnost ověřit deklarované identity. Společně tyto tři funkce vám pomůžou zajistit, aby zprávy byly bezpečně doručeny z jednoho bodu do druhého.  
  
#### <a name="transport-and-message-security-modes"></a>Režimy zabezpečení přenosů a zpráv  
 K implementaci přenosu zabezpečení ve službě WCF se používají dva hlavní mechanismy: režim zabezpečení *přenosu* a režim zabezpečení *zpráv* .  
  
- *Režim zabezpečení přenosu* používá k zajištění zabezpečení přenosu protokol na úrovni přenosu, jako je například https. Přenosový režim má výhodu širokého přijetí, k dispozici na mnoha platformách a méně výpočetně složitých. Nicméně má nevýhodu zabezpečení zpráv pouze z typu Point-to-Point.  
  
- *Režim zabezpečení zpráv*na druhé straně používá k implementaci přenosu zabezpečení protokol WS-Security (a další specifikace). Vzhledem k tomu, že se zabezpečení zpráv používá přímo na zprávy SOAP a je obsaženo uvnitř obálek protokolu SOAP spolu s daty aplikace, má výhodu přenosů, které jsou nezávislé na přenosu, rozšiřitelnosti a zajištění komplexního zabezpečení (oproti Point-to-Point); Nevýhodou je více pomalejší než režim zabezpečení přenosu, protože se musí zabývat XML povahou zpráv SOAP.  
  
 Další informace o těchto rozdílech najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Třetí režim zabezpečení používá předchozí režimy a přináší výhody obou. Tento režim se nazývá `TransportWithMessageCredential`. V tomto režimu se k ověřování serveru používá zabezpečení zprávy a zabezpečení přenosu se používá k ověření serveru a zajištění důvěrnosti a integrity zpráv. Díky tomu je režim zabezpečení `TransportWithMessageCredential` skoro stejně rychlý jako režim zabezpečení přenosu a poskytuje rozšiřitelné ověřování klientů stejným způsobem jako zabezpečení zpráv. Na rozdíl od režimu zabezpečení zpráv ale neposkytuje kompletní zabezpečení.  
  
### <a name="access-control"></a>Access Control  
 *Řízení přístupu* se také označuje jako autorizace. *Autorizace* umožňuje různým uživatelům mít různá oprávnění k zobrazení dat. Například protože soubory lidských zdrojů společnosti obsahují citlivá data zaměstnanců, smějí zobrazovat data zaměstnanců pouze manažeři. Kromě toho mohou manažeři zobrazit pouze data pro své přímé sestavy. V tomto případě je řízení přístupu založeno jak na roli ("správce"), tak i na konkrétní identitě správce (aby se zabránilo jednomu manažerovi v prohlížení záznamů zaměstnanců jiného manažera).  
  
 Ve službě WCF jsou funkce řízení přístupu poskytovány prostřednictvím integrace s modulem CLR (Common Language Runtime) <xref:System.Security.Permissions.PrincipalPermissionAttribute> a prostřednictvím sady rozhraní API, které se označují jako *model identity*. Podrobnosti o řízení přístupu a autorizaci na základě deklarací najdete v tématu [rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Auditování  
 *Auditování* je protokolování událostí zabezpečení do protokolu událostí systému Windows. Můžete protokolovat události související se zabezpečením, jako jsou například selhání ověřování (nebo úspěšné). Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Podrobnosti o programování najdete v tématu [Postupy: Auditovat události zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)
- [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
- [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Informace o zabezpečení a osvědčené postupy](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Konfigurace služeb pomocí konfiguračních souborů](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
