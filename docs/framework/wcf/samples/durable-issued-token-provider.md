---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: bfe8f8bb8c3775760bc69031e338a156d690ab25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487604"
---
# <a name="durable-issued-token-provider"></a>Trvale vydaný poskytovatel tokenu
Tento příklad ukazuje, jak implementovat vlastní klienta vydaný Poskytovatel tokenu.  
  
## <a name="discussion"></a>Diskuse  
 Poskytovatel tokenu ve Windows Communication Foundation (WCF) slouží k zadání přihlašovacích údajů pro zabezpečení infrastruktury. Poskytovatel tokenu obecně zkontroluje cíl a problémů příslušné přihlašovací údaje tak, aby infrastruktura zabezpečení se dají zabezpečit zprávy. WCF se dodává s poskytovatelem token CardSpace. Vlastní poskytovatele tokenů jsou užitečné v následujících případech:  
  
- Pokud máte úložiště přihlašovacích údajů, které nelze použít předdefinovaný poskytovatel tokenů.  
  
- Pokud chcete poskytnout vlastní vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytuje podrobnosti pro případ použití přihlašovacích údajů klienta WCF.  
  
- Pokud vytváříte vlastní token.  
  
 Tento příklad ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který ukládá do mezipaměti tokenům vydaným službou tokenů zabezpečení služby (STS).  
  
 Souhrnně řečeno, tento příklad znázorňuje následující:  
  
- Jak klienta lze nakonfigurovat pomocí vlastního zprostředkovatele tokenů.  
  
- Jak vydané tokeny můžete uložit do mezipaměti a k dispozici klienta WCF.  
  
