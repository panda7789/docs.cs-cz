---
title: 'Postupy: Určení hodnot přihlašovacích údajů klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: a1b2627c8e9899a122f27dc652f8c91230fed0b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225128"
---
# <a name="how-to-specify-client-credential-values"></a>Postupy: Určení hodnot přihlašovacích údajů klienta
Pomocí služby Windows Communication Foundation (WCF), služby můžete zadat jak ověření klienta ke službě. Služba může například stanovit, ověření klienta pomocí certifikátu.  
  
### <a name="to-determine-the-client-credential-type"></a>K určení typu pověření klienta  
  
1.  Načítání metadat z koncových bodů metadat služby. Metadata se obvykle skládá z dva soubory: kód klienta v programovacím jazyce podle vašeho výběru (výchozí hodnota je vizuál C#) a konfigurační soubor XML. Jedním ze způsobů načítání metadat je použití nástroje Svcutil.exe k vrácení kódu klienta a konfigurace klienta. Další informace najdete v tématu [načítání metadat](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  Otevřete konfigurační soubor XML. Pokud pomocí nástroje Svcutil.exe výchozí název souboru je Output.config.  
  
3.  Najít  **\<zabezpečení >** křížkem **režimu** atribut (**< režim zabezpečení =** `MessageOrTransport` **>** kde `MessageOrTransport` nastavená na jeden z režimů zabezpečení.  
  
4.  Najdete podřízený prvek, který se shoduje s hodnotou režimu. Například, pokud je nastavené na **zpráva**, Najít  **\<zpráva >** obsažených v elementu  **\<zabezpečení >** elementu.  
  
5.  Poznamenejte si hodnotu přiřazenou **nebyl typ clientCredentialType** atribut. Skutečná hodnota závisí na režimu, který se používá, přenos nebo zprávy.  
  
 Následující kód XML ukazuje konfigurace pro klienta vyžaduje certifikát zabezpečení zpráv a k ověření klienta.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Příklad: Režim přenosu protokolu TCP s certifikátem jako pověření klienta  
 Tento příklad nastaví režim zabezpečení na režim přenosu a nastaví hodnoty přihlašovacích údajů klienta do certifikátu X.509. Následující postupy ukazují, jak nastavit hodnoty přihlašovacích údajů klienta na straně klienta v kódu a konfigurace. Předpokladem je, že jste použili [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vrátit metadata (kódu a konfigurace) ze služby. Další informace najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>K určení hodnoty přihlašovacích údajů klienta v klientském počítači v kódu  
  
1.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování kódu a konfigurace ze služby.  
  
2.  Vytvořte instanci klienta WCF pomocí generovaného kódu.  
  
3.  Třída klienta nastavena <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy na odpovídající hodnotu. Tento příklad nastaví vlastnost na objekt pomocí certifikátu X.509 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Můžete použít některý z výčtech <xref:System.Security.Cryptography.X509Certificates.X509FindType> třídy. V názvu subjektu je zde použita v případě, že certifikát se změní (z důvodu datum vypršení platnosti). Použití názvu předmětu umožňuje infrastrukturu tak, aby znovu najít certifikát.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>K určení hodnoty přihlašovacích údajů klienta v klientském počítači v konfiguraci  
  
1.  Přidat [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
2.  Přidat [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu. Nezapomeňte nastavit požadovaný `name` atribut na odpovídající hodnotu.  
  
3.  Přidat [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
4.  Nastavte na odpovídající hodnoty následující atributy: `storeLocation`, `storeName`, `x509FindType`, a `findValue`, jak je znázorněno v následujícím kódu. Další informace o certifikátech najdete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
  
5.  Při konfiguraci klienta, zadejte chování tak, že nastavíte `behaviorConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu. Element koncového bodu je podřízeným prvkem [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elementu. Také, zadejte název konfigurace vazby, tak, že nastavíte `bindingConfiguration` atribut vazby pro klienta. Pokud používáte generované konfiguračního souboru, název vazby není automaticky vygenerován. V tomto příkladu je název `"tcpBindingWithCredential"`.  
  
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
- [Programování zabezpečení WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Výběr typu pověření](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<Zpráva >](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
