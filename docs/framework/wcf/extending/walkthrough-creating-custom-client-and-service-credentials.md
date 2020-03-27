---
title: 'Návod: Vytvoření vlastního klienta a pověření služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: ddd9f03e26f7a8345f1070715e4877c533c361fb
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345270"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Návod: Vytvoření vlastního klienta a pověření služby

Toto téma ukazuje, jak implementovat vlastní pověření klienta a služby a jak používat vlastní pověření z kódu aplikace.

## <a name="credentials-extensibility-classes"></a>Třídy rozšiřitelnosti pověření

<xref:System.ServiceModel.Description.ClientCredentials> Třídy <xref:System.ServiceModel.Description.ServiceCredentials> a jsou hlavními vstupními body pro rozšiřitelnost zabezpečení Windows Communication Foundation (WCF). Tyto třídy pověření poskytují pravidla API, která umožňují kódu aplikace nastavit informace o pověřeních a převést typy pověření na tokeny zabezpečení. (*Tokeny zabezpečení* jsou formulář používaný k přenosu informací o pověření uvnitř zpráv SOAP.) Odpovědnosti těchto tříd pověření lze rozdělit do dvou oblastí:

- Zadejte api pro aplikace nastavit informace o pověření.

- Proveďte jako <xref:System.IdentityModel.Selectors.SecurityTokenManager> tovární pro implementace.

Výchozí implementace poskytované v WCF podporují typy pověření poskytované systémem a vytvořit správce tokenů zabezpečení, který je schopen zpracovávat tyto typy pověření.

## <a name="reasons-to-customize"></a>Důvody pro přizpůsobení

Existuje několik důvodů pro přizpůsobení tříd pověření klienta nebo služby. Především je požadavek na změnu výchozího chování zabezpečení WCF s ohledem na zpracování typů pověření poskytovaných systémem, zejména z následujících důvodů:

- Změny, které nejsou možné pomocí jiných bodů rozšiřitelnosti.

- Přidání nových typů pověření.

- Přidání nových vlastních typů tokenů zabezpečení.

Toto téma popisuje, jak implementovat vlastní pověření klienta a služby a jak je používat z kódu aplikace.

## <a name="first-in-a-series"></a>První v řadě

Vytvoření vlastní třídy pověření je pouze prvním krokem, protože důvodem pro přizpůsobení pověření je změna chování WCF týkající se zřizování pověření, serializace tokenů zabezpečení nebo ověřování. Další témata v této části popisují, jak vytvořit vlastní serializátory a ověřovatele. V tomto ohledu vytvoření vlastní třídy pověření je první téma v řadě. Následné akce (vytváření vlastních serializátorů a ověřovatelů) lze provést pouze po vytvoření vlastních pověření. Mezi další témata, která vycházejí z tohoto tématu, patří:

- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)

- [Postupy: Vytvoření vlastního ověřovacího modulu tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)

- [Postup: Vytvoření vlastního tokenu](how-to-create-a-custom-token.md).

## <a name="procedures"></a>Procedury

#### <a name="to-implement-custom-client-credentials"></a>Implementace vlastních pověření klienta

1. Definujte novou třídu <xref:System.ServiceModel.Description.ClientCredentials> odvozenou z třídy.

2. Nepovinný parametr. Přidejte nové metody nebo vlastnosti pro nové typy pověření. Pokud nepřidáte nové typy pověření, tento krok přeskočte. Následující příklad přidá `CreditCardNumber` vlastnost.

3. Přepsat metodu. <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> Tato metoda je automaticky volána infrastrukturou zabezpečení WCF při použití vlastního pověření klienta. Tato metoda je zodpovědná za vytvoření a vrácení <xref:System.IdentityModel.Selectors.SecurityTokenManager> instance implementace třídy.

    > [!IMPORTANT]
    > Je důležité si uvědomit, že <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda je přepsána vytvořit vlastní správce tokenů zabezpečení. Správce tokenů zabezpečení odvozený z aplikace <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>musí vrátit vlastního <xref:System.IdentityModel.Selectors.SecurityTokenProvider>zprostředkovatele tokenu zabezpečení odvozeného z aplikace, aby vytvořil skutečný token zabezpečení. Pokud nechcete postupovat tento vzor pro vytváření tokenů zabezpečení, aplikace může fungovat nesprávně při <xref:System.ServiceModel.ChannelFactory> objekty jsou uloženy do mezipaměti (což je výchozí chování pro servery proxy klienta WCF), potenciálně výsledkem zvýšení oprávnění útoku. Vlastní objekt pověření je uložen do <xref:System.ServiceModel.ChannelFactory>mezipaměti jako součást . Vlastní <xref:System.IdentityModel.Selectors.SecurityTokenManager> je však vytvořen na každé vyvolání, což zmírňuje ohrožení zabezpečení tak <xref:System.IdentityModel.Selectors.SecurityTokenManager>dlouho, dokud logika vytváření tokenu je umístěn v .

4. Přepsat metodu. <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A>

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Implementace vlastního správce tokenů zabezpečení klienta

1. Definujte novou třídu <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>odvozenou z .

2. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pokud musí být vytvořena vlastní implementace. Další informace o vlastních zprostředkovatelích tokenů zabezpečení naleznete v [tématu Postup: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md).

3. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pokud musí být vytvořena vlastní implementace. Další informace o vlastních ověřovateteelých tokenech zabezpečení naleznete v [tématu How to: Create a Custom Security Token Authenticator](how-to-create-a-custom-security-token-authenticator.md).

4. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> pokud musí být vytvořen vlastní. Další informace o vlastních tokenech zabezpečení a vlastních serializárů tokenů zabezpečení naleznete v [tématu How to: Create a Custom Token](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Použití vlastních pověření klienta z kódu aplikace

1. Vytvořte instanci generovaného klienta, která představuje rozhraní služby, nebo vytvořte instanci <xref:System.ServiceModel.ChannelFactory> ukazatele na službu, se kterou chcete komunikovat.

2. Odeberte systémová pověření klienta <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> chování z kolekce, které <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> lze přistupovat prostřednictvím vlastnosti.

3. Vytvořte novou instanci třídy pověření vlastního <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> klienta a přidejte ji <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> do kolekce, ke které lze přistupovat prostřednictvím vlastnosti.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Předchozí postup ukazuje, jak používat pověření klienta z kódu aplikace. Pověření WCF lze také nakonfigurovat pomocí konfiguračního souboru aplikace. Použití konfigurace aplikace je často vhodnější než pevné kódování, protože umožňuje modifikaci parametrů aplikace bez nutnosti úpravy zdroje, rekompilace a opětovného nasazení.

Další postup popisuje, jak poskytnout podporu pro konfiguraci vlastních pověření.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Vytvoření obslužné rutiny konfigurace pro vlastní pověření klienta

1. Definujte novou třídu <xref:System.ServiceModel.Configuration.ClientCredentialsElement>odvozenou z .

2. Nepovinný parametr. Přidejte vlastnosti pro všechny další parametry konfigurace, které chcete zpřístupnit prostřednictvím konfigurace aplikace. Následující příklad přidá jednu vlastnost s názvem `CreditCardNumber`.

3. Přepište <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> vlastnost vrátit typ třídy pověření vlastního klienta vytvořené s konfiguračním prvkem.

4. Přepsat metodu. <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> Metoda je zodpovědná za vytvoření a vrácení instance vlastní třídy pověření na základě nastavení načtených z konfiguračního souboru. Volání základní <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metody z této metody načíst nastavení pověření zadaný systémem načtendo instance vlastní pověření klienta.

5. Nepovinný parametr. Pokud jste přidali další vlastnosti v kroku <xref:System.Configuration.ConfigurationElement.Properties%2A> 2, je třeba přepsat vlastnost, aby bylo možné zaregistrovat další nastavení konfigurace pro konfigurační rámec rozpoznat. Zkombinujte své vlastnosti s vlastnostmi základní třídy a povolte konfiguraci nastavení poskytované systémem prostřednictvím tohoto vlastního konfiguračního prvku pověření klienta.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Jakmile máte třídu obslužné rutiny konfigurace, lze ji integrovat do konfiguračního rámce WCF. To umožňuje vlastní pověření klienta, které mají být použity v prvky chování koncového bodu klienta, jak je znázorněno v dalším postupu.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Registrace a použití obslužné rutiny konfigurace vlastních pověření klienta v konfiguraci aplikace

1. Přidejte `extensions` do konfiguračního souboru prvek <> a <`behaviorExtensions`>.

2. Přidejte `add` prvek <> `behaviorExtensions` do prvku `name` <> a nastavte atribut na příslušnou hodnotu.

3. Nastavte `type` atribut na plně kvalifikovaný název typu. Zahrnout také název sestavení a další atributy sestavení.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    </system.serviceModel>
    ```

4. Po registraci obslužné rutiny konfigurace lze prvek vlastních pověření použít uvnitř `clientCredentials` stejného konfiguračního souboru namísto systémově poskytovaného <> prvku. Můžete použít jak vlastnosti poskytované systémem, tak všechny nové vlastnosti, které jste přidali do implementace obslužné rutiny konfigurace. Následující příklad nastaví hodnotu vlastní `creditCardNumber` vlastnosti pomocí atributu.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Implementace vlastních pověření služby

1. Definujte novou třídu <xref:System.ServiceModel.Description.ServiceCredentials>odvozenou z .

2. Nepovinný parametr. Přidejte nové vlastnosti, které poskytují rozhraní API pro nové hodnoty pověření, které jsou přidávány. Pokud nepřidáte nové hodnoty pověření, tento krok přeskočte. Následující příklad přidá `AdditionalCertificate` vlastnost.

3. Přepsat metodu. <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> Tato metoda je automaticky volána infrastrukturou WCF při použití vlastního pověření klienta. Metoda je zodpovědná za vytvoření a vrácení instance <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace třídy (popsané v dalším postupu).

4. Nepovinný parametr. Přepsat metodu. <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> To je vyžadováno pouze v případě, že přidání nových vlastností nebo vnitřnípole implementace pověření vlastního klienta.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Implementace správce vlastních tokenů zabezpečení služby

1. Definujte novou třídu <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> odvozenou z třídy.

2. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pokud musí být vytvořena vlastní implementace. Další informace o vlastních zprostředkovatelích tokenů zabezpečení naleznete v [tématu Postup: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md).

3. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pokud musí být vytvořena vlastní implementace. Další informace o vlastních ověřovateteelých tokenech zabezpečení najdete v [tématu How to: Create a Custom Security Token Authenticator](how-to-create-a-custom-security-token-authenticator.md) topic.

4. Nepovinný parametr. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metodu, <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> pokud musí být vytvořen vlastní. Další informace o vlastních tokenech zabezpečení a vlastních serializárů tokenů zabezpečení naleznete v [tématu How to: Create a Custom Token](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Použití vlastních pověření služby z kódu aplikace

1. Vytvořte instanci <xref:System.ServiceModel.ServiceHost>.

2. Odeberte chování pověření služby poskytované <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> systémem z kolekce.

3. Vytvořte novou instanci třídy pověření vlastní <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> služby a přidejte ji do kolekce.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Přidejte podporu konfigurace pomocí kroků popsaných`To create a configuration handler for custom client credentials`výše v`To register and use a custom client credentials configuration handler in the application configuration`postupech " " a " . Jediným rozdílem <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> je použití třídy <xref:System.ServiceModel.Configuration.ClientCredentialsElement> namísto třídy jako základní třídy pro obslužnou rutinu konfigurace. Vlastní prvek pověření služby lze pak použít `<serviceCredentials>` všude, kde je použit prvek zadaný systémem.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)
- [Postupy: Vytvoření vlastního ověřovacího modulu tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního tokenu](how-to-create-a-custom-token.md)
