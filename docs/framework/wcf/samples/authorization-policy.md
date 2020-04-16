---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463952"
---
# <a name="authorization-policy"></a>Zásada autorizace

Tato ukázka ukazuje, jak implementovat vlastní zásady autorizace deklarací a přidruženého správce autorizací vlastních služeb. To je užitečné, když služba provádí kontroly přístupu na základě deklarací nároku k operacím služby a před kontrolami přístupu uděluje volajícímu určitá práva. Tato ukázka ukazuje proces přidávání deklarací identity i proces pro provedení kontroly přístupu proti dokončené sadě deklarací. Všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány. Ve výchozím `wsHttpBinding` nastavení s vazbou se uživatelské jméno a heslo zadané klientem používají k přihlášení k platnému účtu systému Windows NT. Tato ukázka ukazuje, jak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> využít vlastní k ověření klienta. Kromě toho tato ukázka ukazuje ověření klienta pro službu pomocí certifikátu X.509. Tento příklad ukazuje <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementaci <xref:System.ServiceModel.ServiceAuthorizationManager>a , která mezi nimi udělují přístup ke konkrétním metodám služby pro konkrétní uživatele. Tato ukázka je založena na [uživatelské jméno zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale <xref:System.ServiceModel.ServiceAuthorizationManager> ukazuje, jak provést transformaci deklarace před voláním.

> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.

 V souhrnu tento vzorek ukazuje, jak:

- Klient může být ověřen pomocí uživatelského jména-hesla.

- Klienta lze ověřit pomocí certifikátu X.509.

- Server ověří pověření klienta proti `UsernamePassword` vlastní validátor.

- Server je ověřen pomocí certifikátu X.509 serveru.

- Server může <xref:System.ServiceModel.ServiceAuthorizationManager> řídit přístup k určitým metodám ve službě.

- Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Služba zpřístupňuje dva koncové body pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a smlouvy. Jedna vazba je `wsHttpBinding` konfigurována se standardní vazbou, která používá ověřování ws-security a uživatelského jména klienta. Druhá vazba je konfigurována se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a client certificate. Chování [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) určuje, že pověření uživatele mají být použita pro ověřování služby. Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu `findValue` vlastnosti jako atribut v [ \<>serviceCertificate ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

Každá konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy pro koncový bod služby, vazby a smlouvy. Vazby klienta jsou konfigurovány s příslušným režimem zabezpečení, `clientCredentialType` jak je v tomto případě specifikováno v [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a jak je uvedeno ve [ \<zprávě>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

Pro koncový bod založený na uživatelském jménu implementací klienta nastaví uživatelské jméno a heslo.

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

Pro koncový bod založený na certifikátu implementace klienta nastaví klientský certifikát, který se má použít.

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

Tato ukázka <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> používá vlastní ověření uživatelských jmen a hesel. Ukázka implementuje `MyCustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>odvozené z . Další informace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> naleznete v dokumentaci. Pro účely prokázání integrace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>s , tento vlastní validátor <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> ukázka implementuje metodu přijmout uživatelské jméno a heslo dvojice, kde uživatelské jméno odpovídá heslo, jak je znázorněno v následujícím kódu.

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

Jakmile je validátor implementován v kódu služby, musí být hostitel služby informován o instanci validátoru, která má být používána. To se provádí pomocí následujícího kódu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Nebo můžete udělat totéž v konfiguraci:

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

Windows Communication Foundation (WCF) poskytuje bohatý model založený na deklaracích identity pro provádění kontrol přístupu. Objekt <xref:System.ServiceModel.ServiceAuthorizationManager> se používá k provedení kontroly přístupu a určení, zda deklarace přidružené ke klientovi splňují požadavky nezbytné pro přístup k metodě služby.

Pro účely demonstrace tato ukázka ukazuje <xref:System.ServiceModel.ServiceAuthorizationManager> implementaci, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> která implementuje metodu, která umožňuje uživateli přístup k metodám založeným na deklaracích typu, `http://example.com/claims/allowedoperation` jehož hodnota je identifikátor URI akce operace, která může být volána.

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

Jakmile je <xref:System.ServiceModel.ServiceAuthorizationManager> vlastní implementována, hostitel služby musí být informován o <xref:System.ServiceModel.ServiceAuthorizationManager> použití. To se provádí tak, jak je znázorněno v následujícím kódu.

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodou k implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> je metoda.

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

Předchozí kód ukazuje, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jak metoda kontroluje, že nebyly přidány žádné nové deklarace identity, které ovlivňují zpracování a přidá konkrétní deklarace identity. Deklarace, které jsou povoleny jsou získány z `GetAllowedOpList` metody, která je implementována vrátit konkrétní seznam operací, které uživatel může provádět. Zásady autorizace přidá deklarace identity pro přístup k určité operaci. To se později <xref:System.ServiceModel.ServiceAuthorizationManager> používá k provedení rozhodnutí o kontrole přístupu.

Jakmile je <xref:System.IdentityModel.Policy.IAuthorizationPolicy> vlastní implementována, hostitel služby musí být informován o zásadách autorizace použít.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Klient úspěšně volá Add, Odečíst a Více metod a získá zprávu "Přístup je odepřen" při pokusu o volání Divide metoda. Stisknutím klávesy ENTER v okně klienta vypněte klienta.

## <a name="setup-batch-file"></a>Instalační dávkový soubor

Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru.

Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci:

- Vytvoření certifikátu serveru.

    Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit. Proměnná %SERVER_NAME% určuje název serveru. Změňte tuto proměnnou a zadejte vlastní název serveru. Výchozí hodnota je localhost.

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

    Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty, které jsou generovány programem Makecert.exe, nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem pomocí certifikátu serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Vytvoření klientského certifikátu.

    Následující řádky z dávkového souboru Setup.bat vytvoří klientský certifikát, který má být použit. Proměnná %USER_NAME% určuje název serveru. Tato hodnota je nastavena na "test1", protože toto je název `IAuthorizationPolicy` hledá. Pokud změníte hodnotu %USER_NAME%, musíte změnit `IAuthorizationPolicy.Evaluate` odpovídající hodnotu metody.

    Certifikát je uložen v úložišti Moje (osobní) pod umístěním úložiště CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.

    Následující řádky v dávkovém souboru Setup.bat zkopírují klientský certifikát do úložiště důvěryhodných osob. Tento krok je vyžadován, protože certifikáty, které jsou generovány programem Makecert.exe, nejsou serverovým systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu – například certifikát emitovaný společností Microsoft – není tento krok naplnění úložiště certifikátů serveru klientským certifikátem vyžadován.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.

> [!NOTE]
> Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači

1. Otevřete příkazový řádek pro vývojáře pro Visual Studio s oprávněními správce a spusťte *soubor Setup.bat* z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře pro sady Visual Studio. Proměnná prostředí PATH nastavená v příkazovém řádku vývojáře pro sadu Visual Studio odkazuje na adresář, který obsahuje spustitelné soubory vyžadované skriptem *Setup.bat.*

1. Spusťte soubor Service.exe ze *služby\bin*.

1. Spusťte soubor Client.exe z *\client\bin*. Aktivita klienta je zobrazena v aplikaci klientské konzole.

Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích

1. Vytvořte adresář v počítači služby.

2. Zkopírujte soubory servisních programů z *\service\bin* do adresáře v počítači služby. Do servisního počítače zkopírujte také soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat.

3. Vytvořte v klientském počítači adresář pro binární soubory klienta.

4. Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.

5. Na serveru spusťte `setup.bat service` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce.

    Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem *Service.cer*.

6. Upravte *service.exe.config* tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v>serviceCertificate), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače. Změňte také **název** \<počítače ve\<službě>/ baseAddresses> element z localhost na plně kvalifikovaný název počítače služby.

7. Zkopírujte soubor *Service.cer* z adresáře služby do klientského adresáře v klientském počítači.

8. Na straně klienta spusťte `setup.bat client` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce.

    Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem **test1** a exportuje klientský certifikát do souboru s názvem *Client.cer*.

9. V souboru *Client.exe.config* v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. To provést nahrazením **localhost** plně kvalifikovaný název domény serveru.

10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.

11. Na straně klienta spusťte *soubor ImportServiceCert.bat* v příkazovém řádku pro vývojáře pro aplikaci Visual Studio otevřenou s oprávněními správce.

    Tím se importuje certifikát služby ze souboru Service.cer do úložiště **CurrentUser - TrustedPeople.**

12. Na serveru spusťte *soubor ImportClientCert.bat* v příkazovém řádku pro vývojáře pro aplikaci Visual Studio otevřenou s oprávněními správce.

    Tím se klientský certifikát importuje ze souboru Client.cer do úložiště **LocalMachine - TrustedPeople.**

13. V počítači serveru spusťte service.exe z okna příkazového řádku.

14. V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.

    Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Vyčistěte po vzorku

Chcete-li vyčistit po vzorku, spusťte *Cleanup.bat* ve složce ukázky po dokončení spuštění ukázky. Tím odeberete certifikáty serveru a klienta z úložiště certifikátů.

> [!NOTE]
> Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF, které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .
