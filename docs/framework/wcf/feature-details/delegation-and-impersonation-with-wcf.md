---
title: Delegace a zosobnění se službou WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
ms.openlocfilehash: b9dd02724b8c2a9e4f50ecd61d822d5f1a478eee
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402341"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegace a zosobnění se službou WCF
*Zosobnění* je běžná technika, služby slouží k omezení klientský přístup k prostředkům služby domény. Prostředky služby domény může být buď počítač prostředky, jako jsou místní soubory (zosobnění), nebo prostředek na jiném počítači, jako jsou sdílené složky (delegování). Ukázková aplikace, najdete v části [zosobnění klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Příklad použití zosobnění, naleznete v tématu [jak: Zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Mějte na paměti, že při zosobnění klienta ve službě, je služba spuštěna pomocí přihlašovacích údajů klienta, které mohou mít větší oprávnění než procesu serveru.  
  
## <a name="overview"></a>Přehled  
 Klienti obvykle volání služby pro službu provést některé akce jménem klienta. Zosobnění umožňuje službě tak, aby fungoval jako klient při provádění akce. Delegování umožňuje front-endové služby pro předávání požadavek klienta do back-end služby tak, že back-end služba může také zosobnit klienta. Zosobnění se nejčastěji používá jako způsob kontroly, jestli je klient autorizaci provést určitou akci, zatímco delegování je možné do back-end služby průchodu funkce zosobnění, spolu s identity klienta. Delegování je funkce domény Windows, která se dá použít při ověřování protokolu Kerberos pomocí provádí. Delegování se liší od identity toku a vzhledem k tomu, že delegování přenáší možnost zosobnění klienta bez vlastnictví hesla klienta, je mnohem vyšší Privilegovaná operace než identity toku.  
  
 Zosobnění a delegování nutné, aby klient Windows identity. Pokud klient nemá k dispozici identita Windows, jediná dostupná možnost je tok identity klienta ke službě druhý.  
  
## <a name="impersonation-basics"></a>Základní informace o zosobnění  
 Windows Communication Foundation (WCF) podporuje zosobnění pro různé přihlašovací údaje pro klienta. Toto téma popisuje podporu modelu služby pro zosobnění volající během provádění metody služby. Popsány také jsou obvyklé scénáře nasazení zahrnující zosobnění a zabezpečení protokolu SOAP a možnosti WCF v těchto scénářích.  
  
 Toto téma se zaměřuje na zosobnění a delegování ve službě WCF při použití zabezpečení protokolu SOAP. Můžete také použít zosobnění a delegování s použitím technologie WCF při použití zabezpečení přenosu, jak je popsáno v [použití zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dvě metody  
 Zabezpečení WCF SOAP má dva různé metody pro provádění zosobnění. Použitá metoda závisí na vazbu. Jeden je zosobnění z Windows tokenu získaného z Security Support Provider Interface (SSPI) nebo protokolu Kerberos ověřování, které se pak zapíší do mezipaměti ve službě. Druhým je zosobnění z Windows tokenu získaného z rozšíření protokolu Kerberos, se nazývají *Service for User* (S4U).  
  
### <a name="cached-token-impersonation"></a>V mezipaměti Token zosobnění  
 Můžete provádět v mezipaměti token zosobnění s následujícími možnostmi:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, a <xref:System.ServiceModel.NetTcpBinding> pomocí pověření klienta Windows.  
  
- <xref:System.ServiceModel.BasicHttpBinding> s <xref:System.ServiceModel.BasicHttpSecurityMode> nastaveno <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> přihlašovacích údajů nebo standardní vazbu kde klient poskytne název přihlašovacích údajů uživatele, který služba můžete namapovat na platný účet Windows.  
  
- Žádné <xref:System.ServiceModel.Channels.CustomBinding> , který používá pověření klienta Windows s `requireCancellation` nastavena na `true`. (Vlastnost je k dispozici na následující třídy: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, a <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Pokud zabezpečené konverzace se používá ve vazbě, musíte také mít `requireCancellation` nastavenou na `true`.  
  
- Žádné <xref:System.ServiceModel.Channels.CustomBinding> kde klient poskytne pověření uživatelského jména. Pokud zabezpečené konverzace se používá ve vazbě, musíte také mít `requireCancellation` nastavenou na `true`.  
  
### <a name="s4u-based-impersonation"></a>Na základě S4U zosobnění  
 Je možné provést zosobnění S4U podle následujícími způsoby:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, a <xref:System.ServiceModel.NetTcpBinding> s pověřením klientských certifikátů služby můžete namapovat na platný účet Windows.  
  
- Žádné <xref:System.ServiceModel.Channels.CustomBinding> , který používá pověření klienta Windows s `requireCancellation` nastavenou na `false`.  
  
- Žádné <xref:System.ServiceModel.Channels.CustomBinding> , která používá uživatelské jméno nebo pověření klienta Windows a zabezpečené konverzace s `requireCancellation` nastavenou na `false`.  
  
 V rozsahu, do které může služba zosobnit klienta závisí na oprávnění, která obsahuje účet služby při pokusu zosobnění, typ používá zosobnění a případně rozsah zosobnění, které je povoleno klienta.  
  
> [!NOTE]
>  Když klient a služba běží na stejném počítači a klient je spuštěn pod účtem systému (například `Local System` nebo `Network Service`), nelze zosobnit klienta, po vytvoření zabezpečené relace s stavové kontext zabezpečení tokeny. Formuláře Windows nebo konzolové aplikace se obvykle běží pod účtem aktuálně přihlášeného tak, aby ve výchozím nastavení se můžou zosobnit účet. Když klient je však stránky technologie ASP.NET a této stránce je hostovaná ve službě IIS 6.0 nebo [!INCLUDE[iisver](../../../../includes/iisver-md.md)], a poté spusťte klienta v části `Network Service` účet ve výchozím nastavení. Ve výchozím nastavení všechny vazby poskytované systémem, které podporují zabezpečených relací použijte token kontextu zabezpečení bezstavové (SCT). Nicméně pokud klient je stránka technologie ASP.NET a zabezpečené relace pomocí stavového SCTs se používají, nelze zosobnit klienta. Další informace o používání stavové SCTs v zabezpečené relaci v tématu [jak: Vytvoření kontextu zabezpečení pro zabezpečenou relaci Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Zosobnění v metodě služby: Deklarativní Model  
 Většina scénářů zosobnění zahrnovat spouštění metody služby v rámci volajícího. Zosobnění funkce, která usnadňuje to udělat tak, že umožňuje uživateli zadat požadavek zosobnění v poskytuje WCF <xref:System.ServiceModel.OperationBehaviorAttribute> atribut. V následujícím kódu, infrastruktura WCF zosobňuje volající před spuštěním `Hello` metody. Žádný pokus o přístup k prostředkům nativní uvnitř `Hello` metoda úspěšné pouze v případě, že seznam řízení přístupu (ACL) prostředku umožňuje volajícímu přístup k oprávnění. Chcete-li povolit zosobnění, nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost na jednu z <xref:System.ServiceModel.ImpersonationOption> hodnot výčtu, buď <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.  
  
> [!NOTE]
>  Pokud služba má vyšší pověření než vzdáleného klienta, se použijí přihlašovací údaje služby, pokud <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> je nastavena na <xref:System.ServiceModel.ImpersonationOption.Allowed>. To znamená pokud uživatel s nízkým oprávněním poskytuje svoje přihlašovací údaje, vyšší úrovní oprávnění služby provede metodu s přihlašovacími údaji služby a využívat prostředky, které uživatele s nízkými oprávněními jinak nebude možné použít.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Pouze v případě, že volající je ověřen pomocí přihlašovacích údajů, které je možné mapovat na uživatelský účet Windows, můžou infrastruktura WCF zosobňují volajícího. Pokud služba je nakonfigurovaná k ověření pomocí přihlašovacích údajů, který nemůže být namapován na účet Windows, metodu služby není spuštěn.  
  
> [!NOTE]
>  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)], zosobnění se nezdaří, pokud stavový SCT se vytvoří, což vede <xref:System.InvalidOperationException>. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Zosobnění v metodě služby: Imperativní modelu  
 Volající někdy není potřeba zosobnit metodu celé služby pro funkci, ale jenom část jeho. V tomto případě získání Windows identitu volajícího uvnitř metody služby a imperativně provést zosobnění. To provést pomocí <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost <xref:System.ServiceModel.ServiceSecurityContext> vrátit instanci <xref:System.Security.Principal.WindowsIdentity> třídy a volání <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metoda před použitím instance.  
  
> [!NOTE]
>  Nezapomeňte použít jazyka Visual Basic`Using` příkazu nebo C# `using` příkaz automaticky Obnova zosobnění akce. Pokud použijete příkaz nebo pokud používá programovací jazyk jiné než Visual Basic nebo C#, je potřeba vrátit úroveň zosobnění. Selhání k tomu může tvoří základ pro útok na dostupnost služby a zvýšení úrovně oprávnění pro útoky.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Zosobnění pro všechny metody služby  
 V některých případech je nutné provést všechny metody služby v kontextu volajícího. Namísto explicitně povolení této funkce na základě-method, použijte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak je znázorněno v následujícím kódu, nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> vlastnost `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Je načten z kolekce chování, <xref:System.ServiceModel.ServiceHost> třídy. Všimněte si také, `Impersonation` vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute> použité pro každou metodu musí také být nastaven na hodnotu <xref:System.ServiceModel.ImpersonationOption.Allowed> nebo <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Následující tabulka popisuje chování WCF pro všechny možné kombinace `ImpersonationOption` a `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Chování|  
|---------------------------|------------------------------------------------|--------------|  
|Požadováno|není k dispozici|Volající zosobňuje WCF|  
|Povoleno|false|WCF není zosobňují volajícího|  
|Povoleno|true|Volající zosobňuje WCF|  
|Hodnotu NotAllowed|false|WCF není zosobňují volajícího|  
|Hodnotu NotAllowed|true|Zakázané. ( <xref:System.InvalidOperationException> Je vyvolána výjimka.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získané z přihlašovacích údajů Windows a uložili do mezipaměti Token zosobnění  
 V některých scénářích má klient částečnou kontrolu nad úrovní zosobnění, které provádí služba zadáním pověření klienta Windows. Jeden scénář nastane, pokud klient určuje úroveň zosobnění anonymní. Druhý vyvolá se při provádění zosobnění pomocí tokenu v mezipaměti. To se provádí tak, že nastavíte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, které je přístupné jako vlastnost Obecné <xref:System.ServiceModel.ChannelFactory%601> třídy.  
  
> [!NOTE]
>  Určení úroveň zosobnění anonymní způsobí, že klient nedovoluje anonymní přihlášení ke službě. Služba proto musí umožňovat anonymní přihlášení, bez ohledu na to, zda se provádí zosobnění.  
  
 Klienta můžete určit úroveň zosobnění jako <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, nebo <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Je vytvořen pouze token na zadané úrovni, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Následující tabulka určuje úroveň zosobnění, které služba získává při zosobňování z tokenu v mezipaměti.  
  
|`AllowedImpersonationLevel` Hodnota|Služba má `SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonymní|Ano|není k dispozici|Zosobnění|  
|Anonymní|Ne|není k dispozici|Identifikace|  
|Identifikace|není k dispozici|není k dispozici|Identifikace|  
|Zosobnění|Ano|není k dispozici|Zosobnění|  
|Zosobnění|Ne|není k dispozici|Identifikace|  
|Delegování|Ano|Ano|Delegování|  
|Delegování|Ano|Ne|Zosobnění|  
|Delegování|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získané z název přihlašovacích údajů uživatele a uložili do mezipaměti Token zosobnění  
 Tím, že jeho uživatelské jméno a heslo, předáte služby, umožňuje klienta WCF pro přihlášení jako tento uživatel, který je ekvivalentem k nastavení `AllowedImpersonationLevel` vlastnost <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Je k dispozici na <xref:System.ServiceModel.Security.WindowsClientCredential> a <xref:System.ServiceModel.Security.HttpDigestClientCredential> třídy.) Následující tabulka obsahuje zosobnění úroveň získali, když služba přijímá název přihlašovacích údajů uživatele.  
  
|`AllowedImpersonationLevel`|Služba má `SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|není k dispozici|Ano|Ano|Delegování|  
|není k dispozici|Ano|Ne|Zosobnění|  
|není k dispozici|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Úroveň zosobnění získaných na základě S4U zosobnění  
  
|Služba má `SeTcbPrivilege`|Služba má `SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Ano|Ano|není k dispozici|Zosobnění|  
|Ano|Ne|není k dispozici|Identifikace|  
|Ne|není k dispozici|není k dispozici|Identifikace|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapování certifikátu klienta na účet Windows  
 Je možné pro klienta ke svému ověření ke službě pomocí certifikátu a mít mapy služeb klienta pro existující účet prostřednictvím služby Active Directory. Následující kód XML ukazuje, jak nakonfigurovat službu mapování certifikátu.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Následující kód ukazuje, jak nakonfigurovat službu.  
  
```  
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Delegování  
 Delegovat do back-end služby, musíte provést služby protokolu Kerberos více větev (SSPI bez použití náhradní lokality NTLM) nebo protokolu Kerberos přímo ověřování ve službě back-end pomocí identity klienta Windows. Pokud chcete delegovat na back-end službu, vytvořte <xref:System.ServiceModel.ChannelFactory%601> a kanál a potom komunikovat prostřednictvím kanálu při zosobňování klienta. V tomto formuláři delegování vzdálenost, jakou může být umístěn z front-endové služby back-end služby závisí na úroveň zosobnění dosahuje front-endové služby. Pokud je úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, front-endovými a back endové služby musí běžet na stejném počítači. Pokud je úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, služba front-endu a back-end může být na samostatných počítačích nebo ve stejném počítači. Povolení delegování úroveň zosobnění vyžaduje, aby zásada domény Windows byly konfigurovány tak, aby povolovala delegování. Další informace o konfiguraci služby Active Directory pro podporu delegování najdete v tématu [povolení delegovaného ověření](https://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Pokud se klient ověřuje na front-endové služby pomocí uživatelského jména a hesla, které odpovídají účtu Windows na back-end služby, může ověřit front-endové služby do back-end služby opětovným použitím uživatelské jméno a heslo klienta. Totiž formuláři zvláště efektivní identity toku předávání uživatelské jméno a heslo k back-end služby umožňuje back-end služby provést zosobnění, ale nepředstavuje delegování, protože se používá protokol Kerberos. Active Directory ovládacích prvků na delegování se nevztahují na ověřování uživatelským jménem a heslem.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Možnost delegování jako funkce úroveň zosobnění  
  
|Úroveň zosobnění|Služby můžete provádět delegování napříč procesy|Služby můžete provádět mezi počítači delegování|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Ne|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Ano|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Ano|Ano|  
  
 Následující příklad kódu ukazuje, jak použít delegování.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Jak nakonfigurovat aplikaci pro použití omezeného delegování  
 Než budete moci použít omezené delegování, odesílatel, příjemce a řadič domény musí být nakonfigurovaný k tomu. Následující postup obsahuje kroky, které umožňují omezené delegování. Podrobnosti o rozdílech mezi delegování a omezeného delegování, najdete v části [rozšíření protokolu Kerberos serveru Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=100194) , který popisuje omezené diskuse.  
  
1. Na řadiči domény, zrušte **účet je citlivý a nelze jej delegovat** zaškrtávací políčko pro účet, pod kterým klientská aplikace běží.  
  
2. Na řadiči domény, vyberte **účet je důvěryhodný pro delegování** zaškrtávací políčko pro účet, pod kterým klientská aplikace běží.  
  
3. Na řadiči domény, nakonfigurujte střední vrstvy počítače tak, aby je důvěryhodný pro delegování, kliknutím **Důvěřovat počítači pro delegování** možnost.  
  
4. Na řadiči domény konfigurace střední vrstvy počítače tak, aby, kliknutím **důvěřovat tomuto počítači pro delegování pouze určeným službám** možnost.  
  
 Podrobnější pokyny týkající se konfigurace omezeného delegování naleznete v následujících tématech na webu MSDN:  
  
- [Řešení potíží s delegování protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkId=36724)  
  
- [Přechod protokolu Kerberos a omezeného delegování](https://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>
- <xref:System.ServiceModel.ImpersonationOption>
- <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>
- <xref:System.ServiceModel.ServiceSecurityContext>
- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ChannelFactory%601>
- <xref:System.Security.Principal.TokenImpersonationLevel.Identification>
- [Použití zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Zosobnění klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Postupy: Zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
