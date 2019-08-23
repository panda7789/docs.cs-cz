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
ms.openlocfilehash: 6e79346a448012255020cc28b6534e734980b1db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968847"
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegace a zosobnění se službou WCF
*Zosobnění* je běžná technika, kterou služby používají k omezení přístupu klientů k prostředkům domény služby. Prostředky domény služby můžou být prostředky počítače, například místní soubory (zosobnění), nebo prostředek na jiném počítači, například sdílená složka (delegování). Ukázkovou aplikaci najdete v tématu [zosobnění klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Příklad použití zosobnění naleznete v tématu [How to: Zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
> Uvědomte si, že při zosobnění klienta ve službě se služba spouští s přihlašovacími údaji klienta, které mohou mít vyšší oprávnění než proces serveru.  
  
## <a name="overview"></a>Přehled  
 Klienti obvykle volají službu, aby služba prováděla nějakou akci jménem klienta. Zosobnění umožňuje službě, aby při provádění této akce fungovala jako klient. Delegování umožňuje front-endové službě předávat požadavek klienta back-end službě takovým způsobem, že back-end služba může také zosobnit klienta. Zosobnění se nejčastěji používá jako způsob kontroly, zda je klient autorizován k provedení určité akce, zatímco delegování je způsob, jakým je tok funkcí zosobnění, spolu s identitou klienta, k back-endové službě. Delegování je funkce domény systému Windows, která se dá použít, když se provádí ověřování založené na protokolu Kerberos. Delegování se liší od toku identity a, protože delegování přenáší schopnost zosobnit klienta bez nutnosti vlastnit heslo klienta, jedná se o mnohem vyšší privilegovanou operaci než tok identity.  
  
 Zosobnění i delegování vyžaduje, aby měl klient identitu Windows. Pokud klient nemá identitu systému Windows, je k dispozici jediná dostupná možnost k vytvoření toku identity klienta k druhé službě.  
  
## <a name="impersonation-basics"></a>Základy zosobnění  
 Windows Communication Foundation (WCF) podporuje zosobnění pro celou řadu přihlašovacích údajů klienta. Toto téma popisuje podporu modelu služby pro zosobnění volajícího při implementaci metody služby. V tomto scénáři jsou také popsány běžné scénáře nasazení zahrnující možnosti zosobnění a zabezpečení SOAP a WCF.  
  
 Toto téma se zaměřuje na zosobnění a delegování v WCF při použití zabezpečení SOAP. Při použití zabezpečení přenosu můžete také použít zosobnění a delegování pomocí WCF, jak je popsáno v tématu [použití zosobnění při zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dvě metody  
 Zabezpečení WCF SOAP má dvě odlišné metody pro vykonávání zosobnění. Použitá metoda závisí na vazbě. Jedna z nich je zosobněná od tokenu Windows získaného z rozhraní SSPI (Security Support Provider Interface) nebo ověřování pomocí protokolu Kerberos, které pak ukládá do mezipaměti služby. Druhá je zosobnění z tokenu Windows získaného z rozšíření protokolu Kerberos, která se společně nazývají *Service-for-User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Zosobnění tokenu v mezipaměti  
 Zosobnění tokenu v mezipaměti můžete provést následujícími kroky:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> a<xref:System.ServiceModel.NetTcpBinding> s přihlašovacími údaji klienta Windows.  
  
- <xref:System.ServiceModel.BasicHttpBinding><xref:System.ServiceModel.BasicHttpSecurityMode> s nastavením <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> přihlašovacích údajů nebo jakékoli jiné standardní vazby, kde klient prezentuje přihlašovací údaje uživatelského jména, které může služba mapovat na platný účet systému Windows.  
  
- Všechny <xref:System.ServiceModel.Channels.CustomBinding> , které používají přihlašovací údaje klienta Windows `requireCancellation` s nastavením na `true`. (Vlastnost je k dispozici pro následující třídy: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, a <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Pokud se ve vazbě používá zabezpečená konverzace, musí mít `requireCancellation` také vlastnost nastavenou na. `true`  
  
- Všechny <xref:System.ServiceModel.Channels.CustomBinding> , kde klient prezentuje přihlašovací údaje uživatelského jména. Pokud se pro vazbu používá zabezpečená konverzace, musí mít `requireCancellation` také vlastnost nastavenou na. `true`  
  
### <a name="s4u-based-impersonation"></a>Zosobnění založené na S4U  
 Zosobnění založené na S4U můžete provést s následujícími možnostmi:  
  
- <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding> a<xref:System.ServiceModel.NetTcpBinding> s přihlašovacími údaji klienta certifikátu, které může služba mapovat na platný účet systému Windows.  
  
- Všechny <xref:System.ServiceModel.Channels.CustomBinding> , které používají přihlašovací údaje klienta Windows `requireCancellation` s vlastností nastavenou `false`na.  
  
- Každý <xref:System.ServiceModel.Channels.CustomBinding> , který používá uživatelské jméno nebo pověření klienta Windows a zabezpečenou konverzaci `requireCancellation` s vlastností nastavenou `false`na.  
  
 Rozsah, ve kterém může služba zosobnit klienta, závisí na oprávněních, která má účet služby při pokusu o zosobnění, typu zosobnění a případně rozsahu zosobnění klienta k povolení.  
  
> [!NOTE]
> Když je klient a služba spuštěná ve stejném počítači a klient nástroje je spuštěný pod účtem systému (například `Local System` nebo `Network Service`), klient se nemůže zosobnit, když je navázána zabezpečená relace s kontextem kontextu zabezpečení. klíčov. Formulářová aplikace Windows nebo Konzolová aplikace se obvykle spouští pod aktuálně přihlášeným účtem, aby bylo možné účet ve výchozím nastavení zosobnit. Pokud je však klient ASP.NET stránka a tato stránka je hostována ve službě IIS 6,0 nebo IIS 7,0, bude klient ve výchozím nastavení spuštěn pod `Network Service` účtem. Všechny vazby poskytnuté systémem, které podporují zabezpečené relace, používají ve výchozím nastavení token kontextu zabezpečení bez stavů (SCT). Pokud je však klient ASP.NET stránku a používají se zabezpečené relace se stavovým SCTs, nelze klienta zosobnit. Další informace o používání stavových SCTs v zabezpečené relaci najdete v tématu [How to: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Zosobnění v metodě služby: Deklarativní model  
 Většina scénářů zosobnění zahrnuje spuštění metody služby v kontextu volajícího. Služba WCF poskytuje funkci zosobnění, která umožňuje uživateli zadat v <xref:System.ServiceModel.OperationBehaviorAttribute> atributu požadavek na zosobnění. Například v následujícím kódu infrastruktura WCF před provedením `Hello` metody zosobní volajícího. Všechny pokusy o přístup k nativním `Hello` prostředkům v metodě jsou úspěšné pouze v případě, že je v seznamu řízení přístupu (ACL) prostředku povoleno oprávnění k přístupu volajícího. Chcete-li povolit zosobnění, nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost na jednu <xref:System.ServiceModel.ImpersonationOption> z hodnot výčtu, a to <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> buď <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>nebo, jak je znázorněno v následujícím příkladu.  
  
> [!NOTE]
> Pokud má služba vyšší přihlašovací údaje než vzdálený klient, použijí se přihlašovací údaje služby, pokud <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> je vlastnost nastavena na <xref:System.ServiceModel.ImpersonationOption.Allowed>hodnotu. To znamená, že pokud uživatel s nízkými oprávněními poskytne své přihlašovací údaje, služba s vyššími oprávněními spustí metodu s přihlašovacími údaji služby a může použít prostředky, které by uživatel s nízkými oprávněními jinak nedokázal použít.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 Infrastruktura WCF může zosobnit volajícího pouze v případě, že je volající ověřen s přihlašovacími údaji, které lze namapovat na uživatelský účet systému Windows. Pokud je služba nakonfigurovaná k ověřování pomocí přihlašovacích údajů, které se nedají namapovat na účet systému Windows, metoda služby se neprovede.  
  
> [!NOTE]
> V [!INCLUDE[wxp](../../../../includes/wxp-md.md)]případě, že se vytvoří stavový SCT, zosobnění v důsledku toho dojde <xref:System.InvalidOperationException>k chybě. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Zosobnění v metodě služby: Imperativní model  
 V některých případech volající nepotřebuje zosobnit celou metodu služby, aby fungoval, ale jenom pro její část. V takovém případě Získejte identitu volajícího volajícího v rámci metody služby a imperativně proveďte zosobnění. Použijte <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext> k tomu vlastnost pro <xref:System.Security.Principal.WindowsIdentity> návrat instance třídy a volání <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody před použitím instance.  
  
> [!NOTE]
> Nezapomeňte použít příkaz Visual Basic`Using` C# `using` nebo příkaz k automatickému vrácení akce zosobnění. Pokud nepoužijete příkaz, nebo pokud používáte programovací jazyk jiný než Visual Basic nebo C#, nezapomeňte vrátit úroveň zosobnění. V takovém případě se může jednat o základ pro odepření služby a zvýšení oprávnění k útokům.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Zosobnění pro všechny metody služby  
 V některých případech je nutné provést všechny metody služby v kontextu volajícího. Namísto explicitního povolení této funkce na základě jednotlivých metod použijte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak je znázorněno v následujícím kódu, nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> vlastnost na `true`hodnotu. Je načten z kolekce chování <xref:System.ServiceModel.ServiceHost> třídy. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Všimněte si také, `Impersonation` že vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute> použité u jednotlivých metod musí být také nastavena na hodnotu <xref:System.ServiceModel.ImpersonationOption.Allowed> nebo <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Následující tabulka popisuje chování služby WCF pro všechny možné kombinace `ImpersonationOption` a. `ImpersonateCallerForAllServiceOperations`  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Chování|  
|---------------------------|------------------------------------------------|--------------|  
|Požadováno|není k dispozici|WCF zosobňuje volajícího|  
|Povoleno|false|WCF nezosobňuje volajícího|  
|Povoleno|true|WCF zosobňuje volajícího|  
|NotAllowed|false|WCF nezosobňuje volajícího|  
|NotAllowed|true|Zakázané. <xref:System.InvalidOperationException> (Je vyvolána.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získaná z pověření systému Windows a zosobnění tokenu v mezipaměti  
 V některých scénářích má klient částečnou kontrolu nad úrovní zosobnění, kterou služba provádí při použití přihlašovacích údajů klienta Windows. K jednomu scénáři dojde, když klient určí anonymní úroveň zosobnění. K druhé dojde při provádění zosobnění s tokenem uloženým v mezipaměti. To se provádí nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnosti <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, která je k dispozici jako vlastnost obecné <xref:System.ServiceModel.ChannelFactory%601> třídy.  
  
> [!NOTE]
> Pokud zadáte úroveň zosobnění anonymní, klient se k této službě přihlašuje anonymně. Služba musí proto umožňovat anonymní přihlášení bez ohledu na to, zda se zosobnění provádí.  
  
 Klient může určit <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>úroveň zosobnění jako, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>nebo <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Vytvoří se pouze token na zadané úrovni, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Následující tabulka určuje úroveň zosobnění, kterou služba získá při zosobnění z tokenu uloženého v mezipaměti.  
  
|`AllowedImpersonationLevel`osa|Služba má`SeImpersonatePrivilege`|Služba a klient podporují delegování|Token uložený v mezipaměti`ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonymous|Ano|není k dispozici|Zosobnění|  
|Anonymous|Ne|není k dispozici|Identifikace|  
|Identifikace|není k dispozici|není k dispozici|Identifikace|  
|Zosobnění|Ano|není k dispozici|Zosobnění|  
|Zosobnění|Ne|není k dispozici|Identifikace|  
|Delegování|Ano|Ano|Delegování|  
|Delegování|Ano|Ne|Zosobnění|  
|Delegování|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získaná od přihlašovacích údajů uživatelského jména a zosobnění tokenu v mezipaměti  
 Po předání služby jeho uživatelskému jménu a heslu umožní klient, aby se služba WCF přihlásila jako tento uživatel, což je `AllowedImpersonationLevel` ekvivalentní nastavení <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>vlastnosti. (Je k dispozici <xref:System.ServiceModel.Security.WindowsClientCredential> v třídách a <xref:System.ServiceModel.Security.HttpDigestClientCredential> .) `AllowedImpersonationLevel` Následující tabulka uvádí úroveň zosobnění získaná, když služba přijímá přihlašovací údaje uživatelského jména.  
  
|`AllowedImpersonationLevel`|Služba má`SeImpersonatePrivilege`|Služba a klient podporují delegování|Token uložený v mezipaměti`ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|není k dispozici|Ano|Ano|Delegování|  
|není k dispozici|Ano|Ne|Zosobnění|  
|není k dispozici|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Úroveň zosobnění získaná z zosobnění založené na S4U  
  
|Služba má`SeTcbPrivilege`|Služba má`SeImpersonatePrivilege`|Služba a klient podporují delegování|Token uložený v mezipaměti`ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Ano|Ano|není k dispozici|Zosobnění|  
|Ano|Ne|není k dispozici|Identifikace|  
|Ne|není k dispozici|není k dispozici|Identifikace|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapování klientského certifikátu na účet systému Windows  
 Je možné, aby se klient mohl přihlásit ke službě pomocí certifikátu a aby služba namapovala klienta na existující účet prostřednictvím služby Active Directory. Následující kód XML ukazuje, jak nakonfigurovat službu pro mapování certifikátu.  
  
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
 Aby bylo možné delegovat službu back-end, musí služba provádět multi-nožku protokolu Kerberos (SSPI bez použití protokolu NTLM Fallback) nebo přímé ověřování pomocí protokolu Kerberos do back-endové služby pomocí identity Windows klienta. Chcete-li delegovat na back-endové služby, vytvořte <xref:System.ServiceModel.ChannelFactory%601> a a kanál a pak při zosobnění klienta komunikujte prostřednictvím kanálu. V této podobě delegování je vzdálenost, na které se back-end služba nachází v front-endové službě, závislá na úrovni zosobnění dosažené front-end službou. Pokud je <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>úroveň zosobnění, musí front-end a back-end služba běžet na stejném počítači. Pokud je <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>úroveň zosobnění, front-endové a back-endové služby můžou být v různých počítačích nebo ve stejném počítači. Povolení zosobnění na úrovni delegování vyžaduje, aby byla zásada domény systému Windows nakonfigurovaná tak, aby povolovala delegování. Další informace o konfiguraci služby Active Directory pro podporu delegování najdete v tématu [Povolení delegovaného ověřování](https://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
> Když se klient ověřuje u front-endové služby pomocí uživatelského jména a hesla, které odpovídá účtu systému Windows v back-endové službě, může se front-end služba ověřit pro back-endové služby tím, že znovu použije uživatelské jméno a heslo klienta. Toto je obzvlášť výkonná forma toku identity, protože předáním uživatelského jména a hesla do back-endové služby umožňuje back-endové službě provádět zosobnění, ale nejedná se o delegování, protože se nepoužívá protokol Kerberos. Ovládací prvky služby Active Directory v delegování neplatí pro ověřování uživatelského jména a hesla.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Možnost delegování jako funkce úrovně zosobnění  
  
|Úroveň zosobnění|Služba může provádět delegování mezi procesy|Služba může provádět delegování mezi počítači|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Ne|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Ano|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Ano|Ano|  
  
 Následující příklad kódu ukazuje, jak použít delegování.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Konfigurace aplikace pro použití omezeného delegování  
 Předtím, než budete moci použít omezené delegování, je nutné nakonfigurovat odesílatele, příjemce a řadič domény. Následující postup obsahuje seznam kroků, které povolují omezené delegování. Podrobnosti o rozdílech mezi delegováním a omezeným delegováním najdete v části [rozšíření protokolu Kerberos pro Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=100194) , která pojednává o omezené diskusi.  
  
1. V řadiči domény zrušte zaškrtnutí políčka **účet je citlivý a nelze jej delegovat** pro účet, pod kterým je spuštěná klientská aplikace.  
  
2. Na řadiči domény zaškrtněte políčko **účet je důvěryhodný pro delegování** pro účet, pod kterým je spuštěná klientská aplikace.  
  
3. Na řadiči domény nakonfigurujte počítač střední vrstvy tak, aby byl důvěryhodný pro delegování, kliknutím na možnost **Důvěřovat počítači pro delegování** .  
  
4. Na řadiči domény nakonfigurujte počítač střední vrstvy na používání omezeného delegování kliknutím na možnost **Důvěřovat tomuto počítači pro delegování pouze určeným službám** .  
  
 Podrobnější pokyny týkající se konfigurace omezeného delegování najdete v následujících tématech na webu MSDN:  
  
- [Řešení potíží s delegováním protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkId=36724)  
  
- [Přechod protokolu Kerberos a omezené delegování](https://go.microsoft.com/fwlink/?LinkId=36725)  
  
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
