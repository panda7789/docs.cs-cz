---
title: 'Návod: Vytvoření vlastního klienta a pověření služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: e59d578407ece9f22925abff57737cca8bf78eac
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374463"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Návod: Vytvoření vlastního klienta a pověření služby

V tomto tématu se dozvíte, jak implementovat vlastní přihlašovací údaje klienta a služby a jak používat vlastní přihlašovací údaje z kódu aplikace.

## <a name="credentials-extensibility-classes"></a>Třídy rozšiřitelnosti přihlašovacích údajů

Třídy <xref:System.ServiceModel.Description.ClientCredentials> a<xref:System.ServiceModel.Description.ServiceCredentials> jsou hlavní vstupními body rozšiřitelnosti zabezpečení služby Windows Communication Foundation (WCF). Tyto třídy přihlašovacích údajů poskytují rozhraní API, která umožňují kódu aplikace nastavit informace o přihlašovacích údajích a převést typy přihlašovacích údajů na tokeny zabezpečení. (*Tokeny zabezpečení* jsou formuláře používané k přenosu přihlašovacích údajů do zpráv SOAP.) Odpovědnosti těchto tříd pověření lze rozdělit do dvou oblastí:

- Poskytněte rozhraní API pro aplikace, aby nastavily informace o přihlašovacích údajích.

- Provést jako továrnu pro <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.

Výchozí implementace poskytované v rámci WCF podporují typy přihlašovacích údajů poskytovaných systémem a vytvoří Správce tokenů zabezpečení, který dokáže zpracovat tyto typy přihlašovacích údajů.

## <a name="reasons-to-customize"></a>Důvody k přizpůsobení

Existuje několik důvodů, jak přizpůsobit třídy přihlašovacích údajů klienta nebo služby. Nejpřednější je požadavek na změnu výchozího chování zabezpečení služby WCF s ohledem na zpracování typů přihlašovacích údajů poskytovaných systémem, zejména z následujících důvodů:

- Změny, které nejsou možné pomocí jiných bodů rozšiřitelnosti.

- Přidávání nových typů přihlašovacích údajů.

- Přidávají se nové typy vlastních tokenů zabezpečení.

Toto téma popisuje, jak implementovat vlastní pověření klienta a služby a jak je používat z kódu aplikace.

## <a name="first-in-a-series"></a>První v řadě

Vytvoření vlastní třídy přihlašovacích údajů je jenom první krok, protože důvodem pro přizpůsobení přihlašovacích údajů je změna chování WCF týkající se zřizování přihlašovacích údajů, serializace tokenu zabezpečení nebo ověřování. Další témata v této části popisují, jak vytvořit vlastní serializace a ověřovatele. V tomto ohledu je vytvoření vlastní třídy přihlašovacích údajů prvním tématem v řadě. Následné akce (vytváření vlastních serializátorů a ověřovatelů) se dají provádět až po vytvoření vlastních přihlašovacích údajů. Mezi další témata, která se vytvářejí v tomto tématu, patří:

- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)

- [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)

- [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)

## <a name="procedures"></a>Procedury

#### <a name="to-implement-custom-client-credentials"></a>Implementace vlastních přihlašovacích údajů klienta

1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Description.ClientCredentials> třídy.

2. Volitelný parametr. Přidejte nové metody nebo vlastnosti pro nové typy přihlašovacích údajů. Pokud nepřidáte nové typy přihlašovacích údajů, přeskočte tento krok. Následující příklad přidá `CreditCardNumber` vlastnost.

