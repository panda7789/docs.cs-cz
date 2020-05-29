---
title: 'Postupy: Zabezpečené koncové body metadat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 2746c608fb47b94446c5d7e10748ba185d555e7f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202333"
---
# <a name="how-to-secure-metadata-endpoints"></a>Postupy: Zabezpečené koncové body metadat

Metadata služby můžou obsahovat citlivé informace o vaší aplikaci, které může využívat uživatel se zlými úmysly. Uživatelé vaší služby můžou také vyžadovat zabezpečený mechanismus pro získání metadat služby. Z tohoto důvodu je někdy nutné publikovat metadata pomocí zabezpečeného koncového bodu.

Koncové body metadat jsou obecně zabezpečeny pomocí standardních mechanismů zabezpečení definovaných v Windows Communication Foundation (WCF) pro zabezpečení koncových bodů aplikace. Další informace najdete v tématu [Přehled zabezpečení](security-overview.md).

Toto téma vás provede kroky pro vytvoření koncového bodu zabezpečeného certifikátem SSL (Secure Sockets Layer) (SSL) nebo jinými slovy koncového bodu HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Vytvoření koncového bodu metadat GET pro zabezpečený protokol HTTPS v kódu

1. Nakonfigurujte port s příslušným certifikátem X. 509. Certifikát musí pocházet z důvěryhodné autority a musí mít zamýšlené použití autorizace služby. K připojení certifikátu k portu je nutné použít nástroj HttpCfg. exe. Informace najdete v tématu [How to: Configure a port with a Certificate SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Předmět certifikátu nebo jeho DNS (Domain Name System) se musí shodovat s názvem počítače. To je nezbytné, protože jeden z prvních kroků mechanismu protokolu HTTPS provede ověření, že certifikát je vydán pro stejný identifikátor URI (Uniform Resource Identifier) jako adresa, na které je vyvolána.

2. Vytvořte novou instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.

3. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy na `true` .

4. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnost na příslušnou adresu URL. Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem `https://` . Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS. Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.

5. Přidejte instanci do kolekce chování, kterou <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> vrátí vlastnost třídy, jak je znázorněno v následujícím kódu.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Vytvoření koncového bodu metadat získat zabezpečený protokol HTTPS v konfiguraci

1. Přidejte [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element do [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) prvku konfiguračního souboru pro vaši službu.

2. Přidejte [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element do [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.

3. Přidejte [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do `<serviceBehaviors>` elementu.

4. Nastavte `name` atribut `<behavior>` prvku na odpovídající hodnotu. `name` Atribut je vyžadován. Následující příklad používá hodnotu `mySvcBehavior` .

5. Přidejte [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.

6. Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` elementu na `true` .

7. Nastavte `httpsGetUrl` atribut `<serviceMetadata>` prvku na odpovídající hodnotu. Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem `https://` . Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS. Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.

8. Chcete-li použít chování se službou, nastavte `behaviorConfiguration` atribut [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu na hodnotu atributu name elementu behavior. Následující konfigurační kód ukazuje kompletní příklad.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a>Příklad

Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá koncový bod. Kód pak vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti pro vytvoření zabezpečeného bodu výměny metadat.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Příklad kódu používá následující obory názvů:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
