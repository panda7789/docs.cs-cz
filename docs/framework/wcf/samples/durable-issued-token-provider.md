---
title: "Trvale vydaný poskytovatel tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc92bd92f688ae2b12889779083142e6ddd481d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="db5dd-102">Trvale vydaný poskytovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="db5dd-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="db5dd-103">Tento příklad ukazuje, jak implementovat vlastní klienta vydaný Poskytovatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="db5dd-104">Diskusní</span><span class="sxs-lookup"><span data-stu-id="db5dd-104">Discussion</span></span>  
 <span data-ttu-id="db5dd-105">Zprostředkovatel tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k zadání přihlašovacích údajů ke Infrastruktura zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-105">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="db5dd-106">Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="db5dd-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="db5dd-107">se dodává s [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-107"> ships with a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="db5dd-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="db5dd-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="db5dd-109">Pokud máte úložiště přihlašovacích údajů, která předdefinované zprostředkovatel tokenu nemůže pracovat s.</span><span class="sxs-lookup"><span data-stu-id="db5dd-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
-   <span data-ttu-id="db5dd-110">Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel nabízí podrobné informace do kdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient používá přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="db5dd-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses the credentials.</span></span>  
  
-   <span data-ttu-id="db5dd-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="db5dd-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="db5dd-112">Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatel tokenu, který ukládá do mezipaměti tokeny vydané podle zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="db5dd-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="db5dd-113">Tento příklad znázorňuje to Shrneme, následující:</span><span class="sxs-lookup"><span data-stu-id="db5dd-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="db5dd-114">Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="db5dd-115">Jak vystavené tokeny můžete do mezipaměti a poskytnuté [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="db5dd-115">How issued tokens can be cached and provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
-   <span data-ttu-id="db5dd-116">Jak server ověření klienta pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="db5dd-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="db5dd-117">Tato ukázka se skládá z konzoly programu klienta (Client.exe), program konzoly služby tokenů zabezpečení (Securitytokenservice.exe) a program konzoly služby (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="db5dd-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="db5dd-118">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="db5dd-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="db5dd-119">Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit).</span><span class="sxs-lookup"><span data-stu-id="db5dd-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="db5dd-120">Klient získá zabezpečení token z Security Token Service (STS) a zadává synchronní požadavků službou pro danou matematické operace a odpovědi služby s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="db5dd-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="db5dd-121">Činnost klienta je viditelný v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="db5dd-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db5dd-122">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="db5dd-123">Tato ukázka zpřístupní ICalculator kontrakt pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db5dd-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="db5dd-124">Konfigurace této vazby v klientovi je zobrazena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="db5dd-125">Na `security` element `wsFederationHttpBinding`, `mode` hodnota konfiguruje slouží kterém režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="db5dd-126">V této ukázce zabezpečení zprávy je používají, což je důvod, proč `message` element `wsFederationHttpBinding` je zadat v rámci `security` element `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="db5dd-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="db5dd-127">`issuer` Element `wsFederationHttpBinding` uvnitř `message` element `wsFederationHttpBinding` Určuje adresu a vazeb pro služby tokenů zabezpečení, která vydá token zabezpečení klientovi, aby klient může ověřit kalkulačky Služba.</span><span class="sxs-lookup"><span data-stu-id="db5dd-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="db5dd-128">Konfigurace tuto vazbu na službu je vidět v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="db5dd-129">Na `security` element `wsFederationHttpBinding`, `mode` hodnota konfiguruje slouží kterém režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="db5dd-130">V této ukázce zabezpečení zprávy je používají, což je důvod, proč `message` element `wsFederationHttpBinding` je zadat v rámci `security` element `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="db5dd-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="db5dd-131">`issuerMetadata` Element `wsFederationHttpBinding` uvnitř `message` element `wsFederationHttpBinding` určuje adrese a identitě pro koncový bod, který slouží k načtení metadat pro služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="db5dd-132">Chování pro službu je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="db5dd-133">`issuedTokenAuthentication` Element uvnitř `serviceCredentials` element umožňuje službě zadejte omezení umožňuje klientům k dispozici při ověřování tokenů.</span><span class="sxs-lookup"><span data-stu-id="db5dd-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="db5dd-134">Tato konfigurace určuje, že tokeny podepsaný certifikát, jehož název subjektu CN = přijímat jsou služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="db5dd-135">Služby tokenů zabezpečení zpřístupní jeden koncový bod pomocí standardní wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="db5dd-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="db5dd-136">Služby tokenů zabezpečení odpovídá na žádosti od klientů pro tokeny a zadaný klient se ověří pomocí účtu Windows, vydá token, který obsahuje jméno uživatele klienta jako deklaraci v vydaných tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="db5dd-137">Při vytváření tokenu služby tokenu zabezpečení přihlásí token pomocí privátní klíč přidružený CN = certifikát služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="db5dd-138">Kromě toho vytvoří symetrického klíče a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikátu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="db5dd-139">Při vracení token do klienta, služby tokenů zabezpečení také vrátí symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="db5dd-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="db5dd-140">Klient uvede vystavený token, který má službu kalkulačky a prokáže, že zná symetrický klíč podepsáním zprávu s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="db5dd-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="db5dd-141">Přihlašovací údaje vlastního klienta a zprostředkovatele tokenu</span><span class="sxs-lookup"><span data-stu-id="db5dd-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="db5dd-142">Následující kroky ukazují, jak vyvíjet vlastní zprostředkovatele tokenu, mezipamětí vystavené tokeny a integrovat s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="db5dd-143">K vývoji vlastního zprostředkovatele tokenu</span><span class="sxs-lookup"><span data-stu-id="db5dd-143">To develop a custom token provider</span></span>  
  
1.  <span data-ttu-id="db5dd-144">Napište vlastního zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="db5dd-145">Ukázka implementuje vlastní zprostředkovatele tokenů, který vrátí token zabezpečení načítat z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="db5dd-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="db5dd-146">K provedení této úlohy, poběží vlastní zprostředkovatel tokenu odvozuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="db5dd-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="db5dd-147">Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nebyl nalezen v mezipaměti, načte token z výchozí zprostředkovatel a pak ukládá do mezipaměti tohoto tokenu.</span><span class="sxs-lookup"><span data-stu-id="db5dd-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="db5dd-148">V obou případech metoda vrátí `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="db5dd-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="db5dd-149">Zápis tokenu správce vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="db5dd-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda.</span><span class="sxs-lookup"><span data-stu-id="db5dd-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="db5dd-151">Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátorů tokenu, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="db5dd-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="db5dd-152">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` je požadovaná metoda vrátí vlastního zprostředkovatele tokenu, když předaný tokenu požadavky označuje, že vystavený token.</span><span class="sxs-lookup"><span data-stu-id="db5dd-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```  
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
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3.  <span data-ttu-id="db5dd-153">Zápis vlastních klientských pověření.</span><span class="sxs-lookup"><span data-stu-id="db5dd-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="db5dd-154">Třídy pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátorů tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
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
        Get  
        {  
          return this.cache;  
        }  
        Set  
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
  
4.  <span data-ttu-id="db5dd-155">Implementujte mezipamětí tokenů.</span><span class="sxs-lookup"><span data-stu-id="db5dd-155">Implement the token cache.</span></span> <span data-ttu-id="db5dd-156">Ukázka implementace používá abstraktní základní třída, pomocí kterého se příjemci daného tokenu mezipaměti interakci s mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="db5dd-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="db5dd-157">Vzorek pro klienta k použití pověření vlastní klienta, odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="db5dd-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="db5dd-158">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="db5dd-158">Running the sample</span></span>  
 <span data-ttu-id="db5dd-159">Přečtěte si následující pokyny ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="db5dd-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="db5dd-160">Při spuštění vzorového žádost o token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="db5dd-161">Operace požadavky a odpovědi se zobrazují v oknech konzoly klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="db5dd-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="db5dd-162">Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db5dd-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="db5dd-163">Setup.cmd dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="db5dd-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="db5dd-164">Dávkový soubor Setup.cmd součástí této ukázky můžete nakonfigurovat server a služby tokenů zabezpečení s příslušnými certifikáty spuštění aplikace s vlastním hostováním.</span><span class="sxs-lookup"><span data-stu-id="db5dd-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="db5dd-165">Dávkový soubor vytvoří dva certifikáty, že oba seznamy v CurrentUser/TrustedPeople úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="db5dd-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="db5dd-166">První certifikát obsahuje název subjektu z CN = služby tokenů zabezpečení a služby tokenů zabezpečení používané k podepisování tokenů zabezpečení, které vystavuje klientovi.</span><span class="sxs-lookup"><span data-stu-id="db5dd-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="db5dd-167">Druhý certifikát obsahuje název subjektu z CN = localhost a slouží k šifrování tajného klíče, aby služba ho dešifrovat pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="db5dd-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="db5dd-168">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="db5dd-168">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="db5dd-169">Spusťte soubor Setup.cmd vytvořit požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="db5dd-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2.  <span data-ttu-id="db5dd-170">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="db5dd-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="db5dd-171">Ujistěte se, že všechny projekty v řešení jsou vytvořeny (sdílené, RSTRSTR, služby, SecurityTokenService a klient).</span><span class="sxs-lookup"><span data-stu-id="db5dd-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3.  <span data-ttu-id="db5dd-172">Zkontrolujte, zda Service.exe a SecurityTokenService.exe jsou obě spuštěn s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="db5dd-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="db5dd-173">Spusťte Client.exe.</span><span class="sxs-lookup"><span data-stu-id="db5dd-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="db5dd-174">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="db5dd-174">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="db5dd-175">Po dokončení spuštění ukázky, spusťte Cleanup.cmd ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="db5dd-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db5dd-176">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="db5dd-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="db5dd-177">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="db5dd-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="db5dd-178">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="db5dd-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db5dd-179">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="db5dd-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a><span data-ttu-id="db5dd-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="db5dd-180">See Also</span></span>
