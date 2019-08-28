---
title: 'Postupy: Zabezpečené koncové body metadat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c6439187560e15ec10f1eea4e1731421904e8643
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045285"
---
# <a name="how-to-secure-metadata-endpoints"></a>Postupy: Zabezpečené koncové body metadat

Metadata služby můžou obsahovat citlivé informace o vaší aplikaci, které může využívat uživatel se zlými úmysly. Uživatelé vaší služby můžou také vyžadovat zabezpečený mechanismus pro získání metadat služby. Z tohoto důvodu je někdy nutné publikovat metadata pomocí zabezpečeného koncového bodu.

Koncové body metadat jsou obecně zabezpečeny pomocí standardních mechanismů zabezpečení definovaných v Windows Communication Foundation (WCF) pro zabezpečení koncových bodů aplikace. (Další informace najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md).)

Toto téma vás provede kroky pro vytvoření koncového bodu zabezpečeného certifikátem SSL (Secure Sockets Layer) (SSL) nebo jinými slovy koncového bodu HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Vytvoření koncového bodu metadat GET pro zabezpečený protokol HTTPS v kódu

1. Nakonfigurujte port s příslušným certifikátem X. 509. Certifikát musí pocházet z důvěryhodné autority a musí mít zamýšlené použití autorizace služby. K připojení certifikátu k portu je nutné použít nástroj HttpCfg. exe. Viz [jak: Konfigurace portu s certifikátem](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)SSL.

    > [!IMPORTANT]
    > Předmět certifikátu nebo jeho DNS (Domain Name System) se musí shodovat s názvem počítače. To je nezbytné, protože jeden z prvních kroků mechanismu protokolu HTTPS provede ověření, že certifikát je vydán pro stejný identifikátor URI (Uniform Resource Identifier) jako adresa, na které je vyvolána.

2. Vytvořte novou instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.

3. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> Nastavte vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy na `true`.

4. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Nastavte vlastnost na příslušnou adresu URL. Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem "https://". Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS. Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.

5. Přidejte instanci do kolekce chování, kterou <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vrátí vlastnost <xref:System.ServiceModel.Description.ServiceDescription> třídy, jak je znázorněno v následujícím kódu.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Vytvoření koncového bodu metadat získat zabezpečený protokol HTTPS v konfiguraci

1. Do prvku [System. ServiceModel > konfiguračního souboru pro vaši službu přidejte > chování. \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

2. Do prvku [> chovánípřidejteprvekserviceBehaviors>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)

3. `<serviceBehaviors>` [ Přidejte\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu do elementu.

4. `name` Nastavte atribut `<behavior>` prvku na odpovídající hodnotu. `name` Atribut je vyžadován. Následující příklad používá hodnotu `mySvcBehavior`.

5. Přidejte [> oddílu serviceMetadata k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) `<behavior>`

6. Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` elementu `true`.

7. `httpsGetUrl` Nastavte atribut `<serviceMetadata>` prvku na odpovídající hodnotu. Všimněte si, že pokud zadáte absolutní adresu, adresa URL musí začínat schématem "https://". Pokud zadáte relativní adresu, musíte pro hostitele služby zadat základní adresu HTTPS. Není-li tato vlastnost nastavena, je použita výchozí adresa "" nebo přímo na základní adrese HTTPS pro službu.

8. Chcete-li použít chování se službou, nastavte `behaviorConfiguration` atribut [ \<> elementu Service](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) na hodnotu atributu name elementu behavior. Následující konfigurační kód ukazuje kompletní příklad.

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

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