3. Přepsat <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Tato metoda je automaticky volána infrastrukturou zabezpečení služby WCF při použití vlastních přihlašovacích údajů klienta. Tato metoda zodpovídá za vytváření a vracení instance implementace <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.

    > [!IMPORTANT]
    > Je důležité si uvědomit, že <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda je přepsaná, aby vytvořila vlastního správce tokenů zabezpečení. Správce tokenu zabezpečení, který je <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>odvozen z, musí vrátit vlastního poskytovatele tokenu zabezpečení, <xref:System.IdentityModel.Selectors.SecurityTokenProvider>který je odvozen z, pro vytvoření vlastního tokenu zabezpečení. Pokud nebudete postupovat podle tohoto vzoru pro vytváření tokenů zabezpečení, může vaše aplikace <xref:System.ServiceModel.ChannelFactory> fungovat nesprávně, když jsou objekty ukládány do mezipaměti (což je výchozí chování pro klientské proxy servery WCF), což může mít za následek zvýšení oprávnění proti útokům. Vlastní objekt přihlašovacích údajů je uložen v mezipaměti jako <xref:System.ServiceModel.ChannelFactory>součást. Vlastní <xref:System.IdentityModel.Selectors.SecurityTokenManager> však je vytvořena při každém vyvolání, což snižuje riziko bezpečnostní hrozby, pokud je logika vytváření tokenu umístěna <xref:System.IdentityModel.Selectors.SecurityTokenManager>v.

4. Přepsat <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metody.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Implementace vlastního správce tokenů zabezpečení klienta

1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.

2. Volitelný parametr. Přepsat metodu, pokud je třeba <xref:System.IdentityModel.Selectors.SecurityTokenProvider> vytvořit vlastní implementaci. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Další informace o vlastních poskytovatelích tokenů zabezpečení naleznete [v tématu How to: Vytvořte vlastního poskytovatele](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)tokenů zabezpečení.

3. Volitelný parametr. Přepsat metodu, pokud je třeba <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> vytvořit vlastní implementaci. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> Další informace o vlastních ověřovacích tokenech tokenu zabezpečení [najdete v tématu How to: Vytvořte vlastní ověřovací data](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)tokenu zabezpečení.

