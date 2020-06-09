---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 5b93f7e05261d9770650335160ddb56404aed94d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585503"
---
# <a name="authorization-policy"></a>Zásada autorizace

Tato ukázka předvádí, jak implementovat vlastní zásady autorizace deklarací identity a přidruženého vlastního Správce autorizací služby. To je užitečné, když služba provádí kontroly přístupu na základě deklarací identity na operace služeb a před kontrolou přístupu uděluje volajícím určitá práva. V této ukázce se zobrazuje jak proces přidávání deklarací identity, tak i proces pro kontrolu přístupu na finalizaci sady deklarací. Všechny zprávy aplikací mezi klientem a serverem jsou podepsané a šifrované. Ve výchozím nastavení s `wsHttpBinding` vazbou se k přihlášení k platnému účtu systému Windows NT používá uživatelské jméno a heslo dodávané klientem. Tato ukázka předvádí, jak použít vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> pro ověření klienta. Kromě této ukázky se zobrazuje klient ověřující službu pomocí certifikátu X. 509. Tato ukázka předvádí implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a <xref:System.ServiceModel.ServiceAuthorizationManager> , která mezi nimi uděluje přístup ke konkrétním metodám služby pro konkrétní uživatele. Tato ukázka je založena na [uživatelském jménu zabezpečení zprávy](message-security-user-name.md), ale ukazuje, jak provést transformaci deklarace před <xref:System.ServiceModel.ServiceAuthorizationManager> voláním.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

 V souhrnu Tato ukázka předvádí, jak:

- Klienta lze ověřit pomocí uživatelského jména a hesla.

- Klienta lze ověřit pomocí certifikátu X. 509.

- Server ověří pověření klienta proti vlastnímu `UsernamePassword` validátoru.

- Server je ověřený pomocí certifikátu X. 509 serveru.

- Server může používat <xref:System.ServiceModel.ServiceAuthorizationManager> k řízení přístupu k určitým metodám ve službě.

- Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy> .

