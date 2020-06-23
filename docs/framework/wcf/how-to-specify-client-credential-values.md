---
title: 'Postupy: Zadání hodnot přihlašovacích údajů klienta'
description: Přečtěte si, jak může služba WCF určit, jak se má klient ověřit pro tuto službu. Tento příklad určuje certifikát X. 509 a režim přenosu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244449"
---
# <a name="how-to-specify-client-credential-values"></a>Postupy: Zadání hodnot přihlašovacích údajů klienta

Pomocí Windows Communication Foundation (WCF) může služba určit, jak bude klient ověřený ke službě. Například služba může určit, že se má klient ověřit pomocí certifikátu.

## <a name="to-determine-the-client-credential-type"></a>Určení typu pověření klienta

1. Načtěte metadata z koncového bodu metadat služby. Metadata se typicky skládají ze dvou souborů: kód klienta v programovacím jazyce podle vašeho výběru (výchozí nastavení je Visual C#) a konfigurační soubor XML. Jedním ze způsobů, jak načíst metadata, je použít nástroj Svcutil.exe k vrácení kódu klienta a konfigurace klienta. Další informace najdete v tématu [načtení metadat](./feature-details/retrieving-metadata.md) a [Nástroj pro nástroj pro metadata ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Otevřete konfigurační soubor XML. Použijete-li nástroj Svcutil.exe, je výchozí název souboru Output.config.

3. Vyhledejte **\<security>** element s atributem **Mode** ( **\<security mode =**`MessageOrTransport`**>** kde `MessageOrTransport` je nastaven na jeden z režimů zabezpečení.

4. Najděte podřízený element, který odpovídá hodnotě Mode. Například pokud je režim nastaven na **zprávy**, najděte **\<message>** element obsažený v **\<security>** elementu.

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

Tento příklad nastaví režim zabezpečení na transportní režim a nastaví hodnotu přihlašovacích údajů klienta na certifikát X. 509. Následující postupy ukazují, jak nastavit hodnotu přihlašovacích údajů klienta v klientovi v kódu a konfiguraci. To předpokládá, že jste použili nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) k vrácení metadat (kódu a konfigurace) ze služby. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Určení hodnoty přihlašovacích údajů klienta na klientovi v kódu

1. K vygenerování kódu a konfigurace ze služby použijte nástroj pro dodané [metadata (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) .

2. Vytvořte instanci klienta WCF pomocí vygenerovaného kódu.

3. Na klientské třídě nastavte <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy na odpovídající hodnotu. Tento příklad nastaví vlastnost na certifikát X. 509 pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Můžete použít kterýkoli z výčtů <xref:System.Security.Cryptography.X509Certificates.X509FindType> třídy. Název subjektu se tady používá pro případ změny certifikátu (kvůli datu vypršení platnosti). Použití názvu subjektu umožní infrastruktuře znovu najít certifikát.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Určení hodnoty přihlašovacích údajů klienta v konfiguraci klienta

1. Přidejte [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.

2. Přidejte [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu. Nezapomeňte nastavit požadovaný `name` atribut na odpovídající hodnotu.

3. Přidejte [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element do [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elementu.

4. Nastavte následující atributy na příslušné hodnoty: `storeLocation` , `storeName` , a `x509FindType` `findValue` , jak je znázorněno v následujícím kódu. Další informace o certifikátech najdete v tématu [práce s certifikáty](./feature-details/working-with-certificates.md).

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

5. Při konfiguraci klienta Určete chování nastavením `behaviorConfiguration` atributu `<endpoint>` prvku, jak je znázorněno v následujícím kódu. Element Endpoint je podřízeným prvkem [\<client>](../configure-apps/file-schema/wcf/client.md) elementu. Také zadejte název konfigurace vazby nastavením `bindingConfiguration` atributu na vazbu pro klienta. Pokud používáte generovaný konfigurační soubor, automaticky se vygeneruje název vazby. V tomto příkladu je název `"tcpBindingWithCredential"` .

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Programování zabezpečení WCF](./feature-details/programming-wcf-security.md)
- [Výběr typu přihlašovacích údajů](./feature-details/selecting-a-credential-type.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Práce s certifikáty](./feature-details/working-with-certificates.md)
- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
