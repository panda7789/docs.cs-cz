---
title: Trvale vydaný poskytovatel tokenu
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144744"
---
# <a name="durable-issued-token-provider"></a>Trvale vydaný poskytovatel tokenu
Tato ukázka ukazuje, jak implementovat vlastního klienta vydaného zprostředkovatele tokenu.  
  
## <a name="discussion"></a>Diskuse  
 Zprostředkovatel tokenů v systému Windows Communication Foundation (WCF) se používá k zadání pověření do infrastruktury zabezpečení. Zprostředkovatel tokenu obecně zkontroluje cíl a vydá příslušná pověření, aby infrastruktura zabezpečení mohla zabezpečit zprávu. WCF je dodáván s poskytovatelem tokenu CardSpace. Vlastní zprostředkovatelé tokenů jsou užitečné v následujících případech:  
  
- Pokud máte úložiště pověření, které předdefinované zprostředkovatel tokenu nelze pracovat s.  
  
- Pokud chcete poskytnout vlastní mechanismus pro transformaci pověření z bodu, kdy uživatel poskytuje podrobnosti, když klient WCF používá pověření.  
  
- Pokud vytváříte vlastní token.  
  
 Tato ukázka ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který ukládá tokeny vydané službou TOKEN (STS).  
  
 Chcete-li shrnout, tato ukázka ukazuje následující:  
  
- Jak lze klienta nakonfigurovat pomocí vlastního zprostředkovatele tokenu.  
  
- Jak vydané tokeny mohou být uloženy do mezipaměti a poskytnuty klientovi WCF.  
  
- Způsob ověření serveru klientem pomocí certifikátu X.509 serveru.  
  
 Tato ukázka se skládá z programu klientské konzole (Client.exe), programu konzoly služby tokenu zabezpečení (Securitytokenservice.exe) a programu konzoly služby (Service.exe). Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje matematické operace (sčítání, odčítání, násobení a dělení). Klient získá token zabezpečení ze služby tokenů zabezpečení (STS) a provede synchronní požadavky na službu pro danou operaci matematiky a odpovědi služby s výsledkem. Aktivita klienta je viditelná v okně konzoly.  
  
> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka zpřístupňuje smlouvu ICalculator pomocí [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfigurace této vazby na straně klienta je uvedena v následujícím kódu.  
  
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
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit. V této ukázce se používá zabezpečení `message` zpráv, což je důvod, proč `wsFederationHttpBinding` je prvek zadán uvnitř `security` prvku . `wsFederationHttpBinding` Prvek `issuer` `wsFederationHttpBinding` uvnitř `message` prvku `wsFederationHttpBinding` určuje adresu a vazbu pro službu tokenů zabezpečení, která vydává klientovi token zabezpečení, aby se klient mohl ověřit na službě Calculator.  
  
 Konfigurace této vazby na službu je zobrazena v následujícím kódu.  
  
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
  
 Na `security` elementu `wsFederationHttpBinding`, `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit. V této ukázce se používá zabezpečení `message` zpráv, což je důvod, proč `wsFederationHttpBinding` je prvek zadán uvnitř `security` prvku . `wsFederationHttpBinding` Prvek `issuerMetadata` `wsFederationHttpBinding` uvnitř elementu `message` `wsFederationHttpBinding` určuje adresu a identitu pro koncový bod, který lze použít k načtení metadat pro službu tokenů zabezpečení.  
  
 Chování služby je zobrazeno v následujícím kódu.  
  
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
  
 Prvek `issuedTokenAuthentication` uvnitř `serviceCredentials` prvku umožňuje službě určit omezení tokenů, které umožňuje klientům prezentovat během ověřování. Tato konfigurace určuje, že tokeny podepsané certifikátem, jehož název subjektu je CN=STS, jsou službou přijímány.  
  
 Služba tokenů zabezpečení zpřístupňuje jeden koncový bod pomocí standardní wsHttpBinding. Služba tokenů zabezpečení reaguje na požadavek klientů na tokeny a za předpokladu, že klient ověří pomocí účtu systému Windows, vydá token, který obsahuje uživatelské jméno klienta jako deklaraci v vydaném tokenu. Jako součást vytváření tokenu služba tokenu zabezpečení podepisuje token pomocí soukromého klíče přidruženého k certifikátu CN=STS. Kromě toho vytvoří symetrický klíč a šifruje jej pomocí veřejného klíče přidruženého k certifikátu CN=localhost. Při vrácení tokenu klientovi služba tokenu zabezpečení také vrátí symetrický klíč. Klient představuje vydaný token službě Kalkulačka a prokáže, že zná symetrický klíč podpisem zprávy pomocí tohoto klíče.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Vlastní pověření klienta a zprostředkovatel tokenů  
 Následující kroky ukazují, jak vyvinout vlastního zprostředkovatele tokenů, který ukládá do mezipaměti vydané tokeny a integrovat je s WCF: zabezpečení.  
  
### <a name="to-develop-a-custom-token-provider"></a>Vývoj vlastního zprostředkovatele tokenů  
  
1. Napište vlastního zprostředkovatele tokenu.  
  
     Ukázka implementuje vlastního zprostředkovatele tokenu, který vrátí token zabezpečení načtený z mezipaměti.  
  
     Chcete-li provést tento úkol, vlastní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> zprostředkovatel tokenu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> odvodí třídu a přepíše metodu. Tato metoda se pokusí získat token z mezipaměti, nebo pokud token nelze nalézt v mezipaměti, načte token od základního zprostředkovatele a pak uloží tento token do mezipaměti. V obou případech metoda `SecurityToken`vrátí .  
  
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
  
2. Napište vlastní správce tokenů zabezpečení.  
  
     Slouží <xref:System.IdentityModel.Selectors.SecurityTokenManager> k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní, <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> který je předán `CreateSecurityTokenProvider` v metodě. Správce tokenů zabezpečení se také používá k vytvoření ověřovačů tokenů a serializátorů tokenů, ale tyto nejsou zahrnuty v této ukázce. V této ukázce vlastní správce <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> tokenů zabezpečení `CreateSecurityTokenProvider` dědí z třídy a přepíše metodu vrátit vlastní zprostředkovatele tokenu, když požadavky na předané tokeny označují, že je požadován vydaný token.  
  
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
  
3. Napište vlastní pověření klienta.  
  
     Třída pověření klienta se používá k reprezentaci pověření, která jsou nakonfigurována pro proxy klienta a vytvoří správce tokenů zabezpečení, který se používá k získání ověřovacích tokenů, zprostředkovatelů tokenů a serializátorů tokenů.  
  
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
  
4. Implementujte mezipaměť tokenů. Ukázková implementace používá abstraktní základní třídu, jejímž prostřednictvím spotřebitelé dané mezipaměti tokenu interagují s mezipamětí.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     Aby klient mohl použít vlastní pověření klienta, ukázka odstraní výchozí třídu pověření klienta a poskytne novou třídu pověření klienta.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ukázku naleznete v následujících pokynech. Při spuštění ukázky je požadavek na token zabezpečení zobrazen v okně konzoly služby Token tokenu zabezpečení. Požadavky na operace a odpovědi jsou zobrazeny v oknech klienta a konzoly služby. Stisknutím klávesy ENTER v libovolném systému konzoly aplikaci vypněte.  
  
## <a name="the-setupcmd-batch-file"></a>Dávkový soubor Setup.cmd  
 Dávkový soubor Setup.cmd, který je součástí této ukázky, umožňuje nakonfigurovat server ovou službu a službu tokenů zabezpečení pomocí příslušných certifikátů pro spuštění samoobslužné aplikace. Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů CurrentUser/TrustedPeople. První certifikát má název subjektu CN =STS a používá služba tokenů zabezpečení k podepsání tokenů zabezpečení, které vydává klientovi. Druhý certifikát má název subjektu CN=localhost a služba Token security token používá k šifrování tajného klíče, aby ho služba mohla dešifrovat.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Spusťte soubor Setup.cmd a vytvořte požadované certifikáty.  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md). Ujistěte se, že jsou sestaveny všechny projekty v řešení (Shared, RSTRSTR, Service, SecurityTokenService a Client).  
  
3. Ujistěte se, že Service.exe a SecurityTokenService.exe jsou spuštěny s oprávněními správce.  
  
4. Spusťte soubor Client.exe.  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
1. Po dokončení spuštění ukázky spusťte soubor Cleanup.cmd ve složce ukázek.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
