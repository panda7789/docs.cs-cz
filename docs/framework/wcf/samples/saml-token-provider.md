---
title: Zprostředkovatel tokenů zabezpečení SAML
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: dfd693e262e7566c865d5b9faed5b9e00a8cfec9
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793627"
---
# <a name="saml-token-provider"></a><span data-ttu-id="fc79d-102">Zprostředkovatel tokenů zabezpečení SAML</span><span class="sxs-lookup"><span data-stu-id="fc79d-102">SAML Token Provider</span></span>
<span data-ttu-id="fc79d-103">Tento příklad ukazuje, jak implementovat vlastní klienta zprostředkovatel tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="fc79d-104">Poskytovatel tokenu ve Windows Communication Foundation (WCF) slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="fc79d-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="fc79d-105">Poskytovatel tokenu obecně zkontroluje cíl a problémů příslušné přihlašovací údaje tak, aby infrastruktura zabezpečení se dají zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="fc79d-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="fc79d-106">WCF se dodává s výchozí poskytovatel tokenu přihlašovacích údajů správce.</span><span class="sxs-lookup"><span data-stu-id="fc79d-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="fc79d-107">WCF se také dodává se [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="fc79d-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="fc79d-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="fc79d-108">Custom token providers are useful in the following cases:</span></span>

-   <span data-ttu-id="fc79d-109">Pokud máte úložiště přihlašovacích údajů, které tyto poskytovatele tokenů nemůže pracovat s.</span><span class="sxs-lookup"><span data-stu-id="fc79d-109">If you have a credential store that these token providers cannot operate with.</span></span>

-   <span data-ttu-id="fc79d-110">Pokud chcete poskytnout vlastní vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel zadá podrobnosti, které chcete při Architektura klienta WCF používá přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="fc79d-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

-   <span data-ttu-id="fc79d-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="fc79d-111">If you are building a custom token.</span></span>

 <span data-ttu-id="fc79d-112">Tento příklad ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který umožňuje získat z mimo Architektura klienta WCF pro použití tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="fc79d-113">Souhrnně řečeno, tento příklad znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="fc79d-113">To summarize, this sample demonstrates the following:</span></span>

-   <span data-ttu-id="fc79d-114">Jak klienta lze nakonfigurovat pomocí vlastního zprostředkovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="fc79d-114">How a client can be configured with a custom token provider.</span></span>

-   <span data-ttu-id="fc79d-115">Jak lze předat SAML token vlastních klientských přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="fc79d-115">How a SAML token can be passed to the custom client credentials.</span></span>

-   <span data-ttu-id="fc79d-116">Jak se do rozhraní klienta WCF zadává tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-116">How the SAML token is provided to the WCF client framework.</span></span>

-   <span data-ttu-id="fc79d-117">Jak ověření serveru klientem pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="fc79d-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="fc79d-118">Služba poskytuje dva koncové body služby pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fc79d-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="fc79d-119">Je vazba konfigurována se standardní `wsFederationHttpBinding`, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="fc79d-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="fc79d-120">Jeden koncový bod očekává, že klient k ověření pomocí tokenu SAML, který používá symetrický vyzkoušený klíč, zatímco druhá očekává, že klient k ověření pomocí tokenu SAML, který používá asymetrický klíč důkazu.</span><span class="sxs-lookup"><span data-stu-id="fc79d-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="fc79d-121">Služba také nakonfiguruje pomocí certifikátu služby `serviceCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="fc79d-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="fc79d-122">`serviceCredentials` Chování umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="fc79d-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="fc79d-123">Certifikát služby se používá pro klienta k ověření služby a zajistit ochranu zprávy.</span><span class="sxs-lookup"><span data-stu-id="fc79d-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="fc79d-124">Následující konfigurace odkazuje na "localhost" certifikát nainstalovat během instalace ukázka, jak je popsáno v pokynech pro instalační program na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="fc79d-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="fc79d-125">`serviceCredentials` Chování lze také nakonfigurovat certifikáty, které jsou důvěryhodní k podepisování tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="fc79d-126">Následující konfigurace odkazuje na "Alice" certifikát nainstalován během ukázky.</span><span class="sxs-lookup"><span data-stu-id="fc79d-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

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

 <span data-ttu-id="fc79d-127">Následující kroky ukazují, jak vyvíjet vlastní zprostředkovatel tokenů SAML a integrace s použitím technologie WCF: architektury zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="fc79d-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1.  <span data-ttu-id="fc79d-128">Napište vlastního zprostředkovatele tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="fc79d-129">Ukázka implementuje vlastního zprostředkovatele tokenů SAML, který vrátí token zabezpečení založené na kontrolní výraz SAML, která je k dispozici v době konstrukce.</span><span class="sxs-lookup"><span data-stu-id="fc79d-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="fc79d-130">K provedení této úlohy, vlastní poskytovatele tokenu, kterého je odvozen z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fc79d-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="fc79d-131">Tato metoda vytvoří a vrátí nový `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="fc79d-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```
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

