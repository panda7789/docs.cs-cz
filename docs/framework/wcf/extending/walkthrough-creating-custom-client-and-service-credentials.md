---
title: 'Návod: Vytvoření vlastního klienta a pověření služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: b78aca1942ea5535a9c6c0f028972243dd512500
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635648"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Návod: Vytvoření vlastního klienta a pověření služby
Toto téma ukazuje, jak implementovat vlastní klienta a pověření služby a jak pomocí vlastních přihlašovacích údajů z kódu aplikace.  
  
## <a name="credentials-extensibility-classes"></a>Přihlašovací údaje rozšíření třídy  
 <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy jsou hlavní vstupní body k rozšiřitelnosti zabezpečení Windows Communication Foundation (WCF). Tyto přihlašovací údaje třídy poskytují rozhraní API, která umožňují kód aplikace, pokud chcete nastavit přihlašovací údaje a převést typy přihlašovacích údajů do tokenů zabezpečení. (*Tokeny zabezpečení* se formulář, který slouží k přenosu přihlašovací údaje uvnitř zprávy protokolu SOAP.) Odpovědnosti tyto přihlašovací údaje třídy je možné rozdělit do dvou oblastí:  
  
- Poskytuje rozhraní API pro aplikace se nastavit přihlašovací údaje.  
  
- Provést jako objekt factory pro <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.  
  
 Jak <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy dědí z abstraktní <xref:System.ServiceModel.Security.SecurityCredentialsManager> třídu, která definuje smlouvu pro návrat <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 Výchozí implementace k dispozici ve službě WCF podporují typy poskytované systémem přihlašovacích údajů a vytvoření zabezpečení Správce tokenů, který je schopen zpracování těchto typů přihlašovacích údajů.  
  
## <a name="reasons-to-customize"></a>Důvody pro přizpůsobení  
 Existuje několik důvodů, proč přizpůsobení tříd přihlašovacích údajů klienta nebo služby. Musíme je potřeba změnit výchozí chování zabezpečení WCF z hlediska zpracování přihlašovací údaje poskytnuté systémem typů, hlavně z následujících důvodů:  
  
- Změny, které nejsou možné pomocí jiné body rozšíření.  
  
- Přidání nových typů přihlašovacích údajů.  
  
- Přidání nové vlastní bezpečnostní token typy.  
  
 Toto téma popisuje, jak implementovat vlastní klienta a pověření služby a jak se dají použít v kódu aplikace.  
  
