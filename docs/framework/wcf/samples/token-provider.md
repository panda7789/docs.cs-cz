---
title: Zprostředkovatel tokenu
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 39a898286447168c68e2b91b03ba816b4b7aa8fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834475"
---
# <a name="token-provider"></a>Zprostředkovatel tokenu
Tento příklad ukazuje, jak implementovat vlastní zprostředkovatele tokenu. Poskytovatel tokenu ve Windows Communication Foundation (WCF) slouží k poskytnutí přihlašovacích údajů k zabezpečení infrastruktury. Poskytovatel tokenu obecně zkontroluje cíl a problémů příslušné přihlašovací údaje tak, aby infrastruktura zabezpečení se dají zabezpečit zprávy. WCF se dodává s výchozí poskytovatel tokenu přihlašovacích údajů správce. WCF se také dodává se [!INCLUDE[infocard](../../../../includes/infocard-md.md)] zprostředkovatele tokenu. Vlastní poskytovatele tokenů jsou užitečné v následujících případech:

-   Pokud máte úložiště přihlašovacích údajů, které tyto poskytovatele tokenů nemůže pracovat s.

-   Pokud chcete poskytnout vlastní vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel zadá podrobnosti, které chcete při Architektura klienta WCF používá přihlašovací údaje.

-   Pokud vytváříte vlastní token.

 Tento příklad ukazuje, jak vytvořit vlastního zprostředkovatele tokenů, který transformuje vstup od uživatele do jiného formátu.

 Souhrnně řečeno, tento příklad znázorňuje následující:

-   Jak klient může ověřit pomocí dvojice uživatelského jména a hesla.

-   Jak klienta lze nakonfigurovat pomocí vlastního zprostředkovatele tokenů.

-   Jak na serveru můžete ověřit pomocí hesla s vlastní přihlašovací údaje klienta <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , který ověří, že uživatelské jméno a heslo odpovídat.

-   Jak ověření serveru klientem pomocí certifikátu X.509 serveru.

 Tento příklad také ukazuje, jak identitu volajícího, jež je přístupné po dokončení procesu vlastních tokenů ověřování.

 Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní `wsHttpBinding`, který používá zabezpečení zpráv ve výchozím nastavení. Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů. Služba nakonfiguruje taky certifikát služby pomocí chování serviceCredentials. Chování serviceCredentials umožňuje nakonfigurovat certifikát služby. Certifikát služby se používá pro klienta k ověření služby a zajistit ochranu zprávy. Následující konfigurace odkazuje nainstalovat během instalace ukázka, jak je popsáno v následující pokyny k instalaci certifikátu localhost.

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
        The serviceCredentials behavior allows one to define a service certificate.
        A service certificate is used by a client to authenticate the service and provide message protection.
        This configuration references the "localhost" certificate installed during the setup instructions.
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt. Klient vazby je nakonfigurovaný s příslušnou `Mode` a zpráva `clientCredentialType`.

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
              address="http://localhost:8000/servicemodelsamples/service"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator">
    </endpoint>
  </client>

  <bindings>
    <wsHttpBinding>
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
</system.serviceModel>
```

 Následující kroky ukazují, jak vytvořit vlastního zprostředkovatele tokenů a integrovat architektury WCF zabezpečení:

1.  Napište vlastního zprostředkovatele tokenů.

     Ukázka implementuje vlastního zprostředkovatele tokenů, který získá uživatelské jméno a heslo. Heslo musí odpovídat toto uživatelské jméno. Tento vlastní zprostředkovatel tokenu je pouze pro demonstrační účely a nedoporučuje se používat pro reálné nasazení.

     K provedení této úlohy je odvozen vlastního zprostředkovatele tokenů <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy a přepsání <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Tato metoda vytvoří a vrátí nový `UserNameSecurityToken`.

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2.  Správce tokenů zabezpečení vlastního zápisu.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je do ní předán v `CreateSecurityTokenProvider` metody. Správce tokenů zabezpečení se také používá k vytvoření ověřovací data tokenu a serializátor, ale nejsou uvedené v této ukázce. V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenProvider` požadovaná metoda vracet poskytovatele tokenu, kterého vlastní uživatelské jméno předané požadavky tokenu určit uživatelské jméno zprostředkovatele.

    ```
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3.  Zápis vlastních klientských přihlašovacích údajů.

     Třída přihlašovacích údajů klienta se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro proxy serveru klienta a vytvoří token správce, který se používá k získání ověřovací data tokenu, poskytovatele tokenů a serializátoru tokenů zabezpečení.

    ```
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4.  Konfigurace klienta pro použití vlastního klienta přihlašovacích údajů.

     Aby klienti měli používat přihlašovací údaje, které vlastní vzorek odstraní výchozí třídu přihlašovacích údajů klienta a poskytuje novou třídu přihlašovacích údajů klienta.

    ```
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 Na službu, použijte k zobrazení informací volajícího, <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím příkladu kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícím.

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušný certifikát ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.

 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:

-   Vytváří se certifikát serveru.

     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnné Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota v tomto souboru služby batch je localhost.

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

> [!NOTE]
>  Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows. To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.

#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku

1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1.  Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio 2012 otevřeného s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.  
  
2.  Spusťte service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Do příkazového řádku uživatelské jméno zadejte uživatelské jméno.  
  
5.  Na výzvu k zadání hesla použijte stejný řetězec, který byl zadán pro řádek uživatelské jméno.  
  
6.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře na počítači se službou pro binární soubory služby.  
  
2.  Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou. Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor Service.exe.config musí aktualizovat tak, aby odrážely tento nový název certifikátu. Certifikát serveru můžete vytvořit tak, že upravíte dávkový soubor Setup.bat. Všimněte si, že se soubor setup.bat musí spustit na příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce. Je nutné nastavit `%SERVER_NAME%` proměnných hostitele plně kvalifikovaný název počítače, který se používá k hostování služby.  
  
4.  Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta. Nemusíte to dělat, když certifikátu serveru vydanému klienta důvěryhodného vystavitele.  
  
5.  V souboru Service.exe.config na počítači se službou změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný, místo localhost.  
  
6.  Na počítači se službou spusťte z příkazového řádku service.exe.  
  
7.  Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
8.  V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.  
  
9. Na klientském počítači spusťte `Client.exe` z okna příkazového řádku.  
  
10. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1.  Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
