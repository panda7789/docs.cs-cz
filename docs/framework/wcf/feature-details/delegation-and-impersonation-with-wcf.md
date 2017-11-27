---
title: "Delegace a zosobnění se službou WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2080ab9264b8110cbc094e7c6064362e634edaaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegace a zosobnění se službou WCF
*Zosobnění* je běžný postup, který služby použít k omezení klientský přístup k prostředkům doména služby. Prostředky služby domény může být buď prostředky počítače, jako je například místní soubory (zosobnění), nebo prostředku na jiném počítači, například do sdílené složky (delegování). Ukázkovou aplikaci, najdete v části [zosobnění klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Příklad použití zosobnění naleznete v části [postupy: zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Upozorňujeme, že při zosobnění klienta ve službě, služba bude spuštěna s přihlašovacími údaji klienta, které mohou mít vyšší oprávnění než procesu serveru.  
  
## <a name="overview"></a>Přehled  
 Klienti obvykle volání služby pro službu provést některé akce jménem klienta. Zosobnění umožňuje služby tak, aby fungoval jako klient při provádění akce. Delegování umožňuje front-endová služba pro předávání požadavek klienta ke službě back-end tak, že služba back endu může také zosobnit klienta. Zosobnění se nejčastěji používá jako způsob kontroly, jestli je klient oprávněn provádět určité akce, zatímco delegování je způsob průchodu možnosti zosobnění, společně s identity klienta ke službě back-end. Delegování je funkce domény systému Windows, která lze použít, pokud se provádí ověřování pomocí protokolu Kerberos. Delegování se liší od identity toku, a protože delegování přenáší možnost zosobnění klienta bez u sebe hesla klienta, je mnohem vyšší privilegované operace než identity toku.  
  
 Zosobnění a delegování nutné, aby klient identitu systému Windows. Pokud klient nemá identitu systému Windows, je k dispozici pouze možnost tok identity klienta ke službě druhý.  
  
## <a name="impersonation-basics"></a>Základní informace o zosobnění  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]podporuje zosobnění pro celou řadu pověření klienta. Toto téma popisuje podporu modelu služby pro zosobnění volajícího během provádění metody služby. Popsány i jsou běžné scénáře nasazení zahrnující zosobnění a zabezpečení protokolu SOAP a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] možnosti v těchto scénářích.  
  
 Toto téma se zaměřuje na zosobnění a delegování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] při použití protokolu SOAP zabezpečení. Můžete také použít zosobnění a delegování s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] při použití zabezpečení přenosu, jak je popsáno v [pomocí zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dvě metody  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Zabezpečení protokolu SOAP má dvě odlišné metody pro provádění zosobnění. Metoda použitá závisí na vazby. Jeden je zosobnění z tokenu Windows získané z rozhraní SSPI (Security Support Provider Interface) nebo protokolu Kerberos ověřování, které jsou pak uloženy v mezipaměti služby. Druhá je zosobnění z tokenu Windows získané z rozšíření protokolu Kerberos, se nazývají *Service-for-User* (S4U).  
  
### <a name="cached-token-impersonation"></a>V mezipaměti Token zosobnění  
 Můžete provádět v mezipaměti token zosobnění s následujícími službami:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, a <xref:System.ServiceModel.NetTcpBinding> s pověření klienta systému Windows.  
  
-   <xref:System.ServiceModel.BasicHttpBinding>s <xref:System.ServiceModel.BasicHttpSecurityMode> nastavte na <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> přihlašovacích údajů nebo standardní vazby kde klient uvede název přihlašovací údaje uživatele, který službu můžete namapovat platný účet systému Windows.  
  
-   Všechny <xref:System.ServiceModel.Channels.CustomBinding> používající pověření klienta systému Windows s `requireCancellation` nastavena na `true`. (Vlastnost je k dispozici na následující třídy: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, a <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Pokud se v vazba používá zabezpečené konverzaci, musí mít rovněž `requireCancellation` vlastnost nastavena na hodnotu `true`.  
  
-   Všechny <xref:System.ServiceModel.Channels.CustomBinding> kde klient uvede název pověření uživatele. Pokud se na vazby používá k zabezpečené konverzaci, musí mít rovněž `requireCancellation` vlastnost nastavena na hodnotu `true`.  
  
### <a name="s4u-based-impersonation"></a>Na základě S4U zosobnění  
 Můžete provádět na základě S4U zosobnění s následujícími službami:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, a <xref:System.ServiceModel.NetTcpBinding> s pověřením certifikátu klienta služby je možné namapovat platný účet systému Windows.  
  
-   Všechny <xref:System.ServiceModel.Channels.CustomBinding> používající pověření klienta systému Windows s `requireCancellation` vlastnost nastavena na hodnotu `false`.  
  
-   Všechny <xref:System.ServiceModel.Channels.CustomBinding> používající uživatelské jméno nebo pověření klienta pro systém Windows a zabezpečené konverzace s `requireCancellation` vlastnost nastavena na hodnotu `false`.  
  
 V rozsahu, ke které může služba zosobnit klienta závisí na oprávnění, které obsahuje účet služby, když se ho pokusí zosobnění, typ zosobnění použít a může být v rozsahu zosobnění, které umožňuje klientovi.  
  
> [!NOTE]
>  Když klient a služba běží na stejném počítači a klient je spuštěn pod účtem systému (například `Local System` nebo `Network Service`), když zabezpečené relace se naváže stavová kontext zabezpečení nelze zosobnit klienta tokeny. Formuláře Windows nebo konzolové aplikace se obvykle běží pod účtem aktuálně přihlášeného tak, aby ve výchozím nastavení se můžou zosobnit účet. Nicméně, pokud je klient [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stránky a že stránky je hostován v [!INCLUDE[iis601](../../../../includes/iis601-md.md)] nebo [!INCLUDE[iisver](../../../../includes/iisver-md.md)], spusťte klienta v části `Network Service` účet ve výchozím nastavení. Ve výchozím nastavení všechny vazby poskytované systémem, které podporují zabezpečených relací pomocí tokenu kontextu zabezpečení bezstavové (SCT). Ale pokud je klient [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stránky a zabezpečených relací s stavová SCTs se používají, nelze jej zosobnit klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí stavová SCTs v zabezpečené relaci, najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Zosobnění v metodě služby: deklarativní Model  
 Většina scénářů zosobnění zahrnovat spuštění metody služby v kontextu volajícího. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nabízí funkci zosobnění, které usnadňuje to provedete tím, že se uživateli zadat požadavek zosobnění v <xref:System.ServiceModel.OperationBehaviorAttribute> atribut. Například v následujícím kódu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zosobňuje volající před provedením `Hello` metoda. Jakýkoli pokus o přístup k prostředkům nativní uvnitř `Hello` metoda úspěšné pouze v případě, že seznam řízení přístupu (ACL) prostředku umožňuje volajícímu přístup oprávnění. Chcete-li povolit zosobnění, nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost na jednu z <xref:System.ServiceModel.ImpersonationOption> hodnot výčtu, buď <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.  
  
> [!NOTE]
>  Když služba má vyšší pověření než vzdáleného klienta, přihlašovací údaje služby se použijí, pokud <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> je nastavena na <xref:System.ServiceModel.ImpersonationOption.Allowed>. To znamená pokud uživatel nízkými oprávněními poskytuje svoje přihlašovací údaje, vyšší úrovní oprávnění služby provede metodu pomocí přihlašovacích údajů služby a mohou používat prostředky, které uživatel nízkými oprávněními jinak nebude moci používat.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury může zosobnit volající pouze v případě, že je volající ověření pomocí přihlašovacích údajů, které lze mapovat na uživatelský účet systému Windows. Pokud služba je nakonfigurována pro ověřování pomocí přihlašovacích údajů, který nejde mapovat na účet systému Windows, není služba metodu provést.  
  
> [!NOTE]
>  Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)], zosobnění se nezdaří, pokud stateful, SCT je vytvořen, což vede <xref:System.InvalidOperationException>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Zosobnění v metodě služby: imperativní modelu  
 Volající někdy nemusí zosobnit metodu celé služby pro funkce, ale pouze část ho. V takovém případě získat Windows identitu volajícího uvnitř metody služby a imperativní provést zosobnění. To provedete pomocí <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost <xref:System.ServiceModel.ServiceSecurityContext> vrátit instanci <xref:System.Security.Principal.WindowsIdentity> třídy a volání <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metoda před použitím instance.  
  
> [!NOTE]
>  Nezapomeňte použít [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] `Using` příkaz nebo jazyka C# `using` příkaz a automaticky vracet akce zosobnění. Pokud použijete příkaz nebo pokud používáte jiné než programovací jazyk [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo C#, je nutné vrátit úroveň zosobnění. Selhání k tomu můžete tvoří základ pro odepření služby a zvýšení úrovně oprávnění útoky.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Zosobnění pro všechny metody služeb  
 V některých případech je nutné provést všechny metody služby v kontextu volajícího. Místo explicitně povolení této funkce na základě za metoda, použít <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Jak je znázorněno v následujícím kódu, nastavit <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> vlastnost `true`. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Se načítají z kolekce chování <xref:System.ServiceModel.ServiceHost> třídy. Všimněte si také, že `Impersonation` vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute> použité pro každou metodu musí také být nastaven na hodnotu <xref:System.ServiceModel.ImpersonationOption.Allowed> nebo <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 Následující tabulka popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování pro všechny možné kombinace `ImpersonationOption` a `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Chování|  
|---------------------------|------------------------------------------------|--------------|  
|Požadováno|není k dispozici|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zosobňuje volající|  
|Povoleno|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]není zosobnit volající|  
|Povoleno|true|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zosobňuje volající|  
|NotAllowed|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]není zosobnit volající|  
|NotAllowed|true|Povoleny. ( <xref:System.InvalidOperationException> Je vyvolána výjimka.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získané z pověření systému Windows a uložili do mezipaměti Token zosobnění  
 V některých scénářích má klient částečné řídit úroveň zosobnění, pokud se používá Windows pověření klienta provede služba. Jeden scénář nastane, když klient určuje úroveň zosobnění anonymní. Druhá nastane při provádění zosobnění s token v mezipaměti. To se provádí nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, která je přístupná jako vlastnost obecná <xref:System.ServiceModel.ChannelFactory%601> třídy.  
  
> [!NOTE]
>  Určení úroveň zosobnění anonymní způsobí, že klient anonymní přihlášení ke službě. Služba proto musí umožňovat anonymní přihlášení, bez ohledu na to, jestli se provedlo zosobnění.  
  
 Klienta můžete zadat úroveň zosobnění jako <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, nebo <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Vytváří jenom token na zadané úrovni, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 Následující tabulka určuje úroveň zosobnění, které služba získává při zosobňování z token v mezipaměti.  
  
|`AllowedImpersonationLevel`Hodnota|Služba má`SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti`ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anonymní|Ano|není k dispozici|Zosobnění|  
|Anonymní|Ne|není k dispozici|Identifikace|  
|Identifikace|není k dispozici|není k dispozici|Identifikace|  
|Zosobnění|Ano|není k dispozici|Zosobnění|  
|Zosobnění|Ne|není k dispozici|Identifikace|  
|Delegování|Ano|Ano|Delegování|  
|Delegování|Ano|Ne|Zosobnění|  
|Delegování|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Úroveň zosobnění získané z název pověření uživatele a uloží do mezipaměti Token zosobnění  
 Předáním službu jeho uživatelské jméno a heslo, klient umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se přihlásit jako tento uživatel, který je ekvivalentní nastavení `AllowedImpersonationLevel` vlastnost <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. ( `AllowedImpersonationLevel` Je k dispozici na <xref:System.ServiceModel.Security.WindowsClientCredential> a <xref:System.ServiceModel.Security.HttpDigestClientCredential> třídy.) Následující tabulka obsahuje zosobnění úroveň získat přihlašovací údaje uživatele název přijetí služby.  
  
|`AllowedImpersonationLevel`|Služba má`SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti`ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|není k dispozici|Ano|Ano|Delegování|  
|není k dispozici|Ano|Ne|Zosobnění|  
|není k dispozici|Ne|není k dispozici|Identifikace|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Úroveň zosobnění získaný na základě S4U zosobnění  
  
|Služba má`SeTcbPrivilege`|Služba má`SeImpersonatePrivilege`|Klienta a služby podporují delegování|Token v mezipaměti`ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Ano|Ano|není k dispozici|Zosobnění|  
|Ano|Ne|není k dispozici|Identifikace|  
|Ne|není k dispozici|není k dispozici|Identifikace|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapování certifikátu klienta pro účet systému Windows  
 Je možné pro klienta k vlastnímu ověření služby pomocí certifikátu a tak, aby měl mapy služeb klienta pro existující účet prostřednictvím služby Active Directory. Následující kód XML ukazuje, jak nakonfigurovat službu, kterou chcete mapovat certifikát.  
  
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
 Pokud chcete delegovat na back-end službu, musíte služby provést více větev protokolu Kerberos (SSPI bez záložní NTLM) nebo protokolu Kerberos přímo ověřování ve službě back-end pomocí identity klienta systému Windows. Pokud chcete delegovat na back-end službu, vytvořte <xref:System.ServiceModel.ChannelFactory%601> a kanál a potom komunikovat prostřednictvím kanálu při zosobňování klienta. Pomocí tohoto formuláře delegování vzdálenost, kdy mohou být umístěny ze služby front-endové službě back-end závisí na úroveň zosobnění dosáhnout ve front-endové služby. Pokud je úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, služby front-end a back-end musí být spuštěné na stejném počítači. Pokud je úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, front-end a back-end služby může být na samostatných počítačích nebo na stejném počítači. Povolení delegování úroveň zosobnění vyžaduje, aby zásada domény Windows nakonfigurovaný tak, aby povolovala delegování. Další informace o konfiguraci služby Active Directory pro podporu delegování najdete v tématu [povolení delegované ověřování](http://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Když klient ověřuje front-endové služby pomocí uživatelského jména a hesla, které odpovídají na účet systému Windows ve službě back-end, front-endová služba ověřit ve službě back-end pomocí opakovaného použití klienta uživatelské jméno a heslo. To je zvláště efektivní forma tok identity, protože předávání uživatelské jméno a heslo ke službě back-end umožňuje back endové služby k zosobnění, ale nepředstavuje delegování, protože se nepoužívá protokolu Kerberos. Ovládací prvky Active Directory na delegování se nevztahují na ověřování uživatelským jménem a heslem.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Možnost delegování jako funkce úroveň zosobnění  
  
|Úroveň zosobnění|Služba může provést delegování napříč procesem|Služby můžete provádět mezi počítači delegování|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Ne|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Ano|Ne|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Ano|Ano|  
  
 Následující příklad kódu ukazuje, jak použít delegování.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Postup konfigurace aplikace pro použití omezeného delegování  
 Než budete moci použít omezené delegování, odesílatel, příjemce a řadič domény musí být konfigurován tak. Následující postup obsahuje kroky, které umožňují omezeného delegování. Podrobnosti o rozdílech mezi omezené delegování a delegování najdete v tématu část [rozšíření systému Windows Server 2003 Kerberos](http://go.microsoft.com/fwlink/?LinkId=100194) diskutuje omezené diskuzi.  
  
1.  Na řadiči domény, zrušte **účet je citlivý a nelze jej delegovat** zaškrtávací políčko pro účet, pod kterým klientská aplikace běží.  
  
2.  Na řadiči domény, vyberte **účet je důvěryhodný pro delegování** zaškrtávací políčko pro účet, pod kterým klientská aplikace běží.  
  
3.  Na řadiči domény, střední vrstvy počítač nakonfigurovat tak, aby byl důvěryhodný pro delegování, kliknutím **Důvěřovat počítači pro delegování** možnost.  
  
4.  Na řadiči domény, konfigurace střední vrstvy počítače použít omezené delegování, kliknutím **důvěřovat tomuto počítači pro delegování pouze určeným službám** možnost.  
  
 Podrobnější pokyny ke konfiguraci omezeného delegování naleznete v následujících tématech na webu MSDN:  
  
-   [Řešení potíží s delegováním protokolu Kerberos](http://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Přechod protokolu Kerberos a omezeného delegování](http://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>  
 <xref:System.ServiceModel.ImpersonationOption>  
 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>  
 <xref:System.ServiceModel.ServiceSecurityContext>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ChannelFactory%601>  
 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>  
 [Použití zosobnění se zabezpečením přenosu](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Zosobnění klienta](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Postupy: zosobnění klienta ve službě](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
