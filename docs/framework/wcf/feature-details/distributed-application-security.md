---
title: Zabezpečení distribuované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
ms.openlocfilehash: cb271bcf8fb27bae4c8ef6b60df0f8d2940ecb9a
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964825"
---
# <a name="distributed-application-security"></a>Zabezpečení distribuované aplikace
Zabezpečení Windows Communication Foundation (WCF) je rozdělené do tří hlavních funkčních oblastí: přenos zabezpečení, řízení přístupu a auditování. Přenos zabezpečení zajišťuje integritu, důvěrnost a ověřování. Zabezpečení přenosu je zajištěno jedním z následujících způsobů: zabezpečení přenosu, zabezpečení zpráv nebo `TransportWithMessageCredential`.  
  
 Přehled zabezpečení zpráv WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o dalších dvou částech zabezpečení služby WCF najdete v tématu [authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) and [audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Scénáře zabezpečení přenosu  
 Mezi běžné scénáře, které využívají zabezpečení služby WCF Transfer, patří následující:  
  
- Zabezpečený přenos pomocí systému Windows. Klient a služba WCF se nasazují v doméně systému Windows (nebo v doménové struktuře Windows). Zprávy obsahují osobní údaje, takže požadavky zahrnují vzájemné ověřování klienta a služby, integritu zpráv a důvěrnost zpráv. Kromě toho je vyžadováno potvrzení, že došlo k určité transakci, například příjemce zprávy by měl zaznamenat informace o podpisu.  
  
- Zabezpečený přenos pomocí `UserName` a HTTPS. Aby bylo možné pracovat přes Internet, je nutné vyvinout klienta a službu WCF. Pověření klienta se ověřují v databázi párů uživatelských jmen a hesel. Služba se nasadí na adresu HTTPS pomocí certifikátu důvěryhodného SSL (Secure Sockets Layer) (SSL). Vzhledem k tomu, že se zprávy cestují přes Internet, musí být klient a služba vzájemně ověřeny a při přenosu musí být zachovány důvěrnost a integrita zprávy.  
  
- Zabezpečený přenos pomocí certifikátů. Aby bylo možné pracovat s veřejným internetem, musí být vyvinutý klient a služba WCF. U klienta i služby jsou k dispozici certifikáty, které lze použít k zabezpečení zpráv. Klient a služba používají Internet ke komunikaci mezi sebou a k provádění transakcí s vysokými hodnotami, které vyžadují integritu zpráv, důvěrnost a vzájemné ověřování.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integrita, důvěrnost a ověřování  
 Tři funkce – integrita, důvěrnost a ověřování – se nazývají zabezpečení přenosu. Možnost přenést zabezpečení poskytuje funkce, které pomáhají zmírnit hrozby distribuované aplikace. Následující tabulka stručně popisuje tři funkce, které tvoří zabezpečení přenosu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|Integrita|*Integrita* je záruka, že data jsou doplněná a přesná, zejména po přechodu z jednoho bodu do druhého a případně přečtená mnoha aktéry. Aby se zabránilo manipulaci s daty, je nutné zachovat integritu a obvykle se dosahuje digitálním podepsáním zprávy.|  
|Důvěrnost|*Důvěrné* je ujištění, že zpráva nebyla přečtena jiným uživatelům než zamýšleným čtenářem. Například číslo platební karty musí být důvěrné při posílání přes Internet. Důvěrnost je často zajištěná šifrováním dat pomocí schématu veřejného klíče a privátního klíče.|  
|Ověřování|*Ověřování* je ověřením deklarované identity. Například při použití bankovního účtu je nutné, aby bylo možné odebrat prostředky pouze skutečnému vlastníkovi účtu. Ověřování může být zajištěno různými prostředky. Jednou z běžných metod je systém uživatele nebo hesla. Druhým je použití certifikátu X. 509, který je poskytován třetí stranou.|  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 WCF má několik režimů přenosu zabezpečení, které jsou popsány v následující tabulce.  
  
|Režim|Popis|  
|----------|-----------------|  
|Žádné|Žádné zabezpečení není k dispozici na transportní vrstvě nebo ve vrstvě zpráv. Žádná z předdefinovaných vazeb nepoužívá tento režim ve výchozím nastavení, s výjimkou [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) prvek nebo, při použití kódu, třídy <xref:System.ServiceModel.BasicHttpBinding>.|  
|Doprava|Používá k zajištění integrity, důvěrnosti a vzájemného ověřování zabezpečenou přenosovou hodnotu, jako je například HTTPS.|  
|Zpráva|Pro zajištění integrity, důvěrnosti a vzájemného ověřování používá zabezpečení SOAP zpráv. Zprávy SOAP jsou zabezpečeny podle standardů WS-Security.|  
|Smíšený režim|Využívá zabezpečení přenosu pro zajištění integrity, důvěrnosti a ověřování serveru. Pro ověřování klientů používá zabezpečení zpráv (WS-Security a jiné standardy).<br /><br /> (Tento výčet pro tento režim je `TransportWithMessageCredential`.)|  
|Obojí|Provádí ochranu a ověřování na obou úrovních. Tento režim je k dispozici pouze v prvku [\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) .|  
  
## <a name="credentials-and-transfer-security"></a>Pověření a přenos zabezpečení  
 *Přihlašovací údaje* jsou data, která se zobrazují pro vytvoření požadované identity nebo schopností. Předložení přihlašovacích údajů zahrnuje prezentaci dat i kontrolu jejich držení. WCF podporuje různé typy přihlašovacích údajů na úrovni zabezpečení Transport i zpráva. Můžete zadat typ přihlašovacích údajů pro vazbu WCF.  
  
 V mnoha zemích nebo oblastech je licence ovladače příkladem přihlašovacích údajů. Licence obsahuje data, která představují identitu a možnosti. Obsahuje důkaz o vlastnictví ve formě obrázku svého držitele. Licence je vydaná důvěryhodnou autoritou, obvykle státním licenčním oddělením. Licence je zapečetěná a může obsahovat hologram, který ukazuje, že není úmyslně poškozen nebo padělaný.  
  
 Můžete například zvážit dva typy přihlašovacích údajů podporovaných v rámci WCF: uživatelské jméno a (X. 509) přihlašovací údaje certifikátu.  
  
 Pro přihlašovací údaje uživatelského jména představuje uživatelské jméno deklaraci identity a heslo prezentuje důkaz o vlastnictví. Důvěryhodná autorita v tomto případě je systém, který ověřuje uživatelské jméno a heslo.  
  
 V pověření certifikátu lze použít název subjektu, alternativní název subjektu nebo konkrétní pole v rámci certifikátu pro reprezentaci deklarované identity nebo možností. Ověření vlastnictví dat v přihlašovacích údajích je vytvořeno pomocí přidruženého privátního klíče k vygenerování podpisu.  
  
 Další informace o programování přenosu [zabezpečení a zadání](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)přihlašovacích údajů najdete v tématu věnovaném [vazbám a zabezpečením](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) .  
  
### <a name="transport-client-credential-types"></a>Typy přihlašovacích údajů klienta přenosu  
 V následující tabulce jsou uvedeny možné hodnoty používané při vytváření aplikace, která používá zabezpečení přenosu. Tyto hodnoty můžete použít buď v kódu, nebo v nastavení vazby.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí prezentovat žádné přihlašovací údaje. To se týká anonymního klienta.|  
|Základní|Určuje základní ověřování. Další informace najdete v tématu RFC2617, "[ověřování http: základní a ověřování algoritmem Digest](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)".|  
|Otisk|Určuje ověřování hodnotou hash. Další informace najdete v tématu RFC2617, "[ověřování http: základní a ověřování algoritmem Digest](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)".|  
|NTLM|Určuje ověřování systému Windows pomocí vyjednávání SSPI v doméně systému Windows.<br /><br /> Vyjednávání SSPI má za následek použití protokolu Kerberos nebo NT LanMan (NTLM).|  
|Windows|Určuje ověřování systému Windows pomocí rozhraní SSPI v doméně systému Windows. Rozhraní SSPI vybere buď protokol Kerberos, nebo protokol NTLM jako ověřovací službu.<br /><br /> Rozhraní SSPI nejprve vyzkouší protokol Kerberos; Pokud se to nepovede, používá protokol NTLM.|  
|Certifikát|Provádí ověřování klientů pomocí certifikátu, obvykle X. 509.|  
  
### <a name="message-client-credential-types"></a>Typy přihlašovacích údajů klienta zprávy  
 V následující tabulce jsou uvedeny možné hodnoty používané při vytváření aplikace, která používá zabezpečení zpráv. Tyto hodnoty můžete použít buď v kódu, nebo v nastavení vazby.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Umožňuje službě interakci s anonymními klienty.|  
|Windows|Umožňuje výměnu zpráv SOAP za ověřeným kontextem pověření systému Windows. Používá mechanismus vyjednávání SSPI k výběru buď protokolu Kerberos, nebo protokolu NTLM jako ověřovací služby.|  
|Uživatelské jméno|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. Všimněte si, že WCF nepovoluje žádné kryptografické operace s uživatelským jménem, jako je například generování podpisu nebo šifrování dat. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu.|  
|CardSpace|Umožňuje službě, aby vyžadovala ověření klienta pomocí služby CardSpace.|  
  
### <a name="programming-credentials"></a>Přihlašovací údaje pro programování  
 Pro každý typ přihlašovacích údajů klienta vám programovací model WCF umožňuje zadat hodnoty přihlašovacích údajů a validátory přihlašovacích údajů pomocí chování služby a kanálu.  
  
 Zabezpečení WCF má dva typy přihlašovacích údajů: chování přihlašovacích údajů služby a chování přihlašovacích údajů kanálu. Chování přihlašovacích údajů ve službě WCF určuje skutečná data, konkrétně přihlašovací údaje použité ke splnění požadavků zabezpečení vyjádřených pomocí vazeb. Ve službě WCF je třída klienta komponenta modulu runtime, která se převádí mezi vyvoláním operace a zprávy. Všichni klienti dědí z třídy <xref:System.ServiceModel.ClientBase%601>. Vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> v základní třídě umožňuje zadat různé hodnoty přihlašovacích údajů klienta.  
  
 Ve službě WCF jsou chování služby atributy aplikovány na třídu implementující kontrakt služby (rozhraní) pro programové řízení služby. Třída <xref:System.ServiceModel.Description.ServiceCredentials> umožňuje zadat certifikáty pro pověření služby a nastavení ověřování klienta pro různé typy přihlašovacích údajů klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Model vyjednávání pro zabezpečení zpráv  
 Režim zabezpečení zpráv umožňuje provést přenos zabezpečení, aby bylo možné pověření služby nakonfigurovat na vzdáleném klientovi. Pokud například používáte certifikát uložený v úložišti certifikátů Windows, je nutné použít nástroj jako modul snap-in konzoly MMC (Microsoft Management Console).  
  
 Režim zabezpečení zpráv také umožňuje provést přenos zabezpečení, aby bylo možné pověření služby vyměňovat s klientem v rámci prvotního vyjednávání. Chcete-li povolit vyjednávání, nastavte vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> na hodnotu `true`.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
