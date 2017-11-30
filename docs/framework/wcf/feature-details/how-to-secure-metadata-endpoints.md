---
title: "Postupy: Zabezpečené koncové body metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e28b4dec851cc4115c2688540ebee151c91e4cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-secure-metadata-endpoints"></a>Postupy: Zabezpečené koncové body metadat
Metadata pro služby mohou obsahovat citlivé údaje o vaší aplikaci, které můžete využít uživatel se zlými úmysly. Příjemci vaší služby také může vyžadovat zabezpečené mechanismus pro získání metadat o služby. Někdy je proto potřeba publikovat metadata pomocí zabezpečený koncový bod.  
  
 Koncové body metadat jsou obecně zabezpečené pomocí mechanismů standardní zabezpečení, které jsou definované v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro zabezpečení koncových bodů aplikace. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Toto téma vás provede kroky k vytvoření koncového bodu zabezpečeny certifikát Secure Sockets Layer (SSL) nebo jinými slovy, koncový bod HTTPS.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Chcete-li vytvořit zabezpečený protokol HTTPS získat metadata koncový bod v kódu  
  
1.  Nakonfigurujte port se příslušný certifikát X.509. Certifikát musí pocházet ze důvěryhodnou autoritou a musí mít zamýšlené použití souboru "Autorizace služby." Musíte použít nástroj HttpCfg.exe připojit certifikát na port. V tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Předmět certifikátu nebo jeho systému DNS (Domain Name) musí odpovídat názvu počítače. Toto je nezbytné, protože jeden z první kroky, které provádí mechanismus HTTPS je zkontrolovat, že je certifikát vystavený k stejný identifikátor URI (Uniform Resource) jako adresu, na kterém je volána.  
  
2.  Vytvořit novou instanci třídy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy.  
  
3.  Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy k `true`.  
  
4.  Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnost příslušnou adresu URL. Všimněte si, že pokud zadáte adresu absolutní, adresa URL musí začínat řetězcem schématu "https://". Pokud zadáte adresu relativní, je třeba zadat základní adresu HTTPS pro svého hostitele služby. Pokud není tato vlastnost určena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.  
  
5.  Přidat do kolekce chování instanci, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceDescription> třídy vrátí, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Chcete-li vytvořit zabezpečený protokol HTTPS získat metadata koncový bod v konfiguraci  
  
1.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu, který chcete [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element konfiguračního souboru pro vaši službu.  
  
2.  Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu, který chcete [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.  
  
3.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu, který chcete `<serviceBehaviors>` elementu.  
  
4.  Nastavte `name` atribut `<behavior>` element na odpovídající hodnotu. `name` Atribut je vyžadován. Následující příklad používá hodnotu `mySvcBehavior`.  
  
5.  Přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) k `<behavior>` elementu.  
  
6.  Nastavte `httpsGetEnabled` atribut `<serviceMetadata>` element `true`.  
  
7.  Nastavte `httpsGetUrl` atribut `<serviceMetadata>` element na odpovídající hodnotu. Všimněte si, že pokud zadáte adresu absolutní, adresa URL musí začínat řetězcem schématu "https://". Pokud zadáte adresu relativní, je třeba zadat základní adresu HTTPS pro svého hostitele služby. Pokud není tato vlastnost určena, výchozí adresa je "", nebo přímo na základní adrese HTTPS pro službu.  
  
8.  Chcete-li použít chování službou, nastavte `behaviorConfiguration` atribut [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) prvku na hodnotu atribut názvu prvku chování. Následující kód konfigurace ukazuje kompletní příklad.  
  
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
 Následující příklad vytvoří instanci <xref:System.ServiceModel.ServiceHost> a přidává koncový bod. Kód vytvoří instanci <xref:System.ServiceModel.Description.ServiceMetadataBehavior> třídy a nastaví vlastnosti, které chcete vytvořit bod zabezpečené metadata exchange.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu používá následujících oborů názvů:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Postupy: Konfigurace portu certifikát protokolu SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Aspekty zabezpečení s metadaty](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
