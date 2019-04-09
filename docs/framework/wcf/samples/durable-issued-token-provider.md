---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 72c8b4e74607a1ed7f616959a6445f21b595a956
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103256"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="21a9f-102">Trvale vydaný poskytovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="21a9f-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="21a9f-103">Tento příklad ukazuje, jak implementovat vlastní klienta vydaný Poskytovatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="21a9f-104">Diskuse</span><span class="sxs-lookup"><span data-stu-id="21a9f-104">Discussion</span></span>  
 <span data-ttu-id="21a9f-105">Poskytovatel tokenu ve Windows Communication Foundation (WCF) slouží k zadání přihlašovacích údajů pro zabezpečení infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="21a9f-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="21a9f-106">Poskytovatel tokenu obecně zkontroluje cíl a problémů příslušné přihlašovací údaje tak, aby infrastruktura zabezpečení se dají zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="21a9f-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="21a9f-107">Součástí WCF [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-107">WCF ships with a [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="21a9f-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="21a9f-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="21a9f-109">Pokud máte úložiště přihlašovacích údajů, které nelze použít předdefinovaný poskytovatel tokenů.</span><span class="sxs-lookup"><span data-stu-id="21a9f-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
-   <span data-ttu-id="21a9f-110">Pokud chcete poskytnout vlastní vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytuje podrobnosti pro případ použití přihlašovacích údajů klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="21a9f-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
-   <span data-ttu-id="21a9f-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="21a9f-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="21a9f-112">Tento příklad ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který ukládá do mezipaměti tokenům vydaným službou tokenů zabezpečení služby (STS).</span><span class="sxs-lookup"><span data-stu-id="21a9f-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="21a9f-113">Souhrnně řečeno, tento příklad znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="21a9f-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="21a9f-114">Jak klienta lze nakonfigurovat pomocí vlastního zprostředkovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="21a9f-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="21a9f-115">Jak vydané tokeny můžete uložit do mezipaměti a k dispozici klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="21a9f-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
-   <span data-ttu-id="21a9f-116">Jak ověření serveru klientem pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="21a9f-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="21a9f-117">Tento příklad se skládá z programu konzoly klienta (Client.exe), program konzoly služby tokenů zabezpečení (Securitytokenservice.exe) a služby konzolový program (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="21a9f-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="21a9f-118">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="21a9f-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="21a9f-119">Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="21a9f-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="21a9f-120">Klient získá bezpečnostní token z tokenu služba zabezpečení (STS) a umožňuje synchronní žádosti o službu pro dané matematické operace a odpovědi služby k výsledku.</span><span class="sxs-lookup"><span data-stu-id="21a9f-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="21a9f-121">Činnost klienta je vidět v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="21a9f-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a9f-122">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="21a9f-123">Tato ukázka poskytuje pomocí kontraktu ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21a9f-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="21a9f-124">Konfiguraci této vazby v klientovi je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="21a9f-125">Na `security` prvek `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit.</span><span class="sxs-lookup"><span data-stu-id="21a9f-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="21a9f-126">V této ukázce zabezpečení zprávy se používá, což je důvod, proč `message` prvek `wsFederationHttpBinding` je zadat v rámci `security` prvek `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="21a9f-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="21a9f-127">`issuer` Prvek `wsFederationHttpBinding` uvnitř `message` prvek `wsFederationHttpBinding` Určuje adresu a vazbu pro službu tokenů zabezpečení, který vydá token zabezpečení do klienta tak, aby se klient může ověřit ke kalkulačce Služba.</span><span class="sxs-lookup"><span data-stu-id="21a9f-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="21a9f-128">Konfiguraci této vazby ve službě je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="21a9f-129">Na `security` prvek `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit.</span><span class="sxs-lookup"><span data-stu-id="21a9f-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="21a9f-130">V této ukázce zabezpečení zprávy se používá, což je důvod, proč `message` prvek `wsFederationHttpBinding` je zadat v rámci `security` prvek `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="21a9f-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="21a9f-131">`issuerMetadata` Prvek `wsFederationHttpBinding` uvnitř `message` prvek `wsFederationHttpBinding` určuje adrese a identitě pro koncový bod, který slouží k načtení metadat pro službu tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21a9f-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="21a9f-132">Chování služby je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-132">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="21a9f-133">`issuedTokenAuthentication` Element v rámci `serviceCredentials` element umožňuje službě a zadat omezení na tokeny, umožňuje klientům k dispozici během ověřování.</span><span class="sxs-lookup"><span data-stu-id="21a9f-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="21a9f-134">Tato konfigurace určuje, že tokeny podepsán certifikátem, jehož název subjektu je CN = služby STS jsou změna přijata službou.</span><span class="sxs-lookup"><span data-stu-id="21a9f-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="21a9f-135">Služba tokenů zabezpečení poskytuje jeden koncový bod pomocí standardní wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="21a9f-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="21a9f-136">Služba tokenů zabezpečení odpoví na požadavek od klientů pro tokeny a pokud klient se ověří pomocí účtu Windows, vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity v vydaný token.</span><span class="sxs-lookup"><span data-stu-id="21a9f-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="21a9f-137">Při vytváření tokenu, značky služby tokenu zabezpečení tokenu pomocí privátního klíče přidružené k CN = certifikátu STS.</span><span class="sxs-lookup"><span data-stu-id="21a9f-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="21a9f-138">Kromě toho vytvoří symetrický klíč a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikát.</span><span class="sxs-lookup"><span data-stu-id="21a9f-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="21a9f-139">V vrácením tokenu klientovi, služba tokenů zabezpečení také vrátí hodnotu symetrický klíč.</span><span class="sxs-lookup"><span data-stu-id="21a9f-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="21a9f-140">Klient prezentuje vydaný token pro službu kalkulačky a prokáže, že zná symetrický klíč pomocí podepsání zprávy s tímto klíčem.</span><span class="sxs-lookup"><span data-stu-id="21a9f-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="21a9f-141">Přihlašovací údaje vlastního klienta a poskytovatel tokenů</span><span class="sxs-lookup"><span data-stu-id="21a9f-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="21a9f-142">Následující kroky ukazují, jak vývoj vlastního zprostředkovatele tokenů, že mezipaměť na vydané tokeny a integrace s použitím technologie WCF: zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21a9f-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
#### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="21a9f-143">Vývoj vlastního zprostředkovatele tokenů</span><span class="sxs-lookup"><span data-stu-id="21a9f-143">To develop a custom token provider</span></span>  
  
1.  <span data-ttu-id="21a9f-144">Napište vlastního zprostředkovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="21a9f-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="21a9f-145">Ukázka implementuje vlastního zprostředkovatele tokenů, který vrátí token zabezpečení načítat z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="21a9f-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="21a9f-146">K provedení této úlohy je odvozen vlastního zprostředkovatele tokenů <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="21a9f-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="21a9f-147">Tato metoda pokusí získat token z mezipaměti, nebo pokud token nebyl nalezen v mezipaměti, načte token z podkladového zprostředkovatele a potom ukládá do mezipaměti tohoto tokenu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="21a9f-148">V obou případech vrátí metoda `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="21a9f-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="21a9f-149">Správce tokenů zabezpečení vlastního zápisu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="21a9f-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je do ní předán v `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="21a9f-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="21a9f-151">Správce tokenů zabezpečení se také používá k vytvoření ověřovací data tokenu a tokenu serializátory, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="21a9f-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="21a9f-152">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` požadovaná metoda vrátí vlastního zprostředkovatele tokenů, při úspěšné požadavky tokenu označuje, že vydaný token.</span><span class="sxs-lookup"><span data-stu-id="21a9f-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
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
  
3.  <span data-ttu-id="21a9f-153">Zápis vlastních klientských přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="21a9f-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="21a9f-154">Třída přihlašovacích údajů klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří Správce tokenů, který se používá k získání poskytovatele tokenů ověřovací data tokenu a tokenu serializátory zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21a9f-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
4.  <span data-ttu-id="21a9f-155">Implementace mezipaměť tokenu.</span><span class="sxs-lookup"><span data-stu-id="21a9f-155">Implement the token cache.</span></span> <span data-ttu-id="21a9f-156">Ukázková implementace používá abstraktní základní třída, přes který příjemci daného mezipaměť tokenu pracovat s mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="21a9f-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="21a9f-157">Klienti měli používat přihlašovací údaje, které vlastní vzorek odstraní výchozí třídu přihlašovacích údajů klienta a poskytuje novou třídu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="21a9f-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="21a9f-158">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="21a9f-158">Running the sample</span></span>  
 <span data-ttu-id="21a9f-159">Přečtěte si následující pokyny ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="21a9f-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="21a9f-160">Když spustíte ukázku, požadavek na token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21a9f-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="21a9f-161">Operace žádosti a odpovědi se zobrazují v oknech konzoly klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="21a9f-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="21a9f-162">Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.</span><span class="sxs-lookup"><span data-stu-id="21a9f-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="21a9f-163">Setup.cmd dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="21a9f-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="21a9f-164">Dávkový soubor Setup.cmd zahrnuté v této ukázce umožňuje nakonfigurovat server a služba tokenů zabezpečení s příslušnými certifikáty ke spuštění aplikace v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="21a9f-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="21a9f-165">Dávkový soubor se vytvoří dva certifikáty, že v CurrentUser/TrustedPeople úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="21a9f-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="21a9f-166">První certifikát má název předmětu CN = STS a služba tokenů zabezpečení používá k podepisování tokenů zabezpečení, které vystavuje do klienta.</span><span class="sxs-lookup"><span data-stu-id="21a9f-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="21a9f-167">Druhý certifikát má název předmětu CN = localhost a služba tokenů zabezpečení používá k šifrování tajného kódu tak, aby služba může dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="21a9f-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21a9f-168">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="21a9f-168">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="21a9f-169">Spusťte soubor Setup.cmd vytvořit požadované certifikáty.</span><span class="sxs-lookup"><span data-stu-id="21a9f-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2.  <span data-ttu-id="21a9f-170">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21a9f-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="21a9f-171">Ujistěte se, že jsou všechny projekty v řešení sestaveny, (sdílené, RSTRSTR, služby, služby SecurityTokenService a klient).</span><span class="sxs-lookup"><span data-stu-id="21a9f-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3.  <span data-ttu-id="21a9f-172">Ujistěte se, že Service.exe a SecurityTokenService.exe se provozují s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="21a9f-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="21a9f-173">Spusťte Client.exe.</span><span class="sxs-lookup"><span data-stu-id="21a9f-173">Run Client.exe.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="21a9f-174">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="21a9f-174">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="21a9f-175">Spusťte Cleanup.cmd ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="21a9f-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21a9f-176">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="21a9f-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21a9f-177">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="21a9f-177">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21a9f-178">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="21a9f-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21a9f-179">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="21a9f-179">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
