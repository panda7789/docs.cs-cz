---
title: "Zprostředkovatel tokenů zabezpečení SAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc6eaa916507c7e1c530d4ee757097bf0bffcd34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="saml-token-provider"></a><span data-ttu-id="67770-102">Zprostředkovatel tokenů zabezpečení SAML</span><span class="sxs-lookup"><span data-stu-id="67770-102">SAML Token Provider</span></span>
<span data-ttu-id="67770-103">Tento příklad ukazuje, jak implementovat vlastní klienta zprostředkovatele tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="67770-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="67770-104">Zprostředkovatel tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="67770-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="67770-105">Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy.</span><span class="sxs-lookup"><span data-stu-id="67770-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="67770-106">se dodává s výchozí zprostředkovatel tokenu správce přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="67770-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="67770-107">také se dodává s [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="67770-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="67770-108">Vlastní poskytovatele tokenů jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="67770-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="67770-109">Pokud máte úložiště přihlašovacích údajů, která tyto poskytovatele tokenů nemůže pracovat s.</span><span class="sxs-lookup"><span data-stu-id="67770-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="67770-110">Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel nabízí podrobné informace do kdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta používá přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="67770-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="67770-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="67770-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="67770-112">Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatele tokenů, který umožňuje získat z mimo tokenu SAML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="67770-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework to be used.</span></span>  
  
 <span data-ttu-id="67770-113">Tento příklad znázorňuje to Shrneme, následující:</span><span class="sxs-lookup"><span data-stu-id="67770-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="67770-114">Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="67770-114">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="67770-115">Jak lze předat tokenu SAML přihlašovací údaje vlastního klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-115">How a SAML token can be passed to the custom client credentials.</span></span>  
  
-   <span data-ttu-id="67770-116">Jak se poskytují tokenu SAML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-116">How the SAML token is provided to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework.</span></span>  
  
-   <span data-ttu-id="67770-117">Jak server ověření klienta pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="67770-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="67770-118">Službu zpřístupní dva koncové body pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="67770-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="67770-119">Vazba je nakonfigurována s standardní `wsFederationHttpBinding`, který používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="67770-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="67770-120">Jeden koncový bod očekává klienta k ověřování SAML token, který používá symetrického klíče doklad při dalších očekává klienta k ověření pomocí tokenu SAML, která používá asymetrické doklad klíč.</span><span class="sxs-lookup"><span data-stu-id="67770-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="67770-121">Služba nakonfiguruje taky certifikát služby pomocí `serviceCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="67770-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="67770-122">`serviceCredentials` Chování umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="67770-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="67770-123">Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy.</span><span class="sxs-lookup"><span data-stu-id="67770-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="67770-124">Následující konfigurace odkazuje "localhost" certifikát nainstalován při instalaci je ukázka, jak je popsáno v pokynů pro instalaci na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="67770-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="67770-125">`serviceCredentials` Chování můžete také konfigurovat certifikáty, které jsou důvěryhodní k podepisování tokenů SAML.</span><span class="sxs-lookup"><span data-stu-id="67770-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="67770-126">Následující konfigurace odkazuje 'Alice' certifikát nainstalován během vzorku.</span><span class="sxs-lookup"><span data-stu-id="67770-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>  
  
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
  
 <span data-ttu-id="67770-127">Následující kroky ukazují, jak vytvořit vlastní zprostředkovatele tokenu SAML a integrovat s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: framework zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="67770-127">The following steps show how to develop a custom SAML token provider and integrate it with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: security framework:</span></span>  
  
1.  <span data-ttu-id="67770-128">Napište vlastní zprostředkovatele tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="67770-128">Write a custom SAML token provider.</span></span>  
  
     <span data-ttu-id="67770-129">Ukázka implementuje vlastního zprostředkovatele tokenu SAML, který vrátí token zabezpečení založené na výrazu SAML, který je zadán v době konstrukce.</span><span class="sxs-lookup"><span data-stu-id="67770-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>  
  
     <span data-ttu-id="67770-130">K provedení této úlohy, poběží vlastní zprostředkovatel tokenu je odvozený od <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="67770-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="67770-131">Tato metoda vytvoří a vrátí novou `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="67770-131">This method creates and returns a new `SecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="67770-132">Zápis tokenu správce vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67770-132">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="67770-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Třída se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda.</span><span class="sxs-lookup"><span data-stu-id="67770-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="67770-134">Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátoru tokenů, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="67770-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="67770-135">V této ukázkové vlastní zabezpečení Správce tokenu dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` je požadovaná metoda vrátí vlastního zprostředkovatele tokenu SAML, když předaný tokenu požadavky označuje, že tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="67770-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="67770-136">Pokud třída pověření klienta (viz krok 3) nebyl zadán kontrolní výrazy, Správce tokenů zabezpečení vytvoří odpovídající instance.</span><span class="sxs-lookup"><span data-stu-id="67770-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>  
  
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
  
3.  <span data-ttu-id="67770-137">Zápis vlastních klientských pověření.</span><span class="sxs-lookup"><span data-stu-id="67770-137">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="67770-138">Třída pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátoru tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67770-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>  
  
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
  
4.  <span data-ttu-id="67770-139">Konfigurace klienta pro použití vlastního klienta přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="67770-139">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="67770-140">Ukázka odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta, takže klient může používat přihlašovací údaje vlastního klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>  
  
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
  
 <span data-ttu-id="67770-141">Ve službě zobrazí se deklarace identity spojené s volajícím.</span><span class="sxs-lookup"><span data-stu-id="67770-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="67770-142">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="67770-143">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-143">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="67770-144">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="67770-144">Setup Batch File</span></span>  
 <span data-ttu-id="67770-145">Dávkový soubor Setup.bat součástí této ukázky můžete nakonfigurovat server se příslušný certifikát spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="67770-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="67770-146">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="67770-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="67770-147">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="67770-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="67770-148">Vytvoření certifikátu serveru:</span><span class="sxs-lookup"><span data-stu-id="67770-148">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="67770-149">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="67770-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="67770-150">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="67770-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="67770-151">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="67770-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="67770-152">Výchozí hodnota v tomto souboru batch je localhost.</span><span class="sxs-lookup"><span data-stu-id="67770-152">The default value in this batch file is localhost.</span></span>  
  
     <span data-ttu-id="67770-153">Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="67770-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="67770-154">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="67770-154">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="67770-155">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="67770-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="67770-156">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="67770-157">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="67770-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="67770-158">Vytváření vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="67770-158">Creating the issuer certificate.</span></span>  
  
     <span data-ttu-id="67770-159">Následující řádky z dávkového souboru Setup.bat vytvořit vystavitele certifikát, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="67770-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="67770-160">`%USER_NAME%` Proměnná Určuje název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="67770-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="67770-161">Změňte tuto proměnnou k určení svůj vlastní název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="67770-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="67770-162">Výchozí hodnota v tomto souboru batch je Alice.</span><span class="sxs-lookup"><span data-stu-id="67770-162">The default value in this batch file is Alice.</span></span>  
  
     <span data-ttu-id="67770-163">Certifikát je uložen v tomto úložišti pod CurrentUser umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="67770-163">The certificate is stored in My store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="67770-164">Instalace vystavitele certifikátu do úložiště důvěryhodných certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="67770-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="67770-165">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="67770-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="67770-166">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="67770-167">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů serveru pomocí vystavitele certifikátu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="67770-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="67770-168">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="67770-168">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="67770-169">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67770-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="67770-170">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67770-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67770-171">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="67770-172">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="67770-172">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="67770-173">Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku spuštěného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="67770-173">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="67770-174">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="67770-174">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67770-175">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="67770-175">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="67770-176">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="67770-176">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="67770-177">Spusťte Service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="67770-177">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="67770-178">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="67770-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="67770-179">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="67770-179">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="67770-180">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="67770-180">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="67770-181">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="67770-181">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="67770-182">Vytvořte adresář na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="67770-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="67770-183">Zkopírujte soubory programu služby do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="67770-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="67770-184">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="67770-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="67770-185">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="67770-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="67770-186">Soubor Service.exe.config musí být aktualizovány tak, aby odrážela tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="67770-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="67770-187">Certifikát serveru můžete vytvořit úpravou Setup.bat dávkového souboru.</span><span class="sxs-lookup"><span data-stu-id="67770-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="67770-188">Všimněte si, že soubor setup.bat musí spustit v okně příkazového řádku Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="67770-188">Note that the setup.bat file must be run in a Visual Studio command prompt window opened with administrator privileges.</span></span> <span data-ttu-id="67770-189">Je nutné nastavit `%SERVER_NAME%` proměnné na hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="67770-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="67770-190">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="67770-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="67770-191">Tento krok není nutné, pokud je certifikát serveru vydána klienta důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="67770-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="67770-192">V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="67770-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="67770-193">Na počítači se službou spusťte z příkazového řádku Service.exe.</span><span class="sxs-lookup"><span data-stu-id="67770-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="67770-194">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="67770-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="67770-195">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="67770-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="67770-196">Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="67770-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="67770-197">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="67770-197">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="67770-198">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="67770-198">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="67770-199">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="67770-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67770-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="67770-200">See Also</span></span>
