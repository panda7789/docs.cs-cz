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
# <a name="saml-token-provider"></a>Zprostředkovatel tokenů zabezpečení SAML
Tento příklad ukazuje, jak implementovat vlastní klienta zprostředkovatele tokenu SAML. Zprostředkovatel tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury. Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]se dodává s výchozí zprostředkovatel tokenu správce přihlašovacích údajů. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také se dodává s [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu. Vlastní poskytovatele tokenů jsou užitečné v následujících případech:  
  
-   Pokud máte úložiště přihlašovacích údajů, která tyto poskytovatele tokenů nemůže pracovat s.  
  
-   Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel nabízí podrobné informace do kdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta používá přihlašovací údaje.  
  
-   Pokud vytváříte vlastní token.  
  
 Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatele tokenů, který umožňuje získat z mimo tokenu SAML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta, který se má použít.  
  
 Tento příklad znázorňuje to Shrneme, následující:  
  
-   Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.  
  
-   Jak lze předat tokenu SAML přihlašovací údaje vlastního klienta.  
  
-   Jak se poskytují tokenu SAML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework klienta.  
  
-   Jak server ověření klienta pomocí certifikátu X.509 serveru.  
  
 Službu zpřístupní dva koncové body pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standardní `wsFederationHttpBinding`, který používá zabezpečení zpráv. Jeden koncový bod očekává klienta k ověřování SAML token, který používá symetrického klíče doklad při dalších očekává klienta k ověření pomocí tokenu SAML, která používá asymetrické doklad klíč. Služba nakonfiguruje taky certifikát služby pomocí `serviceCredentials` chování. `serviceCredentials` Chování umožňuje nakonfigurovat certifikát služby. Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy. Následující konfigurace odkazuje "localhost" certifikát nainstalován při instalaci je ukázka, jak je popsáno v pokynů pro instalaci na konci tohoto tématu. `serviceCredentials` Chování můžete také konfigurovat certifikáty, které jsou důvěryhodní k podepisování tokenů SAML. Následující konfigurace odkazuje 'Alice' certifikát nainstalován během vzorku.  
  
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
  
 Následující kroky ukazují, jak vytvořit vlastní zprostředkovatele tokenu SAML a integrovat s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: framework zabezpečení:  
  
1.  Napište vlastní zprostředkovatele tokenu SAML.  
  
     Ukázka implementuje vlastního zprostředkovatele tokenu SAML, který vrátí token zabezpečení založené na výrazu SAML, který je zadán v době konstrukce.  
  
     K provedení této úlohy, poběží vlastní zprostředkovatel tokenu je odvozený od <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda. Tato metoda vytvoří a vrátí novou `SecurityToken`.  
  
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
  
2.  Zápis tokenu správce vlastní zabezpečení.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Třída se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda. Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátoru tokenů, ale nejsou uvedené v této ukázce. V této ukázkové vlastní zabezpečení Správce tokenu dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` je požadovaná metoda vrátí vlastního zprostředkovatele tokenu SAML, když předaný tokenu požadavky označuje, že tokenu SAML. Pokud třída pověření klienta (viz krok 3) nebyl zadán kontrolní výrazy, Správce tokenů zabezpečení vytvoří odpovídající instance.  
  
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
  
3.  Zápis vlastních klientských pověření.  
  
     Třída pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátoru tokenů zabezpečení.  
  
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
  
4.  Konfigurace klienta pro použití vlastního klienta přihlašovací údaje.  
  
     Ukázka odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta, takže klient může používat přihlašovací údaje vlastního klienta.  
  
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
  
 Ve službě zobrazí se deklarace identity spojené s volajícím. Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat součástí této ukázky můžete nakonfigurovat server se příslušný certifikát spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci.  
  
-   Vytvoření certifikátu serveru:  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota v tomto souboru batch je localhost.  
  
     Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Vytváření vystavitele certifikátu.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit vystavitele certifikát, který chcete použít. `%USER_NAME%` Proměnná Určuje název vystavitele. Změňte tuto proměnnou k určení svůj vlastní název vystavitele. Výchozí hodnota v tomto souboru batch je Alice.  
  
     Certifikát je uložen v tomto úložišti pod CurrentUser umístění úložiště.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace vystavitele certifikátu do úložiště důvěryhodných certifikátů serveru.  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů serveru pomocí vystavitele certifikátu se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku spuštěného s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou pro binární soubory služby.  
  
2.  Zkopírujte soubory programu služby do adresáře služby na počítači se službou. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor Service.exe.config musí být aktualizovány tak, aby odrážela tento nový název certifikátu. Certifikát serveru můžete vytvořit úpravou Setup.bat dávkového souboru. Všimněte si, že soubor setup.bat musí spustit v okně příkazového řádku Visual Studio s oprávněními správce. Je nutné nastavit `%SERVER_NAME%` proměnné na hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Tento krok není nutné, pokud je certifikát serveru vydána klienta důvěryhodného vystavitele.  
  
5.  V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.  
  
6.  Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
7.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.  
  
10. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
## <a name="see-also"></a>Viz také
