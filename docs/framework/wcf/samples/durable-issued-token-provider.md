---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144744"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="baba3-102">Trvale vydaný poskytovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="baba3-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="baba3-103">Tato ukázka ukazuje, jak implementovat vlastního klienta vydaného zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="baba3-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="baba3-104">Diskuse</span><span class="sxs-lookup"><span data-stu-id="baba3-104">Discussion</span></span>  
 <span data-ttu-id="baba3-105">Zprostředkovatel tokenů v systému Windows Communication Foundation (WCF) se používá k zadání pověření do infrastruktury zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="baba3-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="baba3-106">Zprostředkovatel tokenu obecně zkontroluje cíl a vydá příslušná pověření, aby infrastruktura zabezpečení mohla zabezpečit zprávu.</span><span class="sxs-lookup"><span data-stu-id="baba3-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="baba3-107">WCF je dodáván s poskytovatelem tokenu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="baba3-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="baba3-108">Vlastní zprostředkovatelé tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="baba3-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="baba3-109">Pokud máte úložiště pověření, které předdefinované zprostředkovatel tokenu nelze pracovat s.</span><span class="sxs-lookup"><span data-stu-id="baba3-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="baba3-110">Pokud chcete poskytnout vlastní mechanismus pro transformaci pověření z bodu, kdy uživatel poskytuje podrobnosti, když klient WCF používá pověření.</span><span class="sxs-lookup"><span data-stu-id="baba3-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="baba3-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="baba3-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="baba3-112">Tato ukázka ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který ukládá tokeny vydané službou TOKEN (STS).</span><span class="sxs-lookup"><span data-stu-id="baba3-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="baba3-113">Chcete-li shrnout, tato ukázka ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="baba3-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="baba3-114">Jak lze klienta nakonfigurovat pomocí vlastního zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="baba3-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="baba3-115">Jak vydané tokeny mohou být uloženy do mezipaměti a poskytnuty klientovi WCF.</span><span class="sxs-lookup"><span data-stu-id="baba3-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="baba3-116">Způsob ověření serveru klientem pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="baba3-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="baba3-117">Tato ukázka se skládá z programu klientské konzole (Client.exe), programu konzoly služby tokenu zabezpečení (Securitytokenservice.exe) a programu konzoly služby (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="baba3-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="baba3-118">Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="baba3-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="baba3-119">Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="baba3-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="baba3-120">Klient získá token zabezpečení ze služby tokenů zabezpečení (STS) a provede synchronní požadavky na službu pro danou operaci matematiky a odpovědi služby s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="baba3-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="baba3-121">Aktivita klienta je viditelná v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="baba3-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baba3-122">Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="baba3-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="baba3-123">Tato ukázka zpřístupňuje smlouvu ICalculator pomocí [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="baba3-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="baba3-124">Konfigurace této vazby na straně klienta je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="baba3-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="baba3-125">Na `security` elementu `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="baba3-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="baba3-126">V této ukázce se používá zabezpečení `message` zpráv, což je důvod, proč `wsFederationHttpBinding` je prvek zadán uvnitř `security` prvku . `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="baba3-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="baba3-127">Prvek `issuer` `wsFederationHttpBinding` uvnitř `message` prvku `wsFederationHttpBinding` určuje adresu a vazbu pro službu tokenů zabezpečení, která vydává klientovi token zabezpečení, aby se klient mohl ověřit na službě Calculator.</span><span class="sxs-lookup"><span data-stu-id="baba3-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="baba3-128">Konfigurace této vazby na službu je zobrazena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="baba3-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="baba3-129">Na `security` elementu `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="baba3-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="baba3-130">V této ukázce se používá zabezpečení `message` zpráv, což je důvod, proč `wsFederationHttpBinding` je prvek zadán uvnitř `security` prvku . `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="baba3-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="baba3-131">Prvek `issuerMetadata` `wsFederationHttpBinding` uvnitř elementu `message` `wsFederationHttpBinding` určuje adresu a identitu pro koncový bod, který lze použít k načtení metadat pro službu tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="baba3-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="baba3-132">Chování služby je zobrazeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="baba3-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="baba3-133">Prvek `issuedTokenAuthentication` uvnitř `serviceCredentials` prvku umožňuje službě určit omezení tokenů, které umožňuje klientům prezentovat během ověřování.</span><span class="sxs-lookup"><span data-stu-id="baba3-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="baba3-134">Tato konfigurace určuje, že tokeny podepsané certifikátem, jehož název subjektu je CN=STS, jsou službou přijímány.</span><span class="sxs-lookup"><span data-stu-id="baba3-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="baba3-135">Služba tokenů zabezpečení zpřístupňuje jeden koncový bod pomocí standardní wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="baba3-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="baba3-136">Služba tokenů zabezpečení reaguje na požadavek klientů na tokeny a za předpokladu, že klient ověří pomocí účtu systému Windows, vydá token, který obsahuje uživatelské jméno klienta jako deklaraci v vydaném tokenu.</span><span class="sxs-lookup"><span data-stu-id="baba3-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="baba3-137">Jako součást vytváření tokenu služba tokenu zabezpečení podepisuje token pomocí soukromého klíče přidruženého k certifikátu CN=STS.</span><span class="sxs-lookup"><span data-stu-id="baba3-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="baba3-138">Kromě toho vytvoří symetrický klíč a šifruje jej pomocí veřejného klíče přidruženého k certifikátu CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="baba3-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="baba3-139">Při vrácení tokenu klientovi služba tokenu zabezpečení také vrátí symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="baba3-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="baba3-140">Klient představuje vydaný token službě Kalkulačka a prokáže, že zná symetrický klíč podpisem zprávy pomocí tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="baba3-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="baba3-141">Vlastní pověření klienta a zprostředkovatel tokenů</span><span class="sxs-lookup"><span data-stu-id="baba3-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="baba3-142">Následující kroky ukazují, jak vyvinout vlastního zprostředkovatele tokenů, který ukládá do mezipaměti vydané tokeny a integrovat je s WCF: zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="baba3-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="baba3-143">Vývoj vlastního zprostředkovatele tokenů</span><span class="sxs-lookup"><span data-stu-id="baba3-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="baba3-144">Napište vlastního zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="baba3-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="baba3-145">Ukázka implementuje vlastního zprostředkovatele tokenu, který vrátí token zabezpečení načtený z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="baba3-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="baba3-146">Chcete-li provést tento úkol, vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> zprostředkovatel tokenu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> odvodí třídu a přepíše metodu.</span><span class="sxs-lookup"><span data-stu-id="baba3-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="baba3-147">Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nelze nalézt v mezipaměti, načte token od základního zprostředkovatele a pak uloží tento token do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="baba3-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="baba3-148">V obou případech metoda `SecurityToken`vrátí .</span><span class="sxs-lookup"><span data-stu-id="baba3-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2. <span data-ttu-id="baba3-149">Napište vlastní správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="baba3-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="baba3-150">Slouží <xref:System.IdentityModel.Selectors.SecurityTokenManager> k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní, <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> který je předán `CreateSecurityTokenProvider` v metodě.</span><span class="sxs-lookup"><span data-stu-id="baba3-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="baba3-151">Správce tokenů zabezpečení se také používá k vytvoření ověřovačů tokenů a serializátorů tokenů, ale tyto nejsou zahrnuty v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="baba3-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="baba3-152">V této ukázce vlastní správce <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> tokenů zabezpečení `CreateSecurityTokenProvider` dědí z třídy a přepíše metodu vrátit vlastní zprostředkovatele tokenu, když požadavky na předané tokeny označují, že je požadován vydaný token.</span><span class="sxs-lookup"><span data-stu-id="baba3-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3. <span data-ttu-id="baba3-153">Napište vlastní pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="baba3-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="baba3-154">Třída pověření klienta se používá k reprezentaci pověření, která jsou nakonfigurována pro proxy klienta a vytvoří správce tokenů zabezpečení, který se používá k získání ověřovacích tokenů, zprostředkovatelů tokenů a serializátorů tokenů.</span><span class="sxs-lookup"><span data-stu-id="baba3-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4. <span data-ttu-id="baba3-155">Implementujte mezipaměť tokenů.</span><span class="sxs-lookup"><span data-stu-id="baba3-155">Implement the token cache.</span></span> <span data-ttu-id="baba3-156">Ukázková implementace používá abstraktní základní třídu, jejímž prostřednictvím spotřebitelé dané mezipaměti tokenu interagují s mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="baba3-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="baba3-157">Aby klient mohl použít vlastní pověření klienta, ukázka odstraní výchozí třídu pověření klienta a poskytne novou třídu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="baba3-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="baba3-158">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="baba3-158">Running the sample</span></span>  
 <span data-ttu-id="baba3-159">Ukázku naleznete v následujících pokynech.</span><span class="sxs-lookup"><span data-stu-id="baba3-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="baba3-160">Při spuštění ukázky je požadavek na token zabezpečení zobrazen v okně konzoly služby Token tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="baba3-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="baba3-161">Požadavky na operace a odpovědi jsou zobrazeny v oknech klienta a konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="baba3-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="baba3-162">Stisknutím klávesy ENTER v libovolném systému konzoly aplikaci vypněte.</span><span class="sxs-lookup"><span data-stu-id="baba3-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="baba3-163">Dávkový soubor Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="baba3-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="baba3-164">Dávkový soubor Setup.cmd, který je součástí této ukázky, umožňuje nakonfigurovat server ovou službu a službu tokenů zabezpečení pomocí příslušných certifikátů pro spuštění samoobslužné aplikace.</span><span class="sxs-lookup"><span data-stu-id="baba3-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="baba3-165">Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů CurrentUser/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="baba3-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="baba3-166">První certifikát má název subjektu CN =STS a používá služba tokenů zabezpečení k podepsání tokenů zabezpečení, které vydává klientovi.</span><span class="sxs-lookup"><span data-stu-id="baba3-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="baba3-167">Druhý certifikát má název subjektu CN=localhost a služba Token security token používá k šifrování tajného klíče, aby ho služba mohla dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="baba3-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="baba3-168">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="baba3-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="baba3-169">Spusťte soubor Setup.cmd a vytvořte požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="baba3-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="baba3-170">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="baba3-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="baba3-171">Ujistěte se, že jsou sestaveny všechny projekty v řešení (Shared, RSTRSTR, Service, SecurityTokenService a Client).</span><span class="sxs-lookup"><span data-stu-id="baba3-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="baba3-172">Ujistěte se, že Service.exe a SecurityTokenService.exe jsou spuštěny s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="baba3-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="baba3-173">Spusťte soubor Client.exe.</span><span class="sxs-lookup"><span data-stu-id="baba3-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="baba3-174">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="baba3-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="baba3-175">Po dokončení spuštění ukázky spusťte soubor Cleanup.cmd ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="baba3-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="baba3-176">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="baba3-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="baba3-177">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="baba3-177">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="baba3-178">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="baba3-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="baba3-179">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="baba3-179">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