2.  <span data-ttu-id="fc79d-132">Správce tokenů zabezpečení vlastního zápisu.</span><span class="sxs-lookup"><span data-stu-id="fc79d-132">Write custom security token manager.</span></span>

     <span data-ttu-id="fc79d-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Třída se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je do ní předán v `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="fc79d-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="fc79d-134">Správce tokenů zabezpečení se také používá k vytvoření ověřovací data tokenu a tokenu serializátor, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="fc79d-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="fc79d-135">V této ukázkové vlastní bezpečnostní zdědí Správce tokenů <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` požadovaná metoda vrátí vlastního zprostředkovatele tokenů SAML, při úspěšné požadavky tokenu označuje, že tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="fc79d-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="fc79d-136">Pokud kontrolní výraz (viz krok 3) nebyla zadaná třída přihlašovací údaje klienta, Správce tokenů zabezpečení vytvoří příslušnou instanci.</span><span class="sxs-lookup"><span data-stu-id="fc79d-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```
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

3.  <span data-ttu-id="fc79d-137">Zápis vlastních klientských přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="fc79d-137">Write a custom client credential.</span></span>

     <span data-ttu-id="fc79d-138">Třída přihlašovacích údajů klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který se používá k získání ověřovací data tokenu, poskytovatele tokenů a serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fc79d-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```
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

4.  <span data-ttu-id="fc79d-139">Konfigurace klienta pro použití vlastního klienta přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="fc79d-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="fc79d-140">Ukázka odstraní výchozí třídu přihlašovacích údajů klienta a poskytuje novou třídu přihlašovacích údajů klienta, může klient použít přihlašovací údaje, které vlastní.</span><span class="sxs-lookup"><span data-stu-id="fc79d-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```
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

 <span data-ttu-id="fc79d-141">Ve službě zobrazí se deklarací spojené s volajícím.</span><span class="sxs-lookup"><span data-stu-id="fc79d-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="fc79d-142">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="fc79d-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fc79d-143">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="fc79d-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="fc79d-144">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="fc79d-144">Setup Batch File</span></span>
 <span data-ttu-id="fc79d-145">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušný certifikát ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="fc79d-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="fc79d-146">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="fc79d-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="fc79d-147">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fc79d-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

-   <span data-ttu-id="fc79d-148">Vytváří se certifikát serveru:</span><span class="sxs-lookup"><span data-stu-id="fc79d-148">Creating the server certificate:</span></span>

     <span data-ttu-id="fc79d-149">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="fc79d-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="fc79d-150">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="fc79d-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="fc79d-151">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="fc79d-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="fc79d-152">Výchozí hodnota v tomto souboru služby batch je localhost.</span><span class="sxs-lookup"><span data-stu-id="fc79d-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="fc79d-153">Certifikát je uložen v úložišti (osobních) v části umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="fc79d-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="fc79d-154">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="fc79d-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="fc79d-155">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="fc79d-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="fc79d-156">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="fc79d-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="fc79d-157">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="fc79d-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="fc79d-158">Vytvoření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fc79d-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="fc79d-159">Následující řádky z dávkový soubor Setup.bat vytvořit certifikát vystavitele, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="fc79d-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="fc79d-160">`%USER_NAME%` Proměnná Určuje název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fc79d-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="fc79d-161">Změňte tuto proměnnou k určení vlastní název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fc79d-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="fc79d-162">Výchozí hodnota v tomto souboru služby batch je Alice.</span><span class="sxs-lookup"><span data-stu-id="fc79d-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="fc79d-163">Certifikát je uložen v úložišti v rámci CurrentUser umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="fc79d-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="fc79d-164">Instalace certifikátu vystavitele do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="fc79d-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="fc79d-165">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="fc79d-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="fc79d-166">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="fc79d-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="fc79d-167">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – v tomto kroku naplnění úložiště certifikátů serveru s certifikátem vystavitele se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="fc79d-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="fc79d-168">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="fc79d-168">To set up and build the sample</span></span>

1.  <span data-ttu-id="fc79d-169">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc79d-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="fc79d-170">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fc79d-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="fc79d-171">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="fc79d-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="fc79d-172">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="fc79d-172">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="fc79d-173">Spusťte Setup.bat z instalační složky s ukázkou uvnitř příkazový řádek sady Visual Studio 2012, spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fc79d-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="fc79d-174">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="fc79d-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fc79d-175">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="fc79d-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="fc79d-176">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="fc79d-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="fc79d-177">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="fc79d-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="fc79d-178">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="fc79d-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="fc79d-179">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc79d-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="fc79d-180">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="fc79d-180">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="fc79d-181">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="fc79d-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="fc79d-182">Vytvoření adresáře na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="fc79d-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="fc79d-183">Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="fc79d-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="fc79d-184">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="fc79d-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="fc79d-185">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="fc79d-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="fc79d-186">Soubor Service.exe.config musí aktualizovat tak, aby odrážely tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fc79d-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="fc79d-187">Certifikát serveru můžete vytvořit tak, že upravíte dávkový soubor Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="fc79d-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="fc79d-188">Všimněte si, že se soubor setup.bat musí být spuštěn v sadě Visual Studio okno příkazového řádku otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="fc79d-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="fc79d-189">Je nutné nastavit `%SERVER_NAME%` proměnných hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="fc79d-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="fc79d-190">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="fc79d-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="fc79d-191">Tento krok není nezbytný, pokud certifikátu serveru vydanému klienta důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fc79d-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="fc79d-192">V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný, místo localhost.</span><span class="sxs-lookup"><span data-stu-id="fc79d-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="fc79d-193">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="fc79d-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="fc79d-194">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="fc79d-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="fc79d-195">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="fc79d-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="fc79d-196">Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fc79d-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="fc79d-197">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="fc79d-197">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fc79d-198">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="fc79d-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="fc79d-199">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="fc79d-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc79d-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc79d-200">See Also</span></span>
