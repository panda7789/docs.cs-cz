---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 202c7bfc7f60afbad8220950e46c08c0a71eb001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183251"
---
# <a name="user-name-password-validator"></a>Validátor hesel pro uživatelská jména
Tato ukázka ukazuje, jak implementovat vlastní UserNamePassword Validator. To je užitečné v případech, kdy žádný z předdefinovaných režimů ověření usernamepassword je vhodný pro požadavky aplikace; například když jsou dvojice uživatelského jména a hesla uloženy v některém externím úložišti, například v databázi. Tato ukázka ukazuje službu, která má vlastní validátor, který kontroluje dva konkrétní dvojice uživatelského jména a hesla. Klient používá takový pár uživatelského jména a hesla k ověření služby.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Vzhledem k tomu, že kdokoli může vytvořit pověření uživatelského jména, které používá dvojice uživatelského jména a hesla, které přijímá vlastní validátor, je služba méně zabezpečená než výchozí chování poskytované standardním validátorem UserNamePassword. Standardní uživatelPasswordPassword Validator se pokusí namapovat zadaný pár uživatelského jména a hesla na účet systému Windows a pokud se toto mapování nezdaří, ověření se nezdaří. Vlastní UživatelPasswordPassword Validator v této ukázce nesmí být použit v produkčním kódu, je pouze pro ilustrační účely.

 V souhrnu tento vzorek ukazuje, jak:

- Klient může být ověřen pomocí tokenu uživatelského jména.

- Server ověří pověření klienta proti vlastní UserNamePasswordValidator a jak šířit vlastní chyby z uživatelského jména a logiky ověření hesla do klienta.

- Server je ověřen pomocí certifikátu X.509 serveru.

 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a smlouvy. Vazba je konfigurována `wsHttpBinding` se standardem, který je výchozí pro použití ws-security a ověřování uživatelského jména. Chování služby určuje `Custom` režim pro ověřování párů uživatelského jména a hesla klienta spolu s typem třídy validátoru. Chování také určuje certifikát serveru `serviceCertificate` pomocí prvku. Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu `findValue` jako v [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy pro koncový bod služby, vazby a smlouvy. Vazby klienta je konfigurována `clientCredentialType`s příslušným režimem a zprávou .

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 Implementace klienta vyzve uživatele k zadání uživatelského jména a hesla.

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 Tato ukázka používá vlastní UserNamePasswordValidator k ověření dvojice uživatelského jména a hesla. Ukázka implementuje `CustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>odvozené z . Další informace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> naleznete v dokumentaci. Tento konkrétní vlastní validátor ukázka implementuje metodu `Validate` přijmout dvě konkrétní uživatelské jméno a heslo dvojice, jak je znázorněno v následujícím kódu.

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
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
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 Jakmile je validátor implementován v kódu služby, musí být hostitel služby informován o instanci validátoru, která má být používána. To se provádí pomocí následujícího kódu.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Nebo můžete udělat totéž v konfiguraci následujícím způsobem.

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Klient by měl úspěšně volat všechny metody. Stisknutím klávesy ENTER v okně klienta vypněte klienta.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru. Tento dávkový soubor musí být upraven tak, aby fungoval napříč počítači nebo aby fungoval v případě, který není hostovaný sám.

 Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci.

- Vytvoření certifikátu serveru:

     Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit. Proměnná %SERVER_NAME% určuje název serveru. Změňte tuto proměnnou a zadejte vlastní název serveru. Výchozí hodnota je localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:

     Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem pomocí certifikátu serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky ve stejném počítači

1. Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory vyžadované skriptem Setup.bat.  
  
2. Spusťte soubor Service.exe ze služby\přihrádka.  
  
3. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
4. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Vytvořte adresář na servisním počítači pro binární soubory služby.  
  
2. Zkopírujte soubory servisních programů do adresáře služby v počítači služby. Zkopírujte také soubory Setup.bat a Cleanup.bat do servisního stroje.  
  
3. Potřebujete certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Konfigurační soubor serveru musí být aktualizován tak, aby odrážel tento nový název certifikátu.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta. To je třeba provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.  
  
5. V souboru App.config v servisním počítači změňte hodnotu základní adresy a zadejte plně kvalifikovaný název počítače namísto localhost.  
  
6. Na servisním počítači spusťte service.exe z okna příkazového řádku.  
  
7. Zkopírujte soubory klientských programů ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.  
  
10. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
1. Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek. Tím odeberete certifikát serveru z úložiště certifikátů.  
