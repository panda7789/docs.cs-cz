---
title: "Overview1 zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
caps.latest.revision: "37"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74a2e5c15b25dc9958b74ddeb0abf9adcad10bc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a>Přehled zabezpečení
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]je SOAP na základě zpráv distribuované programovací platforma a zabezpečení zpráv mezi klienty a služby je důležité chránit data. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje platformu univerzální a vzájemná spolupráce pro výměnu zabezpečených zpráv na základě existující infrastruktura zabezpečení a standardy rozpoznaný zabezpečení protokolu SOAP zprávy.  
  
> [!NOTE]
>  Komplexní pokyny k zabezpečení WCF, najdete v části [doprovodné materiály zabezpečení WCF](http://go.microsoft.com/fwlink/?LinkID=158912).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá koncepty, které znáte, pokud jste vytvořili zabezpečené, distribuovaných aplikací pomocí existujících technologií, jako je například HTTPS, Windows integrované zabezpečení, nebo uživatelská jména a hesla k ověřování uživatelů. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jenom se integruje s existující infrastruktury zabezpečení, ale taky ji rozšiřuje distribuované zabezpečení nad rámec domény pouze pro systém Windows pomocí zabezpečených zpráv protokolu SOAP. Vezměte v úvahu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace existující mechanismy zabezpečení se hlavní výhodou použití protokolu SOAP jako protokol kromě existující protokoly. Přihlašovací údaje, které identifikují klienta nebo služby, jako je uživatelské jméno a heslo nebo certifikáty X.509, například mít umožňuje vzájemnou spolupráci profily založené na XML protokolu SOAP. Pomocí těchto profilů, zprávy se vyměňují bezpečně využitím open specifikace jako XML – digitální podpisy a šifrování XML. Seznam specifikací najdete v tématu [webové služby protokoly podporované vazbami vzájemné spolupráce System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Jiné paralelní je modelu COM (Component Object) na platformě Windows, která umožňuje zabezpečený, distribuované aplikace. COM má mechanismus komplexní zabezpečení, které mohou být předávány kontext zabezpečení mezi součástmi; Tento mechanismus vynucuje integrity, šifrování a ověřování. Ale COM není povolen a platformy, zabezpečení, jako je zasílání zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepodporuje. Pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], můžete vytvořit služeb a klientů, které jsou rozmístěny z domén systému Windows přes Internet. Vzájemná spolupráce zprávy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou nezbytné pro vytváření dynamických, řízenými podnikem služby, které vám pomůžou jistotu, že v okně zabezpečení vašich informací.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Výhody zabezpečení aplikace Windows Communication Foundation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]je Distribuovaný programovací platforma založená na protokolu SOAP zprávy. Pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], můžete vytvořit aplikace, že fungují jako služby a služby klientů, vytváření a zpracování zpráv ze neomezený počet jiných služeb a klientů. V takové distribuované aplikace můžete zprávy toku z jednoho uzlu do druhého, přes brány firewall na Internetu a prostřednictvím mnoha zprostředkovatelů protokolu SOAP. To představuje celou řadu bezpečnostních hrozeb zprávy. Následující příklady ilustrují některé běžné hrozby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení může pomoci zmírnit při výměně zpráv mezi entitami:  
  
-   Sledování síťových přenosů získat citlivé informace. Například v případě pomocí online bankovnictví klient požádá o převod prostředků z jednoho účtu na jiný. Uživatel se zlými úmysly zachycuje zprávy a číslo účtu a heslo, později provádí převod prostředků ze ohrožení bezpečnosti účtu.  
  
-   Neautorizovaných serverů entity, který funguje jako služby, bez vědomí klienta. Uživatel se zlými úmysly (podvodný) v tomto scénáři funguje jako služba online a zachytí zprávy z klienta získat citlivé informace. Potom podvodný používá odcizené data převádět prostředky z ohrožení bezpečnosti účtu. Tento útok je také známá *útoky phishing*.  
  
-   Změnou zprávy a pokuste se získat jiné výsledky než volajícím určené. Například změna číslo účtu, do které se provádí záloha umožňuje fondů přejít na podvodný účtu.  
  
-   Opětovná přehrání hackerům, ve kterých se hacker nepříjemnosti replays stejné nákupní objednávka. Například v online knihkupectví přijímá stovky objednávek a odesílá webu knihy zákazníkovi, který nebyl řazení je.  
  
-   Neschopnost služby ověření klienta. Službu nelze v tomto případě zajistil, provést příslušné osoby transakce.  
  
 Zabezpečení přenosu v souhrnu, poskytuje následující:  
  
-   Ověřování služby koncového bodu (respondent).  
  
-   Ověření objektu zabezpečení (iniciátor) klienta.  
  
-   Zpráva integrity.  
  
-   Důvěrnost zpráv.  
  
-   Zjišťování opakování.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integrace se stávající infrastruktury zabezpečení  
 Nasazení webové služby mají často, existující řešení zabezpečení na místě, například Secure Sockets Layer (SSL) nebo protokol Kerberos. Některé využít výhod infrastruktury zabezpečení, která již byla nasazena, jako je například doménách systému Windows pomocí služby Active Directory. Často je potřeba integrovat tyto existujících technologií při vyhodnocování a přijetí ty, které jsou novější.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpečení se integruje s existující modely zabezpečení přenosu a můžete využít stávající infrastrukturu pro novější modely zabezpečení přenosu založené na protokolu SOAP zprávy zabezpečení.  
  
### <a name="integration-with-existing-authentication-models"></a>Integrace s existující modely ověřování  
 Důležitou součástí kteréhokoli modelu zabezpečení komunikace je schopnost identifikovat a ověřovat entity v komunikaci. Tyto entity v komunikaci používají "digitální identity", nebo přihlašovací údaje k ověření pravosti s komunikuje partnerské uzly. Jako vyvinuly distribuované komunikace platformy, je implementovaná různé ověřování přihlašovacích údajů a zabezpečení modelů. Například na Internetu, je běžné použití uživatelské jméno a heslo k identifikaci uživatelů. V intranetu se stává stále běžné použití řadiče domény pomocí protokolu Kerberos pro zálohování uživatele a ověřování služby. V některých scénářích například mezi dvěma obchodními partnery, lze použít certifikáty pro vzájemné ověření partnery.  
  
 V celém světě webových služeb, kde mohou být vystaveny stejnou službu k interní podnikové zákazníky také tak, aby externí partnery nebo Internet zákazníků, z toho důvodu je důležité, aby poskytovaly infrastruktury pro integraci se tyto existující zabezpečení ověřování modelů. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpečení podporuje celou řadu typů přihlašovacích údajů (ověřování modelů), včetně:  
  
-   Anonymní volající.  
  
-   Pověření klienta název uživatele.  
  
-   Certifikát pověření klienta.  
  
-   Windows (protokol Kerberos a NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy a vzájemná funkční spolupráce  
 Ve světě s velké existující nasazení je taková situace vzácná homogenity. Distribuované computing nebo komunikace platformy musí spolupracovat s technologie, které nabízejí různých výrobců. Podobně zabezpečení musí být taky umožňuje vzájemnou spolupráci.  
  
 Chcete-li systémy umožňuje vzájemnou spolupráci zabezpečení, společnosti v odvětví webové služby vytvořili celou řadu standardů. Konkrétně týkající se zabezpečení, byly navrženy několik upozorňují na důležité standardy: WS-zabezpečení: zabezpečení zpráv protokolu SOAP (subjektem standardy OASIS a dříve označované jako WS-zabezpečení), WS-Trust, WS-SecureConversation a WS-SecurityPolicy.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje širokou škálu scénářů interoperability. <xref:System.ServiceModel.BasicHttpBinding> Třída zaměřuje na základní profil zabezpečení (BSP) a <xref:System.ServiceModel.WSHttpBinding> třída je zaměřený na nejnovější standardy zabezpečení, jako je WS-zabezpečení 1.1 a WS-SecureConversation. Dodržujte tyto standardům [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení můžete zajistit vzájemnou funkční spolupráci a integraci s webovými službami, které jsou hostované na operačních systémů a jinými platformami než Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Funkčním oblastem zabezpečení WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpečení je rozdělené do tří funkčním oblastem: přenos zabezpečení, řízení přístupu a auditování. V následujících částech stručně popisují tyto oblasti a zadejte odkazy pro další informace.  
  
### <a name="transfer-security"></a>Zabezpečení přenosu  
 Zabezpečení přenosu zahrnuje tři hlavní zabezpečení funkce: integrity, šifrování a ověřování. *Integrita* je schopnost rozpoznat, zda zpráva bylo manipulováno. *Důvěrnost* je schopnost zachovat zprávu nejde přečíst nikdo jiný než zamýšlený příjemce; toho je dosaženo pomocí šifrování. *Ověřování* je schopnost ověření uváděné identity. Tyto tři funkce společně pomáhají zajistit, aby bezpečně doručování zpráv z jednoho bodu do jiného.  
  
#### <a name="transport-and-message-security-modes"></a>Přenos a režimy zabezpečení zpráv  
 Dva hlavní mechanismy slouží k implementaci zabezpečení přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: *přenosu* režimu zabezpečení a *zpráva* režim zabezpečení.  
  
-   *Režim zabezpečení přenosu* používá protokol transportní vrstvy, jako je například HTTPS, abyste dosáhli zabezpečení přenosu. Režim přenosu má výhodu v podobě se široce přijímaná, k dispozici na mnoha platformách a méně výpočetně komplexní. Má však nevýhodou zabezpečení zpráv jenom z typu point-to-point.  
  
-   *Režim zabezpečení zprávy*na druhé straně, používá zabezpečení WS (a dalších specifikacích) k implementaci zabezpečení přenosu. Vzhledem k tomu, že zabezpečení zpráv se použije přímo ke zprávám SOAP a se nachází v obálky protokolu SOAP, společně s dat aplikací, má výhodu v podobě probíhá přenos nezávislý, více rozšiřitelný a zajistit – koncové zabezpečení (oproti point-to-point); má nevýhodou je několikrát pomalejší než režim zabezpečení přenosu, protože se musí řešit XML povaha protokolu SOAP zprávy.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tyto rozdíly, najdete v části [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Třetí režim zabezpečení používá oba režimy předchozí a přináší výhody obou. Tento režim se nazývá `TransportWithMessageCredential`. V tomto režimu zabezpečení zpráv se používá k ověření klienta a zabezpečení přenosu se používá k ověření serveru a zajištění důvěrnosti zpráv a integrita. Díky tomu `TransportWithMessageCredential` režim zabezpečení je téměř tak rychlý jako režim zabezpečení přenosu a zajišťuje rozšiřitelnost ověřování klienta stejným způsobem jako zabezpečení zpráv. Ale na rozdíl od režim zabezpečení zprávy, neposkytuje dokončení – koncové zabezpečení.  
  
### <a name="access-control"></a>Access Control  
 *Řízení přístupu* je také označován jako autorizace. *Autorizace* umožňuje různým uživatelům různých oprávnění k zobrazení dat. Například protože společnosti lidských zdrojů soubory obsahují zaměstnanec citlivá data, jsou povolena pouze správci zobrazíte údaje o zaměstnancích. Správci navíc můžete zobrazit jenom data pro jejich přímé podřízené. V takovém případě řízení přístupu podle rolí ("správce") jak konkrétní identity manager (Chcete-li zabránit prohlížení záznamy o jiný správce zaměstnanci jeden správce).  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], jsou k dispozici funkce řízení přístupu prostřednictvím integrace s common language runtime (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> přes sadu rozhraní API, které jsou známé jako *modelu identity*. Podrobnosti o řízení přístupu a autorizace na základě deklarací identity najdete v tématu [rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Auditování  
 *Auditování* je protokolování událostí zabezpečení do protokolu událostí systému Windows. Můžete protokolovat události související se zabezpečením, jako je například selhání ověřování (nebo úspěchy). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programovací podrobnosti najdete v tématu [postup: události auditu zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)  
 [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Informace o zabezpečení a doporučené postupy](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Konfigurace služeb pomocí konfiguračních souborů](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Rozšíření zabezpečení](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
