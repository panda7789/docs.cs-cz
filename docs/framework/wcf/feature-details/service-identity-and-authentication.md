---
title: Identita a ověřování služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: f9ed2a7c284588a0fb481d41dca61e663fd090b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969237"
---
# <a name="service-identity-and-authentication"></a>Identita a ověřování služby
*Identita koncového bodu* služby je hodnota generovaná z jazyka WSDL (Service Web Services Description Language). Tato hodnota se rozšíří na libovolného klienta, který se používá k ověření služby. Poté, co klient zahájí komunikaci s koncovým bodem a služba se sama ověří pro klienta, klient porovná hodnotu identity koncového bodu se skutečnou hodnotou vrácenou procesem ověřování koncového bodu. Pokud se shodují, je zajištěno, že klient kontaktoval očekávaný koncový bod služby. Tato funkce je chráněná proti *útokům phishing* tím, že brání klientovi v přesměrování na koncový bod hostovaný škodlivou službou.  
  
 Ukázkovou aplikaci, která demonstruje nastavení identity, najdete v tématu [Ukázka identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md). Další informace o koncových bodech a adresách koncových bodů najdete v tématu [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
> Pokud pro ověřování použijete NT LanMan (NTLM), identita služby se neověří, protože v části NTLM není klient schopen Server ověřit. Protokol NTLM se používá v případě, že jsou počítače součástí pracovní skupiny systému Windows nebo pokud používáte starší verzi systému Windows, která nepodporuje ověřování pomocí protokolu Kerberos.  
  
 Když klient inicializuje zabezpečený kanál pro odeslání zprávy službě přes něj, infrastruktura Windows Communication Foundation (WCF) ověří službu a pošle zprávu pouze v případě, že identita služby odpovídá identitě zadané v koncovém bodu. adresa klienta používá.  
  
 Zpracování identity se skládá z následujících fází:  
  
- V době návrhu určí vývojář klienta identitu služby z metadat koncového bodu (zveřejněných prostřednictvím WSDL).  
  
- Klientská aplikace za běhu kontroluje deklarace přihlašovacích údajů zabezpečení služby předtím, než posílá jakékoli zprávy službě.  
  
 Zpracování identity na klientovi je obdobné jako ověřování klientů ve službě. Zabezpečená služba nespustí kód, dokud nebudou pověření klienta ověřena. Podobně klient neodesílá zprávy službě, dokud nejsou ověřeny přihlašovací údaje služby na základě toho, co je v metadatech služby známo předem.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Vlastnost<xref:System.ServiceModel.EndpointAddress> třídy představuje identitu služby volanou klientem. Služba publikuje <xref:System.ServiceModel.EndpointAddress.Identity%2A> ve svých metadatech. Když vývojář klienta spustí nástroj pro dodané [metadata (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti koncovému bodu služby, vygenerovaná konfigurace obsahuje hodnotu <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnosti služby. Infrastruktura WCF (Pokud je nakonfigurovaná s zabezpečením) ověří, že služba má zadanou identitu.  
  
> [!IMPORTANT]
> Metadata obsahují očekávanou identitu služby, proto doporučujeme, abyste metadata služby vystavili zabezpečeným způsobem, například vytvořením koncového bodu HTTPS pro službu. Další informace najdete v tématu [jak: Zabezpečené koncové body](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)metadat  
  
## <a name="identity-types"></a>Typy identit  
 Služba může poskytovat šest typů identit. Každý typ identity odpovídá prvku, který může být obsažen uvnitř `<identity>` elementu v konfiguraci. Použitý typ závisí na scénáři a požadavcích na zabezpečení služby. V následující tabulce jsou popsány jednotlivé typy identity.  
  
|Typ identity|Popis|Typický scénář|  
|-------------------|-----------------|----------------------|  
|DNS (Domain Name System)|Tento prvek použijte s certifikáty X. 509 nebo účty systému Windows. Porovnává název DNS zadaný v přihlašovacích údajích s hodnotou zadanou v tomto elementu.|Kontrolu DNS umožňuje používat certifikáty s názvy DNS nebo subjektu. Pokud se certifikát vydává znovu se stejným názvem DNS nebo subjektu, je tato kontroler identity stále platná. Když se certifikát znovu vydá, získá nový klíč RSA, ale uchová stejný název DNS nebo subjektu. To znamená, že klienti nemusí aktualizovat informace o identitě služby.|  
|Certifikát. Výchozí hodnota, `ClientCredentialType` Pokud je nastavena na certifikát.|Tento prvek určuje hodnotu certifikátu X. 509 zakódovaného ve formátu base64, která se má porovnat s klientem.<br /><br /> Tento prvek použijte také při použití služby CardSpace jako přihlašovacích údajů pro ověření služby.|Tento prvek omezuje ověřování na jeden certifikát na základě jeho hodnoty kryptografického otisku. To umožňuje striktní ověřování, protože hodnoty kryptografických otisků jsou jedinečné. To má jednu výstrahu: Pokud se certifikát vydává znovu se stejným názvem subjektu, má také nový kryptografický otisk. Proto klienti nebudou moci ověřit službu, pokud není známý nový kryptografický otisk. Další informace o tom, jak najít kryptografický otisk certifikátu, [najdete v tématu How to: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Odkaz na certifikát|Stejné jako dříve popsaná možnost certifikátu. Tento element však umožňuje zadat název certifikátu a umístění úložiště, ze kterého se má certifikát načíst.|Stejné jako scénář certifikátu popsaný výše.<br /><br /> Výhodou je, že umístění úložiště certifikátů se může změnit.|  
|RSA|Tento prvek určuje hodnotu klíče RSA pro porovnání s klientem. To se podobá možnosti certifikátu, ale místo použití kryptografického otisku certifikátu se místo toho použije klíč RSA certifikátu.|Ověřování RSA umožňuje výslovně omezit ověřování na jeden certifikát založený na jeho klíči RSA. To umožňuje striktní ověřování konkrétního klíče RSA na úkor služby, která už nefunguje se stávajícími klienty, pokud se změní hodnota klíče RSA.|  
|Hlavní název uživatele (UPN). Výchozí hodnota v případě `ClientCredentialType` , že je nastavena na hodnotu Windows a proces služby není spuštěn pod jedním ze systémových účtů.|Tento prvek určuje hlavní název uživatele (UPN), pod kterým je služba spuštěná. V části protokol a identita protokolu Kerberos [můžete přepsat identitu služby pro ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že služba bude běžet v rámci určitého uživatelského účtu systému Windows. Uživatelský účet může být buď aktuálně přihlášený uživatel, nebo služba spuštěná v rámci určitého uživatelského účtu.<br /><br /> Toto nastavení využívá zabezpečení protokolu Kerberos systému Windows, pokud je služba spuštěna pod účtem domény v prostředí služby Active Directory.|  
|Hlavní název služby (SPN). Výchozí hodnota v případě `ClientCredentialType` , že je nastavena na hodnotu Windows a proces služby je spuštěn pod jedním ze systémových účtů – LocalService, LocalSystem nebo NetworkService.|Tento prvek určuje hlavní název služby (SPN) přidružený k účtu služby. V části protokol a identita protokolu Kerberos [můžete přepsat identitu služby pro ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Tím se zajistí, že hlavní název služby (SPN) a konkrétní účet systému Windows přidružený k hlavnímu názvu služby identifikují službu.<br /><br /> K přidružení účtu počítače k uživatelskému účtu služby můžete použít nástroj Setspn. exe.<br /><br /> Toto nastavení využívá zabezpečení služby Windows Kerberos, pokud je služba spuštěna pod jedním z účtů systému nebo pod účtem domény, který má přidružený název SPN a počítač je členem domény v prostředí služby Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Zadání identity ve službě  
 Obvykle není nutné nastavovat identitu na službě, protože výběr typu přihlašovacích údajů klienta Určuje typ identity, která je vystavena v metadatech služby. Další informace o tom, jak přepsat nebo zadat identitu služby, najdete v tématu [přepisující identitu služby pro ověřování](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Použití prvku \<identity > v konfiguraci  
 Pokud změníte typ přihlašovacích údajů klienta ve vazbě, která `Certificate,` se dřív zobrazila, pak vygenerovaný WSDL obsahuje serializovaný certifikát X. 509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí nastavení pro všechny typy přihlašovacích údajů klienta jiné než Windows.  

 Můžete změnit hodnotu výchozí identity služby nebo změnit typ identity pomocí `<identity>` elementu v konfiguraci nebo nastavením identity v kódu. Následující konfigurační kód nastaví identitu DNS (Domain Name System) s hodnotou `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Nastavování identity prostřednictvím kódu programu  
 Vaše služba nemusí explicitně určovat identitu, protože ji WCF automaticky určí. Služba WCF ale umožňuje v případě potřeby zadat identitu pro koncový bod. Následující kód přidá nový koncový bod služby s konkrétní identitou DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Určení identity na klientovi  
 V době návrhu obvykle klientský vývojář k vygenerování konfigurace klienta používá nástroj pro dodávání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) . Generovaný konfigurační soubor (určený pro použití klientem) obsahuje identitu serveru. Například následující kód je vygenerován ze služby, která určuje identitu DNS, jak je znázorněno v předchozím příkladu. Všimněte si, že hodnota identity koncového bodu klienta odpovídá hodnotě služby. V takovém případě, když klient obdrží pověření Windows (Kerberos) pro službu, očekává hodnotu `contoso.com`.  

 Pokud místo systému Windows služba Určuje certifikát jako typ pověření klienta, očekává se, že vlastnost DNS certifikátu bude hodnota `contoso.com`. (Nebo pokud je `null`vlastnost DNS, musí být `contoso.com`název subjektu certifikátu.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Použití konkrétní hodnoty identity  
 Následující konfigurační soubor klienta ukazuje, jak se očekává, že identita služby bude konkrétní hodnotou. V následujícím příkladu může klient komunikovat se dvěma koncovými body. První je identifikovaný s kryptografickým otiskem certifikátu a druhým s certifikátem RSA. To znamená certifikát, který obsahuje pouze dvojici veřejného klíče a privátního klíče, ale není vydán důvěryhodnou autoritou.  

## <a name="identity-checking-at-run-time"></a>Kontrola identity v době běhu  
 V době návrhu určí vývojář klienta identitu serveru prostřednictvím svých metadat. V době běhu se kontroler identity provede před voláním libovolných koncových bodů ve službě.  
  
 Hodnota identity je svázána s typem ověřování určeného metadaty. Jinými slovy typ přihlašovacích údajů, které se používají pro službu.  
  
 Pokud je kanál nakonfigurovaný k ověřování pomocí protokolu SSL nebo SSL (Secure Sockets Layer) úrovně transportu (TLS) s certifikáty X. 509 pro ověřování, jsou platné následující hodnoty identity:  
  
- NÁZV. Služba WCF zajišťuje, že certifikát poskytnutý během ověřování SSL obsahuje atribut DNS nebo `CommonName` (CN), který se rovná hodnotě zadané v identitě DNS na klientovi. Všimněte si, že tyto kontroly se provádí Kromě určení platnosti certifikátu serveru. Ve výchozím nastavení služba WCF ověřuje, že certifikát serveru je vydaný důvěryhodnou kořenovou autoritou.  
  
- Certifikát. Během ověřování SSL zajišťuje služba WCF, že vzdálený koncový bod poskytuje přesnou hodnotu certifikátu zadanou v identitě.  
  
- Odkaz na certifikát Stejné jako certifikát.  
  
- RSA. Během ověřování SSL zajišťuje služba WCF, že vzdálený koncový bod poskytuje přesný klíč RSA zadaný v identitě.  
  
 Pokud se služba ověřuje pomocí protokolu SSL nebo přenosu SSL s přihlašovacími údaji Windows pro ověřování a vyjednává přihlašovací údaje, jsou platné následující hodnoty identity:  
  
- NÁZV. Vyjednávání předá hlavní název služby (SPN), aby bylo možné zkontrolovat název DNS. Hlavní název služby (SPN) `host/<dns name>`je ve formátu.  
  
- SPN. Vrátí se explicitní hlavní název služby (SPN), `host/myservice`například.  
  
- NÁZVU. Hlavní název uživatele (UPN) účtu služby. Hlavní název uživatele (UPN) `username`je ve formátu @ `domain`. Například pokud je služba spuštěna v uživatelském účtu, může být `username@contoso.com`.  
  
 Zadání identity programově (pomocí <xref:System.ServiceModel.EndpointAddress.Identity%2A> vlastnosti) je volitelné. Pokud není zadaná žádná identita a typ přihlašovacích údajů klienta je Windows, výchozí hodnota je hlavní název služby (SPN) s hodnotou nastavenou na název hostitele v adrese koncového bodu služby s literálem Host/. Pokud není zadaná žádná identita a jako typ přihlašovacích údajů klienta je certifikát, výchozí hodnota je `Certificate`. To platí pro zabezpečení na úrovni zpráv i přenosů.  
  
## <a name="identity-and-custom-bindings"></a>Identity a vlastní vazby  
 Vzhledem k tomu, že identita služby závisí na použitém typu vazby, zajistěte, aby byla při vytváření vlastní vazby vystavena příslušná identita. Například v následujícím příkladu kódu není vystavená identita kompatibilní s typem zabezpečení, protože identita pro spouštěcí vazby zabezpečené konverzace neodpovídá identitě vazby na koncovém bodu. Vazba zabezpečené konverzace nastavuje identitu DNS, zatímco <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> nastavuje hlavní název uživatele (UPN) nebo hlavní název služby (SPN).  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Další informace o tom, jak správně Stack prvků svázat pro vlastní vazbu, najdete v tématu [vytváření uživatelsky definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Další informace o vytvoření vlastní vazby s nástrojem <xref:System.ServiceModel.Channels.SecurityBindingElement>naleznete v tématu [How to: Vytvoří SecurityBindingElement pro zadaný režim](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)ověřování.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Postupy: Vytvoření vlastního ověřovatele identity klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Vytváření uživatelem definovaných vazeb](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
