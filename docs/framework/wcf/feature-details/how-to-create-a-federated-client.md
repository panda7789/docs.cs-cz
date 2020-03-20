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
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185043"
---
# <a name="how-to-create-a-federated-client"></a>Postupy: Vytvoření federovaného klienta
V systému Windows Communication Foundation (WCF) se vytvoření klienta pro *federovní službu* skládá ze tří hlavních kroků:  
  
1. Nakonfigurujte>[ \<wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo podobnou vlastní vazbu. Další informace o vytvoření vhodné vazby naleznete v [tématu How to: Create a WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Případně spusťte [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proti koncovému bodu metadat federované služby a vygenerujte konfigurační soubor pro komunikaci s federovanou službou a jednou nebo více službami tokenů zabezpečení.  
  
2. Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential> vlastnosti, které řídí různé aspekty interakce klienta se službou tokenů zabezpečení.  
  
3. Nastavte vlastnosti <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, který umožňuje certifikáty potřebné pro bezpečnou komunikaci s danými koncovými body, jako jsou například služby tokenů zabezpečení.  
  
> [!NOTE]
> Může <xref:System.Security.Cryptography.CryptographicException> být vyvolána, když klient používá zosobněné pověření, <xref:System.ServiceModel.WSFederationHttpBinding> vazby nebo vlastní vydaný token a asymetrické klíče. Asymetrické klíče se <xref:System.ServiceModel.WSFederationHttpBinding> používají s tokeny vazby <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> a <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> vlastní vydané tokeny, <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>pokud a vlastnosti, v uvedeném pořadí, jsou nastaveny na . Je <xref:System.Security.Cryptography.CryptographicException> vyvolána, když se klient pokusí odeslat zprávu a profil uživatele neexistuje pro identitu, kterou klient zosobňuje. Chcete-li tento problém zmírnit, přihlaste se ke klientské počítači nebo volání `LoadUserProfile` před odesláním zprávy.  
  
 Toto téma obsahuje podrobné informace o těchto postupech. Další informace o vytvoření vhodné vazby naleznete v [tématu How to: Create a WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Další informace o fungování federované služby naleznete v [tématu Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Generování a zkoumání konfigurace federované služby  
  
1. Spusťte [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s adresou adresy URL metadat služby jako parametr příkazového řádku.  
  
2. Otevřete vygenerovaný konfigurační soubor v příslušném editoru.  
  
3. Zkontrolujte atributy a obsah všech generovaných [ \<vyvolaných vystavitele>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) a [ \<vystavitemetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) prvky. Ty jsou umístěny [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) v rámci>prvků zabezpečení pro [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo vlastní prvky vazby. Ujistěte se, že adresy obsahují očekávané názvy domén nebo jiné informace o adrese. Je důležité zkontrolovat tyto informace, protože klient ověřuje tyto adresy a může zveřejnit informace, jako je například dvojice uživatelského jména a hesla. Pokud adresa není očekávaná adresa, může to mít za následek zpřístupnění informací nezamýšlenému příjemci.  
  
4. Zkontrolujte všechny další `alternativeIssuedTokenParameters` [ \<issuedTokenParameters>prvky](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) uvnitř komentované <> prvek. Při použití nástroje Svcutil.exe ke generování konfigurace pro federovanou službu, pokud federovaná služba nebo jakékoli zprostředkující služby tokenů zabezpečení neurčují adresu vystavittele, ale spíše zadejte adresu metadat pro službu tokenů zabezpečení, která zveřejňuje více koncových bodů, výsledný konfigurační soubor odkazuje na první koncový bod. Další koncové body jsou v konfiguračním souboru jako komentované <`alternativeIssuedTokenParameters`> prvky.  
  
     Zjistěte, zda `issuedTokenParameters` je jedna z těchto <> vhodnější než ta, která je již v konfiguraci k dispozici. Klient může například upřednostňovat ověření služby tokenů zabezpečení pomocí tokenu služby Windows CardSpace před dvojicí uživatelského jména a hesla.  
  
    > [!NOTE]
    > Pokud více služeb tokenů zabezpečení musí být provázána před komunikací se službou, je možné pro zprostředkující token služby zabezpečení nasměrovat klienta na nesprávnou službu tokenu zabezpečení. Proto zajistěte, aby koncový bod pro službu tokenů zabezpečení v [ \<vydanétokenparameters>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) je očekávaná služba tokenu zabezpečení a není neznámá služba tokenu zabezpečení.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Konfigurace pověření klienta IssuedTokenV kódu  
  
1. Přístup <xref:System.ServiceModel.Security.IssuedTokenClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost <xref:System.ServiceModel.Description.ClientCredentials> třídy (vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> vlastností třídy <xref:System.ServiceModel.ChannelFactory> nebo prostřednictvím třídy), jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Pokud ukládání tokenů do mezipaměti <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> není `false`vyžadováno, nastavte vlastnost na . Vlastnost <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> určuje, zda jsou tyto tokeny ze služby tokenů zabezpečení uloženy do mezipaměti. Pokud je tato `false`vlastnost nastavena na , klient požaduje nový token ze služby tokenů zabezpečení vždy, když musí znovu ověřit sám federované služby, bez ohledu na to, zda předchozí token je stále platný. Pokud je tato `true`vlastnost nastavena na , klient znovu použije existující token vždy, když musí znovu ověřit sám federované služby (tak dlouho, dokud platnost tokenu vypršela). Výchozí formát je `true`.  
  
3. Pokud je u tokenů uložených v <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> mezipaměti <xref:System.TimeSpan> vyžadován časový limit, nastavte vlastnost na hodnotu. Vlastnost určuje, jak dlouho může být token uložen do mezipaměti. Po uplynutí zadaného časového rozpětí je token odebrán z mezipaměti klienta. Ve výchozím nastavení jsou tokeny ukládány do mezipaměti po dobu neurčitou. Následující příklad nastaví časové rozpětí na 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Nepovinný parametr. Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> procento. Výchozí hodnota je 60 (procent). Vlastnost určuje procento doby platnosti tokenu. Například pokud vydaný token je platný po <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> dobu 10 hodin a je nastavena na 80, pak token se obnoví po osmi hodinách. Následující příklad nastaví hodnotu na 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interval obnovení určený obdobíplatnosti tokenu `IssuedTokenRenewalThresholdPercentage` a hodnota je `MaxIssuedTokenCachingTime` přepsána hodnotou v případech, kdy je doba ukládání do mezipaměti kratší než doba prahu obnovení. Například pokud součin `IssuedTokenRenewalThresholdPercentage` a trvání tokenu je osm `MaxIssuedTokenCachingTime` hodin a hodnota je 10 minut, klient kontaktuje službu tokenu zabezpečení pro aktualizovaný token každých 10 minut.  
  
5. Pokud režim entropie <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> klíče než je potřeba na vazbu, která nepoužívá zabezpečení zprávy nebo zabezpečení přenosu s pověření zprávy (například. vazba nemá <xref:System.ServiceModel.Channels.SecurityBindingElement>), nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost na příslušnou hodnotu. Režim *entropie určuje,* zda symetrické <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> klíče lze ovládat pomocí vlastnosti. Toto <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>výchozí nastavení je , kde klient i vystavitel tokenu poskytují data, která jsou kombinována k vytvoření skutečného klíče. Ostatní hodnoty <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>jsou a , což znamená, že celý klíč je určen klientem nebo serverem. Následující příklad nastaví vlastnost tak, aby používala pouze data serveru pro klíč.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Pokud <xref:System.ServiceModel.Channels.SecurityBindingElement> a je k dispozici ve službě <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> token <xref:System.ServiceModel.Security.IssuedTokenClientCredential> zabezpečení nebo vazby služby, je nastavena na <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> přepsána vlastnost . `SecurityBindingElement`  
  
6. Nakonfigurujte všechny chování koncového bodu specifické pro <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> vystavitna přidáním do kolekce vrácené vlastností.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Konfigurace pověření klienta IssuedTokenCredential v konfiguraci  
  
1. Vytvořte [ \<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) prvek jako podřízený [ \<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) prvek v chování koncového bodu.  
  
2. Pokud ukládání tokenů do mezipaměti `cacheIssuedTokens` není vyžadováno, nastavte atribut (<`issuedToken`> element) na `false`.  
  
3. Pokud je u tokenů uložených v `maxIssuedTokenCachingTime` mezipaměti vyžadován `issuedToken` časový limit, nastavte atribut na <> prvek na příslušnou hodnotu. Například:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Pokud je preferována jiná než `issuedTokenRenewalThresholdPercentage` výchozí hodnota, `issuedToken` nastavte atribut na <> prvku na příslušnou hodnotu, například:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Pokud režim entropie `CombinedEntropy` klíče než je na vazbu, která nepoužívá zabezpečení zprávy nebo zabezpečení přenosu s `SecurityBindingElement`pověření `defaultKeyEntropyMode` zprávy (například vazba nemá ), nastavte atribut na `<issuedToken>` prvek buď `ServerEntropy` nebo `ClientEntropy` podle potřeby.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Nepovinný parametr. Nakonfigurujte jakékoli chování vlastního koncového `issuerChannelBehaviors` bodu specifické pro vystavitela vytvořením prvku <> jako podřízeného prvku <`issuedToken`>. Pro každé chování vytvořte prvek <`add`> `issuerChannelBehaviors` jako podřízený prvek <>. Zadejte adresu vystavitela chování `issuerAddress` nastavením atributu na <`add`> prvku. Určete samotné chování `behaviorConfiguration` nastavením atributu na elementu <`add`>.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Konfigurace pověření klienta klienta X509CertificateRecipientCredential v kódu  
  
1. Přístup <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> prostřednictvím <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnosti třídy <xref:System.ServiceModel.ClientBase%601> nebo <xref:System.ServiceModel.ChannelFactory> vlastnost.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> je instance k dispozici pro certifikát pro <xref:System.Collections.Generic.ICollection%601.Add%2A> daný koncový bod, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> použijte metodu kolekce vrácené vlastností.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance není k dispozici, použijte metodu <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> třídy, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Konfigurace pověření klienta klienta Klienta X509CertificateClientCredential v konfiguraci  
  
1. Vytvořte [ \<scopedCertificates>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) prvek jako podřízený [ \<prvek serviceCertificate>,](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) který je sám podřízeným prvkem [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) prvek v chování koncového bodu.  
  
2. Vytvořte `<add>` prvek jako podřízený `<scopedCertificates>` prvek. Zadejte hodnoty `storeLocation` `storeName`pro `x509FindType`, `findValue` , a atributy odkazovat na příslušný certifikát. Nastavte `targetUri` atribut na hodnotu, která poskytuje adresu koncového bodu, pro který má být certifikát použit, jak je znázorněno v následujícím příkladu.  
  
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
 Následující ukázka kódu konfiguruje instanci třídy <xref:System.ServiceModel.Security.IssuedTokenClientCredential> v kódu.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li zabránit možnému zpřístupnění informací, klienti, kteří používají nástroj Svcutil.exe pro zpracování metadat z federovaných koncových bodů, by měli zajistit, aby výsledné adresy služby tokenů zabezpečení byly takové, jaké očekávají. To je obzvláště důležité, když služba tokenu zabezpečení zveřejňuje více koncových bodů, protože nástroj Svcutil.exe generuje výsledný konfigurační soubor pro použití prvního takového koncového bodu, který nemusí být ten, který by měl klient používat.  
  
## <a name="localissuer-required"></a>Je vyžadován ošetřátor LocalIssuer.  
 Pokud se očekává, že klienti vždy používají místního vystavittele, všimněte si následujícího: výchozí výstup programu Svcutil.exe má za následek, že místní vystavitel není používán, pokud předposlední služba tokenů zabezpečení v řetězci určuje adresu vystavitela nebo adresu metadat vystavittele.  
  
 Další informace o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>nastavení <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastností <xref:System.ServiceModel.Security.IssuedTokenClientCredential> třídy naleznete v tématu How [to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certifikáty s rozsahem  
 Pokud certifikáty služeb musí být určeny pro komunikaci s některou ze služeb tokenů zabezpečení, obvykle <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> proto, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> že vyjednávání certifikátu není používáno, mohou být určeny pomocí vlastnosti třídy. Metoda <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> trvá <xref:System.Uri> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> a jako parametry. Zadaný certifikát se používá při komunikaci s koncovými body na zadaném identifikátoru URI. Alternativně můžete použít <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodu k přidání certifikátu do <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> kolekce vrácené vlastností.  
  
> [!NOTE]
> Klientská myšlenka certifikátů, které jsou vymezeny na daný identifikátor URI, se vztahuje pouze na aplikace, které provádějí odchozí volání služeb, které zveřejňují koncové body na těchto identifikátorech URI. Nevztahuje se na certifikáty, které se používají k podepisování <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vydaných tokenů, jako <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> jsou například ty, které jsou nakonfigurovány na serveru v kolekci vrácené třídou. Další informace naleznete v [tématu Postup: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Konfigurace místního vystavitele](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Postupy: Zabezpečené koncové body metadat](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
