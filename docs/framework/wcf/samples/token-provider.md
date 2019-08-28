---
title: Zprostředkovatel tokenu
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 9f008204c6ff8d3d134dbb17fc445b460f757f13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038754"
---
# <a name="token-provider"></a>Zprostředkovatel tokenu
Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenů. Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů infrastruktuře zabezpečení. Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu. WCF se dodává s výchozím poskytovatelem tokenu správce přihlašovacích údajů. WCF se dodává i s poskytovatelem tokenů služby CardSpace. Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:

- Pokud máte úložiště přihlašovacích údajů, pomocí kterého tyto poskytovatelé tokenů nemůžou pracovat s nástrojem.

- Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne informace, když klient rozhraní WCF použije přihlašovací údaje.

- Pokud vytváříte vlastní token.

 V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který transformuje vstup od uživatele do jiného formátu.

 Pro Shrnutí Tato ukázka demonstruje následující:

- Jak se může klient ověřit pomocí dvojice uživatelského jména a hesla.

- Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.

- Jak může server ověřit přihlašovací údaje klienta pomocí hesla s vlastními <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , které ověří, že se uživatelské jméno a heslo shodují.

- Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.

 Tato ukázka také ukazuje, jak je identita volajícího přístupná po procesu ověřování vlastního tokenu.

 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurovaná se standardem `wsHttpBinding`, který ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka nastavuje standard `wsHttpBinding` pro použití ověřování uživatelského jména klienta. Služba také nakonfiguruje certifikát služby pomocí chování serviceCredentials. Chování serviceCredentials vám umožňuje nakonfigurovat certifikát služby. Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv. Následující konfigurace odkazuje na certifikát localhost nainstalovaný během ukázkové instalace, jak je popsáno v následujících pokynech k instalaci.

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

 Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurovaná s použitím příslušné `Mode` zprávy `clientCredentialType`a.

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

 Následující kroky ukazují, jak vyvíjet vlastního poskytovatele tokenů a integrovat ho s architekturou zabezpečení WCF:

1. Napište vlastního poskytovatele tokenů.

     Ukázka implementuje vlastního poskytovatele tokenu, který získá uživatelské jméno a heslo. Heslo se musí shodovat s tímto uživatelským jménem. Tento vlastní poskytovatel tokenu je určen pouze pro demonstrační účely a nedoporučuje se pro reálné nasazení.

     Chcete-li provést tuto úlohu, zprostředkovatel vlastního tokenu odvodí <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídu a <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> přepíše metodu. Tato metoda vytvoří a vrátí nový `UserNameSecurityToken`.

    ```csharp
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

2. Napsat vlastního správce tokenů zabezpečení.

     Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> , který je předán v `CreateSecurityTokenProvider` metodě. <xref:System.IdentityModel.Selectors.SecurityTokenManager> Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátoru tokenů, ale u těch se tato ukázka nezabývá. V této ukázce vlastní Správce tokenů zabezpečení dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a `CreateSecurityTokenProvider` přepíše metodu, která vrátí vlastního poskytovatele tokenu uživatelského jména, pokud požadavky na předaný token označují, že poskytovatel uživatelského jména je požadován.

    ```csharp
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

3. Napište vlastní přihlašovací údaje klienta.

     Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátoru tokenů.

    ```csharp
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

4. Nakonfigurujte klienta tak, aby používal vlastní přihlašovací údaje klienta.

     Aby klient mohl používat vlastní přihlašovací údaje klienta, vzorek odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta.

    ```csharp
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

 Chcete-li ve službě zobrazit informace o volajícím, použijte <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> , jak je znázorněno v následujícím příkladu kódu. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje informace o deklaracích aktuálního volajícího.

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:

- Vytváří se certifikát serveru.

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota v tomto dávkovém souboru je localhost.

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

> [!NOTE]
> Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku Windows SDK. Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována. Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.

#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 otevřené s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.  
  
2. Spustit Service. exe z service\bin.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Do výzvy uživatelské jméno zadejte uživatelské jméno.  
  
5. Na výzvu k zadání hesla použijte stejný řetězec, který byl zadán pro výzvu k zadání uživatelského jména.  
  
6. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář v počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na počítači služby. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače. Soubor Service. exe. config je třeba aktualizovat, aby odrážel tento nový název certifikátu. Certifikát serveru můžete vytvořit úpravou dávkového souboru Setup. bat. Všimněte si, že soubor Setup. bat musí být spuštěný z Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce. Je nutné nastavit `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, který se používá k hostování služby.  
  
4. Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta. Nemusíte to dělat, když certifikát serveru vydává důvěryhodný vydavatel klienta.  
  
5. V souboru Service. exe. config v počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.  
  
6. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
7. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. V klientském počítači spusťte `Client.exe` z okna příkazového řádku.  
  
10. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
1. Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
