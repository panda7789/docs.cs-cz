---
title: 'Postupy: Vytvoření federovaného klienta'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 38436a83bf58c4903a931ecafebf922800d230c1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-federated-client"></a>Postupy: Vytvoření federovaného klienta
V [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], vytvoření klienta pro *Federovaná služba* zahrnuje tři hlavní kroky:  
  
1.  Konfigurace [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo podobné vlastní vazby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] vytváření odpovídající vazby, najdete v části [postupy: vytvoření třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternativně spusťte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na koncový bod metadat federované služby pro generování konfigurační soubor pro komunikaci s federované služby a jeden nebo více služby tokenů zabezpečení.  
  
2.  Nastavit vlastnosti <xref:System.ServiceModel.Security.IssuedTokenClientCredential> která řídí různé aspekty klienta interakci s služby tokenů zabezpečení.  
  
3.  Nastavit vlastnosti <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, což umožňuje certifikáty, které jsou potřebné k bezpečné komunikaci s danou koncových bodů, například služby tokenů zabezpečení.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> mohou být vyvolány, pokud klient používá zosobněnou přihlašovací údaje, <xref:System.ServiceModel.WSFederationHttpBinding> vazba nebo vydala vlastní token a asymetrické klíče. Asymetrické klíče se používají s <xref:System.ServiceModel.WSFederationHttpBinding> vazby a vlastní vystavené tokeny, kdy <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> a <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> vlastností, jsou nastavenými na hodnoty <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> Se vyvolá, když se klient pokusí odeslat zprávu a neexistuje uživatelský profil pro identitu, který zosobňuje klienta. Ke zmírnění tohoto problému, přihlaste se k počítači klienta nebo volání `LoadUserProfile` před odesláním zprávy.  
  
 Toto téma obsahuje podrobné informace o těchto postupů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] vytváření odpovídající vazby, najdete v části [postupy: vytvoření třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Jak funguje federované služby, najdete v části [Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Generovat a zkontrolujte konfiguraci pro federované služby  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s adresou URL adresu metadat služby jako parametr příkazového řádku.  
  
2.  Vygenerovaný konfigurační soubor otevřete v editoru vhodné.  
  
3.  Podívejte se na atributy a obsahu všech generované [ \<vystavitele >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) a [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementy. Tyto se nacházejí v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) prvky pro [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo vlastní vazby elementy. Ujistěte se, že adresy obsahovat názvy očekávané domény nebo Další informace o adrese. Je důležité zkontrolovat tyto informace, protože klient přihlásí k tyto adresy a poskytnout informace, jako je párů jméno a heslo uživatele. Pokud adresa není očekávaný adresu, to může vést ke zpřístupnění informací nezamýšleným příjemce.  
  
4.  Zkontrolujte všechny další [ \<– issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementy uvnitř komentáři out <`alternativeIssuedTokenParameters`> elementu. Při použití nástroje Svcutil.exe pro generování konfigurace pro federované služby, pokud služba federované nebo žádné služby tokenu zabezpečení zprostředkující nezadávejte adresu vystavitele, ale spíš zadejte adresu metadat pro služby tokenů zabezpečení, která zveřejňuje víc koncových bodů, bude výsledný soubor konfigurace odkazuje na první koncový bod. Další koncové body jsou v konfiguračním souboru jako komentované <`alternativeIssuedTokenParameters`> elementy.  
  
     Určení, zda se jeden z těchto <`issuedTokenParameters`> je vhodnější než jedna již existuje v konfiguraci. Například nastavit klienta tak, aby ověření systému Windows pomocí služby tokenů zabezpečení [!INCLUDE[infocard](../../../../includes/infocard-md.md)] tokenu místo pár uživatelské jméno a heslo.  
  
    > [!NOTE]
    >  Kde nutné více služby tokenů zabezpečení projít před komunikaci se službou, je možné služby tokenů zabezpečení zprostředkující k nasměrovat klienta služby tokenů zabezpečení nesprávné. Proto zajistěte, aby koncový bod pro služby tokenů zabezpečení v [ \<– issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) služby tokenů zabezpečení očekávané a není neznámé zabezpečení tokenu služby.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Ke konfiguraci IssuedTokenClientCredential v kódu  
  
1.  Přístup <xref:System.ServiceModel.Security.IssuedTokenClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost <xref:System.ServiceModel.Description.ClientCredentials> – třída (vrácený <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy, nebo pomocí <xref:System.ServiceModel.ChannelFactory> – třída), jak ukazuje následující příklad kódu.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  Pokud token ukládání do mezipaměti není potřeba, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> vlastnost `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Vlastnosti ovládacích prvků, jestli tyto tokeny od zabezpečení token služby jsou uložené v mezipaměti. Pokud je tato vlastnost nastavena na `false`, klient požádá o nový token ze služby tokenů zabezpečení vždy, když se musí znovu prokázal svojí totožnost federované služby, bez ohledu na to zda předchozí token je stále platný. Pokud je tato vlastnost nastavena na `true`, klient opětovně používá existující token vždy, když se musí znovu prokázal svojí totožnost federované služby (Pokud je nevypršela platnost tokenu). Výchozí hodnota je `true`.  
  
3.  Pokud časový limit je potřeba na uložené v mezipaměti tokeny, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> vlastnosti <xref:System.TimeSpan> hodnotu. Vlastnost určuje, jak dlouho může být token do mezipaměti. Po uplynutí zadané časové období, token odeberou z mezipaměti klienta. Ve výchozím nastavení tokeny jsou uložené v mezipaměti po neomezenou dobu. Následující příklad nastaví časový interval na 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  Volitelné. Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> na procentuální hodnotu. Výchozí hodnota je 60 (v procentech). Tato vlastnost určuje procento doby platnosti tokenu. Například, pokud je vystavený token je platný 10 hodin a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> nastavený na 80, pak token byl obnoven po osmi hodinách. Následující příklad nastaví hodnotu až 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interval obnovování dáno doba platnosti tokenu a `IssuedTokenRenewalThresholdPercentage` je hodnotu přepsat `MaxIssuedTokenCachingTime` hodnota v případech, kdy je kratší než doba obnovení prahová hodnota doby ukládání do mezipaměti. Například pokud produkt `IssuedTokenRenewalThresholdPercentage` a doba trvání je token je 8 hodin a `MaxIssuedTokenCachingTime` hodnota je 10 minut, klient kontaktuje služby tokenů zabezpečení pro aktualizovaný token každých 10 minut.  
  
5.  Pokud režimu entropie klíče jinak než <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> je potřeba na vazbu, která nemá používat zabezpečení zpráv nebo přenosu zabezpečení s přihlašovacími údaji zprávu (např. nemá vazbu <xref:System.ServiceModel.Channels.SecurityBindingElement>), můžete nastavit <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost na odpovídající hodnotu. *Entropie* režim určuje, zda symetrické klíče se dá řídit pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost. Toto výchozí nastavení je <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, kde klient a vydavatel tokenu zadat data, která je k vytvoření klíče, skutečný kombinaci. Další hodnoty jsou <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> a <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, což znamená, že celý klíč je určený klienta nebo serveru, v uvedeném pořadí. Následující příklad nastaví vlastnosti pro klíč použít pouze dat serveru.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Pokud <xref:System.ServiceModel.Channels.SecurityBindingElement> je k dispozici v služby tokenů zabezpečení nebo vazby služby <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> nastavit na <xref:System.ServiceModel.Security.IssuedTokenClientCredential> je přepsat <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> vlastnost `SecurityBindingElement`.  
  
6.  Konfigurovat žádné koncový bod vystavitele konkrétní chování jejich přidáním do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Nakonfigurovat IssuedTokenClientCredential v konfiguraci  
  
1.  Vytvoření [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) jako podřízený element [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element v chování koncového bodu.  
  
2.  Pokud token ukládání do mezipaměti není potřeba, nastavte `cacheIssuedTokens` atribut (z <`issuedToken`> element) k `false`.  
  
3.  Pokud časový limit je potřeba na uložené v mezipaměti tokeny, nastavte `maxIssuedTokenCachingTime` atributu u <`issuedToken`> elementu na odpovídající hodnotu. Příklad:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  Upřednostňuje-li jinou hodnotu než výchozí, nastavte `issuedTokenRenewalThresholdPercentage` atributu u <`issuedToken`> elementu na odpovídající hodnotu, např.:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  Pokud režimu entropie klíče jinak než `CombinedEntropy` na vazbu, která nemá zabezpečení zpráv nebo přenos zabezpečení s pověřením zpráv (například nemá vazbu `SecurityBindingElement`), nastavte `defaultKeyEntropyMode` atributu u `<issuedToken>` Element buď `ServerEntropy` nebo `ClientEntropy` podle potřeby.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  Volitelné. Nakonfigurujte všechny vlastní koncový bod vystavitele konkrétní chování vytvořením <`issuerChannelBehaviors`> jako podřízený element <`issuedToken`> elementu. Pro každý chování vytvořit <`add`> jako podřízený element <`issuerChannelBehaviors`> elementu. Zadejte adresu vystavitele chování nastavením `issuerAddress` atributu u <`add`> elementu. Určete chování, samotné nastavením `behaviorConfiguration` atributu u <`add`> elementu.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Ke konfiguraci X509CertificateRecipientClientCredential v kódu  
  
1.  Přístup <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy nebo <xref:System.ServiceModel.ChannelFactory> vlastnost.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance je k dispozici pro certifikát pro daný koncový bod, použijte <xref:System.Collections.Generic.ICollection%601.Add%2A> metoda kolekce vrácené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance není k dispozici, použijte <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> třídy, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Nakonfigurovat X509CertificateRecipientClientCredential v konfiguraci  
  
1.  Vytvoření [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) jako podřízený element [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element, který je sám podřízeným [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element v chování koncového bodu.  
  
2.  Vytvoření `<add>` jako podřízený element `<scopedCertificates>` elementu. Zadejte hodnoty pro `storeLocation`, `storeName`, `x509FindType`, a `findValue` atributy odkazovat na příslušný certifikát. Nastavte `targetUri` atributu na hodnotu, která poskytuje adresu koncového bodu, který certifikát má být použita, jak je znázorněno v následujícím příkladu.  
  
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
 Následující ukázka kódu nakonfiguruje instanci <xref:System.ServiceModel.Security.IssuedTokenClientCredential> – třída v kódu.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Aby se zabránilo možné přístup k informacím, by měl klientů, kteří jsou spuštění nástroje Svcutil.exe zpracovat metadata z federované koncových bodů zajistěte, aby byly výsledné adresy služby tokenů zabezpečení, co očekávat. To je zvlášť důležité při služby tokenů zabezpečení zpřístupňuje několik koncových bodů, protože nástroje Svcutil.exe generuje výsledný soubor konfigurace použít první takové koncový bod, který nemusí být ten by měl klient používat.  
  
## <a name="localissuer-required"></a>LocalIssuer vyžaduje  
 Pokud klienti budou vždy nutné použít místního vystavitele, vezměte na vědomí následující: Výchozí výstup výsledků Svcutil.exe v místního vystavitele nepoužívala Pokud služby tokenů zabezpečení sekundu poslední v řetězu určuje vystavitele adresy nebo adresu metadat vystavitele.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] nastavení <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnosti <xref:System.ServiceModel.Security.IssuedTokenClientCredential> třídy najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Vymezená certifikáty  
 Pokud certifikáty služby musí být určeny pro komunikaci s žádným z služby tokenu zabezpečení, obvykle vyjednávání certifikátu není používán, že je možné zadat pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> třídy. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Metoda trvá <xref:System.Uri> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> jako parametry. Zadaný certifikát se používá při komunikaci s koncovými body na zadaný identifikátor URI. Alternativně můžete použít <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metoda přidat certifikát do kolekce vrácené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost.  
  
> [!NOTE]
>  Rada klientských certifikátů, která jsou omezená na daný identifikátor URI platí jenom pro aplikace, které jsou odchozí volání ke službám, které zveřejňují koncových bodů na tyto identifikátory URI. Nevztahuje se na certifikáty, které se používají k podpisu vystavené tokeny, například nakonfigurovaným na serveru v kolekci vrácené <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy. Další informace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Postupy: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
