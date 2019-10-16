---
title: 'Postupy: Zadání hodnot přihlašovacích údajů klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319853"
---
# <a name="how-to-specify-client-credential-values"></a>Postupy: Zadání hodnot přihlašovacích údajů klienta

Pomocí Windows Communication Foundation (WCF) může služba určit, jak bude klient ověřený ke službě. Například služba může určit, že se má klient ověřit pomocí certifikátu.

## <a name="to-determine-the-client-credential-type"></a>Určení typu pověření klienta

1. Načtěte metadata z koncového bodu metadat služby. Metadata se typicky skládají ze dvou souborů: kód klienta v programovacím jazyce podle vašeho výběru (výchozí je vizuál C#) a konfigurační soubor XML. Jedním ze způsobů, jak načíst metadata, je použít nástroj Svcutil. exe k vrácení kódu klienta a konfigurace klienta. Další informace najdete v tématu [načtení metadat](./feature-details/retrieving-metadata.md) a [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Otevřete konfigurační soubor XML. Použijete-li nástroj Svcutil. exe, výchozí název souboru je Output. config.

3. Vyhledejte **> prvek \<security** s atributem **Mode** ( **\<security mode =** `MessageOrTransport` **>** , kde `MessageOrTransport` je nastaveno na jeden z režimů zabezpečení.

4. Najděte podřízený element, který odpovídá hodnotě Mode. Například pokud je režim nastaven na **zprávy**, vyhledejte **> prvek \<message** obsažený v elementu **> \<security** .

5. Poznamenejte si hodnotu přiřazenou atributu **ClientCredentialType** . Skutečná hodnota závisí na použitém režimu, přenosu nebo zprávě.

Následující kód XML ukazuje konfiguraci klienta pomocí zabezpečení zpráv a vyžádání certifikátu pro ověření klienta.

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Příklad: režim přenosu TCP s certifikátem jako přihlašovací údaje klienta

Tento příklad nastaví režim zabezpečení na transportní režim a nastaví hodnotu přihlašovacích údajů klienta na certifikát X. 509. Následující postupy ukazují, jak nastavit hodnotu přihlašovacích údajů klienta v klientovi v kódu a konfiguraci. To předpokládá, že jste použili nástroj pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který vrací metadata (kód a konfiguraci) ze služby. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Určení hodnoty přihlašovacích údajů klienta na klientovi v kódu

1. K vygenerování kódu a konfigurace ze služby použijte nástroj pro dodané [metadata (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) .

2. Vytvořte instanci klienta WCF pomocí vygenerovaného kódu.

3. Na klientské třídě nastavte vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> třídy <xref:System.ServiceModel.ClientBase%601> na odpovídající hodnotu. Tento příklad nastaví vlastnost na certifikát X. 509 pomocí metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> třídy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Můžete použít kterýkoli z výčtů třídy <xref:System.Security.Cryptography.X509Certificates.X509FindType>. Název subjektu se tady používá pro případ změny certifikátu (kvůli datu vypršení platnosti). Použití názvu subjektu umožní infrastruktuře znovu najít certifikát.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Určení hodnoty přihlašovacích údajů klienta v konfiguraci klienta

1. Přidejte prvek [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do prvku [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .

2. Přidejte prvek [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) do prvku [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) . Nezapomeňte nastavit požadovaný atribut `name` na odpovídající hodnotu.

3. Přidejte prvek [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) do prvku [> \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) .

4. Nastavte následující atributy na příslušné hodnoty: `storeLocation`, `storeName`, `x509FindType` a `findValue`, jak je znázorněno v následujícím kódu. Další informace o certifikátech najdete v tématu [práce s certifikáty](./feature-details/working-with-certificates.md).

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. Při konfiguraci klienta Určete chování nastavením atributu `behaviorConfiguration` prvku `<endpoint>`, jak je znázorněno v následujícím kódu. Element Endpoint je podřízeným prvkem prvku [\<client >](../configure-apps/file-schema/wcf/client.md) . Také zadejte název konfigurace vazby nastavením atributu `bindingConfiguration` na vazbu pro klienta. Pokud používáte generovaný konfigurační soubor, automaticky se vygeneruje název vazby. V tomto příkladu je název `"tcpBindingWithCredential"`.

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Programování zabezpečení WCF](./feature-details/programming-wcf-security.md)
- [Výběr typu přihlašovacích údajů](./feature-details/selecting-a-credential-type.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Práce s certifikáty](./feature-details/working-with-certificates.md)
- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
- [@no__t – 1netTcpBinding >](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [@no__t – 1security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [@no__t – 1message >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [@no__t – 1behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [@no__t – 1behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
- [@no__t – 1clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [@no__t – 1clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)
