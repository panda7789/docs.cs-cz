---
title: Identita a ověřování služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: 695b6c24700fe42664944d6f9c1e03010248d86a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487737"
---
# <a name="service-identity-and-authentication"></a>Identita a ověřování služby
Služby *identitě koncového bodu* je hodnota vygenerovaná ze služby webové služby WSDL (Description Language). Tato hodnota, rozšíří na všechny klienty, se používá k ověřování. Poté, co klient inicializuje komunikaci na koncový bod a služby se ověří na klienta, klient porovná hodnotu identity koncový bod s skutečná hodnota vrácená v procesu ověřování koncového bodu. Pokud se shodují, klient jistotu, že kontaktoval koncový bod služby očekávané. Tato operace funguje jako ochranu proti *phishing* zabraňuje klient se přesměrovává na koncový bod hostitelem škodlivé služby.  
  
 Ukázková aplikace, který ukazuje nastavení identity, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md). Další informace o koncových bodech a adresy koncových bodů najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  Když LanMan NT (NTLM) se používají k ověřování, identity služby není kontrolovat, protože v protokolu NTLM, klient se nemůže ověřit server. Je použit protokol NTLM, když se počítače pracovní skupiny Windows nebo při spuštění starší verzi Windows, který nepodporuje ověřování pomocí protokolu Kerberos.  
  
 Když klient zahájí zabezpečený kanál pro odeslání zprávy do služby přes něj, ověřuje služby infrastruktury Windows Communication Foundation (WCF) a pouze odešle zprávu, pokud služba identity odpovídá identitě zadané v koncovém bodě Adresa, kterou klient používá.  
  
 Zpracování identity se skládá z následujících fází:  
  
- V době návrhu vývojáře klienta určuje identitu služby z koncového bodu metadat (vystavené prostřednictvím WSDL).  
  
