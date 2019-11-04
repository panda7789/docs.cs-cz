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
# <a name="saml-token-provider"></a>Zprostředkovatel tokenů zabezpečení SAML
Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenu SAML klienta. Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů infrastruktuře zabezpečení. Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu. WCF se dodává s výchozím poskytovatelem tokenu správce přihlašovacích údajů. WCF se dodává i s poskytovatelem tokenů služby CardSpace. Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:

- Pokud máte úložiště přihlašovacích údajů, pomocí kterého tyto poskytovatelé tokenů nemůžou pracovat s nástrojem.

- Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne informace, když klient rozhraní WCF použije přihlašovací údaje.

- Pokud vytváříte vlastní token.

 V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který umožňuje získat token SAML z vnějšku rozhraní klienta WCF, který se má použít.

 Pro Shrnutí Tato ukázka demonstruje následující:

- Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.

- Jak je možné předat token SAML vlastním přihlašovacím údajům klienta.

- Způsob, jakým se poskytuje token SAML pro klientské rozhraní WCF.

- Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.

 Služba zpřístupňuje dva koncové body pro komunikaci se službou, které jsou definovány pomocí konfiguračního souboru App. config. Každý koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurovaná se standardním `wsFederationHttpBinding`, která používá zabezpečení zpráv. Jeden koncový bod očekává, že klient provede ověřování pomocí tokenu SAML, který používá symetrický klíč ověření, zatímco druhý očekává ověřování klienta s tokenem SAML, který používá asymetrický klíč ověření. Služba také nakonfiguruje certifikát služby pomocí chování `serviceCredentials`. Chování `serviceCredentials` umožňuje nakonfigurovat certifikát služby. Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv. Následující konfigurace odkazuje na certifikát "localhost" nainstalovaný během ukázkové instalace, jak je popsáno v pokynech k instalaci na konci tohoto tématu. Chování `serviceCredentials` také umožňuje nakonfigurovat certifikáty, které jsou důvěryhodné k podepisování tokenů SAML. Následující konfigurace odkazuje na certifikát Alice nainstalovaný během ukázky.

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

 Následující kroky ukazují, jak vyvíjet vlastního zprostředkovatele tokenu SAML a integrovat ho do WCF: Security Framework:

1. Napište vlastního zprostředkovatele tokenu SAML.

     Ukázka implementuje vlastního zprostředkovatele tokenu SAML, který vrací token zabezpečení na základě kontrolního výrazu SAML, který je k dispozici v době konstrukce.

     K provedení této úlohy je poskytovatel vlastního tokenu odvozen z třídy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> a přepisuje metodu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>. Tato metoda vytvoří a vrátí nový `SecurityToken`.

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

2. Napsat vlastního správce tokenů zabezpečení.

     Třída <xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, která je předána metodě `CreateSecurityTokenProvider`. Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátoru tokenů, ale u těch se tato ukázka nezabývá. V této ukázce vlastní Správce tokenů zabezpečení dědí z třídy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> a přepíše metodu `CreateSecurityTokenProvider`, která vrátí vlastního zprostředkovatele tokenu SAML, když požadavky na předané tokeny označují, že je požadován token SAML. Pokud třída pověření klienta (viz krok 3) nezadala kontrolní výraz, vytvoří Správce tokenů zabezpečení příslušnou instanci.

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

3. Napište vlastní přihlašovací údaje klienta.

     Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátoru tokenů.

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

4. Nakonfigurujte klienta tak, aby používal vlastní přihlašovací údaje klienta.

     Ukázka odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta, aby klient mohl používat vlastní přihlašovací údaje klienta.

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

 Ve službě se zobrazí deklarace identity přidružené k volajícímu. Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.

- Vytváří se certifikát serveru:

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná `%SERVER_NAME%` Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota v tomto dávkovém souboru je localhost.

     Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:

     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- Vytváří se certifikát vystavitele.

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát vystavitele, který se má použít. Proměnná `%USER_NAME%` Určuje název vystavitele. Změňte tuto proměnnou tak, aby určovala vlastní název vystavitele. Výchozí hodnota v tomto dávkovém souboru je Alice.

     Certifikát je uložený v úložišti úložiště v umístění úložiště CurrentUser.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu vystavitele do důvěryhodného úložiště certifikátů serveru.

     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů serveru s certifikátem vystavitele se nevyžaduje.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

> [!NOTE]
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 spustit s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.  
  
2. Spustit Service. exe z service\bin.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář v počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na počítači služby. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor Service. exe. config je třeba aktualizovat, aby odrážel tento nový název certifikátu. Certifikát serveru můžete vytvořit úpravou dávkového souboru Setup. bat. Všimněte si, že soubor Setup. bat musí být spuštěn v okně Developer Command Prompt pro aplikaci Visual Studio otevřené s oprávněními správce. Musíte nastavit `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, který se používá k hostování služby.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta. Tento krok není nutný, pokud je certifikát serveru vydán důvěryhodným vystavitelem klienta.  
  
5. V souboru Service. exe. config v počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.  
  
6. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
7. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. V klientském počítači spusťte `Client.exe` z okna příkazového řádku.  
  
10. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
