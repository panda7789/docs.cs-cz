---
title: Overview1 zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 94f1284e864bc63c321e004ac4a20843b191711d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136952"
---
# <a name="security-overview"></a>Přehled zabezpečení
Windows Communication Foundation (WCF) je protokol SOAP založenou na zprávách programovací platforma pro distribuované a zabezpečení zpráv mezi klienty a službami je nezbytné pro ochranu dat. WCF poskytuje všestranné a interoperabilní platformu pro výměnu zabezpečených zpráv na základě existující infrastruktura zabezpečení a standardům hlediska zabezpečení pro zprávy protokolu SOAP.  
  
> [!NOTE]
>  Komplexní pokyny k zabezpečení WCF najdete v části [doprovodné materiály zabezpečení WCF](https://go.microsoft.com/fwlink/?LinkID=158912).  
  
 Koncepty používá WCF, které jsou známé, pokud jste vytvořili zabezpečené distribuované aplikace se stávajícími technologiemi, jako je například HTTPS, Windows integrované zabezpečení, nebo uživatelská jména a hesla k ověřování uživatelů. WCF nejen integruje do stávající infrastruktury zabezpečení, ale také rozšiřuje distribuovanou zabezpečení nad rámec domény jen pro Windows pomocí zabezpečených zpráv SOAP. Zvažte implementaci stávající mechanismy zabezpečení se hlavní výhodou použití protokolu SOAP jako protokol kromě existující protokoly WCF. Přihlašovací údaje, které identifikují klienta nebo služby, jako je uživatelské jméno a heslo nebo certifikáty X.509, například mít interoperabilní profily založené na XML protokolu SOAP. Pomocí těchto profilů, zprávy se vyměňují bezpečně s využitím open specifikace jako XML digitálních podpisů a šifrování XML. Seznam specifikací najdete v tématu [webové služby protokoly podporované vazbami Interoperability System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Jiné paralelní je modelu COM (Component Object) na platformě Windows, který umožňuje zabezpečené distribuované aplikace. COM má komplexního zabezpečení mechanismus, kterým mohou být předávány kontext zabezpečení mezi součástmi; Tento mechanismus vynucuje integrity, šifrování a ověřování. COM ale neumožňuje víc platforem, zabezpečené, zasílání zpráv jako WCF. Pomocí WCF, můžete vytvořit služeb a klientů, které jsou rozmístěny v doménách Windows přes Internet. Interoperabilní zprávy WCF jsou zásadní pro sestavování dynamických, řízenými podnikem služby, které vám pomůžou jistotu, že v zabezpečení vašich informací.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Výhodné kvůli zabezpečení Windows Communication Foundation  
 WCF je Distribuovaný programovací platforma založená na protokolu SOAP zprávy. Pomocí technologie WCF, můžete vytvořit aplikace, že fungují jako služby a služby klientů, vytvoření a zpracování zpráv ze neomezený počet dalších služeb a klientů. V takových distribuovanou aplikaci zprávy čárách uzly, prostřednictvím brány firewall na Internetu a mnoho zprostředkovatelů SOAP. To přináší širokou škálu zpráva bezpečnostní hrozby. Následující příklady znázorňují některé běžné hrozby, které pomůžou zmírnit při výměně zpráv mezi entitami v zabezpečení WCF:  
  
-   Sledování síťových přenosů získat citlivé informace. Například ve scénáři online bankovnictví, klient požádá o převod prostředků z jednoho účtu do druhého. Uživatel se zlými úmysly zachycuje zpráva a máte číslo účtu a heslo, později provede převod prostředků z ohrožení bezpečnosti účtu.  
  
-   Neautorizovaných serverů entity, který funguje jako služby, bez sledování serverů klienta. V tomto scénáři uživatel se zlými úmysly (podvodný) funguje jako služba online a zachytí zpráv od klienta k získání citlivé informace. Potom podvodný používá odcizeného data převádět prostředky z ohrožení bezpečnosti účtu. Tento útok je rovněž známé *útoku*.  
  
-   Změna zpráv získat jiné výsledky než modul volající určené. Například změna číslo účtu, ke kterému vklad provedení umožňuje fondů přejdete na podvodného účtu.  
  
-   Riziko kyberzločinci, ve kterých se hacker nepříjemný přehrává stejné nákupní objednávky. Například v online knihkupectví přijímá stovky objednávek a odesílá knih pro zákazníky, kteří ještě seřadili.  
  
-   Nemožnost služby ověření klienta. V tomto případě služba nelze zajistit, že příslušné osoby provádět transakce.  
  
 Stručně řečeno přenos security poskytuje následující:  
  
-   Služba ověřování koncových bodů (respondent).  
  
-   Ověření objektu zabezpečení (iniciátor) klienta.  
  
-   Integrity zprávy.  
  
-   Důvěrnost zpráv.  
  
-   Zjišťování opakování.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integrovat do stávajících infrastruktur zabezpečení  
 Nasazení webové služby mají často, stávající řešení zabezpečení v místě, například vrstvy SSL (Secure Sockets) nebo protokolu Kerberos. Některé využít výhod zabezpečení infrastruktury, která již byla nasazena, jako je například domén Windows pomocí služby Active Directory. Často je potřeba integrovat se stávajícími technologiemi, tyto při testování a přijímání novější značky.  
  
 Zabezpečení WCF integruje do stávající modely zabezpečení přenosu a využít stávající infrastrukturu pro novější modely zabezpečení přenosu založené na protokolu SOAP zprávy zabezpečení.  
  
### <a name="integration-with-existing-authentication-models"></a>Integrace se stávajícími modely ověřování  
 Důležitou součástí jakékoli komunikační model zabezpečení je schopnost identifikovat a ověřovat entity v komunikaci. Tyto entity v komunikaci pomocí "digitálních identit" nebo přihlašovací údaje, sami ověření pomocí komunikující partnerských uzlů. Jak vyvinula platformy distribuovaných komunikace, byly implementovány různé ověřování přihlašovacích údajů a zabezpečení modely. Například v síti Internet, je běžné použití uživatelské jméno a heslo k identifikaci uživatelů. V síti intranet je stále běžné použití řadiče domény pomocí protokolu Kerberos pro zálohování uživatele a ověření služby. V některých scénářích jako například mezi dvěma obchodními partnery, lze použít certifikáty pro vzájemné ověření partnerů.  
  
 Ve světě velkých webových služeb, kde ve stejné službě mohou být vystaveny pro zákazníky internetové nebo interní firemní zákazníky i jako externí partnery, je proto důležité, že poskytují infrastrukturu pro integraci s těmito existující zabezpečení modely ověřování. Zabezpečení WCF podporuje širokou škálu typů přihlašovacích údajů (ověřování modelů), včetně:  
  
-   Anonymní volajícího.  
  
-   Pověření klienta uživatelského jména.  
  
-   Certifikát přihlašovacích údajů klienta.  
  
-   Windows (protokol Kerberos a LanMan NT [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy a vzájemná funkční spolupráce  
 Ve světě s velké stávající nasazení homogenity není obvyklé. Distribuované výpočetní/komunikace platformy musí spolupracovat s technologiemi, které nabízejí různých výrobců. Obdobně zabezpečení musí být také interoperabilní.  
  
 Pokud chcete povolit interoperabilní zabezpečení systémů, jste vytvořili společností v oboru webové služby active celou řadu norem. Konkrétně týkající se zabezpečení byly navrženy několik významných standardů: WS-Security: Zabezpečení zpráv SOAP (subjektem OASIS standardy a dříve označované jako WS-Security), WS-Trust, WS-SecureConversation a WS-SecurityPolicy.  
  
 WCF podporuje širokou škálu scénářů vzájemná funkční spolupráce. <xref:System.ServiceModel.BasicHttpBinding> Třídy, zaměřuje na základní profil zabezpečení (BSP) a <xref:System.ServiceModel.WSHttpBinding> třídy je zaměřený na nejnovějších standardů zabezpečení, jako je WS-Security 1.1 a WS-SecureConversation. Zabezpečení WCF díky dodržování těchto standardů, můžete spolupracovat a integraci s webovými službami, které jsou hostované v operačních systémech a platformách než Windows Microsoft.  
  
## <a name="wcf-security-functional-areas"></a>Funkční oblasti zabezpečení WCF  
 Zabezpečení WCF je rozdělené do tří funkčních oblastí: přenos zabezpečení, řízení přístupu a auditování. Následující části stručně popisují tyto oblasti a poskytují odkazy pro další informace.  
  
### <a name="transfer-security"></a>Zabezpečení přenosu  
 Zabezpečení přenosu zahrnuje tři hlavní zabezpečení funkce: integrity, šifrování a ověřování. *Integrita* je na schopnost detekce, zda zprávy bylo manipulováno. *Důvěrnost* je schopnost uchovat zprávy nejde přečíst kdokoli než zamýšlený příjemce; toho je dosaženo pomocí šifrování. *Ověřování* je schopnost ověřit požadovanou identitu. Společně tyto tři funkce pomáhají zajistit, že bezpečné doručování zpráv z jednoho místa do jiného.  
  
#### <a name="transport-and-message-security-modes"></a>Přenos a režimy zabezpečení zpráv  
 Pro implementaci přenosu zabezpečení ve službě WCF se používají dva hlavní mechanismy: *přenosu* režim zabezpečení a *zpráva* režim zabezpečení.  
  
-   *Režim zabezpečení Transport* používá protokol transportní vrstvy, jako je například HTTPS, abyste dosáhli zabezpečení přenosu. Režim přenosu nabízí výhodu v podobě běžně používaná, dostupnost na spoustě platforem a méně výpočetně složité. Má však nevýhodou zabezpečení zprávy pouze z typu point-to-point.  
  
-   *Režim zabezpečených zpráv*na druhou stranu, použití WS-Security (a dalších specifikacích) k implementaci zabezpečení přenosu. Vzhledem k tomu, že zabezpečení zprávy se u přímo zprávy protokolu SOAP a je obsaženo uvnitř obálky protokolu SOAP, spolu s daty aplikace má výhodu v podobě se zabezpečením přenosu nezávislé na protokol, více rozšiřitelné a zajistit, že začátku do konce (oproti point-to-point); má nevýhodou je několikrát pomalejší než režim zabezpečení transport, protože bylo potřeba zabývat XML povaze zprávy protokolu SOAP.  
  
 Další informace o těchto rozdílech najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Třetí režim zabezpečení používá obou předchozích režimech a přináší výhody obou. Tento režim se nazývá `TransportWithMessageCredential`. V tomto režimu se zabezpečení zprávy se používá k ověření klienta a zabezpečení přenosu se používá k ověření tohoto serveru a poskytují zprávu důvěrnost a integrita. Díky tomu `TransportWithMessageCredential` režim zabezpečení je téměř stejně rychlé jako režim zabezpečení transport a poskytuje klienta možnosti rozšíření ověřování stejným způsobem jako zabezpečení zpráv. Ale na rozdíl od režim zabezpečených zpráv, neposkytuje kompletní zabezpečení začátku do konce.  
  
### <a name="access-control"></a>Řízení přístupu  
 *Řízení přístupu* se také nazývá autorizace. *Autorizace* umožňuje různým uživatelům mají různá oprávnění zobrazit data. Například protože vaší společnosti lidských zdrojů soubory obsahují zaměstnance citlivých dat, jsou povoleny pouze správci zobrazíte data zaměstnanců. Správci dál, můžete zobrazit pouze data pro své přímé podřízené. V takovém případě řízení přístupu podle role (dále jen "správce") i konkrétní identity Manageru (aby se zabránilo jeden správce z pohledu záznamy zaměstnanců jiného správce).  
  
 Ve službě WCF, funkce řízení přístupu jsou k dispozici díky integraci se službou common language runtime (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> a prostřednictvím sady rozhraní API, nazývá *modelem identity*. Podrobnosti o řízení přístupu a autorizace na základě rolí najdete v tématu [rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Auditování  
 *Auditování* je protokolování událostí zabezpečení do protokolu událostí Windows. Můžete protokolovat události související se zabezpečením, jako je například selhání ověřování (nebo úspěšné). Další informace najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programování podrobnosti najdete v tématu [jak: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
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
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
