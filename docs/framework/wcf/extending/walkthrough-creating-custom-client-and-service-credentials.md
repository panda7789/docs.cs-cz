---
title: "Návod: Vytvoření vlastního klienta a pověření služby"
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
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99ee624ef6198ed67141d3d92e63fb9ba815c4fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Návod: Vytvoření vlastního klienta a pověření služby
Toto téma ukazuje, jak implementovat vlastní klienta a pověření služby a jak používat vlastní pověření z kódu aplikace.  
  
## <a name="credentials-extensibility-classes"></a>Přihlašovací údaje rozšíření třídy  
 <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy jsou hlavní vstupní body k [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] rozšiřitelnost zabezpečení. Tyto přihlašovací údaje třídy poskytují rozhraní API, které umožňují kódu aplikace, pokud chcete nastavit přihlašovací údaje informace a pro převod typů přihlašovacích údajů do tokenů zabezpečení. (*Tokeny zabezpečení* jsou formulář, který slouží k předání přihlašovacích údajů uvnitř protokolu SOAP zprávy.) Odpovědnosti tyto přihlašovací údaje třídy je možné rozdělit do dvou oblastech:  
  
-   Poskytují rozhraní API pro aplikace, nastavení informací o přihlašovací údaje.  
  
-   Provést jako objekt factory pro <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.  
  
 Jak <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy dědí z abstraktní <xref:System.ServiceModel.Security.SecurityCredentialsManager> třídu, která definuje kontrakt pro návrat <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]třídy přihlašovací údaje a jak je začlenit do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Architektura zabezpečení, najdete v části [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 Výchozí implementace součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporovat typy poskytované systémem přihlašovacích údajů a vytvořit token správce, který je schopen zpracování těchto typů pověření zabezpečení.  
  
## <a name="reasons-to-customize"></a>Důvody k přizpůsobení  
 Existuje několik důvodů pro přizpůsobení tříd pověření klienta nebo služby. Přední je potřeba změnit výchozí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování bezpečnostních s ohledem na zpracování typy poskytované systémem přihlašovacích údajů, hlavně pro z následujících důvodů:  
  
-   Změny, které nejsou možné pomocí jiné body rozšíření.  
  
-   Přidávání nových typů přihlašovacích údajů.  
  
-   Přidání nové typy tokenů vlastní zabezpečení.  
  
 Toto téma popisuje, jak implementovat vlastní klienta a pověření služby a jak je používat z kódu aplikace.  
  
## <a name="first-in-a-series"></a>První ze série  
 Vytvoření třídy vlastní pověření je jenom první krok, protože důvod pro přizpůsobení přihlašovacích údajů je změna [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chování týkající se zřizování přihlašovací údaje, serializace tokenu zabezpečení nebo ověřování. Další témata v této části popisují, jak vytvořit vlastní serializátorů a ověřovací data. Vytvoření vlastní pověření třídy v tomto ohledu je první téma v řadě. Následující akce (vytváření vlastní serializátorů a ověřovací data) lze provést pouze po vytvoření vlastní pověření. Další témata, která vycházejí v tomto tématu:  
  
-   [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-implement-custom-client-credentials"></a>K implementaci vlastních klientských pověření  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Description.ClientCredentials> třídy.  
  
2.  Volitelné. Přidáte nové metody nebo vlastnosti pro nové typy přihlašovacích údajů. Pokud je nemůžete přidat nové typy přihlašovacích údajů, tento krok přeskočte. Následující příklad přidá `CreditCardNumber` vlastnost.  
  
3.  Přepsání <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda. Tato metoda je volána automaticky [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpečení, pokud je použita pověření vlastní klienta. Tato metoda je odpovědná za vytváření a vrací instanci třídy implementaci <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.  
  
    > [!IMPORTANT]
    >  Je důležité si uvědomit, že <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> je metoda potlačena za účelem vytvoření vlastní zabezpečení Správce tokenu. Správce tokenu zabezpečení, odvozené od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, musí vracet poskytovatele tokenu zabezpečení vlastní, odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, k vytvoření tohoto tokenu zabezpečení. Pokud nepostupujte podle tohoto vzoru pro vytváření tokenů zabezpečení, může vaše aplikace fungovat správně při <xref:System.ServiceModel.ChannelFactory> objekty jsou uložené v mezipaměti (což je výchozí chování pro proxy klienta WCF), potenciálně výsledné ke zvýšení oprávnění. Vlastní pověření objekt se uloží do mezipaměti jako součást <xref:System.ServiceModel.ChannelFactory>. Však vlastní <xref:System.IdentityModel.Selectors.SecurityTokenManager> je vytvořen v každé volání, které minimalizují ohrožení zabezpečení, dokud logice vytvoření tokenu je umístěn v <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Přepsání <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metoda.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>K implementaci správce tokenů zabezpečení vlastního klienta  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]poskytovatelé tokenů vlastní zabezpečení, najdete v části [postupy: vytvoření vlastního poskytovatele tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementace musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vlastní zabezpečovací token ověřovací data, najdete v části [postupy: vytvoření vlastní ověřovací Token zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokeny vlastní zabezpečení a serializátorů tokenu vlastní zabezpečení, najdete v části [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Pokud chcete použít vlastní klienta pověření z kódu aplikace  
  
1.  Vytvořte instanci generovaného klienta, který představuje rozhraní služby nebo vytvořit instanci <xref:System.ServiceModel.ChannelFactory> odkazující na služby chcete komunikovat s.  
  
2.  Odebrat chování klient poskytovaný systémem přihlašovací údaje z <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, který je přístupný prostřednictvím <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost.  
  
3.  Vytvoření nové instance třídy přihlašovací údaje vlastního klienta a přidat ji do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, který je přístupný prostřednictvím <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Předchozí postup ukazuje, jak používat pověření klienta z kódu aplikace. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]přihlašovací údaje můžete konfigurovat taky pomocí konfiguračního souboru aplikace. Pomocí konfigurace aplikace je často vhodnější pevně kódováno protože umožní Změna parametrů aplikace bez nutnosti upravit zdroj, nutnosti rekompilace a opětovné nasazení.  
  
 Následující postup popisuje, jak zajistit podporu pro konfiguraci vlastních přihlašovacích údajů.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Vytvoření konfigurace obslužné rutiny pro přihlašovací údaje vlastního klienta  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  Volitelné. Přidáte vlastnosti pro všechny další konfigurační parametry, které chcete zpřístupnit prostřednictvím konfigurace aplikace. Následující příklad přidá jednu vlastnost s názvem `CreditCardNumber`.  
  
3.  Přepsání <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> vlastnost, která má návratový typ vlastního klienta pověření třídy, které jsou vytvořené pomocí konfiguračního elementu.  
  
4.  Přepsání <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metoda. Metoda odpovídá za vytváření a vrací instanci třídy vlastní pověření na základě nastavení načíst z konfiguračního souboru. Volat základní <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metoda z této metody k načtení nastavení poskytované systémem pověření načíst v instanci vlastního klienta přihlašovací údaje.  
  
5.  Volitelné. Pokud jste přidali další vlastnosti v kroku 2, budete muset přepsat <xref:System.Configuration.ConfigurationElement.Properties%2A> vlastnost k registraci další konfiguraci nastavení pro rozhraní konfigurace rozpoznány. Kombinovat vaší vlastnosti s vlastnostmi základní třída umožňuje konfigurovat prostřednictvím tohoto elementu konfigurace přihlašovacích údajů vlastních klientských nastavení poskytované systémem.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Jakmile máte konfigurační třídě obslužná rutina, lze ji integrovat do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework konfigurace. Umožňující vlastní klienta pověření pro použití v elementech chování klienta koncový bod, jak je vidět v dalším postupu.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>K registraci a pomocí vlastního klienta pověření obslužná rutina konfigurace v konfiguraci aplikace  
  
1.  Přidat <`extensions`> elementu a <`behaviorExtensions`> element konfiguračního souboru.  
  
2.  Přidat <`add`> elementu, který chcete <`behaviorExtensions`> elementu a sadu `name` atribut na odpovídající hodnotu.  
  
3.  Nastavte `type` atribut typu plně kvalifikovaný název. Také zahrnovat název sestavení a další atributy sestavení.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Po registraci vaší konfiguraci obslužné rutiny, dá se použít vlastní pověření element uvnitř stejné konfiguračního souboru místo poskytované systémem <`clientCredentials`> elementu. Můžete použít vlastnosti poskytované systémem a všechny nové vlastnosti, které jste přidali k implementaci obslužné rutiny konfigurace. Následující příklad nastaví hodnotu vlastní vlastnosti pomocí `creditCardNumber` atribut.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>K implementaci pověření vlastní služby  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  Volitelné. Přidání nových vlastností zajistit rozhraní API pro nové hodnoty přihlašovacích údajů, které se přidávají. Pokud je nemůžete přidat nové hodnoty přihlašovacích údajů, tento krok přeskočte. Následující příklad přidá `AdditionalCertificate` vlastnost.  
  
3.  Přepsání <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda. Tato metoda je volána automaticky [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury, když se používá přihlašovací údaje vlastního klienta. Metoda je odpovědná za vytváření a vrací instanci třídy implementaci <xref:System.IdentityModel.Selectors.SecurityTokenManager> – třída (popsaný v dalším postupu).  
  
4.  Volitelné. Přepsání <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metoda. To je potřeba, pouze v případě přidání nových vlastností nebo interní pole pro implementaci vlastního klienta přihlašovací údaje.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>K implementaci vlastní služby Správce tokenů zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy.  
  
2.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]poskytovatelé tokenů vlastní zabezpečení, najdete v části [postupy: vytvoření vlastního poskytovatele tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementace musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vlastní zabezpečovací token ověřovací data, najdete v části [postupy: vytvoření vlastní ověřovací Token zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tématu.  
  
4.  Volitelné. Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metoda Pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musí být vytvořen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokeny vlastní zabezpečení a serializátorů tokenu vlastní zabezpečení, najdete v části [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Použít vlastní služba přihlašovací údaje z kódu aplikace  
  
1.  Vytvoření instance <xref:System.ServiceModel.ServiceHost>.  
  
2.  Odebrat chování přihlašovací údaje služby poskytované systémem z <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce.  
  
3.  Vytvořit novou instanci třídy vlastní služeb, pověření a přidejte ho do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Přidání podpory pro konfiguraci pomocí kroky popsané v postupech "`To create a configuration handler for custom client credentials`"a"`To register and use a custom client credentials configuration handler in the application configuration`." Jediným rozdílem je, používat <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> místo <xref:System.ServiceModel.Configuration.ClientCredentialsElement> jako základní třída pro obslužnou rutinu konfigurace. Element pověření vlastní služby lze použít kdekoli poskytované systémem `<serviceCredentials>` element se používá.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