4. Volitelný parametr. Přepsat metodu, pokud je nutné <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> vytvořit vlastní. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> Další informace o vlastních tokenech zabezpečení a vlastních serializátorech tokenů zabezpečení naleznete [v tématu How to: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Použití vlastních přihlašovacích údajů klienta z kódu aplikace

1. Buď vytvořte instanci vygenerovaného klienta, která představuje rozhraní služby, nebo vytvořte instanci <xref:System.ServiceModel.ChannelFactory> ukazující na službu, se kterou chcete komunikovat.

2. Odeberte chování přihlašovacích údajů klienta poskytnuté systémem z <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, ke kterému lze přistupovat <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> prostřednictvím vlastnosti.

3. Vytvořte novou instanci vlastní třídy přihlašovacích údajů klienta a přidejte ji do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekce, ke které se dá dostat <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> prostřednictvím vlastnosti.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Předchozí postup ukazuje použití přihlašovacích údajů klienta z kódu aplikace. Přihlašovací údaje WCF je taky možné konfigurovat pomocí konfiguračního souboru aplikace. Použití konfigurace aplikace je často vhodnější pro pevnění kódování, protože umožňuje úpravu parametrů aplikace bez nutnosti upravovat zdroj, znovu zkompilovat a znovu nasadit.

Další postup popisuje, jak poskytnout podporu pro konfiguraci vlastních přihlašovacích údajů.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Vytváření obslužné rutiny konfigurace pro vlastní přihlašovací údaje klienta

1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.

2. Volitelný parametr. Přidejte vlastnosti pro všechny další konfigurační parametry, které chcete zveřejnit prostřednictvím konfigurace aplikace. Následující příklad přidá jednu vlastnost s názvem `CreditCardNumber`.

3. Přepište <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> vlastnost a vraťte typ vlastní třídy přihlašovacích údajů klienta vytvořené pomocí elementu konfigurace.

4. Přepsat <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metody. Metoda zodpovídá za vytváření a vracení instance vlastní třídy přihlašovacích údajů na základě nastavení načtených z konfiguračního souboru. Voláním základní <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metody z této metody načtěte nastavení přihlašovacích údajů poskytnuté systémem, které se načte do vlastní instance přihlašovacích údajů klienta.

5. Volitelný parametr. Pokud jste přidali další vlastnosti v kroku 2, je nutné <xref:System.Configuration.ConfigurationElement.Properties%2A> vlastnost přepsat, aby bylo možné zaregistrovat další nastavení konfigurace pro rozhraní Configuration Framework, aby je bylo možné rozpoznat. Zkombinujte své vlastnosti s vlastnostmi základní třídy, aby se nastavení poskytnutá systémem mohla konfigurovat prostřednictvím tohoto vlastního elementu konfigurace přihlašovacích údajů klienta.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Jakmile máte třídu obslužné rutiny konfigurace, lze ji integrovat do konfiguračního rozhraní WCF. To umožňuje použití přihlašovacích údajů pro vlastní klienta v prvcích chování koncového bodu klienta, jak je znázorněno v následujícím postupu.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Registrace a použití vlastní obslužné rutiny konfigurace přihlašovacích údajů klienta v konfiguraci aplikace

1. Přidejte prvek <`extensions`> a <`behaviorExtensions`> element do konfiguračního souboru.

2. Do prvku <`add``behaviorExtensions`>přidejteprvek > < a nastavte atributnaodpovídajícíhodnotu.`name`

3. `type` Nastavte atribut na plně kvalifikovaný název typu. Také zahrňte název sestavení a další atributy sestavení.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    <system.serviceModel>
    ```

4. Po registraci obslužné rutiny konfigurace je možné vlastní element přihlašovacích údajů použít ve stejném konfiguračním souboru místo <`clientCredentials`> elementu poskytnutém systémem. Můžete použít jak vlastnosti poskytované systémem, tak všechny nové vlastnosti, které jste přidali do implementace obslužné rutiny konfigurace. Následující příklad nastaví hodnotu vlastní vlastnosti pomocí `creditCardNumber` atributu.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Implementace vlastních přihlašovacích údajů služby

1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Description.ServiceCredentials>.

2. Volitelný parametr. Přidejte nové vlastnosti, které poskytují rozhraní API pro nové hodnoty přihlašovacích údajů, které se přidávají. Pokud nepřidáte nové hodnoty přihlašovacích údajů, přeskočte tento krok. Následující příklad přidá `AdditionalCertificate` vlastnost.

3. Přepsat <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Tato metoda je automaticky volána infrastrukturou WCF při použití vlastních přihlašovacích údajů klienta. Metoda zodpovídá za vytváření a vracení instance implementace <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy (popsané v dalším postupu).

4. Volitelný parametr. Přepsat <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metody. To se vyžaduje jenom v případě, že se přidávají nové vlastnosti nebo interní pole do implementace vlastních přihlašovacích údajů klienta.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Implementace vlastního správce tokenů zabezpečení služby

1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy.

2. Volitelný parametr. Přepsat metodu, pokud je třeba <xref:System.IdentityModel.Selectors.SecurityTokenProvider> vytvořit vlastní implementaci. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> Další informace o vlastních poskytovatelích tokenů zabezpečení naleznete [v tématu How to: Vytvořte vlastního poskytovatele](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)tokenů zabezpečení.

3. Volitelný parametr. Přepsat metodu, pokud je třeba <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> vytvořit vlastní implementaci. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> Další informace o vlastních ověřovacích tokenech tokenu zabezpečení [najdete v tématu How to: Vytvořte vlastní téma ověřovatele](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) bezpečnostního tokenu.

4. Volitelný parametr. Přepsat metodu, pokud je nutné <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> vytvořit vlastní. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> Další informace o vlastních tokenech zabezpečení a vlastních serializátorech tokenů zabezpečení naleznete [v tématu How to: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Použití vlastních přihlašovacích údajů služby z kódu aplikace

1. Vytvořte instanci <xref:System.ServiceModel.ServiceHost>.

2. Odebere chování přihlašovacích údajů ze služby poskytnutých systémem <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> z kolekce.

3. Vytvořte novou instanci vlastní třídy přihlašovacích údajů služby a přidejte ji do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Přidání podpory pro konfiguraci pomocí kroků popsaných dříve v postupech`To create a configuration handler for custom client credentials``To register and use a custom client credentials configuration handler in the application configuration`a. Jediným rozdílem je použití <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> třídy namísto <xref:System.ServiceModel.Configuration.ClientCredentialsElement> třídy jako základní třídy pro obslužnou rutinu konfigurace. Vlastní element přihlašovacích údajů služby se pak dá použít všude, kde se `<serviceCredentials>` používá prvek poskytovaný systémem.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