- Klientská aplikace za běhu, zkontroluje deklarací zabezpečovací přihlašovací údaje služby před odesláním jakýchkoli zpráv do služby.  
  
 Identita zpracování na straně klienta je obdobou ověřování klientů na službu. Služba Zabezpečené nespustí kódu až po ověření pověření klienta. Podobně klient nezasílal zprávy do služby až po ověření přihlašovacích údajů služby založené na co předem známý z metadat služby.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnost <xref:System.ServiceModel.EndpointAddress> třída reprezentuje identitu služby volána klientem. Služba zveřejňuje <xref:System.ServiceModel.EndpointAddress.Identity%2A> ve svých metadatech. Při spuštění klienta pro vývojáře [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na koncový bod služby vygenerovanou konfiguraci obsahuje hodnotu služby <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost. Infrastruktura WCF (Pokud je nakonfigurovaná s zabezpečení) ověřuje, že služba má identita zadaná.  
  
> [!IMPORTANT]
>  Metadata obsahuje Očekávaná identita služby, proto se doporučuje zpřístupňují metadata služby prostřednictvím zabezpečené prostředky, třeba tak, že vytvoříte koncový bod HTTPS pro službu. Další informace najdete v tématu [jak: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Typy identity  
 Služba může poskytnout šest typů identit. Každý typ identity odpovídá elementu, který může být obsažena uvnitř `<identity>` element v konfiguraci. Typ použitý závisí na scénáře a požadavky na zabezpečení služby. Následující tabulka popisuje každý typ identity.  
  
|Typ identity|Popis|Typický scénář|  
|-------------------|-----------------|----------------------|  
|Domain Name System (DNS)|Tento prvek pomocí certifikátů X.509 nebo účty Windows. Porovná název DNS zadaný v přihlašovacích údajích s hodnotou zadanou v tomto elementu.|Kontrola DNS umožňuje používat certifikáty s DNS nebo názvy subjektu. Pokud je ho znova vydat certifikát se stejným DNS nebo názvu subjektu, kontrola identity je stále platný. Když se ho znova vydat certifikát, získá nový klíč RSA, ale zachováte stejný DNS nebo názvu subjektu. To znamená, že klienti, není nutné aktualizovat své identity informace o službě.|  
|certifikát. Výchozí hodnota při `ClientCredentialType` je nastavena na certifikát.|Tento prvek Určuje certifikát X.509 s kódováním Base64 hodnotu k porovnání s klientem.<br /><br /> Tento prvek používejte také při použití CardSpace jako přihlašovací údaj k ověřování.|Tento prvek omezuje ověřování na základě jeho hodnotu kryptografického otisku jeden certifikát. To umožňuje přísnější ověřování, protože jsou jedinečné hodnoty kryptografického otisku. Součástí jednoho výstrahou: Pokud se ho znova vydat certifikát se stejným názvem subjektu, má také nový kryptografický otisk. Proto klienti nebudou se moct k ověření služby, pokud je známý nový kryptografický otisk. Další informace o vyhledání kryptografický otisk certifikátu najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Odkaz na certifikát|Stejné možnosti certifikátů je popsáno výše. Tento element však umožňuje zadat název certifikátu a umístění, ze kterého se má načíst certifikát uložit.|Stejné jako certifikát scénář je popsáno výše.<br /><br /> Výhodou je, že můžete změnit umístění úložiště certifikátů.|  
|RSA|Tento prvek určuje hodnotu klíče RSA k porovnání s klientem. Je to podobné možnosti certifikátů, ale místo použití kryptografického otisku certifikátu, se místo toho používá klíč RSA certifikátu.|Kontrolu RSA umožňuje konkrétně omezit ověření na základě jeho klíč RSA jeden certifikát. To umožňuje přísnější ověřování z určitého klíče RSA za cenu službu, která už funguje s existující klienty, pokud se změní hodnota klíče RSA.|  
|Hlavní název uživatele (UPN). Výchozí hodnota při `ClientCredentialType` nastavena Windows a proces není spuštěn v rámci jednoho systémové účty.|Tento prvek určuje, na kterém běží služba v rámci hlavní název uživatele. Najdete v části protokol Kerberos a Identity [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že služba běží v rámci konkrétní uživatelský účet Windows. Uživatelský účet může být aktuální přihlášeného uživatele nebo služby spuštěné v rámci určitého uživatelského účtu.<br /><br /> Toto nastavení využívá výhod zabezpečení Windows protokolu Kerberos, pokud je služba spuštěna pod účtem domény v prostředí služby Active Directory.|  
|Hlavní název služby (SPN). Výchozí hodnota při `ClientCredentialType` je nastavena na Windows a služby je proces spuštěn pod jeden z účtů systému – LocalService, LocalSystem nebo NetworkService.|Tento prvek určuje hlavní název služby přidružené k účtu služby. Najdete v části protokol Kerberos a Identity [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že hlavní název služby a konkrétní Windows účet spojený s hlavní název služby identifikaci služby.<br /><br /> Chcete-li přidružit účet počítače pro uživatelský účet služby můžete použít nástroje Setspn.exe.<br /><br /> Toto nastavení využívá Windows protokolu Kerberos, zabezpečení, pokud je služba spuštěná v jednom ze systémové účty nebo pod účtem domény, který má odpovídající název SPN se ho a počítač je členem domény v prostředí služby Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Určení Identity na službu  
 Standardně nastavit identitu ve službě, protože výběr typu pověření klienta Určuje typ identity v metadatech služby není nutné. Další informace o tom, jak přepsat nebo zadejte identitu služby najdete v tématu [přepsání Identity služby kvůli ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Použití \<identity > v elementu konfigurace  
 Pokud změníte typ přihlašovacích údajů klienta ve vazbě bylo dříve uvedeno na `Certificate,` generovaného WSDL obsahuje Base64 serializovat certifikátů X.509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí pro všechny typy přihlašovacích údajů klienta jiné než Windows.  

 Můžete změnit hodnotu výchozí identitu služby nebo změňte typ identity pomocí `<identity>` element v konfiguraci nebo nastavením identita v kódu. Následující kód konfigurace nastaví identitou system (DNS) název domény s hodnotou `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Nastavení Identity prostřednictvím kódu programu  
 Vaše služba není nutné explicitně určit identitu, protože WCF automaticky určuje. Ale WCF umožňuje určit identitu, která v koncovém bodě, podle potřeby. Následující kód přidá nový koncový bod služby s konkrétní identitu DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Určení Identity klienta  
 V době návrhu, vývojáři klientského programu obvykle používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování konfigurace klienta. Vygenerovaný konfigurační soubor (určené pro použití klientem) obsahuje identitu serveru. Například následující kód je generován ze služby, která určuje identitu DNS, jak je znázorněno v předchozím příkladu. Všimněte si, že hodnota identity klienta koncový bod odpovídá služby. V tomto případě, když klient obdrží pověření Windows (Kerberos) pro službu, očekává hodnota, která má být `contoso.com`.  

 Pokud, místo Windows, tato služba Určuje certifikát jako typ pověření klienta, pak vlastnost DNS tento certifikát má být hodnota `contoso.com`. (Nebo pokud je vlastnost DNS `null`, musí být název subjektu certifikátu `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Pomocí konkrétní hodnoty pro identitu  
 Následující konfigurační soubor klienta ukazuje, jak služby identita má být konkrétní hodnotu. V následujícím příkladu klient může komunikovat s dva koncové body. První je označena kryptografický otisk certifikátu a druhý s klíčem RSA certifikátu. To znamená, že certifikát, který obsahuje pouze veřejný klíč nebo privátní pár klíčů, ale není vydán důvěryhodnou autoritou.  

## <a name="identity-checking-at-run-time"></a>Identita kontrolu za běhu  
 V době návrhu vývojáře klienta určuje identitu serveru pomocí jeho metadata. V době běhu je provedena kontrola identity před voláním žádné koncové body služby.  
  
 Hodnota identity je vázán na typ ověřování určené metadata; jinými slovy zadejte přihlašovací údaje použité pro službu.  
  
 Pokud kanál je nakonfigurován k ověření zprávy nebo transportní vrstvy SSL (Secure Sockets) pomocí certifikátů X.509 pro ověřování, platí následující hodnoty identity:  
  
- DNS. WCF zajišťuje, že obsahuje položku certifikátu poskytnutého během metody handshake SSL DNS nebo `CommonName` (CN) atributu rovná hodnotě zadané v identitu DNS na klientovi. Všimněte si, že tyto kontroly se provádějí kromě toho pro určení platnosti certifikátu serveru. Ve výchozím nastavení WCF ověří, že je certifikát serveru vydané důvěryhodnou kořenovou autoritou.  
  
- certifikát. Během metody handshake SSL WCF zajistí, že vzdálený koncový bod poskytuje přesnou certifikátu hodnotu zadanou v identitě.  
  
- Odkaz na certifikát. Stejné jako certifikát.  
  
- RSA. Během metody handshake SSL WCF zajistí, že vzdálený koncový bod poskytuje přesnou klíč RSA zadaný v identitě.  
  
 Pokud služba se ověřuje pomocí SSL na úrovni zprávy nebo přenosu pomocí přihlašovacích údajů Windows pro ověřování a vyjedná přihlašovací údaje, platí následující hodnoty identity:  
  
- DNS. Vyjednávání předá SPN služby tak, aby název DNS můžete kontrolovat. Hlavní název služby je ve formě `host/<dns name>`.  
  
- HLAVNÍ NÁZEV SLUŽBY. Explicitní služby se vrátí hlavní název služby, například `host/myservice`.  
  
- HLAVNÍ NÁZEV UŽIVATELE. Hlavní název uživatele účtu služby. Hlavní název uživatele je ve formě `username` @ `domain`. Například pokud služba je spuštěna v uživatelském účtu, může být `username@contoso.com`.  
  
 Programové určení identity (pomocí <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnost) je volitelný. Pokud je zadána žádná identita a je typu pověření klienta Windows, výchozí hodnota je hodnota nastavena na název hostitele součástí adresu koncového bodu služby s předponou hlavního názvu služby "hostitele /" literál. Pokud je zadána žádná identita a typu pověření klienta je certifikát, výchozí hodnota je `Certificate`. To platí pro obě zprávy a přenos úroveň zabezpečení.  
  
## <a name="identity-and-custom-bindings"></a>Identita a vlastních vazeb  
 Protože identity služby závisí na typu vazbu použít, ujistěte se, že je přístupný správnou identitu, při vytváření vlastní vazby. Například v následujícím příkladu kódu identity vystavit není kompatibilní s typem zabezpečení, protože identita pro zaváděcí vazbu zabezpečené konverzace neodpovídá identitě pro vazbu v koncovém bodě. Vazbu zabezpečené konverzace nastaví identitu DNS, zatímco <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> nastaví identitu (UPN) nebo hlavní název služby.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Další informace o tom, jak zásobníku vazby prvky správně pro vlastní vazbu, naleznete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Další informace o vytvoření vlastní vazby s <xref:System.ServiceModel.Channels.SecurityBindingElement>, naleznete v tématu [jak: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Postupy: Vytvoření vlastního ověřovatele Identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
