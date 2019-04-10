---
title: 'Postupy: Zabezpečené koncové body metadat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 8481048dd31652a69f9284a44145bd4abfed89bc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307519"
---
# <a name="how-to-secure-metadata-endpoints"></a>Postupy: Zabezpečené koncové body metadat
Metadata služby mohou obsahovat citlivé údaje o aplikaci, která uživatel se zlými úmysly využívat. Příjemci služby budete možná muset zabezpečené mechanismus pro získání metadat o vaší služby. Proto je někdy nezbytné pro publikování metadata pomocí zabezpečeného koncového bodu.  
  
 Koncové body metadat jsou obecně zabezpečené pomocí mechanismů standard zabezpečení definovaná ve Windows Communication Foundation (WCF) pro zabezpečení koncových bodů aplikace. (Další informace najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Toto téma vás provede kroky k vytvoření koncového bodu zabezpečené pomocí certifikátu vrstvy SSL (Secure Sockets) nebo jinými slovy, koncový bod HTTPS.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Chcete-li vytvořit zabezpečené HTTPS GET koncových bodů metadat v kódu  
  
1. Konfigurace portu s příslušný certifikát X.509. Certifikát musí pocházet od důvěryhodné autority a musí mít zamýšlené použití "Ověřování služby." Musíte použít nástroj HttpCfg.exe připojit certifikát na port. Zobrazit [jak: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Předmět certifikátu nebo jeho systému DNS (Domain Name) musí odpovídat názvu počítače. To je nezbytné, protože jeden z prvních kroků, které provádí mechanismus HTTPS je ke kontrole, jestli se certifikát vydal do stejný identifikátor URI (Uniform Resource) jako adresu, na kterém je vyvolána.  
  
2. Vytvořit novou instanci třídy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.  
  
3. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídu `true`.  
  
4. Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti na příslušné adrese URL. Všimněte si, že pokud zadáte absolutní adresa, adresa URL musí začínat schématem "https://". Pokud zadáte relativní adresu, musíte zadat základní adresu HTTPS pro hostitele vaší služby. Pokud není tato vlastnost nastavena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.  
  
5. Přidání instance kolekce chování, která <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDescription> třídy vrací, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Chcete-li vytvořit zabezpečené HTTPS GET koncových bodů metadat v konfiguraci  
  
1. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element konfiguračního souboru pro vaši službu.  
  
2. Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
3. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu `<serviceBehaviors>` elementu.  
  
4. Nastavte `name` atribut `<behavior>` element na odpovídající hodnotu. `name` Atribut je vyžadován. Následující příklad používá hodnotu `mySvcBehavior`.  
  
5. Přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.  
  
6. Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` elementu `true`.  
  
7. Nastavte `httpsGetUrl` atribut `<serviceMetadata>` element na odpovídající hodnotu. Všimněte si, že pokud zadáte absolutní adresa, adresa URL musí začínat schématem "https://". Pokud zadáte relativní adresu, musíte zadat základní adresu HTTPS pro hostitele vaší služby. Pokud není tato vlastnost nastavena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.  
  
8. Chcete-li používat chování se službou, nastavte `behaviorConfiguration` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) prvku na hodnotu atribut name elementu chování. Následující kód konfigurace ukazuje kompletní příklad.  
  
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
 Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá koncový bod. Kód poté vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti pro vytvoření bod zabezpečené metadata exchange.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu používá následující obory názvů:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Informace o zabezpečení pro metadata](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
