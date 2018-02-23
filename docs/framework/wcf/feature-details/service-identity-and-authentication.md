---
title: "Identita a ověřování služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 579f41a213564dd18dae719a14170100903efd92
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2018
---
# <a name="service-identity-and-authentication"></a>Identita a ověřování služby
Služby *identitu koncového bodu*je hodnota vygenerovaná ze služby webové služby popis Language (WSDL). Tato hodnota, rozšíří do libovolného klienta se používá k ověřování. Jakmile klient inicializuje komunikaci pro koncový bod a služby se ověří na klienta, klient porovná hodnotu identitu koncového bodu se proces ověřování koncového bodu vrácená hodnota. Pokud se shodují, klient jistotu, že nekontaktoval koncový bod očekávanou službu. To funguje jako ochrana proti *phishing* tak, že zabrání se přesměruje na koncový bod hostitelem škodlivý služba klienta.  
  
 Ukázkovou aplikaci, která demonstruje nastavení identity, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Koncové body a adresy koncových bodů, najdete v části [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  Použijete-li LanMan NT (NTLM) pro ověřování, identita služby není zkontrolovat, protože v rámci protokolu NTLM, klient nelze provést ověření serveru. NTLM se používá, když počítače jsou součástí pracovní skupiny systému Windows, nebo když se používá starší verzi systému Windows, který nepodporuje ověřování pomocí protokolu Kerberos.  
  
 Když klient zahájí zabezpečený kanál pro odeslání zprávy do služby, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury ověřuje službu a pouze odešle zprávu, pokud odpovídá identitě zadané v adresa koncového bodu, klient použije identitu služby.  
  
 Zpracování identity se skládá z těchto fází:  
  
-   V době návrhu určuje vývojáře klienta služby Identita z metadata pro koncový bod (vystavený prostřednictvím WSDL).  
  
-   Klientské aplikace za běhu, zkontroluje deklarace identity služby zabezpečovací pověření před odesláním všechny zprávy ve službě.  
  
 Identita, zpracování na straně klienta je obdobou ověřování klientů na službu. Služba Zabezpečené nespustí kód, dokud po ověření pověření klienta. Podobně klient neodesílá podle zprávy a pokuste se službu až po ověření přihlašovacích údajů služby, která se označuje předem z metadat služby.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnost <xref:System.ServiceModel.EndpointAddress> třída reprezentuje identitu služby nazvaná klientem. Publikuje službu <xref:System.ServiceModel.EndpointAddress.Identity%2A> ve svých metadatech. Při spuštění klienta Vývojář [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na koncový bod služby vygenerované konfigurace obsahuje hodnotu služby <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury (Pokud je nakonfigurovaná s zabezpečení) ověří, zda má služba identita zadaná.  
  
> [!IMPORTANT]
>  Metadata obsahuje Očekávaná identita služby, proto se doporučuje vystavit metadata služby prostřednictvím zabezpečené prostředky, například tak, že vytvoříte koncový bod HTTPS pro službu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Postupy: zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Typy identity  
 Služba může poskytnout šest typů identit. Každý typ identity odpovídá element, který může být obsažený uvnitř `<identity>` element v konfiguraci. Typ použitý závisí na scénáře a požadavky na zabezpečení služby. Následující tabulka popisuje každý typ identity.  
  
|Typ identity|Popis|Typický scénář|  
|-------------------|-----------------|----------------------|  
|Domain Name System (DNS)|Pomocí tohoto prvku s certifikáty X.509 nebo účty v systému Windows. Porovná název DNS zadaný v přihlašovacích údajích s hodnotou zadanou v tomto elementu.|Kontrolu DNS můžete použít certifikáty s DNS nebo názvy předmětu. Pokud certifikát je znova vydat se stejnou službou DNS nebo název subjektu, kontrola identity je stále platný. Pokud je znova certifikát vydat, získá nový klíč RSA, ale zachová stejné DNS nebo název subjektu. To znamená, že klienti nemusí aktualizovat své identity informace o službě.|  
|Certifikát. Výchozí hodnota při `ClientCredentialType` je nastavena na certifikát.|Tento element určuje hodnotu certifikát X.509 s kódováním Base64 má být porovnán s klientem.<br /><br /> Při použití také použít tento prvek [!INCLUDE[infocard](../../../../includes/infocard-md.md)] jako pověření pro ověřování.|Tento element omezuje ověřování na základě jeho hodnota kryptografického otisku jeden certifikát. To umožňuje přísnější ověřování, protože jsou hodnoty kryptografického otisku jedinečné. Příčinou jeden přímý přístup paměti: Pokud se stejným názvem subjektu je znova vydat certifikát, je také nový kryptografický otisk. Proto nejsou schopný ověřit službu, pokud je známý nový kryptografický otisk pro klienty. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] hledání kryptografický otisk certifikátu, najdete v části [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Odkaz na certifikát|Stejné možnosti certifikátů popsané. Tento element však umožňuje zadejte název certifikátu a umístění, ze kterého chcete načíst certifikát úložiště.|Stejné jako certifikát scénář popsaný dřív.<br /><br /> Výhodou je, že můžete změnit umístění úložiště certifikátů.|  
|RSA|Tento element určuje hodnotu klíče RSA k porovnání s klientem. To se podobá možnost certifikátů, ale místo pomocí kryptografický otisk certifikátu, se místo toho používá klíč RSA certifikátu.|Kontrolu RSA umožňuje konkrétně omezit ověření na jeden certifikát na základě jeho klíče RSA. To umožňuje přísnější ověřování konkrétního klíče RSA za cenu službu, která již pracuje se stávající klienty, pokud se změní hodnota klíče RSA.|  
|Hlavní název uživatele (UPN). Výchozí hodnota při `ClientCredentialType` je nastaven pro Windows a služba není proces spuštěn pod jeden z účtů systému.|Tento element určuje názvu UPN, které služba běží pod. Najdete v části protokolu Kerberos a Identity [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že služba běží v rámci konkrétní uživatelský účet systému Windows. Uživatelský účet může být aktuální přihlášeného uživatele nebo služby spuštěné v rámci určitého uživatelského účtu.<br /><br /> Toto nastavení využívá výhod zabezpečení systému Windows pomocí protokolu Kerberos, pokud služba běží pod účtem domény v prostředí služby Active Directory.|  
|Hlavní název služby (SPN). Výchozí hodnota při `ClientCredentialType` je nastaven pro systém Windows a službu proces běží v rámci jednoho z účty systému – LocalService, LocalSystem nebo NetworkService.|Tento element určuje hlavní název služby přidružené k účtu služby. Najdete v části protokolu Kerberos a Identity [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že hlavní název služby a konkrétní účet systému Windows, které jsou přidružené k názvu SPN identifikaci služby.<br /><br /> Nástroje Setspn.exe můžete přidružit účet počítače pro uživatelský účet služby.<br /><br /> Toto nastavení využívá Windows protokolu Kerberos, zabezpečení, pokud je služba spuštěna pod jeden z účtů system nebo pod účtem domény, který má odpovídající název SPN se ho a počítač je členem domény v prostředí služby Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Určení Identity na službu  
 Obvykle nemáte nastavit identitu u služby, protože výběr typu pověření klienta Určuje typ identity vystavené v metadatech služby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] přepsání nebo zadejte identitu služby najdete v tématu [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Pomocí \<identity > Element v konfiguraci  
 Pokud změníte typ pověření klienta vazba dříve zobrazené `Certificate,` pak generovaného WSDL obsahuje Base64 serializovat certifikátů X.509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí nastavení pro všechny typy pověření klienta než Windows.  
  
  
  
 Můžete změnit hodnotu výchozí identitu služby nebo změňte typ identity pomocí `<identity>` element v konfiguraci nebo nastavení identity v kódu. Následující kód konfigurace nastaví identitu domain name system (DNS) s hodnotou `contoso.com`.  
  
  
  
## <a name="setting-identity-programmatically"></a>Nastavení Identity prostřednictvím kódu programu  
 Služby není nutné explicitně zadat svou identitu, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky určuje ho. Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vám umožní určit identity na koncový bod, pokud je to nutné. Následující kód přidá nový koncový bod služby s konkrétní identity DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Určení Identity na straně klienta  
 V době návrhu se většinou používá vývojář klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování konfigurace klienta. Vygenerovaný konfigurační soubor (určený pro použití klientem) obsahuje identitu serveru. Například následující kód se generují z služba, která určuje identitu DNS, jak je znázorněno v předchozím příkladu. Všimněte si, že hodnotu koncového bodu identity klienta se shoduje s službu. V takovém případě, když klient obdrží pověření systému Windows (Kerberos) do služby, se očekává, že hodnota, která má být `contoso.com`.  
  
  
  
 Pokud, místo systému Windows, službu Určuje certifikát jako typ pověření klienta, pak vlastnost DNS certifikátu musí být hodnota `contoso.com`. (Nebo pokud je vlastnost DNS `null`, musí být název subjektu certifikátu `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Pomocí konkrétní hodnoty pro identitu  
 Následující konfigurační soubor klienta ukazuje, jak identity služby musí být konkrétní hodnotu. V následujícím příkladu klient může komunikovat s dva koncové body. První je identifikován s kryptografický otisk certifikátu a druhý s klíčem RSA certifikátu. To znamená certifikát, který obsahuje pouze veřejný klíč nebo privátní klíče dvojice, ale nebyl vydán důvěryhodnou autoritou.  
  
  
  
## <a name="identity-checking-at-run-time"></a>Identity kontrola za běhu  
 V době návrhu vývojář klienta určuje identitu serveru prostřednictvím jeho metadata. Za běhu se provádí kontrola identity před voláním žádné koncové body služby.  
  
 Hodnota identity je vázaný na typ ověřování určeného metadata; jinými slovy typ pověření použitá pro službu.  
  
 Pokud chcete ověřit pomocí zprávy nebo transportní vrstvy SSL (Secure Sockets) pro ověřování pomocí certifikátů X.509 je nakonfigurovaný kanál, jsou platné tyto hodnoty identity:  
  
-   DNS. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zajišťuje, že má certifikát zadaný během metody handshake SSL obsahuje DNS nebo `CommonName` (CN) atribut rovna hodnotě zadané v identity DNS na klientovi. Všimněte si, že tyto kontroly se provádějí kromě k určení platnost certifikátu serveru. Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ověří, že certifikát serveru je vydán důvěryhodnou kořenovou autoritou.  
  
-   Certifikát. Během metody handshake SSL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zajistí, že vzdálený koncový bod poskytuje přesnou certifikát hodnota zadaná v identitě.  
  
-   Odkaz na certifikát. Stejné jako certifikát.  
  
-   RSA. Během metody handshake SSL [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zajistí, že vzdálený koncový bod poskytuje přesnou RSA klíč zadaný v identitě.  
  
 Pokud službu ověřuje zpráva nebo transportní SSL pomocí pověření systému Windows pro ověřování a vyjedná přihlašovacích údajů, jsou platné tyto hodnoty identity:  
  
-   DNS. Vyjednávání předá SPN služby, aby bylo možné kontrolovat název DNS. Hlavní název služby je ve formátu `host/<dns name>`.  
  
-   HLAVNÍ NÁZEV SLUŽBY. Explicitní služby SPN vrátí, například `host/myservice`.  
  
-   HLAVNÍ NÁZEV UŽIVATELE. Hlavní název uživatele účtu služby. Hlavní název uživatele je ve formátu `username` @ `domain`. Například pokud služba je spuštěna v uživatelském účtu, může být `username@contoso.com`.  
  
 Určení identity prostřednictvím kódu programu (pomocí <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost) je volitelný. Pokud je zadána žádná identita a typu pověření klienta je systém Windows, výchozí hodnota je hodnota nastavena na název hostitele součástí předponu adresa koncového bodu služby SPN "hostitel nebo" literálu. Pokud je zadána žádná identita a typu pověření klienta je certifikát, výchozí hodnota je `Certificate`. To platí pro obě zabezpečení na úrovni zpráv a přenosu.  
  
## <a name="identity-and-custom-bindings"></a>Identity a vlastní vazby  
 Protože identity služby závisí na používá typ vazby, ujistěte se, že příslušné identity je vystaven při vytváření vlastní vazby. Například v následujícím příkladu kódu identity vystavené není kompatibilní s typem zabezpečení, protože identita bootstrap vazby zabezpečené konverzaci neodpovídá identitě pro vazbu na koncovém bodu. Zabezpečené konverzace vazby nastaví identitu DNS, zatímco <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> nastaví identitu (UPN) nebo hlavní název služby.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Zásobník elementů správně pro vlastní vazby vazby naleznete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Vytvoření vlastní vazby s <xref:System.ServiceModel.Channels.SecurityBindingElement>, najdete v části [postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 [Postupy: Vytvoření vlastního ověřovatele identity klientů](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
