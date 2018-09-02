---
title: Zabezpečení distribuované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dbc06afd4695b85f426fad2859b4c6d4b6684d6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402910"
---
# <a name="distributed-application-security"></a>Zabezpečení distribuované aplikace
Zabezpečení Windows Communication Foundation (WCF) se dělí na tři hlavní oblasti funkčnosti: přenos zabezpečení, řízení přístupu a auditování. Zabezpečení přenosu poskytuje integritu, šifrování a ověřování. Zabezpečení přenosu poskytuje jednu z následujících: zabezpečení, zabezpečení zprávy přenosu nebo `TransportWithMessageCredential`.  
  
 Přehled zabezpečení zpráv WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o dalších dvou částech zabezpečení WCF najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) a [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Scénáře zabezpečení přenosu  
 Běžné scénáře, které využívají zabezpečení přenosu WCF patří:  
  
-   Vyžádání bezpečného přenosu pomocí Windows. Klient WCF a služby jsou nasazené v doméně Windows (nebo doménové struktury Windows). Zprávy obsahují osobní údaje, takže požadavky zahrnují vzájemného ověřování klienta a služby, zprávu, integritu a důvěrnost zpráv. Navíc se vyžaduje ověření, že konkrétní operace došlo k chybě, například příjemce zprávy měli zaznamenávat informace o podpisu.  
  
-   Zabezpečení přenosu pomocí `UserName` a HTTPS. Klient WCF a služby musí být vyvinuto pro práci na Internetu. Přihlašovací údaje pro klienta ověřit proti databázi párů jméno/heslo uživatele. Nasazení služby na adrese HTTPS pomocí důvěryhodného certifikátu vrstvy SSL (Secure Sockets). Protože zprávy putovat po Internetu, klient a služba musí být vzájemně se ověřují a musí být zachovány tyto zprávy důvěrnost a integrita během přenosu.  
  
-   Vyžádání bezpečného přenosu pomocí certifikátů. Klienta WCF a služby musí být vyvinuto pro práci prostřednictvím veřejného Internetu. Klient a služba mít certifikáty, které lze použít k zabezpečení zprávy. Klient a služba používat Internet bude komunikovat mezi sebou a provádět transakce vysoké hodnoty, které vyžadují integrity zprávy, utajení a vzájemné ověřování.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integritu, šifrování a ověřování  
 Tři funkce, integritu a důvěrnost ověřování – se společně nazývají zabezpečení přenosu. Zabezpečení přenosu poskytuje funkce, které pomůžou zmírnit hrozby do distribuované aplikace. Následující tabulka stručně popisuje tři funkce, které tvoří zabezpečení přenosu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|Integrita|*Integrita* je jistotou, že jsou data úplné a přesné, zejména v případě, že má procházet z jednoho místa do jiného a pravděpodobně byl načten pomocí mnoha účastníky. Integrita je třeba udržovat zabráníte tak možné manipulaci s daty a se obvykle dosahuje digitální podpis zprávy.|  
|Důvěrnost|*Důvěrnost* je jistotu, že zpráva nebyla přečtena kdokoli než zamýšlené čtečky. Například číslo kreditní karty musí být důvěrný při přenosu přes Internet. Důvěrnost často zajišťuje šifrování dat s využitím veřejné klíče a soukromého klíče schéma.|  
|Ověřování|*Ověřování* je ověření uváděné identity. Například při použití bankovním účtu, je nutné, bude moct odvolat fondů skutečné vlastník účtu. Ověřování můžete zadat různé prostředky. Jeden běžnou metodu je systém pro uživatele a hesla. Druhou je použití certifikát X.509, který pochází od třetích stran.|  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 WCF má několik režimů zabezpečení přenosu, které jsou popsány v následující tabulce.  
  
|Režim|Popis|  
|----------|-----------------|  
|Žádné|Žádné zabezpečení je poskytnut na přenosové vrstvě nebo ve vrstvě zprávy. Žádná z předdefinovaných vazeb tento režim používejte ve výchozím nastavení s výjimkou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element nebo při použití kódu, <xref:System.ServiceModel.BasicHttpBinding> třídy.|  
|Přenos|Používá zabezpečeného přenosu, jako je například HTTPS pro integritu, utajení a vzájemné ověřování.|  
|Zpráva|Používá zabezpečení zprávu protokolu SOAP pro integritu, utajení a vzájemné ověřování. Podle specifikace WS-Security standardy, které jsou zabezpečené zprávy protokolu SOAP.|  
|Ve smíšeném režimu|Zabezpečení pro ověřování integrity, utajení a server přenosu používá. Používá zprávy zabezpečení (WS-Security a dalších standardů) pro ověřování klientů.<br /><br /> (Tento výčet pro tento režim je `TransportWithMessageCredential`.)|  
|Obojí|Provádí ochranu a ověřování na obou úrovních. Je k dispozici pouze v tomto režimu [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) elementu.|  
  
## <a name="credentials-and-transfer-security"></a>Přihlašovací údaje a zabezpečení přenosu  
 A *přihlašovacích údajů* jsou data, která se zobrazí k navázání uváděné identity nebo funkce. Zobrazení přihlašovacích údajů zahrnuje prezentace dat i doklad o vlastnictví dat. WCF podporuje celou řadu typů přihlašovacích údajů při přenosu i zpráva úrovně zabezpečení. Můžete určit typ přihlašovacích údajů pro vazby WCF.  
  
 V mnoha zemích nebo oblastech licence ovladače je příkladem přihlašovacích údajů. Licence obsahuje data, která představují identitu svých a možnosti. Obsahuje doklad o vlastnictví v podobě obrázku vlastníka. Licence je vydán důvěryhodnou autoritou, obvykle vládní licencování oddělení. Licence je zapečetěná a může obsahovat hologram, zobrazuje, že nebyla úmyslně nebo padělat.  
  
 Jako příklad, vezměte v úvahu dva typy přihlašovacích údajů, které jsou podporované ve službě WCF: uživatelské jméno a (X.509) certifikát přihlašovacích údajů.  
  
 Pro přístupové uživatelské jméno uváděné identity představuje uživatelské jméno a heslo představuje doklad o vlastnictví. Jako důvěryhodnou autoritu v tomto případě je systém, který ověří uživatelské jméno a heslo.  
  
 V přihlašovacích údajích certifikát názvu subjektu, konkrétních polí v rámci certifikátu nebo alternativní název subjektu slouží k reprezentaci uváděné identity a/nebo funkce. Doklad o vlastnictví dat v přihlašovacích údajích se naváže s využitím přidružený privátní klíč podpis.  
  
 Další informace o programování zabezpečení přenosu a zadání přihlašovacích údajů, naleznete v tématu [vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) a [chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Přenos typy přihlašovacích údajů klienta  
 V následující tabulce jsou uvedeny možné hodnot použitá při vytváření aplikace, který používá zabezpečení přenosu. Můžete použít tyto hodnoty do kódu nebo nastavení vazby.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient není potřeba k dispozici žádné přihlašovací údaje. Výsledkem je k anonymní klienta.|  
|Základní|Určuje základní ověřování.  Další informace najdete v tématu RFC2617, "[ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|ověřování algoritmem Digest|Určuje, ověřování hodnotou hash.  Další informace najdete v tématu RFC2617, "[ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Určuje ověřování Windows pomocí vyjednávání SSPI v doméně Windows.<br /><br /> Vyjednávání SSPI je výsledkem použití protokolu Kerberos nebo NT LanMan (NTLM).|  
|Windows|Určuje ověřování Windows s použitím rozhraní SSPI v doméně Windows. Rozhraní SSPI vybere z protokolu Kerberos nebo NTLM jako ověřovací služby.<br /><br /> Rozhraní SSPI protokolu Kerberos pokusí nejprve; Pokud se nezdaří, pak používá protokol NTLM.|  
|Certifikát|Provádí ověření klienta pomocí certifikátu, obvykle X.509.|  
  
### <a name="message-client-credential-types"></a>Typy zpráv klienta přihlašovacích údajů  
 V následující tabulce jsou uvedeny možné hodnot použitá při vytváření aplikace, který používá zabezpečení zpráv. Můžete použít tyto hodnoty do kódu nebo nastavení vazby.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Umožňuje službě komunikovat s anonymní klienty.|  
|Windows|Umožňuje výměny zpráv SOAP dojde za ověřený kontext přihlašovacích údajů Windows. Vybrat si z protokolu Kerberos nebo NTLM jako ověřovací služba používá mechanismus vyjednávání SSPI.|  
|uživatelské jméno|Umožňuje službě tak, aby vyžadovala ověření klienta s pověření uživatelského jména. Všimněte si, že WCF nepovoluje žádné kryptografické operace s uživatelským jménem, například generování podpis nebo šifrovat data. V důsledku toho WCF vynutí, že při použití uživatelských přihlašovacích údajů název je zabezpečený přenos.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Programování přihlašovacích údajů  
 Pro každý typ přihlašovacích údajů klienta umožňuje programovacího modelu WCF zadání hodnot přihlašovacích údajů a přihlašovacích údajů validátory pomocí chování služby a chování kanálu.  
  
 Zabezpečení WCF má dva typy přihlašovacích údajů: chování přihlašovacích údajů a chování přihlašovacích údajů kanálu služby. Zadejte chování přihlašovacích údajů ve službě WCF skutečná data, a to, přihlašovací údaje použité pro splnění požadavků zabezpečení vyjádřen prostřednictvím vazby. Ve službě WCF je třída klienta za běhu součást, která převede mezi volání operace a zprávy. Všichni klienti Zdědit <xref:System.ServiceModel.ClientBase%601> třídy. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Vlastnost v základní třídě můžete zadat různé hodnoty přihlašovacích údajů klienta.  
  
 Chování služby ve službě WCF, jsou atributy použité na třídy implementace kontraktu služby (interface) k programovému řízení služby. <xref:System.ServiceModel.Description.ServiceCredentials> Třída umožňuje určit certifikáty pro přihlašovací údaje a klienta ověření nastavení služby pro různé typy přihlašovacích údajů klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Model vyjednávání zabezpečení zpráv  
 Režim zabezpečených zpráv umožňuje provádět přenos zabezpečení tak, aby přihlašovacích údajů služby se konfiguruje v klientovi mimo pásmo. Například pokud používáte certifikát uložený v úložišti certifikátů Windows, musíte použít nástroje, jako je modul snap-in konzoly Microsoft Management Console (MMC).  
  
 Režim zabezpečených zpráv také umožňuje provádět přenos zabezpečení tak, aby přihlašovacích údajů služby se vyměňují pomocí klienta jako součást počáteční vyjednávání. Chcete-li povolit vyjednávání, nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
