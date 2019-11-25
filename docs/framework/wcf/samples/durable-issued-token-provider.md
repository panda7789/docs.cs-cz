---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 52c4e99f8b2a834d7200c2d2c2383fbdb21bdd1a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978328"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="80559-102">Trvale vydaný poskytovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="80559-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="80559-103">Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenu vydaných klientů.</span><span class="sxs-lookup"><span data-stu-id="80559-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="80559-104">Účely</span><span class="sxs-lookup"><span data-stu-id="80559-104">Discussion</span></span>  
 <span data-ttu-id="80559-105">Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů do infrastruktury zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80559-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="80559-106">Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu.</span><span class="sxs-lookup"><span data-stu-id="80559-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="80559-107">WCF se dodává se zprostředkovatelem tokenů služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="80559-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="80559-108">Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="80559-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="80559-109">Máte úložiště přihlašovacích údajů, se kterým nemůže integrovaný zprostředkovatel tokenů pracovat s nástrojem.</span><span class="sxs-lookup"><span data-stu-id="80559-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="80559-110">Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne podrobnosti o tom, kdy klient služby WCF používá pověření.</span><span class="sxs-lookup"><span data-stu-id="80559-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="80559-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="80559-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="80559-112">V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který ukládá tokeny do mezipaměti, které vystavuje služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="80559-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="80559-113">Pro Shrnutí Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="80559-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="80559-114">Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.</span><span class="sxs-lookup"><span data-stu-id="80559-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="80559-115">Jak mohou být vydávané tokeny uloženy do mezipaměti a poskytnuty klientovi WCF.</span><span class="sxs-lookup"><span data-stu-id="80559-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="80559-116">Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="80559-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="80559-117">Tato ukázka se skládá z programu klientské konzoly (Client. exe), programu konzoly služby tokenu zabezpečení (SecurityTokenService. exe) a programu konzoly služby (Service. exe).</span><span class="sxs-lookup"><span data-stu-id="80559-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="80559-118">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="80559-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="80559-119">Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="80559-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="80559-120">Klient získá token zabezpečení ze služby tokenu zabezpečení (STS) a provede synchronní požadavky služby pro danou matematickou operaci a odpověď služby s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="80559-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="80559-121">Aktivita klienta se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="80559-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80559-122">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="80559-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="80559-123">Tato ukázka zveřejňuje kontrakt ICalculator pomocí [\<WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="80559-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="80559-124">Konfigurace této vazby na klientovi je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="80559-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="80559-125">U `security`ho prvku `wsFederationHttpBinding`hodnota `mode` konfiguruje, který režim zabezpečení by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="80559-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="80559-126">V této ukázce se používá zabezpečení zpráv, což je důvod, proč je `message` element `wsFederationHttpBinding` zadán uvnitř `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="80559-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="80559-127">Prvek `issuer` `wsFederationHttpBinding` uvnitř `message` elementu `wsFederationHttpBinding` Určuje adresu a vazbu pro službu tokenu zabezpečení, která vydává token zabezpečení pro klienta, aby se klient mohl ověřit ve službě kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="80559-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="80559-128">Konfigurace této vazby ve službě je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="80559-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="80559-129">U `security`ho prvku `wsFederationHttpBinding`hodnota `mode` konfiguruje, který režim zabezpečení by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="80559-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="80559-130">V této ukázce se používá zabezpečení zpráv, což je důvod, proč je `message` element `wsFederationHttpBinding` zadán uvnitř `security` elementu `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="80559-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="80559-131">Prvek `issuerMetadata` `wsFederationHttpBinding` uvnitř `message` elementu `wsFederationHttpBinding` Určuje adresu a identitu koncového bodu, který lze použít k načtení metadat pro službu tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80559-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="80559-132">Chování služby se zobrazí v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="80559-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="80559-133">Element `issuedTokenAuthentication` uvnitř elementu `serviceCredentials` umožňuje službě určovat omezení pro tokeny, které umožňuje klientům prezentovat během ověřování.</span><span class="sxs-lookup"><span data-stu-id="80559-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="80559-134">Tato konfigurace určuje, že služba přijímá tokeny podepsané certifikátem, jehož název subjektu je CN = STS.</span><span class="sxs-lookup"><span data-stu-id="80559-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="80559-135">Služba tokenů zabezpečení zpřístupňuje jeden koncový bod pomocí standardu wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="80559-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="80559-136">Služba tokenů zabezpečení reaguje na žádosti od klientů na tokeny a za předpokladu, že se klient ověřuje pomocí účtu systému Windows, vydá token, který obsahuje uživatelské jméno klienta jako deklaraci identity v vystaveném tokenu.</span><span class="sxs-lookup"><span data-stu-id="80559-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="80559-137">V rámci vytváření tokenu podepisuje služba tokenů zabezpečení token pomocí privátního klíče přidruženého k certifikátu CN = STS.</span><span class="sxs-lookup"><span data-stu-id="80559-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="80559-138">Kromě toho vytvoří symetrický klíč a zašifruje ho pomocí veřejného klíče přidruženého k certifikátu CN = localhost.</span><span class="sxs-lookup"><span data-stu-id="80559-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="80559-139">Při vrácení tokenu klientovi vrátí služba tokenů zabezpečení také symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="80559-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="80559-140">Klient prezentuje vydaný token službě kalkulačky a ukáže, že zná symetrický klíč podepsáním zprávy pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="80559-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="80559-141">Vlastní přihlašovací údaje klienta a Poskytovatel tokenů</span><span class="sxs-lookup"><span data-stu-id="80559-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="80559-142">Následující kroky ukazují, jak vyvíjet vlastního poskytovatele tokenů, který ukládá do mezipaměti vydané tokeny a integruje ho s WCF: Security.</span><span class="sxs-lookup"><span data-stu-id="80559-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="80559-143">Vývoj vlastního poskytovatele tokenů</span><span class="sxs-lookup"><span data-stu-id="80559-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="80559-144">Napište vlastního poskytovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="80559-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="80559-145">Ukázka implementuje vlastního poskytovatele tokenu, který vrací token zabezpečení načtený z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="80559-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="80559-146">Chcete-li provést tuto úlohu, zprostředkovatel vlastního tokenu odvozuje třídu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> a přepíše metodu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="80559-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="80559-147">Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nejde v mezipaměti najít, načte token od základního poskytovatele a pak tento token uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="80559-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="80559-148">V obou případech metoda vrací `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="80559-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="80559-149">Napsat vlastního správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80559-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="80559-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, která je předána do této metody `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="80559-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="80559-151">Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátorů tokenů, ale u těch se tato ukázka nezabývá.</span><span class="sxs-lookup"><span data-stu-id="80559-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="80559-152">V této ukázce správce vlastního tokenu zabezpečení dědí z třídy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> a přepíše metodu `CreateSecurityTokenProvider`, aby vrátila vlastního zprostředkovatele tokenu, když požadavky na předané tokeny naznačují, že vydaný token je vyžádán.</span><span class="sxs-lookup"><span data-stu-id="80559-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="80559-153">Napište vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="80559-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="80559-154">Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátorů tokenů.</span><span class="sxs-lookup"><span data-stu-id="80559-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="80559-155">Implementujte mezipaměť tokenů.</span><span class="sxs-lookup"><span data-stu-id="80559-155">Implement the token cache.</span></span> <span data-ttu-id="80559-156">Ukázková implementace používá abstraktní základní třídu, přes kterou uživatelé dané mezipaměti tokenů komunikují s mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="80559-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="80559-157">Aby mohl klient používat vlastní přihlašovací údaje klienta, odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="80559-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="80559-158">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="80559-158">Running the sample</span></span>  
 <span data-ttu-id="80559-159">Pokud chcete ukázku spustit, přečtěte si následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="80559-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="80559-160">Při spuštění ukázky se žádost o token zabezpečení zobrazí v okně konzoly služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80559-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="80559-161">Požadavky na operace a odpovědi se zobrazí v oknech klienta a služby Service Console.</span><span class="sxs-lookup"><span data-stu-id="80559-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="80559-162">Ukončete aplikaci stisknutím klávesy ENTER v libovolném z oken konzoly.</span><span class="sxs-lookup"><span data-stu-id="80559-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="80559-163">Dávkový soubor Setup. cmd</span><span class="sxs-lookup"><span data-stu-id="80559-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="80559-164">Dávkový soubor Setup. cmd, který je součástí této ukázky, vám umožní nakonfigurovat službu token serveru a zabezpečení pomocí relevantních certifikátů pro spuštění samoobslužné aplikace.</span><span class="sxs-lookup"><span data-stu-id="80559-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="80559-165">Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů CurrentUser/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="80559-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="80559-166">První certifikát má název subjektu CN = STS a služba tokenů zabezpečení ji používá k podepsání tokenů zabezpečení, které vystaví klientovi.</span><span class="sxs-lookup"><span data-stu-id="80559-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="80559-167">Druhý certifikát má název subjektu CN = localhost a používá ho služba tokenů zabezpečení k šifrování tajného klíče, aby ho služba mohla dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="80559-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80559-168">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="80559-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="80559-169">Chcete-li vytvořit požadované certifikáty, spusťte soubor Setup. cmd.</span><span class="sxs-lookup"><span data-stu-id="80559-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="80559-170">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80559-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="80559-171">Ujistěte se, že jsou všechny projekty v řešení sestaveny (Shared, RSTRSTR, Service, SecurityTokenService a Client).</span><span class="sxs-lookup"><span data-stu-id="80559-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="80559-172">Zajistěte, aby byly služby Service. exe a SecurityTokenService. exe spuštěné s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="80559-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="80559-173">Spusťte soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="80559-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="80559-174">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="80559-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="80559-175">Až skončíte s ukázkou, spusťte na složce Samples Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="80559-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="80559-176">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="80559-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80559-177">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="80559-177">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="80559-178">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="80559-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80559-179">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="80559-179">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
