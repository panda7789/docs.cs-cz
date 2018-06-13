---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 145faaae709119708240863f85eb5352fb2c5a1b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807548"
---
# <a name="durable-issued-token-provider"></a>Trvale vydaný poskytovatel tokenu
Tento příklad ukazuje, jak implementovat vlastní klienta vydaný Poskytovatel tokenu.  
  
## <a name="discussion"></a>Diskusní  
 Zprostředkovatel tokenu ve Windows Communication Foundation (WCF) slouží k zadání přihlašovacích údajů ke Infrastruktura zabezpečení. Zprostředkovatel tokenu obecně prozkoumá cíl a problémy vhodné přihlašovací údaje, aby infrastruktura zabezpečení můžete zabezpečit zprávy. WCF se dodává s [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu. Vlastní poskytovatele tokenů jsou užitečné v následujících případech:  
  
-   Pokud máte úložiště přihlašovacích údajů, která předdefinované zprostředkovatel tokenu nemůže pracovat s.  
  
-   Pokud chcete zadat vlastní vlastní mechanismus pro transformaci přihlašovací údaje z bodu, když uživatel poskytuje podrobnosti pro případ použití klienta WCF přihlašovací údaje.  
  
-   Pokud vytváříte vlastní token.  
  
 Tento příklad ukazuje, jak vytvořit vlastní zprostředkovatel tokenu, který ukládá do mezipaměti tokeny vydané podle zabezpečení tokenu služby (STS).  
  
 Tento příklad znázorňuje to Shrneme, následující:  
  
-   Jak klienta můžete nakonfigurovat vlastní zprostředkovatele tokenu.  
  
-   Jak lze do mezipaměti a zadaný pro klienta WCF vystavené tokeny.  
  
-   Jak server ověření klienta pomocí certifikátu X.509 serveru.  
  
 Tato ukázka se skládá z konzoly programu klienta (Client.exe), program konzoly služby tokenů zabezpečení (Securitytokenservice.exe) a program konzoly služby (Service.exe). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit). Klient získá zabezpečení token z Security Token Service (STS) a zadává synchronní požadavků službou pro danou matematické operace a odpovědi služby s výsledkem. Činnost klienta je viditelný v okně konzoly.  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka zpřístupní ICalculator kontrakt pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby v klientovi je zobrazena v následujícím kódu.  
  
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
  
 Na `security` element `wsFederationHttpBinding`, `mode` hodnota konfiguruje slouží kterém režimu zabezpečení. V této ukázce zabezpečení zprávy je používají, což je důvod, proč `message` element `wsFederationHttpBinding` je zadat v rámci `security` element `wsFederationHttpBinding`. `issuer` Element `wsFederationHttpBinding` uvnitř `message` element `wsFederationHttpBinding` Určuje adresu a vazeb pro služby tokenů zabezpečení, která vydá token zabezpečení klientovi, aby klient může ověřit kalkulačky Služba.  
  
 Konfigurace tuto vazbu na službu je vidět v následujícím kódu.  
  
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
  
 Na `security` element `wsFederationHttpBinding`, `mode` hodnota konfiguruje slouží kterém režimu zabezpečení. V této ukázce zabezpečení zprávy je používají, což je důvod, proč `message` element `wsFederationHttpBinding` je zadat v rámci `security` element `wsFederationHttpBinding`. `issuerMetadata` Element `wsFederationHttpBinding` uvnitř `message` element `wsFederationHttpBinding` určuje adrese a identitě pro koncový bod, který slouží k načtení metadat pro služby tokenů zabezpečení.  
  
 Chování pro službu je znázorněno v následujícím kódu.  
  
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
  
 `issuedTokenAuthentication` Element uvnitř `serviceCredentials` element umožňuje službě zadejte omezení umožňuje klientům k dispozici při ověřování tokenů. Tato konfigurace určuje, že tokeny podepsaný certifikát, jehož název subjektu CN = přijímat jsou služby tokenů zabezpečení.  
  
 Služby tokenů zabezpečení zpřístupní jeden koncový bod pomocí standardní wsHttpBinding. Služby tokenů zabezpečení odpovídá na žádosti od klientů pro tokeny a zadaný klient se ověří pomocí účtu Windows, vydá token, který obsahuje jméno uživatele klienta jako deklaraci v vydaných tokenu. Při vytváření tokenu služby tokenu zabezpečení přihlásí token pomocí privátní klíč přidružený CN = certifikát služby tokenů zabezpečení. Kromě toho vytvoří symetrického klíče a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikátu. Při vracení token do klienta, služby tokenů zabezpečení také vrátí symetrický klíč. Klient uvede vystavený token, který má službu kalkulačky a prokáže, že zná symetrický klíč podepsáním zprávu s tímto klíčem.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Přihlašovací údaje vlastního klienta a zprostředkovatele tokenu  
 Následující kroky ukazují, jak vyvíjet vlastní zprostředkovatele tokenu, mezipamětí vystavené tokeny a integraci s použitím technologie WCF: zabezpečení.  
  
#### <a name="to-develop-a-custom-token-provider"></a>K vývoji vlastního zprostředkovatele tokenu  
  
1.  Napište vlastního zprostředkovatele tokenu.  
  
     Ukázka implementuje vlastní zprostředkovatele tokenů, který vrátí token zabezpečení načítat z mezipaměti.  
  
     K provedení této úlohy, poběží vlastní zprostředkovatel tokenu odvozuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda. Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nebyl nalezen v mezipaměti, načte token z výchozí zprostředkovatel a pak ukládá do mezipaměti tohoto tokenu. V obou případech metoda vrátí `SecurityToken`.  
  
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
  
2.  Zápis tokenu správce vlastní zabezpečení.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , je do ní předán v `CreateSecurityTokenProvider` metoda. Správce tokenu zabezpečení se také používá k vytvoření tokenu ověřovací data a serializátorů tokenu, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` je požadovaná metoda vrátí vlastního zprostředkovatele tokenu, když předaný tokenu požadavky označuje, že vystavený token.  
  
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
  
3.  Zápis vlastních klientských pověření.  
  
     Třídy pověření klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátorů tokenu zabezpečení.  
  
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
  
4.  Implementujte mezipamětí tokenů. Ukázka implementace používá abstraktní základní třída, pomocí kterého se příjemci daného tokenu mezipaměti interakci s mezipamětí.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Vzorek pro klienta k použití pověření vlastní klienta, odstraní výchozí třídu pověření klienta a poskytuje novou třídu pověření klienta.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Přečtěte si následující pokyny ke spuštění ukázky. Při spuštění vzorového žádost o token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení. Operace požadavky a odpovědi se zobrazují v oknech konzoly klienta a služby. Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd dávkového souboru  
 Dávkový soubor Setup.cmd součástí této ukázky můžete nakonfigurovat server a služby tokenů zabezpečení s příslušnými certifikáty spuštění aplikace s vlastním hostováním. Dávkový soubor vytvoří dva certifikáty, že oba seznamy v CurrentUser/TrustedPeople úložiště certifikátů. První certifikát obsahuje název subjektu z CN = služby tokenů zabezpečení a služby tokenů zabezpečení používané k podepisování tokenů zabezpečení, které vystavuje klientovi. Druhý certifikát obsahuje název subjektu z CN = localhost a slouží k šifrování tajného klíče, aby služba ho dešifrovat pomocí služby tokenů zabezpečení.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Spusťte soubor Setup.cmd vytvořit požadované certifikáty.  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Ujistěte se, že všechny projekty v řešení jsou vytvořeny (sdílené, RSTRSTR, služby, SecurityTokenService a klient).  
  
3.  Zkontrolujte, zda Service.exe a SecurityTokenService.exe jsou obě spuštěn s oprávněními správce.  
  
4.  Spusťte Client.exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.cmd ve složce Ukázky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a>Viz také