## <a name="first-in-a-series"></a>První z řady  
 Vytvoření třídy vlastní přihlašovací údaje je jenom prvním krokem, protože je důvod pro přizpůsobení přihlašovací údaje ke změně chování WCF týkající se zřizování přihlašovací údaje, serializaci tokenu zabezpečení nebo ověřování. Další témata v této části popisují, jak vytvořit vlastní serializátory a ověřovací data. Vytvoření vlastních přihlašovacích údajů třídy v tomto ohledu je první téma v řadě. Následné akce (vytváření vlastní serializátory a ověřovací data) můžete udělat jenom po vytvoření vlastních přihlašovacích údajů. Další témata, které vycházejí z tohoto tématu patří:  
  
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
- [Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
- [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-implement-custom-client-credentials"></a>K implementaci vlastních klientských přihlašovacích údajů  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Description.ClientCredentials> třídy.  
  
2. Volitelné. Přidáte nové metody nebo vlastnosti pro nové typy přihlašovacích údajů. Pokud nepřidáte nové typy přihlašovacích údajů, tento krok přeskočte. Následující příklad přidá `CreditCardNumber` vlastnost.  
  
3. Přepsat <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Tato metoda je automaticky volána Infrastruktura zabezpečení WCF při použití vlastních klientských přihlašovacích údajů. Tato metoda je zodpovědný za vytváření a vrací instanci implementaci <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.  
  
    > [!IMPORTANT]
    >  Je důležité si uvědomit, že <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> je metoda potlačena za účelem vytvoření vlastní bezpečnostní správce tokenů. Správce tokenů zabezpečení, odvozený z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, musí vracet vlastního zprostředkovatele tokenů zabezpečení, odvozený z <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, k vytvoření tohoto tokenu zabezpečení. Pokud nepostupujte podle tohoto vzoru pro vytváření tokenů zabezpečení, může vaše aplikace fungovat správně při <xref:System.ServiceModel.ChannelFactory> objekty jsou uložené v mezipaměti (což je výchozí chování pro proxy klienta WCF), potenciálně výsledkem zvýšení oprávnění. Objekt vlastní přihlašovací údaje se uloží do mezipaměti jako součást <xref:System.ServiceModel.ChannelFactory>. Nicméně vlastní <xref:System.IdentityModel.Selectors.SecurityTokenManager> se vytvoří v každé volání, což snižuje riziko zneužití ohrožení zabezpečení, tak dlouho, dokud token vytvoření logiky, nachází ve <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4. Přepsat <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metody.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>K implementaci správce tokenů zabezpečení vlastního klienta  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace se musí vytvořit. Další informace o poskytovatelích vlastní bezpečnostní token, naleznete v tématu [jak: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementace se musí vytvořit. Další informace o ověřovací data tokenu zabezpečení vlastní najdete v tématu [jak: Vytvořit ověřovací data tokenu zabezpečení vlastní](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musí být vytvořeny. Další informace o zabezpečení vlastních tokenů a vlastní bezpečnostní token serializátory najdete v tématu [jak: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Použití vlastního klienta přihlašovacích údajů z kódu aplikace  
  
1. Vytvořte instanci generovaného klienta, který představuje rozhraní služby nebo vytvoření instance <xref:System.ServiceModel.ChannelFactory> odkazuje na službu chcete komunikovat.  
  
2. Odebrat přihlašovací údaje chování klient poskytovaný systémem než <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, která je přístupná prostřednictvím <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost.  
  
3. Vytvořit novou instanci třídy přihlašovací údaje vlastního klienta a přidat ji do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, která je přístupná prostřednictvím <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Předchozí postup ukazuje, jak použít přihlašovací údaje klienta z kódu aplikace. Přihlašovací údaje WCF lze konfigurovat taky pomocí konfiguračního souboru aplikace. Pomocí konfigurace aplikace je často vhodnější pevnému zakódování protože umožňuje úpravy parametry aplikace bez nutnosti upravovat zdroje, opětovné kompilace a opětovné nasazení.  
  
 Následující postup popisuje, jak poskytovat podporu pro konfiguraci vlastních přihlašovacích údajů.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Vytvoření obslužné rutiny konfiguračního pro přihlašovací údaje vlastního klienta  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2. Volitelné. Přidání vlastnosti pro všechny další konfigurační parametry, které chcete zveřejnit prostřednictvím konfigurace aplikace. Následující příklad přidá jednu vlastnost s názvem `CreditCardNumber`.  
  
3. Přepsat <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> vlastnost má být vrácen typ vlastního klienta přihlašovacích údajů třídy vytvořené pomocí konfiguračního elementu.  
  
4. Přepsat <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metody. Metoda je zodpovědný za vytváření a vrací instanci třídy vlastních přihlašovacích údajů na základě nastavení načíst z konfiguračního souboru. Volání základní <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> z tuto metodu za účelem nastavení přihlašovacích údajů poskytované systémem načíst metodu načtení do vaší instance vlastního klienta přihlašovacích údajů.  
  
5. Volitelné. Pokud jste přidali další vlastnosti v kroku 2, je nutné přepsat <xref:System.Configuration.ConfigurationElement.Properties%2A> vlastnost-li se zaregistrovat další konfigurační nastavení pro rozhraní konfigurace rozpoznány. Kombinovat vlastnosti s vlastnostmi základní třídy umožňující poskytované systémem nastavení, které se dá nakonfigurovat přes tento prvek konfigurace vlastních klientských přihlašovacích údajů.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Jakmile budete mít konfigurační třídě obslužné rutiny, je možné integrovat do rozhraní konfigurace WCF. Jak je znázorněno v následujícím postupu, který umožňuje přihlašovací údaje vlastního klienta použitého v elementech chování koncového bodu klienta.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>K registraci a používání vlastního klienta přihlašovacích údajů obslužné rutiny konfiguračního v konfiguraci aplikace  
  
1. Přidat <`extensions`> element a <`behaviorExtensions`> element do konfiguračního souboru.  
  
2. Přidat <`add`> element <`behaviorExtensions`> element a nastavte `name` atribut na odpovídající hodnotu.  
  
3. Nastavte `type` atribut plně kvalifikovaný název typu. Zahrnují také název sestavení a dalších atributů sestavení.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4. Po registraci vaší obslužné rutiny konfiguračního elementu vlastní přihlašovací údaje lze použít ve stejném konfiguračním souboru místo poskytnuté systémem <`clientCredentials`> element. Můžete použít vlastnosti poskytované systémem a všechny nové vlastnosti, které jste přidali do vaší konfigurace implementaci obslužné rutiny. Následující příklad nastaví hodnotu vlastní vlastnosti pomocí `creditCardNumber` atribut.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>K implementaci vlastní službu pověření  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2. Volitelné. Přidání nových vlastností k zadání nových hodnot přihlašovacích údajů, které se přidávají rozhraní API. Pokud nepřidáte nový přihlašovací údaj hodnoty, tento krok přeskočte. Následující příklad přidá `AdditionalCertificate` vlastnost.  
  
3. Přepsat <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Tato metoda je automaticky volána infrastruktura WCF při použití vlastních klientských přihlašovacích údajů. Metoda je zodpovědný za vytváření a vrací instanci implementaci <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy (popsaný v dalším postupu).  
  
4. Volitelné. Přepsat <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metody. To je potřeba, pouze pokud přidat nové vlastnosti nebo interní pole k implementaci vlastních klientských přihlašovacích údajů.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>K implementaci vlastní službu Správce tokenů zabezpečení  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy.  
  
2. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace se musí vytvořit. Další informace o poskytovatelích vlastní bezpečnostní token, naleznete v tématu [jak: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementace se musí vytvořit. Další informace o ověřovací data tokenu zabezpečení vlastní najdete v tématu [jak: Vytvořit vlastní ověřovací data tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tématu.  
  
4. Volitelné. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metodu, pokud vlastní <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musí být vytvořeny. Další informace o zabezpečení vlastních tokenů a vlastní bezpečnostní token serializátory najdete v tématu [jak: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Pomocí přihlašovacích údajů vlastní službu od kódu aplikace  
  
1. Vytvoření instance <xref:System.ServiceModel.ServiceHost>.  
  
2. Odebrat chování přihlašovací údaje služby poskytované systémem od <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce.  
  
3. Vytvořit novou instanci třídy pověření vlastní služby a přidejte ji tak <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Přidání podpory pro konfiguraci pomocí kroků popsaných dříve v postupech "`To create a configuration handler for custom client credentials`"a"`To register and use a custom client credentials configuration handler in the application configuration`." Jediným rozdílem je použít <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> místo na třídě <xref:System.ServiceModel.Configuration.ClientCredentialsElement> třídu jako základní třída pro obslužnou rutinu konfigurace. Element vlastní služby přihlašovací údaje pak lze použít všude, kde poskytovaných systémem `<serviceCredentials>` element se používá.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
