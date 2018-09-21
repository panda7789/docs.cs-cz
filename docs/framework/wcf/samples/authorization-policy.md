---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 78ca42abfd2df56edeeb273fcd8ba585aa16f635
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508788"
---
# <a name="authorization-policy"></a>Zásada autorizace

Tento příklad ukazuje, jak implementovat zásady autorizace vlastních deklarací identity a přidružená služba vlastního Správce autorizací. To je užitečné, když služba usnadňující kontroly přístupu podle deklarací identity k operacím služby a před kontroly přístupu udělí volajícímu určitá práva. Tento příklad ukazuje obě proces přidávání deklarací identity, stejně jako proces pro provádění kontroly přístupu pro dokončené sadu deklarací identity. Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný. Ve výchozím nastavení se `wsHttpBinding` vazby, uživatelské jméno a heslo, které poskytl klient, slouží k přihlášení k platný účet systému Windows NT. Tato ukázka předvádí, jak využívat vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> k ověření klienta. Kromě toho tento příklad ukazuje ověřování do služby pomocí certifikátu X.509 klienta. Tento příklad ukazuje implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a <xref:System.ServiceModel.ServiceAuthorizationManager>, která mezi nimi udělit přístup na konkrétní metody služby pro konkrétní uživatele. Tato ukázka je založena na [zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale ukazuje, jak provádět transformace deklarací identity před verzí <xref:System.ServiceModel.ServiceAuthorizationManager> volána.

> [!NOTE]
> Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

 Stručně řečeno, tento příklad ukazuje, jak:

-   Klient lze ověřit pomocí uživatelského jména a hesla.

-   Klient lze ověřit pomocí certifikátu X.509.

-   Server ověří klienta přihlašovacích údajů, kteří vlastní `UsernamePassword` program pro ověření.

-   Server byl ověřovaný pomocí certifikátu X.509 serveru.

-   Server můžete použít <xref:System.ServiceModel.ServiceAuthorizationManager> pro řízení přístupu k určité metody ve službě.

-   Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Služba poskytuje dva koncové body služby pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontrakt. Jedna vazba konfigurována se standardní `wsHttpBinding` vazby, která používá ověřování uživatelským jménem WS-Security a klienta. Druhé vazby má nakonfigurovanou standardní `wsHttpBinding` vazby, která používá ověřování certifikátem WS-Security a klienta. [ \<Chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Určuje, že má být použit pro ověřování služby jsou přihlašovací údaje uživatele. Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` vlastnost jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

Konfigurace koncového bodu každá klient se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt. Vazba je klient nakonfigurovaný s režimem zabezpečení uvedené v tomto případě v [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a `clientCredentialType` podle [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).

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

Implementace klienta pro uživatele na základě názvu koncového bodu, nastaví uživatelské jméno a heslo pro použití.

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

Implementace klienta pro koncový bod pomocí certifikátu, nastaví klientský certifikát k použití.

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

Tato ukázka používá vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> k ověření uživatelského jména a hesla. Implementuje vzorek `MyCustomUserNamePasswordValidator`odvozenou z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. V dokumentaci <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace. Pro účely integrace s představením toho, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, tato ukázka vlastní validátor implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu tak, aby přijímal párů jméno/heslo uživatele kde uživatelské jméno odpovídá heslu, jak je znázorněno v následujícím kódu.

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

Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít. To se provádí pomocí následujícího kódu:

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Nebo můžete provést totéž v konfiguraci:

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) poskytuje bohaté možnosti založené na deklaracích model pro provádění kontroly přístupu. <xref:System.ServiceModel.ServiceAuthorizationManager> Objekt se používá k provádění kontroly přístupu a určit, jestli deklarace identity přidružené ke klientovi splňují požadavky potřebné pro přístup k metodě služby.

Pro demonstrační účely, tento příklad ukazuje implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> , který implementuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda umožňující uživateli přístup k metodám založené na deklaracích identity typu http://example.com/claims/allowedoperation jehož hodnota je identifikátor URI akce, která je operace mohou být volána.

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

Jednou vlastní <xref:System.ServiceModel.ServiceAuthorizationManager> je implementováno, hostitele služby musí být informováni o <xref:System.ServiceModel.ServiceAuthorizationManager> používat. Důvodem je, jak je znázorněno v následujícím kódu.

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metody k implementaci je <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody.

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

Předchozí kód ukazuje jak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda zkontroluje, že byly přidány žádné nové deklarace identity, která ovlivňují zpracování a přidává deklarace identity specifické pro. Deklarace identity, které jsou povoleny jsou získávány z `GetAllowedOpList` metodu, která je implementováno s cílem vrátit konkrétní seznam operací, které uživatel může provádět. Zásady autorizace přidá deklarace identity pro přístup k určité operace. Používá se později pomocí <xref:System.ServiceModel.ServiceAuthorizationManager> k provedení rozhodnutí o kontrolu přístupu.

Jednou vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementované, hostitele služby musí být informováni o zásad autorizace tak, aby používat.

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně volá přidat, rozdílového a několik metod a získá zprávu "Přístup byl odepřen" při pokusu o volání metody dělení. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor

Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.

Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:

-   Vytváří se certifikát serveru.

     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. % Proměnná % název_serveru Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota je localhost.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.

     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je vyžadován, protože certifikáty, které jsou generovány Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Vytváří se certifikát klienta.

     Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít. % Proměnná % uživatelské_jméno Určuje název serveru. Tato hodnota nastavená na "test1", protože jde o název `IAuthorizationPolicy` hledá. Pokud změníte hodnotu % uživatelské_jméno musíte změnit odpovídající hodnotu v `IAuthorizationPolicy.Evaluate` metody.

     Certifikát je uložen v úložišti (osobních) v části CurrentUser umístění úložiště.

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   Instalaci klientského certifikátu do úložiště důvěryhodných certifikátů serveru.

     Následující řádky do dávkový soubor Setup.bat zkopírujte klientský certifikát do úložiště důvěryhodných osob. Tento krok je nutný, protože certifikáty, které jsou generovány Makecert.exe implicitně nedůvěřuje serverového systému. Pokud už máte certifikát, který je integrován v důvěryhodných kořenových certifikátů – například certifikátů vystavených Microsoftem – v tomto kroku naplnění úložiště certifikátů serveru pomocí certifikátu klienta se nevyžaduje.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku

1. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Ke spuštění ukázky v konfiguraci s jedním nebo více počítači, použijte následující pokyny.

> [!NOTE]
> Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.

### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1. Otevřete Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spusťte *Setup.bat* z instalační složky vzorku. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup.bat slouží ke spuštění z příkazového řádku pro vývojáře pro sadu Visual Studio. Proměnné prostředí PATH v nastavení v rámci příkazového řádku pro vývojáře pro Visual Studio odkazuje na adresář obsahující spustitelné soubory, které jsou vyžadované *Setup.bat* skriptu.

1. Spuštění Service.exe z *service\bin*.

1. Spusťte Client.exe z *\client\bin*. Činnost klienta se zobrazí na klientské aplikace konzoly.

  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích

1. Vytvoření adresáře na počítači se službou.

2. Kopírování souborů program služby *\service\bin* do adresáře na počítači se službou. Také kopírovat soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.

3. Vytvoření adresáře v klientském počítači pro binární soubory klienta.

4. Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.

5. Na serveru, spusťte `setup.bat service` v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.

   Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem *Service.cer*.

6. Upravit *Service.exe.config* tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače. Také změnit **computername** v \<služby > /\<baseAddresses > element z místního hostitele, plně kvalifikovaný název počítače služby.

7. Kopírovat *Service.cer* soubor z adresáře služby do adresáře klienta v klientském počítači.

8. Na straně klienta, spouštění `setup.bat client` v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.

   Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem **test1** a exportuje certifikát klienta do souboru s názvem *Client.cer*.

9. V *Client.exe.config* souborů v klientském počítači, změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. To udělat tak, že nahradíte **localhost** s plně kvalifikovaný název serveru.

10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.

11. Na straně klienta, spouštění *ImportServiceCert.bat* v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.

   Tento postup importuje certifikát služby ze souboru Service.cer do **CurrentUser - TrustedPeople** ukládat.

12. Na serveru, spusťte *ImportClientCert.bat* v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.

   Tento postup importuje klientský certifikát ze souboru Client.cer do **LocalMachine - TrustedPeople** ukládat.

13. Na počítači serveru spusťte Service.exe z okna příkazového řádku.

14. Na klientském počítači spusťte Client.exe z okna příkazového řádku.

   Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).

### <a name="clean-up-after-the-sample"></a>Vyčištění po vzorku

Chcete-li vyčistit po ukázce, spusťte *Cleanup.bat* ve složce samples po dokončení spuštění ukázky. Tím serverových a klientských certifikátů z úložiště certifikátů.

> [!NOTE]
> Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste spustili Ukázky WCF, které používají certifikáty na počítačích, je nutné vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople uložit. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.