- Jak ověření serveru klientem pomocí certifikátu X.509 serveru.  
  
 Tento příklad se skládá z programu konzoly klienta (Client.exe), program konzoly služby tokenů zabezpečení (Securitytokenservice.exe) a služby konzolový program (Service.exe). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). Klient získá bezpečnostní token z tokenu služba zabezpečení (STS) a umožňuje synchronní žádosti o službu pro dané matematické operace a odpovědi služby k výsledku. Činnost klienta je vidět v okně konzoly.  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka poskytuje pomocí kontraktu ICalculator [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguraci této vazby v klientovi je znázorněno v následujícím kódu.  
  
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
  
 Na `security` prvek `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit. V této ukázce zabezpečení zprávy se používá, což je důvod, proč `message` prvek `wsFederationHttpBinding` je zadat v rámci `security` prvek `wsFederationHttpBinding`. `issuer` Prvek `wsFederationHttpBinding` uvnitř `message` prvek `wsFederationHttpBinding` Určuje adresu a vazbu pro službu tokenů zabezpečení, který vydá token zabezpečení do klienta tak, aby se klient může ověřit ke kalkulačce Služba.  
  
 Konfiguraci této vazby ve službě je znázorněno v následujícím kódu.  
  
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
  
 Na `security` prvek `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit. V této ukázce zabezpečení zprávy se používá, což je důvod, proč `message` prvek `wsFederationHttpBinding` je zadat v rámci `security` prvek `wsFederationHttpBinding`. `issuerMetadata` Prvek `wsFederationHttpBinding` uvnitř `message` prvek `wsFederationHttpBinding` určuje adrese a identitě pro koncový bod, který slouží k načtení metadat pro službu tokenů zabezpečení.  
  
 Chování služby je uvedeno v následujícím kódu.  
  
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
  
 `issuedTokenAuthentication` Element v rámci `serviceCredentials` element umožňuje službě a zadat omezení na tokeny, umožňuje klientům k dispozici během ověřování. Tato konfigurace určuje, že tokeny podepsán certifikátem, jehož název subjektu je CN = služby STS jsou změna přijata službou.  
  
 Služba tokenů zabezpečení poskytuje jeden koncový bod pomocí standardní wsHttpBinding. Služba tokenů zabezpečení odpoví na požadavek od klientů pro tokeny a pokud klient se ověří pomocí účtu Windows, vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity v vydaný token. Při vytváření tokenu, značky služby tokenu zabezpečení tokenu pomocí privátního klíče přidružené k CN = certifikátu STS. Kromě toho vytvoří symetrický klíč a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikát. V vrácením tokenu klientovi, služba tokenů zabezpečení také vrátí hodnotu symetrický klíč. Klient prezentuje vydaný token pro službu kalkulačky a prokáže, že zná symetrický klíč pomocí podepsání zprávy s tímto klíčem.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Přihlašovací údaje vlastního klienta a poskytovatel tokenů  
 Následující kroky ukazují, jak vývoj vlastního zprostředkovatele tokenů, že mezipaměť na vydané tokeny a integrace s použitím technologie WCF: zabezpečení.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Vývoj vlastního zprostředkovatele tokenů  
  
1. Napište vlastního zprostředkovatele tokenů.  
  
     Ukázka implementuje vlastního zprostředkovatele tokenů, který vrátí token zabezpečení načítat z mezipaměti.  
  
     K provedení této úlohy je odvozen vlastního zprostředkovatele tokenů <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metody. Tato metoda pokusí získat token z mezipaměti, nebo pokud token nebyl nalezen v mezipaměti, načte token z podkladového zprostředkovatele a potom ukládá do mezipaměti tohoto tokenu. V obou případech vrátí metoda `SecurityToken`.  
  
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
  
2. Správce tokenů zabezpečení vlastního zápisu.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je do ní předán v `CreateSecurityTokenProvider` metody. Správce tokenů zabezpečení se také používá k vytvoření ověřovací data tokenu a tokenu serializátory, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` požadovaná metoda vrátí vlastního zprostředkovatele tokenů, při úspěšné požadavky tokenu označuje, že vydaný token.  
  
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
  
3. Zápis vlastních klientských přihlašovacích údajů.  
  
     Třída přihlašovacích údajů klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří Správce tokenů, který se používá k získání poskytovatele tokenů ověřovací data tokenu a tokenu serializátory zabezpečení.  
  
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
  
4. Implementace mezipaměť tokenu. Ukázková implementace používá abstraktní základní třída, přes který příjemci daného mezipaměť tokenu pracovat s mezipamětí.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Klienti měli používat přihlašovací údaje, které vlastní vzorek odstraní výchozí třídu přihlašovacích údajů klienta a poskytuje novou třídu přihlašovacích údajů klienta.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Přečtěte si následující pokyny ke spuštění ukázky. Když spustíte ukázku, požadavek na token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení. Operace žádosti a odpovědi se zobrazují v oknech konzoly klienta a služby. Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd dávkového souboru  
 Dávkový soubor Setup.cmd zahrnuté v této ukázce umožňuje nakonfigurovat server a služba tokenů zabezpečení s příslušnými certifikáty ke spuštění aplikace v místním prostředí. Dávkový soubor se vytvoří dva certifikáty, že v CurrentUser/TrustedPeople úložiště certifikátů. První certifikát má název předmětu CN = STS a služba tokenů zabezpečení používá k podepisování tokenů zabezpečení, které vystavuje do klienta. Druhý certifikát má název předmětu CN = localhost a služba tokenů zabezpečení používá k šifrování tajného kódu tak, aby služba může dešifrovat.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Spusťte soubor Setup.cmd vytvořit požadované certifikáty.  
  
2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Ujistěte se, že jsou všechny projekty v řešení sestaveny, (sdílené, RSTRSTR, služby, služby SecurityTokenService a klient).  
  
3. Ujistěte se, že Service.exe a SecurityTokenService.exe se provozují s oprávněními správce.  
  
4. Spusťte Client.exe.  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1. Spusťte Cleanup.cmd ve složce samples po dokončení spuštění ukázky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