Služba zpřístupňuje dva koncové body pro komunikaci se službou, které jsou definovány pomocí konfiguračního souboru App. config. Každý koncový bod se skládá z adresy, vazby a kontraktu. Jedna vazba je nakonfigurovaná se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a uživatelské jméno klienta. Druhá vazba je nakonfigurovaná se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a klientský certifikát. [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Určuje, že pověření uživatele má být použito pro ověřování služby. Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` vlastnosti jako `findValue` atribut v [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

Každá konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurována s odpovídajícím režimem zabezpečení, jak je uvedeno v tomto případě v [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a, `clientCredentialType` jak je uvedeno v části [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

Pro koncový bod uživatelského jména nastaví implementace klienta uživatelské jméno a heslo, které se má použít.

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

Pro koncový bod založený na certifikátu nastaví implementace klienta klientský certifikát, který se má použít.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

Tato ukázka používá vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ověření uživatelských jmen a hesel. Ukázka implementuje `MyCustomUserNamePasswordValidator` odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> . Další informace najdete v dokumentaci <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> . Pro účely demonstrování integrace s nástrojem <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Tato ukázka vlastního validátoru implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu pro příjem párů uživatelského jména a hesla, kde uživatelské jméno odpovídá heslu, jak je znázorněno v následujícím kódu.

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

Po implementaci ověřovacího modulu v kódu služby musí být hostitel služby informován o instanci validátoru, která se má použít. To se provádí pomocí následujícího kódu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Nebo můžete stejnou věc provést v konfiguraci:

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) poskytuje bohatý model založený na deklaracích pro provádění kontrol přístupu. <xref:System.ServiceModel.ServiceAuthorizationManager>Objekt se používá k provedení kontroly přístupu a určení, zda deklarace přidružené k klientovi splňují požadavky nezbytné pro přístup k metodě služby.

Pro účely ukázky ukazuje Tato ukázka implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> , která implementuje metodu, která <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> umožňuje uživateli přístup k metodám na základě deklarací typu, `http://example.com/claims/allowedoperation` jejichž hodnota je identifikátor URI akce operace, která může být volána.

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

Po implementaci vlastního uživatelského <xref:System.ServiceModel.ServiceAuthorizationManager> rozhraní musí být hostitel služby informován o tom, jak se <xref:System.ServiceModel.ServiceAuthorizationManager> má použít. To se provádí, jak je znázorněno v následujícím kódu.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metoda, která má být implementována, je <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda.

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

Předchozí kód ukazuje <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> , jak metoda kontroluje, zda nebyly přidány žádné nové deklarace identity, které mají vliv na zpracování a přidávají konkrétní deklarace identity. Deklarace, které jsou povoleny, jsou získány z `GetAllowedOpList` metody, která je implementována k vrácení konkrétního seznamu operací, které může uživatel provést. Zásady autorizace přidávají deklarace identity pro přístup k určité operaci. Tato služba je později používána <xref:System.ServiceModel.ServiceAuthorizationManager> k rozhodování o kontrole přístupu.

Po implementaci vlastního uživatelského <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní musí být hostitel služby informován o zásadách autorizace, které se mají použít.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Klient úspěšně volá metodu Add, odečíst a více metod a při pokusu o volání metody dělení Získá zprávu "přístup byl odepřen". V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru

Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.

Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:

- Vytváří se certifikát serveru.

    Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná% SERVER_NAME% Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota je localhost.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

    Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty generované pomocí nástroje MakeCert. exe pro klientský systém implicitně nedůvěřují. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Vytváří se klientský certifikát.

    Následující řádky z dávkového souboru Setup. bat vytvoří klientský certifikát, který se má použít. Proměnná% USER_NAME% Určuje název serveru. Tato hodnota je nastavená na "test1", protože se jedná o název, který `IAuthorizationPolicy` hledá. Pokud změníte hodnotu% USER_NAME%, je nutné změnit odpovídající hodnotu v `IAuthorizationPolicy.Evaluate` metodě.

    Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Probíhá instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.

    Následující řádky v dávkovém souboru Setup. bat kopírují klientský certifikát do úložiště důvěryhodných osob. Tento krok je povinný, protože serverové systémy, které jsou vygenerované pomocí nástroje MakeCert. exe, nejsou implicitně důvěryhodné. Pokud již máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu, například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů serveru pomocí klientského certifikátu není vyžadováno.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.

> [!NOTE]
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte *Setup. bat* z ukázkové instalační složky. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio. Proměnná prostředí PATH nastavená v rámci Developer Command Prompt pro Visual Studio odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript *Setup. bat* .

1. Spusťte Service. exe z *service\bin*.

1. Spusťte soubor Client. exe z *\client\bin*. Aktivita klienta se zobrazí v klientské aplikaci konzoly.

Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači

1. Vytvořte adresář na počítači služby.

2. Zkopírujte programové soubory služby z *\service\bin* do adresáře na počítači služby. Zkopírujte také soubory Setup. bat, Cleanup. bat, GetComputerName. vbs a ImportClientCert. bat do počítače služby.

3. Vytvořte v klientském počítači adresář pro binární soubory klienta.

4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.

5. Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.

    Při spuštění `setup.bat` s `service` argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem *Service. cer*.

6. Upravte soubor *Service. exe. config* tak, aby odrážel nový název certifikátu (v `findValue` atributu), [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) který je stejný jako plně kvalifikovaný název počítače. Také změňte název **počítače** v \<service> / \<baseAddresses> elementu z localhost na plně kvalifikovaný název počítače služby.

7. Zkopírujte soubor *Service. cer* z adresáře služby do adresáře klienta v klientském počítači.

8. V klientovi spusťte `setup.bat client` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.

    Při spuštění `setup.bat` s `client` argumentem se vytvoří klientský certifikát s názvem **test1** a exportuje se klientský certifikát do souboru s názvem *Client. cer*.

9. V souboru *Client. exe. config* v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Provedete to tak, že nahradíte **localhost** názvem domény, který má plně kvalifikovaný název domény serveru.

10. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.

11. Na straně klienta spusťte *ImportServiceCert. bat* v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.

    Tím se certifikát služby importuje ze souboru Service. cer do úložiště **CurrentUser-TrustedPeople** .

12. Na serveru spusťte *ImportClientCert. bat* v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.

    Tím se certifikát klienta importuje ze souboru Client. cer do úložiště **LocalMachine-TrustedPeople** .

13. V počítači serveru spusťte z okna příkazového řádku Service. exe.

14. V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.

    Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Vyčištění po ukázce

Po dokončení ukázky spusťte *Cleanup. bat* ve složce Samples, až skončíte s jeho spuštěním. Tím dojde k odebrání certifikátů serveru a klienta z úložiště certifikátů.

> [!NOTE]
> Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky WCF, které používají certifikáty napříč počítači, ujistěte se, že jste vymazali certifikáty služby nainstalované v úložišti CurrentUser-TrustedPeople. Použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .
