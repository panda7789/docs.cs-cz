---
title: Zprostředkovatel tokenů zabezpečení SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 87aef572c2179034d295361c62942cea2ad6ed7a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424241"
---
# <a name="saml-token-provider"></a><span data-ttu-id="1f713-102">Zprostředkovatel tokenů zabezpečení SAML</span><span class="sxs-lookup"><span data-stu-id="1f713-102">SAML Token Provider</span></span>
<span data-ttu-id="1f713-103">Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenu SAML klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="1f713-104">Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů infrastruktuře zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1f713-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="1f713-105">Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu.</span><span class="sxs-lookup"><span data-stu-id="1f713-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="1f713-106">WCF se dodává s výchozím poskytovatelem tokenu správce přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="1f713-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="1f713-107">WCF se dodává i s poskytovatelem tokenů služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="1f713-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="1f713-108">Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="1f713-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="1f713-109">Pokud máte úložiště přihlašovacích údajů, pomocí kterého tyto poskytovatelé tokenů nemůžou pracovat s nástrojem.</span><span class="sxs-lookup"><span data-stu-id="1f713-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="1f713-110">Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne informace, když klient rozhraní WCF použije přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="1f713-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="1f713-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="1f713-111">If you are building a custom token.</span></span>

 <span data-ttu-id="1f713-112">V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který umožňuje získat token SAML z vnějšku rozhraní klienta WCF, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1f713-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="1f713-113">Pro Shrnutí Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="1f713-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="1f713-114">Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.</span><span class="sxs-lookup"><span data-stu-id="1f713-114">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="1f713-115">Jak je možné předat token SAML vlastním přihlašovacím údajům klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-115">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="1f713-116">Způsob, jakým se poskytuje token SAML pro klientské rozhraní WCF.</span><span class="sxs-lookup"><span data-stu-id="1f713-116">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="1f713-117">Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="1f713-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="1f713-118">Služba zpřístupňuje dva koncové body pro komunikaci se službou, které jsou definovány pomocí konfiguračního souboru App. config. Každý koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1f713-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1f713-119">Vazba je nakonfigurovaná se standardním `wsFederationHttpBinding`, která používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f713-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="1f713-120">Jeden koncový bod očekává, že klient provede ověřování pomocí tokenu SAML, který používá symetrický klíč ověření, zatímco druhý očekává ověřování klienta s tokenem SAML, který používá asymetrický klíč ověření.</span><span class="sxs-lookup"><span data-stu-id="1f713-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="1f713-121">Služba také nakonfiguruje certifikát služby pomocí chování `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="1f713-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="1f713-122">Chování `serviceCredentials` umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="1f713-123">Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f713-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="1f713-124">Následující konfigurace odkazuje na certifikát "localhost" nainstalovaný během ukázkové instalace, jak je popsáno v pokynech k instalaci na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1f713-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="1f713-125">Chování `serviceCredentials` také umožňuje nakonfigurovat certifikáty, které jsou důvěryhodné k podepisování tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="1f713-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="1f713-126">Následující konfigurace odkazuje na certifikát Alice nainstalovaný během ukázky.</span><span class="sxs-lookup"><span data-stu-id="1f713-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="1f713-127">Následující kroky ukazují, jak vyvíjet vlastního zprostředkovatele tokenu SAML a integrovat ho do WCF: Security Framework:</span><span class="sxs-lookup"><span data-stu-id="1f713-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="1f713-128">Napište vlastního zprostředkovatele tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="1f713-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="1f713-129">Ukázka implementuje vlastního zprostředkovatele tokenu SAML, který vrací token zabezpečení na základě kontrolního výrazu SAML, který je k dispozici v době konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1f713-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="1f713-130">K provedení této úlohy je poskytovatel vlastního tokenu odvozen z třídy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> a přepisuje metodu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f713-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="1f713-131">Tato metoda vytvoří a vrátí nový `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="1f713-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="1f713-132">Napsat vlastního správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1f713-132">Write custom security token manager.</span></span>

     <span data-ttu-id="1f713-133">Třída <xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, která je předána metodě `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="1f713-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="1f713-134">Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátoru tokenů, ale u těch se tato ukázka nezabývá.</span><span class="sxs-lookup"><span data-stu-id="1f713-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="1f713-135">V této ukázce vlastní Správce tokenů zabezpečení dědí z třídy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> a přepíše metodu `CreateSecurityTokenProvider`, která vrátí vlastního zprostředkovatele tokenu SAML, když požadavky na předané tokeny označují, že je požadován token SAML.</span><span class="sxs-lookup"><span data-stu-id="1f713-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="1f713-136">Pokud třída pověření klienta (viz krok 3) nezadala kontrolní výraz, vytvoří Správce tokenů zabezpečení příslušnou instanci.</span><span class="sxs-lookup"><span data-stu-id="1f713-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager :
     ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="1f713-137">Napište vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-137">Write a custom client credential.</span></span>

     <span data-ttu-id="1f713-138">Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátoru tokenů.</span><span class="sxs-lookup"><span data-stu-id="1f713-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="1f713-139">Nakonfigurujte klienta tak, aby používal vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="1f713-140">Ukázka odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta, aby klient mohl používat vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="1f713-141">Ve službě se zobrazí deklarace identity přidružené k volajícímu.</span><span class="sxs-lookup"><span data-stu-id="1f713-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="1f713-142">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1f713-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1f713-143">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="1f713-144">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="1f713-144">Setup Batch File</span></span>
 <span data-ttu-id="1f713-145">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="1f713-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="1f713-146">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="1f713-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="1f713-147">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1f713-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="1f713-148">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="1f713-148">Creating the server certificate:</span></span>

     <span data-ttu-id="1f713-149">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1f713-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="1f713-150">Proměnná `%SERVER_NAME%` Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="1f713-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="1f713-151">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="1f713-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="1f713-152">Výchozí hodnota v tomto dávkovém souboru je localhost.</span><span class="sxs-lookup"><span data-stu-id="1f713-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="1f713-153">Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1f713-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="1f713-154">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="1f713-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="1f713-155">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1f713-156">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="1f713-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1f713-157">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="1f713-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="1f713-158">Vytváří se certifikát vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1f713-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="1f713-159">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát vystavitele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1f713-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="1f713-160">Proměnná `%USER_NAME%` Určuje název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1f713-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="1f713-161">Změňte tuto proměnnou tak, aby určovala vlastní název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1f713-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="1f713-162">Výchozí hodnota v tomto dávkovém souboru je Alice.</span><span class="sxs-lookup"><span data-stu-id="1f713-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="1f713-163">Certifikát je uložený v úložišti úložiště v umístění úložiště CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="1f713-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="1f713-164">Instalace certifikátu vystavitele do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="1f713-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="1f713-165">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1f713-166">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="1f713-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1f713-167">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů serveru s certifikátem vystavitele se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="1f713-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="1f713-168">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="1f713-168">To set up and build the sample</span></span>

1. <span data-ttu-id="1f713-169">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f713-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1f713-170">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1f713-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1f713-171">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1f713-172">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="1f713-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="1f713-173">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 spustit s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1f713-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="1f713-174">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="1f713-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f713-175">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1f713-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="1f713-176">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="1f713-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="1f713-177">Spustit Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="1f713-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="1f713-178">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="1f713-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="1f713-179">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="1f713-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="1f713-180">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1f713-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1f713-181">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="1f713-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="1f713-182">Vytvořte adresář v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="1f713-183">Zkopírujte programové soubory služby do adresáře služby na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="1f713-184">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="1f713-185">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="1f713-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="1f713-186">Soubor Service. exe. config je třeba aktualizovat, aby odrážel tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="1f713-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="1f713-187">Certifikát serveru můžete vytvořit úpravou dávkového souboru Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="1f713-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="1f713-188">Všimněte si, že soubor Setup. bat musí být spuštěn v okně Developer Command Prompt pro aplikaci Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1f713-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="1f713-189">Musíte nastavit `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="1f713-190">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="1f713-191">Tento krok není nutný, pokud je certifikát serveru vydán důvěryhodným vystavitelem klienta.</span><span class="sxs-lookup"><span data-stu-id="1f713-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="1f713-192">V souboru Service. exe. config v počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="1f713-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="1f713-193">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="1f713-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="1f713-194">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="1f713-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="1f713-195">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="1f713-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="1f713-196">V klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1f713-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="1f713-197">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="1f713-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="1f713-198">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="1f713-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="1f713-199">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="1f713-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
