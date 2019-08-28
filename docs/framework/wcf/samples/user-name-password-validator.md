---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 4db661e80663b7b5b22a17d244f0204717fef652
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044562"
---
# <a name="user-name-password-validator"></a>Validátor hesel pro uživatelská jména
Tato ukázka předvádí, jak implementovat vlastní validátor UserNamePassword. To je užitečné v případech, kdy žádný z vestavěných režimů ověřování UserNamePassword není vhodný pro požadavky aplikace. například když jsou páry uživatelského jména a hesla uložené v některém externím úložišti, jako je třeba databáze. Tato ukázka obsahuje službu, která má vlastní validátor, který kontroluje dvě konkrétní páry uživatelského jména a hesla. Klient používá k ověření ve službě takové párování uživatelského jména a hesla.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Vzhledem k tomu, že kdokoli může vytvořit přihlašovací údaje pro uživatelské jméno, které používají páry uživatelské jméno a heslo, které vlastní validátor akceptuje, je tato služba méně bezpečná, než je výchozí chování, které poskytuje standardní validátor UserNamePassword. Standardní validátor UserNamePassword se pokusí mapovat zadané párování uživatelského jména a hesla k účtu systému Windows a ověřování se nepovede, pokud toto mapování neproběhne úspěšně. Vlastní validátor UserNamePassword v této ukázce nesmí být použit v produkčním kódu, je určen pouze pro ilustraci.

 V části Souhrn tento příklad ukazuje, jak:

- Klienta lze ověřit pomocí tokenu uživatelského jména.

- Server ověří pověření klienta proti vlastnímu UserNamePasswordValidator a rozšíří vlastní chyby z logiky ověření uživatelského jména a hesla na klienta.

- Server je ověřený pomocí certifikátu X. 509 serveru.

 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je konfigurovaná se standardem `wsHttpBinding` , který používá výchozí ověřování pomocí protokolu WS-Security a uživatelského jména. Chování služby určuje `Custom` režim pro ověření párů uživatelského jména a hesla klienta spolu s typem třídy validátoru. Chování také Určuje certifikát serveru pomocí `serviceCertificate` elementu. Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` `findValue` jako v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurovaná s odpovídajícím režimem a `clientCredentialType`zprávou.

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

```
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

 Tato ukázka používá vlastní UserNamePasswordValidator k ověření párů uživatelského jména a hesla. Ukázka implementuje `CustomUserNamePasswordValidator`odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Další informace najdete v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> dokumentaci. Tato konkrétní ukázka vlastního validátoru implementuje `Validate` metodu pro přijetí dvou konkrétních párů uživatelského jména a hesla, jak je znázorněno v následujícím kódu.

```
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

 Po implementaci ověřovacího modulu v kódu služby musí být hostitel služby informován o instanci validátoru, která se má použít. To se provádí pomocí následujícího kódu.

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Nebo můžete stejnou věc provést v konfiguraci následujícím způsobem.

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

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Klient by měl úspěšně volat všechny metody. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor je potřeba upravit tak, aby fungoval napříč počítači nebo fungoval v nesamoobslužném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.

- Vytváří se certifikát serveru:

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná% Název_serveru% Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota je localhost.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:

     Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači

1. Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.  
  
2. Spustit Service. exe z service\bin.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Vytvořte adresář na počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na počítači služby. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Potřebujete certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Konfigurační soubor pro server se musí aktualizovat, aby odrážel tento nový název certifikátu.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta. To je nutné provést pouze v případě, že certifikát serveru není vydán důvěryhodným vystavitelem.  
  
5. V souboru App. config na počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.  
  
6. Na počítači služby spusťte z okna příkazového řádku Service. exe.  
  
7. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. Na klientském počítači spusťte soubor Client. exe z okna příkazového řádku.  
  
10. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat. Tím se odebere certifikát serveru z úložiště certifikátů.  
