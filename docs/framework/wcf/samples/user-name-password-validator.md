---
title: Validátor hesel pro uživatelská jména
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 33df3a7a8d463a9c2cd2d2586f0aa812e25a16ff
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305452"
---
# <a name="user-name-password-validator"></a>Validátor hesel pro uživatelská jména
Tento příklad ukazuje, jak implementovat vlastní UserNamePassword validátor. To je užitečné v případech, kdy se žádná z předdefinovaných režimy ověřování UserNamePassword je vhodné pro požadavky na aplikaci. například když páry uživatelského jména a hesla ukládají v některé externí úložiště, například do databáze. Tento příklad ukazuje služba, která má vlastní validátor, který kontroluje dvě dvojice konkrétního uživatelského jména a hesla. Klient používá k ověření ve službě dvojici uživatelského jména a hesla.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  Vzhledem k tomu, že kdokoli může vytvořit uživatelské jméno pověření, která používá následující páry uživatelského jména a hesla, které přijímá vlastní validátor, tato služba je méně bezpečné než výchozí chování poskytuje standardní UserNamePassword validátoru. Validátor standardní UserNamePassword pokusí mapovat pár zadané uživatelské jméno a heslo k účtu Windows a ověřování se nezdaří, pokud tato mapování se nezdaří. Vlastní UserNamePassword validátor v této ukázce musí není se dá použít v produkčním kódu, je jen jako ukázka.

 V souhrnu Tato ukázka předvádí, jak:

-   Klient lze ověřit pomocí tokenu uživatelské jméno.

-   Server ověří klienta přihlašovacích údajů, kteří vlastní objekt UserNamePasswordValidator a tom, jak rozšířit vlastní chyby z logiku ověřování uživatelského jména a hesla ke klientovi.

-   Server byl ověřovaný pomocí certifikátu X.509 serveru.

 Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní `wsHttpBinding` , která ve výchozím nastavení používá ověřování uživatelským jménem WS Securityand. Určuje chování služby `Custom` režimu pro ověřování klienta páry uživatelského jména a hesla společně s typem třídy program pro ověření. Také určuje chování serveru pomocí certifikátu `serviceCertificate` elementu. Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).

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

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt. Klient vazby je nakonfigurován příslušný režim, zpráva `clientCredentialType`.

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

 Implementace klienta se zobrazí výzva k zadání uživatelského jména a hesla.

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

 Tato ukázka používá vlastní objekt UserNamePasswordValidator k ověření uživatelského jména a hesla dvojice. Implementuje vzorek `CustomUserNamePasswordValidator`odvozenou z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Najdete v dokumentaci k <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace. Tato ukázka konkrétní vlastní validátor implementuje `Validate` metodu tak, aby přijímal dvě dvojice konkrétního uživatelského jména a hesla, jak je znázorněno v následujícím kódu.

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

 Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít. To se provádí pomocí následujícího kódu.

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Nebo můžete provést totéž v konfiguraci následujícím způsobem.

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

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně by měly volat všechny metody. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě bez vlastního hostitele.

 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.

-   Vytváří se certifikát serveru:

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

-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:

     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku

1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

2.  Ke spuštění ukázky v konfiguraci s jedním nebo více počítačů, použijte následující pokyny.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači

1.  Spusťte Setup.bat ve složce instalace ukázkové uvnitř příkazový řádek sady Visual Studio 2012. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře v počítači služby pro binární soubory služby.  
  
2.  Kopírování souborů program služby adresáře služby v počítači služby. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Budete potřebovat certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Konfigurační soubor serveru musí být aktualizovány tak, aby odrážely tento nový název certifikátu.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Budete muset provést pouze v případě, že certifikát serveru není vystavený důvěryhodného vystavitele.  
  
5.  V souboru App.config v počítači služby změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný místo localhost.  
  
6.  Na počítači služby spusťte Service.exe z okna příkazového řádku.  
  
7.  Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
8.  V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. Na klientském počítači a spusťte Client.exe z okna příkazového řádku.  
  
10. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1.  Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky. Tím certifikát serveru z úložiště certifikátů.  
  
## <a name="see-also"></a>Viz také:
