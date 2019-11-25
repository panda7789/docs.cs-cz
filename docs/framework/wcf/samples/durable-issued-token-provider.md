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
# <a name="durable-issued-token-provider"></a>Trvale vydaný poskytovatel tokenu
Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenu vydaných klientů.  
  
## <a name="discussion"></a>Účely  
 Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů do infrastruktury zabezpečení. Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu. WCF se dodává se zprostředkovatelem tokenů služby CardSpace. Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:  
  
- Máte úložiště přihlašovacích údajů, se kterým nemůže integrovaný zprostředkovatel tokenů pracovat s nástrojem.  
  
- Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne podrobnosti o tom, kdy klient služby WCF používá pověření.  
  
- Pokud vytváříte vlastní token.  
  
 V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který ukládá tokeny do mezipaměti, které vystavuje služba tokenů zabezpečení (STS).  
  
 Pro Shrnutí Tato ukázka demonstruje následující:  
  
- Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.  
  
- Jak mohou být vydávané tokeny uloženy do mezipaměti a poskytnuty klientovi WCF.  
  
- Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.  
  
 Tato ukázka se skládá z programu klientské konzoly (Client. exe), programu konzoly služby tokenu zabezpečení (SecurityTokenService. exe) a programu konzoly služby (Service. exe). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient získá token zabezpečení ze služby tokenu zabezpečení (STS) a provede synchronní požadavky služby pro danou matematickou operaci a odpověď služby s výsledkem. Aktivita klienta se zobrazí v okně konzoly.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka zveřejňuje kontrakt ICalculator pomocí [\<WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby na klientovi je uvedena v následujícím kódu.  
  
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
  
 U `security`ho prvku `wsFederationHttpBinding`hodnota `mode` konfiguruje, který režim zabezpečení by měl být použit. V této ukázce se používá zabezpečení zpráv, což je důvod, proč je `message` element `wsFederationHttpBinding` zadán uvnitř `security` elementu `wsFederationHttpBinding`. Prvek `issuer` `wsFederationHttpBinding` uvnitř `message` elementu `wsFederationHttpBinding` Určuje adresu a vazbu pro službu tokenu zabezpečení, která vydává token zabezpečení pro klienta, aby se klient mohl ověřit ve službě kalkulačky.  
  
 Konfigurace této vazby ve službě je uvedena v následujícím kódu.  
  
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
  
 U `security`ho prvku `wsFederationHttpBinding`hodnota `mode` konfiguruje, který režim zabezpečení by měl být použit. V této ukázce se používá zabezpečení zpráv, což je důvod, proč je `message` element `wsFederationHttpBinding` zadán uvnitř `security` elementu `wsFederationHttpBinding`. Prvek `issuerMetadata` `wsFederationHttpBinding` uvnitř `message` elementu `wsFederationHttpBinding` Určuje adresu a identitu koncového bodu, který lze použít k načtení metadat pro službu tokenů zabezpečení.  
  
 Chování služby se zobrazí v následujícím kódu.  
  
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
  
 Element `issuedTokenAuthentication` uvnitř elementu `serviceCredentials` umožňuje službě určovat omezení pro tokeny, které umožňuje klientům prezentovat během ověřování. Tato konfigurace určuje, že služba přijímá tokeny podepsané certifikátem, jehož název subjektu je CN = STS.  
  
 Služba tokenů zabezpečení zpřístupňuje jeden koncový bod pomocí standardu wsHttpBinding. Služba tokenů zabezpečení reaguje na žádosti od klientů na tokeny a za předpokladu, že se klient ověřuje pomocí účtu systému Windows, vydá token, který obsahuje uživatelské jméno klienta jako deklaraci identity v vystaveném tokenu. V rámci vytváření tokenu podepisuje služba tokenů zabezpečení token pomocí privátního klíče přidruženého k certifikátu CN = STS. Kromě toho vytvoří symetrický klíč a zašifruje ho pomocí veřejného klíče přidruženého k certifikátu CN = localhost. Při vrácení tokenu klientovi vrátí služba tokenů zabezpečení také symetrický klíč. Klient prezentuje vydaný token službě kalkulačky a ukáže, že zná symetrický klíč podepsáním zprávy pomocí tohoto klíče.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Vlastní přihlašovací údaje klienta a Poskytovatel tokenů  
 Následující kroky ukazují, jak vyvíjet vlastního poskytovatele tokenů, který ukládá do mezipaměti vydané tokeny a integruje ho s WCF: Security.  
  
### <a name="to-develop-a-custom-token-provider"></a>Vývoj vlastního poskytovatele tokenů  
  
1. Napište vlastního poskytovatele tokenů.  
  
     Ukázka implementuje vlastního poskytovatele tokenu, který vrací token zabezpečení načtený z mezipaměti.  
  
     Chcete-li provést tuto úlohu, zprostředkovatel vlastního tokenu odvozuje třídu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> a přepíše metodu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>. Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nejde v mezipaměti najít, načte token od základního poskytovatele a pak tento token uloží do mezipaměti. V obou případech metoda vrací `SecurityToken`.  
  
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
  
2. Napsat vlastního správce tokenů zabezpečení.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, která je předána do této metody `CreateSecurityTokenProvider`. Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátorů tokenů, ale u těch se tato ukázka nezabývá. V této ukázce správce vlastního tokenu zabezpečení dědí z třídy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> a přepíše metodu `CreateSecurityTokenProvider`, aby vrátila vlastního zprostředkovatele tokenu, když požadavky na předané tokeny naznačují, že vydaný token je vyžádán.  
  
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
  
3. Napište vlastní přihlašovací údaje klienta.  
  
     Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátorů tokenů.  
  
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
  
4. Implementujte mezipaměť tokenů. Ukázková implementace používá abstraktní základní třídu, přes kterou uživatelé dané mezipaměti tokenů komunikují s mezipamětí.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     Aby mohl klient používat vlastní přihlašovací údaje klienta, odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Pokud chcete ukázku spustit, přečtěte si následující pokyny. Při spuštění ukázky se žádost o token zabezpečení zobrazí v okně konzoly služby tokenu zabezpečení. Požadavky na operace a odpovědi se zobrazí v oknech klienta a služby Service Console. Ukončete aplikaci stisknutím klávesy ENTER v libovolném z oken konzoly.  
  
## <a name="the-setupcmd-batch-file"></a>Dávkový soubor Setup. cmd  
 Dávkový soubor Setup. cmd, který je součástí této ukázky, vám umožní nakonfigurovat službu token serveru a zabezpečení pomocí relevantních certifikátů pro spuštění samoobslužné aplikace. Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů CurrentUser/TrustedPeople. První certifikát má název subjektu CN = STS a služba tokenů zabezpečení ji používá k podepsání tokenů zabezpečení, které vystaví klientovi. Druhý certifikát má název subjektu CN = localhost a používá ho služba tokenů zabezpečení k šifrování tajného klíče, aby ho služba mohla dešifrovat.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li vytvořit požadované certifikáty, spusťte soubor Setup. cmd.  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Ujistěte se, že jsou všechny projekty v řešení sestaveny (Shared, RSTRSTR, Service, SecurityTokenService a Client).  
  
3. Zajistěte, aby byly služby Service. exe a SecurityTokenService. exe spuštěné s oprávněními správce.  
  
4. Spusťte soubor Client. exe.  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Až skončíte s ukázkou, spusťte na složce Samples Cleanup. cmd.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
