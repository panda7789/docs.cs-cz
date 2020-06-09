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
ms.openlocfilehash: 47e59452edfff74daf17d94a058ce8b12af7867c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593539"
---
# <a name="how-to-create-a-federated-client"></a>Postupy: Vytvoření federovaného klienta
V Windows Communication Foundation (WCF) se vytváření klienta pro *federované služby* skládá ze tří hlavních kroků:  
  
1. Nakonfigurujte [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo podobnou vlastní vazbu. Další informace o vytváření příslušné vazby naleznete v tématu [How to: Create a WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md). Případně můžete spustit [Nástroj pro DoSvcutilování metadat (ServiceModel. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) na koncový bod metadat federované služby a vygenerovat konfigurační soubor pro komunikaci se službou federované služby a jednou nebo více službami tokenů zabezpečení.  
  
2. Nastavte vlastnosti ovládacího <xref:System.ServiceModel.Security.IssuedTokenClientCredential> prvku, který řídí různé aspekty interakce klienta se službou tokenů zabezpečení.  
  
3. Nastavte vlastnosti <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> , které umožňují zabezpečenou komunikaci s danými koncovými body, jako jsou třeba služby tokenů zabezpečení.  
  
> [!NOTE]
> <xref:System.Security.Cryptography.CryptographicException>Může být vyvolána, když klient použije zosobněná pověření, <xref:System.ServiceModel.WSFederationHttpBinding> vazbu nebo vlastní token vydaný pomocí a asymetrické klíče. Asymetrické klíče se používají spolu s <xref:System.ServiceModel.WSFederationHttpBinding> tokeny s vazbou a vlastním vydanými <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> , pokud jsou vlastnosti a v uvedeném pořadí nastaveny na <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey> . Vyvolá se, <xref:System.Security.Cryptography.CryptographicException> když se klient pokusí odeslat zprávu a profil uživatele neexistuje pro identitu, kterou klient zosobňuje. Chcete-li tento problém zmírnit, přihlaste se ke klientskému počítači nebo zavolejte `LoadUserProfile` před odesláním zprávy.  
  
 V tomto tématu najdete podrobné informace o těchto postupech. Další informace o vytváření příslušné vazby naleznete v tématu [How to: Create a WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md). Další informace o tom, jak federované služba funguje, najdete v tématu [federace](federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Generování a kontrola konfigurace federované služby  
  
1. Spusťte [Nástroj pro DoSvcutilí metadat (ServiceModel. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) s adresou URL metadat služby jako parametr příkazového řádku.  
  
2. Otevřete generovaný konfigurační soubor v příslušném editoru.  
  
3. Prověřte atributy a obsah všech generovaných [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) a [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) elementů. Ty jsou umístěny v rámci [\<security>](../../configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) prvků pro [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) prvky nebo vlastní prvky vazby. Zajistěte, aby adresy obsahovaly očekávané názvy domén nebo jiné informace o adrese. Tyto informace je důležité ověřit, protože se klient ověřuje na těchto adresách a může zveřejnit informace, jako jsou dvojice uživatelského jména a hesla. Pokud adresa není očekávanou adresou, může to mít za následek zpřístupnění informací nezamýšlenému příjemci.  
  
4. Prověřte všechny další [\<issuedTokenParameters>](../../configure-apps/file-schema/wcf/issuedtokenparameters.md) prvky uvnitř komentáře <`alternativeIssuedTokenParameters`> elementu. Při použití nástroje Svcutil. exe ke generování konfigurace pro federované služby, pokud federační služba nebo jakékoli služby zprostředkujícího tokenu zabezpečení neurčí adresu vystavitele, ale místo toho určíte adresu metadat pro službu tokenu zabezpečení, která zveřejňuje více koncových bodů, výsledný konfigurační soubor odkazuje na první koncový bod. Další koncové body jsou v konfiguračním souboru jako <> prvky s poznámkou `alternativeIssuedTokenParameters` .  
  
     Určete, zda je jeden z těchto <`issuedTokenParameters`> výhodnější pro tu, která je již přítomna v konfiguraci. Například klient může upřednostňovat ověřování ve službě tokenů zabezpečení pomocí tokenu služby Windows CardSpace místo dvojice uživatelského jména a hesla.  
  
    > [!NOTE]
    > Aby bylo možné před komunikací se službou procházet více služeb tokenů zabezpečení, je možné, že služba zprostředkujícího tokenu zabezpečení směruje klienta na nesprávnou službu tokenu zabezpečení. Proto zajistěte, aby byl koncový bod služby tokenu zabezpečení v rozhraní [\<issuedTokenParameters>](../../configure-apps/file-schema/wcf/issuedtokenparameters.md) očekávanou službou tokenu zabezpečení a neznámou službou tokenu zabezpečení.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Konfigurace IssuedTokenClientCredential v kódu  
  
1. Přístup k <xref:System.ServiceModel.Security.IssuedTokenClientCredential> <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnostem <xref:System.ServiceModel.Description.ClientCredentials> třídy (vrácená <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastností <xref:System.ServiceModel.ClientBase%601> třídy nebo prostřednictvím <xref:System.ServiceModel.ChannelFactory> třídy), jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Pokud není vyžadována mezipaměť tokenu, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> vlastnost na hodnotu `false` . <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A>Vlastnost určuje, zda jsou tyto tokeny ze služby tokenu zabezpečení uloženy v mezipaměti. Pokud je tato vlastnost nastavená na `false` , klient si vyžádá nový token ze služby tokenu zabezpečení, kdykoli se musí znovu ověřit pro federované služby, bez ohledu na to, jestli je předchozí token stále platný. Pokud je tato vlastnost nastavená na `true` , klient znovu použije existující token, kdykoli se musí znovu ověřit pro federované služby (Pokud platnost tokenu nevypršela). Výchozí formát je `true`.  
  
3. Je-li pro tokeny uložené v mezipaměti vyžadován časový limit, nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> vlastnost na <xref:System.TimeSpan> hodnotu. Vlastnost určuje, jak dlouho může být token uložen do mezipaměti. Po uplynutí zadaného časového rozsahu se token odebere z mezipaměti klienta. Ve výchozím nastavení jsou tokeny ukládány do mezipaměti po neomezenou dobu. Následující příklad nastaví časový rozsah na 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Nepovinný parametr. Nastavte na <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> procento. Výchozí hodnota je 60 (procento). Vlastnost určuje procento doby platnosti tokenu. Pokud je například vydaný token platný po dobu 10 hodin a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> je nastaven na 80, pak se token obnoví po osmi hodinách. Následující příklad nastaví hodnotu na 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interval obnovování stanovený obdobím platnosti tokenu a `IssuedTokenRenewalThresholdPercentage` hodnota je přepsána `MaxIssuedTokenCachingTime` hodnotou v případech, kdy je doba ukládání do mezipaměti kratší než prahová hodnota doby obnovení. Pokud je například produkt `IssuedTokenRenewalThresholdPercentage` a doba trvání tokenu osm hodin a `MaxIssuedTokenCachingTime` hodnota je 10 minut, klient kontaktuje službu tokenu zabezpečení na aktualizovaný token každých 10 minut.  
  
5. Je-li pro <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> vazbu, která nepoužívá zabezpečení zpráv nebo zabezpečení přenosu s přihlašovacími údaji zprávy, vyžadován jiný režim entropie (například). Vazba nemá a <xref:System.ServiceModel.Channels.SecurityBindingElement> ), nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> vlastnost na odpovídající hodnotu. Režim *entropie* určuje, zda lze pomocí vlastnosti ovládat symetrické klíče <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> . Toto je výchozí nastavení <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> , kde klient i Vystavitel tokenů poskytují data, která jsou kombinována, aby vytvořila skutečný klíč. Další hodnoty jsou <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> a <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy> , což znamená, že je celý klíč specifikován klientem nebo serverem. Následující příklad nastaví vlastnost tak, aby pro klíč používala pouze data serveru.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Pokud <xref:System.ServiceModel.Channels.SecurityBindingElement> je přítomen ve službě tokenu zabezpečení nebo ve vazbě služby, je <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> sada nastavena na <xref:System.ServiceModel.Security.IssuedTokenClientCredential> přepsána <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> vlastností třídy `SecurityBindingElement` .  
  
6. Nakonfiguruje všechna chování koncových bodů specifická pro vystavitele jejich přidáním do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> vlastností.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Konfigurace IssuedTokenClientCredential v konfiguraci  
  
1. Vytvořte [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element jako podřízený [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) prvek elementu v chování koncového bodu.  
  
2. Pokud není vyžadována mezipaměť tokenu, nastavte `cacheIssuedTokens` atribut (<`issuedToken`> elementu) na `false` .  
  
3. Je-li pro tokeny uložené v mezipaměti vyžadován časový limit, nastavte `maxIssuedTokenCachingTime` atribut `issuedToken` prvku <> na odpovídající hodnotu. Například:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Pokud upřednostňujete jinou hodnotu než výchozí, nastavte `issuedTokenRenewalThresholdPercentage` atribut `issuedToken` prvku <> na odpovídající hodnotu, například:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Pokud je klíč entropie jiný než `CombinedEntropy` ve vazbě, která nepoužívá zabezpečení zpráv nebo zabezpečení přenosu, s přihlašovacími údaji zprávy (například vazba nemá `SecurityBindingElement` ), nastavte `defaultKeyEntropyMode` atribut `<issuedToken>` prvku na buď `ServerEntropy` nebo `ClientEntropy` podle potřeby.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Nepovinný parametr. Nakonfigurujte jakékoli chování vlastního koncového bodu specifického pro vystavitele vytvořením `issuerChannelBehaviors` prvku <> jako podřízeného `issuedToken` prvku <>. Pro každé chování vytvořte <`add`> prvek jako podřízenou položku `issuerChannelBehaviors` prvku <>. Určete adresu vystavitele chování nastavením `issuerAddress` atributu u `add` prvku <>. Určete chování samotné nastavením `behaviorConfiguration` atributu <`add`> elementu.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Konfigurace X509CertificateRecipientClientCredential v kódu  
  
1. Přístup k vlastnostem <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnosti <xref:System.ServiceModel.ClientBase%601> třídy nebo <xref:System.ServiceModel.ChannelFactory> Vlastnosti.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> je pro daný koncový bod k dispozici instance pro certifikát, použijte <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu kolekce vrácenou <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastností.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Pokud <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> instance není k dispozici, použijte <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodu třídy, jak je <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> znázorněno v následujícím příkladu.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Konfigurace X509CertificateRecipientClientCredential v konfiguraci  
  
1. Vytvořte [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) prvek jako podřízený [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) prvek prvku, který je podřízeným prvkem [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) prvku v chování koncového bodu.  
  
2. Vytvořte `<add>` prvek jako podřízený `<scopedCertificates>` prvek elementu. Zadejte hodnoty pro `storeLocation` atributy, `storeName` , `x509FindType` a, `findValue` aby odkazovaly na příslušný certifikát. Nastavte `targetUri` atribut na hodnotu, která poskytuje adresu koncového bodu, pro který se má certifikát použít, jak je znázorněno v následujícím příkladu.  
  
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
 Následující ukázka kódu nakonfiguruje instanci <xref:System.ServiceModel.Security.IssuedTokenClientCredential> třídy v kódu.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Aby se zabránilo možnému zpřístupnění informací, klienti, kteří spouštějí nástroj Svcutil. exe pro zpracování metadat z federovaných koncových bodů, by měli mít jistotu, že výsledné adresy služby tokenu zabezpečení jsou očekávané. To je obzvláště důležité, když služba tokenů zabezpečení zveřejňuje několik koncových bodů, protože nástroj Svcutil. exe vygeneruje výsledný konfigurační soubor pro použití prvního tohoto koncového bodu, který nemusí být ten, který by měl být používán klientem.  
  
## <a name="localissuer-required"></a>Požadováno LocalIssuer  
 Pokud se očekává, že klienti budou vždycky používat místní vystavitele, pamatujte na následující: výchozí výstup Svcutil. exe využije při použití místního vystavitele, pokud má druhá-poslední služba tokenů zabezpečení v řetězci název vystavitele nebo adresa metadat vystavitele.  
  
 Další informace o nastavení <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastností, a naleznete v <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential> tématu [How to: Configure a Local vystavitele](how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Vymezené certifikáty  
 Pokud musí být pro komunikaci se všemi službami tokenů zabezpečení zadány certifikáty služeb, obvykle protože vyjednávání certifikátů není používáno, lze je zadat pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnosti <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> třídy. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A>Metoda přijímá <xref:System.Uri> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> parametry a jako. Zadaný certifikát se používá při komunikaci s koncovými body na zadaném identifikátoru URI. Alternativně můžete použít <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodu k přidání certifikátu do kolekce vrácené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastností.  
  
> [!NOTE]
> Klientská představu o certifikátech, které jsou v oboru daného identifikátoru URI, platí pouze pro aplikace, které provádějí odchozí volání služeb, které zveřejňují koncové body v těchto identifikátorech URI. Nevztahuje se na certifikáty, které se používají k podepsání vystavených tokenů, jako jsou ty, které jsou nakonfigurované na serveru v kolekci vrácené <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídou. Další informace najdete v tématu [Postup: konfigurace přihlašovacích údajů na služba FS (Federation Service)](how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázka federace](../samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Konfigurace místního vystavitele](how-to-configure-a-local-issuer.md)
- [Informace o zabezpečení metadat](security-considerations-with-metadata.md)
- [Postupy: Zabezpečené koncové body metadat](how-to-secure-metadata-endpoints.md)
