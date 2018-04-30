---
title: Zabezpečení distribuované aplikace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: 32
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 8b5bc311262aae1110f7d0249be60135e318785e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="distributed-application-security"></a>Zabezpečení distribuované aplikace
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečení je rozdělená do tří hlavních funkčním oblastem: přenos zabezpečení, řízení přístupu a auditování. Zabezpečení přenosu poskytuje integrity, šifrování a ověřování. Zabezpečení přenosu poskytuje jednu z následujících: přenosu zabezpečení, zabezpečení zpráv nebo `TransportWithMessageCredential`.  
  
 Přehled [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení zpráv najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o další dvě požadované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení, najdete v části [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) a [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Scénáře zabezpečení přenosu  
 Běžné scénáře, které využívají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení přenosu zahrnují následující:  
  
-   Zabezpečení přenosu pomocí systému Windows. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a služby jsou nasazeny v doméně systému Windows (nebo doménové struktury systému Windows). Zprávy obsahovat osobní data, takže požadavky na zahrnují vzájemné ověřování klienta a služby, zpráva integrity a důvěrnosti zpráv. Kromě toho se vyžaduje ověření, že konkrétní transakce došlo k chybě, například příjemce zprávy měli zaznamenat informace o podpisu.  
  
-   Zabezpečení přenosu pomocí `UserName` a HTTPS. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a služby je třeba pro práci v síti Internet. Pověření klienta ověřování na základě databáze párů jméno a heslo uživatele. Nasazení služby na adresu HTTPS pomocí důvěryhodného certifikátu vrstvy SSL (Secure Sockets). Protože zprávy putovat po Internetu, klient a služba vyžaduje vzájemně ověření a utajení a integrity zprávy musí být zachováno při přenosu.  
  
-   Zabezpečení přenosu pomocí certifikátů. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient a služba musí být vyvinutá fungovat prostřednictvím veřejného Internetu. Klient a služba mají obě certifikáty, které lze použít k zabezpečení zprávy. Klient a služba pomocí Internetu ke komunikaci mezi sebou a k provádění transakcí vysoké hodnoty, které vyžadují integrity zprávy, důvěrnost a vzájemné ověřování.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integrity, šifrování a ověřování  
 Tři funkce – integrity, šifrování a ověřování – společně se nazývají zabezpečení přenosu. Přenos zabezpečení poskytuje funkce, které pomůžou zmírnit hrozby do distribuované aplikace. Následující tabulka stručně popisuje tři funkce, které tvoří zabezpečení přenosu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|Integrita|*Integrita* jistotu, že data jsou úplné a přesné, zejména v případě, že má provázán z jednoho bodu do jiného a pravděpodobně byla číst mnoho aktéři. Integrity musí být zachovaná, chcete-li zabránit manipulaci s daty a digitální podpis zprávy, které se obvykle dosahuje.|  
|Důvěrnost|*Důvěrnost* jistotu zprávu nepřečtená nikdo jiný než zamýšlený čtečky. Například číslo platební karty musí být důvěrné při přenosu přes Internet. Důvěrnost často zajišťuje šifrování dat pomocí veřejného klíče a privátního klíče schématu.|  
|Ověřování|*Ověřování* je ověření uváděné identity. Například pokud používáte účet bank, je nutné, aby pouze skutečný vlastník účtu povoleno odstoupení fondů. Ověřování se dá zajistit řadu způsobem. Jedna společná metoda je systém uživatele a heslo. Druhý je použití certifikátu X.509. certifikát od třetích stran.|  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] má několik režimů zabezpečení přenosu, které jsou popsané v následující tabulce.  
  
|Režim|Popis|  
|----------|-----------------|  
|Žádné|V přenosové vrstvě nebo ve vrstvě zprávy je k dispozici žádné zabezpečení. Žádná z předdefinovaných vazby tento režim používejte ve výchozím nastavení s výjimkou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element nebo při použití kódu, <xref:System.ServiceModel.BasicHttpBinding> třídy.|  
|Přenos|Zabezpečení přenosu, jako je například HTTPS používá pro integritu, šifrování a vzájemné ověřování.|  
|Zpráva|Zprávu SOAP zabezpečení se používá pro integritu, šifrování a vzájemné ověřování. Podle standardů WS-zabezpečení jsou zabezpečené protokolu SOAP zprávy.|  
|Ve smíšeném režimu|Používá přenosu zabezpečení pro ověřování integrity, důvěrnost a serveru. Používá zpráva zabezpečení (WS-zabezpečení a jiné standardy) pro ověřování klientů.<br /><br /> (Tento výčet v tomto režimu je `TransportWithMessageCredential`.)|  
|Obě|Provede ochrany a ověřování na obou úrovních. Je k dispozici pouze v tomto režimu [ \<– netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) element.|  
  
## <a name="credentials-and-transfer-security"></a>Přihlašovací údaje a zabezpečení přenosu  
 A *pověření* jsou data, která se zobrazí k navázání uváděné identity nebo funkce. Prezentace pověření zahrnuje prezentací data a ověření vlastní data. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje celou řadu typů přihlašovacích údajů při přepravě a zpráva úrovně zabezpečení. Můžete zadat typ přihlašovacích údajů pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby.  
  
 V mnoha zemích nebo oblastech licence ovladače je příkladem pověření. Licence obsahuje data představující identity jeden společnosti a možnosti. Obsahuje důkaz vlastnictví ve formě obrázku vlastník. Licence je vydán důvěryhodnou autoritou, většinou vládních licencování oddělení. Licence je zapečetěná a může obsahovat hologram, zobrazující, že nebyla manipulováno nebo padělat.  
  
 Jako příklad, zvažte dva typy podporovaných v pověření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: uživatelské jméno a (X.509) certifikát přihlašovacích údajů.  
  
 Pro přihlašovací údaje uživatele název deklarovaná identita představuje uživatelské jméno a heslo uvede ověření u sebe. Jako důvěryhodnou autoritu v tomto případě je systém, který ověří uživatelské jméno a heslo.  
  
 V přihlašovacích údajích certifikát může být názvu subjektu, konkrétních polí v rámci certifikátu nebo alternativní název subjektu používá k reprezentování deklarovaná identita a možnosti. Ověření u sebe data v přihlašovacích údajích lze navázat pomocí přidružený privátní klíč ke generování podpis.  
  
 Další informace o programování zabezpečení přenosu a zadání přihlašovacích údajů, najdete v části [vazby a zabezpečení](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) a [chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Přenos klienta pověření typy  
 V následující tabulce jsou uvedeny možné hodnoty používané při vytvoření aplikace, která používá zabezpečení přenosu. Můžete použít tyto hodnoty v kódu nebo vazby nastavení.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí k dispozici žádné pověření. Výsledkem anonymním klientem.|  
|Základní|Určuje základní ověřování.  Další informace najdete v tématu RFC2617, "[ověřování protokolu HTTP: Basic a ověřování algoritmem Digest](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Ověřování algoritmem Digest|Určuje, ověřování hodnotou hash.  Další informace najdete v tématu RFC2617, "[ověřování protokolu HTTP: Basic a ověřování algoritmem Digest](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Určuje ověřování systému Windows pomocí vyjednávání SSPI v doméně systému Windows.<br /><br /> Vyjednávání SSPI výsledkem pomocí protokolu Kerberos nebo LanMan NT (NTLM).|  
|Windows|Určuje ověřování systému Windows pomocí rozhraní SSPI v doméně systému Windows. Rozhraní SSPI vybere z protokolu Kerberos nebo NTLM jako ověřovací služby.<br /><br /> Rozhraní SSPI se nejprve pokusí protokolu Kerberos Pokud to nepomůže, pak používá protokol NTLM.|  
|certifikát|Provede ověření klienta, používá certifikát, obvykle X.509.|  
  
### <a name="message-client-credential-types"></a>Typy zpráv klienta přihlašovacích údajů  
 V následující tabulce jsou uvedeny možné hodnoty používané při vytvoření aplikace, která používá zabezpečení zpráv. Můžete použít tyto hodnoty v kódu nebo vazby nastavení.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Umožňuje pracovat s anonymní klienty služby.|  
|Windows|Umožňuje výměny zpráv protokolu SOAP dojde za ověřený kontext pověření systému Windows. Vybrat z protokolu Kerberos nebo NTLM jako ověřovací služba používá mechanismus vyjednávání SSPI.|  
|Uživatelské jméno|Umožňuje službě tak, aby vyžadovala ověření klienta s názvem pověření uživatele. Všimněte si, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] všechny kryptografické operace s uživatelským jménem, jako je například generování podpis nebo šifrování dat není povoleno. Jako takový [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vynutí, že při použití přihlašovací údaje uživatele název zabezpečené přenosu.|  
|certifikát|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Umožňuje službě vyžadují, ověření klienta pomocí [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Programování přihlašovací údaje  
 Pro každý typ pověření klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací model k zadání hodnot přihlašovacích údajů a může validátory přihlašovacích údajů pomocí služby chování kanálu chování.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení má dva typy přihlašovacích údajů: služby chování přihlašovacích údajů a chování přihlašovacích údajů kanálu. Přihlašovací údaje chování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zadejte skutečná data, a to, přihlašovací údaje použít ke splnění požadavků na zabezpečení vyjádřit pomocí vazby. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], třída klienta je běhové komponenty, která převede mezi volání operace a zprávy. Dědí všechny klienty <xref:System.ServiceModel.ClientBase%601> třídy. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Vlastnost na základní třída umožňuje určit různé hodnoty pověření klienta.  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], chování služby jsou atributy použité u třídy implementace kontraktu služby (rozhraní) k programovému řízení služby. <xref:System.ServiceModel.Description.ServiceCredentials> Třída umožňuje určit certifikáty pro služby přihlašovacích údajů a klientské nastavení ověřování pro různé typy pověření klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Vyjednávání modelu zabezpečení zpráv  
 Režim zabezpečení zpráv umožňuje provádět přenos zabezpečení tak, aby přihlašovací údaje služby je nakonfigurován na straně klienta vzdálené správy. Například pokud používáte certifikát uložený v úložišti certifikátů systému Windows, musíte použít nástroje, jako je modul snap-in konzoly Microsoft Management Console (MMC).  
  
 Režim zabezpečení zprávy také umožňuje provádět přenos zabezpečení tak, aby přihlašovací údaje služby se vyměňují pomocí klienta jako součást počáteční vyjednávání. Chcete-li povolit vyjednávání, nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
