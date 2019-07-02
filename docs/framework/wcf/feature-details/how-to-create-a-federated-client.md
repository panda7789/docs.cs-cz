---
title: 'Postupy: Vytvoření federovaného klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: 8de673fae16da8189589e20b6d9a66b96e1823ba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487109"
---
# <a name="how-to-create-a-federated-client"></a>Postupy: Vytvoření federovaného klienta
Ve Windows Communication Foundation (WCF), vytvoření klienta pro *Federovaná služba* zahrnuje tři hlavní kroky:  
  
1. Konfigurace [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo podobné vlastní vazby. Další informace o vytváření příslušnou datovou vazbu najdete v tématu [jak: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Další možností je spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na koncový bod metadat federované služby pro generování konfiguračního souboru pro komunikaci s federované služby a jeden nebo více služby tokenu zabezpečení.  
  
2. Nastavte vlastnosti <xref:System.ServiceModel.Security.IssuedTokenClientCredential> , který řídí různé aspekty interakce klienta pomocí služby tokenů zabezpečení.  
  
3. Nastavte vlastnosti <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, což umožňuje certifikáty, které jsou potřebné k bezpečné komunikaci s danou koncových bodů, jako jsou služby tokenu zabezpečení.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> by mohla být vyvolána, když klient použije zosobněného přihlašovací údaje <xref:System.ServiceModel.WSFederationHttpBinding> vazby nebo token vydaný vlastní a asymetrické klíče. Asymetrické klíče se používají s <xref:System.ServiceModel.WSFederationHttpBinding> vazby a vlastní vydané tokeny, kdy <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> a <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> vlastnosti, jsou nastaveny na <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> Je vyvolána, když se klient pokusí o odeslání zprávy a neexistuje uživatelský profil pro identitu, která zosobnění klienta. Chcete-li tento problém zmírnit, přihlaste se na klientský počítač nebo volání `LoadUserProfile` před odesláním zprávy.  
  
 Toto téma obsahuje podrobné informace o těchto postupů. Další informace o vytváření příslušnou datovou vazbu najdete v tématu [jak: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Další informace o tom, jak funguje federované služby najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>K vytvoření a otestování konfigurace pro federované služby  
  
1. Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s adresou URL adresu metadat služby jako parametr příkazového řádku.  
  
2. Otevřete vygenerovaný konfigurační soubor ve vhodném editoru.  
  
3. Podívejte se na atributy a obsah některé generované [ \<issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) a [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementy. Jsou umístěny v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) prvky pro [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo prvky vlastních vazeb. Ujistěte se, že adresy obsahovat názvy očekávané domény nebo jiné informace o adrese. Je důležité zkontrolovat tyto informace, protože klient ověřuje na tyto adresy a zpřístupnit informace, jako jsou páry jméno/heslo uživatele. Pokud adresa není očekávána adresa, to mohlo způsobit zpřístupnění informací neúmyslnému příjemci.  
  
4. Prozkoumejte všechny další [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementů v rámci komentářem out <`alternativeIssuedTokenParameters`> element. Při použití nástroje Svcutil.exe k federované službě nebo všechny služby tokenu zabezpečení zprostředkující nezadávejte adresu vystavitele, ale místo toho zadat adresu metadat služby tokenů zabezpečení, který zpřístupňuje generovat konfigurace pro federované služby více koncových bodů, výsledný konfigurační soubor odkazuje na první koncový bod. Další koncové body jsou v konfiguračním souboru jako komentovaná <`alternativeIssuedTokenParameters`> elementy.  
  
     Určete, zda některá z těchto <`issuedTokenParameters`> je vhodnější než ten, který je již v konfiguraci. Například klient možná dáte přednost ověřování do služby tokenu zabezpečení pomocí služby Windows CardSpace token spíše než páru jméno/heslo uživatele.  
  
    > [!NOTE]
    >  Pokud několik služeb tokenů zabezpečení musí procházet před komunikaci se službou, je možné pro token služby zprostředkující zabezpečení můžete směrovat klienta do služby tokenu zabezpečení nesprávné. Proto se ujistěte se, že koncový bod pro služby tokenů zabezpečení v [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) je služba tokenů zabezpečení očekávané a není token služby neznámý zabezpečení.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Ke konfiguraci IssuedTokenClientCredential v kódu  
  
1. Přístup <xref:System.ServiceModel.Security.IssuedTokenClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost <xref:System.ServiceModel.Description.ClientCredentials> třídy (vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy, nebo prostřednictvím <xref:System.ServiceModel.ChannelFactory> třídy), jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Pokud token ukládání do mezipaměti není vyžadována, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> vlastnost `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Ovládací prvky vlastnost určuje, zda tyto tokeny od bezpečnostní token služby jsou uložené v mezipaměti. Pokud je tato vlastnost nastavená na `false`si klient vyžádá nový token od služby tokenů zabezpečení pokaždé, když ji musíte znovu autentizaci k federované služby, bez ohledu na to, jestli předchozí token je stále platný. Pokud je tato vlastnost nastavená na `true`, klient opětovně používá existující token pokaždé, když ji musíte znovu autentizaci k federované služby (za předpokladu nevypršela platnost tokenu). Výchozí hodnota je `true`.  
  
3. Pokud časový limit je vyžadováno na tokeny v mezipaměti, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> vlastnost <xref:System.TimeSpan> hodnotu. Vlastnost určuje, jak dlouho smí být token v mezipaměti. Po uplynutí zadané časové období, token, který se odebere z mezipaměti klienta. Ve výchozím nastavení tokeny uchovávány v mezipaměti po neomezenou dobu. Následující příklad nastaví časový interval na 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Volitelné. Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> na procenta. Výchozí hodnota je 60 (procenta). Tato vlastnost určuje procento doby platnosti tokenu. Například, pokud vydaný token je platný 10 hodin a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> je nastavený na 80, pak tento token se obnovuje po osmi hodinách. Následující příklad nastaví hodnotu až 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interval obnovování určené doby platnosti tokenu a `IssuedTokenRenewalThresholdPercentage` hodnotu přepsat `MaxIssuedTokenCachingTime` hodnoty v případech, kdy je kratší než doba obnovení prahové hodnoty doby ukládání do mezipaměti. Například pokud součin `IssuedTokenRenewalThresholdPercentage` a doba trvání tokenu je 8 hodin a `MaxIssuedTokenCachingTime` hodnota je 10 minut, klient kontaktů služby tokenů zabezpečení pro aktualizovaný token každých 10 minut.  
  
5. Pokud v režimu entropie klíče jiných než <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> vyžaduje vazbu, která použijte zabezpečení zpráv nebo zabezpečení s přihlašovacími údaji zprávy přenosu (např. nemá vazbu <xref:System.ServiceModel.Channels.SecurityBindingElement>), můžete nastavit <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost na odpovídající hodnotu. *Entropie* režim určuje, zda symetrické klíče se dá řídit pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost. Toto výchozí nastavení je <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, ve kterém klienta a vydavatel tokenu zadat data, která se spojí dohromady a vytvoří skutečné klíč. Jiné hodnoty nejsou <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> a <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, což znamená, že celý klíč je určená klienta nebo serveru, v uvedeném pořadí. Následující příklad nastaví vlastnost na hodnotu pro klíč použít pouze data ze serveru.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Pokud <xref:System.ServiceModel.Channels.SecurityBindingElement> je součástí služby tokenů zabezpečení nebo vazby služby <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> nastavit na <xref:System.ServiceModel.Security.IssuedTokenClientCredential> přepsán <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> vlastnost `SecurityBindingElement`.  
  
6. Konfigurace neovlivní žádné chování, koncový bod specifický pro vystavitele jejich přidáním do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Ke konfiguraci IssuedTokenClientCredential v konfiguraci  
  
1. Vytvoření [ \<třídy issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element jako podřízený objekt [ \<třídy issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) prvek chování koncového bodu.  
  
2. Pokud token ukládání do mezipaměti není vyžadována, nastavte `cacheIssuedTokens` atribut (z <`issuedToken`> element) k `false`.  
  
3. Pokud časový limit je vyžadováno na tokeny v mezipaměti, nastavte `maxIssuedTokenCachingTime` atribut na <`issuedToken`> element na odpovídající hodnotu. Příklad:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Pokud jinou hodnotu než výchozí, je nastavit `issuedTokenRenewalThresholdPercentage` atribut na <`issuedToken`> element na odpovídající hodnotu, například:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Pokud v režimu entropie klíče jiných než `CombinedEntropy` je u vazby, která provádí zabezpečení zpráv nebo přenos zabezpečení s přihlašovacími údaji zprávy (například nemá vazbu `SecurityBindingElement`), nastavte `defaultKeyEntropyMode` atribut na `<issuedToken>` Element buď `ServerEntropy` nebo `ClientEntropy` podle potřeby.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Volitelné. Nakonfigurujte všechna vlastní koncový bod vydavatele konkrétní chování tak, že vytvoříte <`issuerChannelBehaviors`> jako podřízený element <`issuedToken`> element. Každý chování pro vytvoření <`add`> jako podřízený element <`issuerChannelBehaviors`> element. Zadejte adresu vystavitele chování tak, že nastavíte `issuerAddress` atribut na <`add`> element. Určete chování, samotný nastavením `behaviorConfiguration` atribut na <`add`> element.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Ke konfiguraci X509CertificateRecipientClientCredential v kódu  
  
1. Přístup <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy nebo <xref:System.ServiceModel.ChannelFactory> vlastnost.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance je k dispozici pro certifikát pro daný koncový bod, použijte <xref:System.Collections.Generic.ICollection%601.Add%2A> metoda kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance není k dispozici, použijte <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> třídy, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Ke konfiguraci X509CertificateRecipientClientCredential v konfiguraci  
  
1. Vytvoření [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) element jako podřízený objekt [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element, který je sám podřízeným prvkem [ \< třídu clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) prvek chování koncového bodu.  
  
2. Vytvoření `<add>` element jako podřízený objekt `<scopedCertificates>` elementu. Zadejte hodnoty `storeLocation`, `storeName`, `x509FindType`, a `findValue` atributy odkazovat na příslušný certifikát. Nastavte `targetUri` atributu na hodnotu, která obsahuje adresu koncového bodu, který certifikát se použije pro, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"   
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu konfiguruje instance <xref:System.ServiceModel.Security.IssuedTokenClientCredential> třídu v kódu.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Abyste zabránili odhalení informací je to možné, klienti, na kterých běží nástroje Svcutil.exe pro zpracování metadat z koncových bodů federované by měl zajistili výsledný adresy služby tokenů zabezpečení co očekávat. To je zvlášť důležité při služby tokenů zabezpečení zveřejňuje několik koncových bodů, protože generuje výsledný konfigurační soubor pro první použití nástroje Svcutil.exe takové koncový bod, který nemusí být jeden klient by měl používat.  
  
## <a name="localissuer-required"></a>LocalIssuer vyžaduje  
 Pokud se očekává, že klienti vždy používejte lokálního vystavitele, pamatujte na Tyhle věci: Výchozí výstup Svcutil.exe za následek nepoužití, pokud služba tokenů zabezpečení druhé poslední v řetězci určuje adresa vydavatele nebo adresa vystavitele metadat lokálního vystavitele.  
  
 Další informace o nastavení <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnosti <xref:System.ServiceModel.Security.IssuedTokenClientCredential> najdete v tématu [jak: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Vymezených certifikátů  
 Pokud certifikáty služby musí být zadána pro komunikaci se žádné služby tokenů zabezpečení, obvykle vzhledem k tomu, že certifikát vyjednávání se nepoužívá, mohou být určeny pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> třídy. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Přijímá metodu <xref:System.Uri> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> jako parametry. Zadaný certifikát se používá při komunikaci s koncovými body se zadaným identifikátorem URI. Alternativně můžete použít <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> způsob, jak přidat certifikát na kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost.  
  
> [!NOTE]
>  Nápad klientských certifikátů, která jsou omezená na daný identifikátor URI se vztahuje jenom na aplikace, které jsou odchozích volání služeb, které zpřístupňují koncové body na tyto identifikátory URI. Nevztahuje se na certifikáty, které se používají k podepisování vydaných tokenů, například nakonfigurovaným na serveru v kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy. Další informace najdete v tématu [jak: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Postupy: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
