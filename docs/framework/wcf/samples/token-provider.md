---
title: Zprostředkovatel tokenu
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 6971a70e633f7768c165ee6171fd83f0eefc4183
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425126"
---
# <a name="token-provider"></a><span data-ttu-id="a4f81-102">Zprostředkovatel tokenu</span><span class="sxs-lookup"><span data-stu-id="a4f81-102">Token Provider</span></span>
<span data-ttu-id="a4f81-103">Tato ukázka předvádí, jak implementovat vlastního poskytovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="a4f81-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="a4f81-104">Poskytovatel tokenu v Windows Communication Foundation (WCF) se používá k poskytnutí přihlašovacích údajů infrastruktuře zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4f81-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="a4f81-105">Poskytovatel tokenů v nástroji General prověřuje cíl a vydá odpovídající přihlašovací údaje, aby mohla infrastruktura zabezpečení zabezpečit zprávu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="a4f81-106">WCF se dodává s výchozím poskytovatelem tokenu správce přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="a4f81-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="a4f81-107">WCF se dodává i s poskytovatelem tokenů služby CardSpace.</span><span class="sxs-lookup"><span data-stu-id="a4f81-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="a4f81-108">Vlastní zprostředkovatelé tokeny jsou užitečné v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a4f81-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="a4f81-109">Pokud máte úložiště přihlašovacích údajů, pomocí kterého tyto poskytovatelé tokenů nemůžou pracovat s nástrojem.</span><span class="sxs-lookup"><span data-stu-id="a4f81-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="a4f81-110">Pokud chcete poskytnout vlastní mechanismus pro transformaci přihlašovacích údajů z bodu, když uživatel poskytne informace, když klient rozhraní WCF použije přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="a4f81-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="a4f81-111">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="a4f81-111">If you are building a custom token.</span></span>

 <span data-ttu-id="a4f81-112">V této ukázce se dozvíte, jak vytvořit vlastního poskytovatele tokenů, který transformuje vstup od uživatele do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="a4f81-113">Pro Shrnutí Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="a4f81-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="a4f81-114">Jak se může klient ověřit pomocí dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="a4f81-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="a4f81-115">Jak lze nakonfigurovat klienta s vlastním poskytovatelem tokenů.</span><span class="sxs-lookup"><span data-stu-id="a4f81-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="a4f81-116">Způsob, jakým může server ověřovat přihlašovací údaje klienta pomocí hesla s vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, který ověřuje, jestli se shoduje uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="a4f81-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="a4f81-117">Způsob ověřování serveru klientem pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="a4f81-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="a4f81-118">Tato ukázka také ukazuje, jak je identita volajícího přístupná po procesu ověřování vlastního tokenu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="a4f81-119">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="a4f81-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="a4f81-120">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a4f81-121">Vazba je nakonfigurovaná se standardním `wsHttpBinding`, která ve výchozím nastavení používá zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="a4f81-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="a4f81-122">Tato ukázka nastaví standardní `wsHttpBinding` pro použití ověřování uživatelského jména klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="a4f81-123">Služba také nakonfiguruje certifikát služby pomocí chování serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="a4f81-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="a4f81-124">Chování serviceCredentials vám umožňuje nakonfigurovat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="a4f81-125">Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="a4f81-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="a4f81-126">Následující konfigurace odkazuje na certifikát localhost nainstalovaný během ukázkové instalace, jak je popsáno v následujících pokynech k instalaci.</span><span class="sxs-lookup"><span data-stu-id="a4f81-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

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

 <span data-ttu-id="a4f81-127">Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="a4f81-128">Vazba klienta je nakonfigurovaná s příslušnými `Mode` a `clientCredentialType`zpráv.</span><span class="sxs-lookup"><span data-stu-id="a4f81-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="a4f81-129">Následující kroky ukazují, jak vyvíjet vlastního poskytovatele tokenů a integrovat ho s architekturou zabezpečení WCF:</span><span class="sxs-lookup"><span data-stu-id="a4f81-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="a4f81-130">Napište vlastního poskytovatele tokenů.</span><span class="sxs-lookup"><span data-stu-id="a4f81-130">Write a custom token provider.</span></span>

     <span data-ttu-id="a4f81-131">Ukázka implementuje vlastního poskytovatele tokenu, který získá uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="a4f81-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="a4f81-132">Heslo se musí shodovat s tímto uživatelským jménem.</span><span class="sxs-lookup"><span data-stu-id="a4f81-132">The password must match this username.</span></span> <span data-ttu-id="a4f81-133">Tento vlastní poskytovatel tokenu je určen pouze pro demonstrační účely a nedoporučuje se pro reálné nasazení.</span><span class="sxs-lookup"><span data-stu-id="a4f81-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="a4f81-134">Chcete-li provést tuto úlohu, zprostředkovatel vlastního tokenu odvozuje třídu <xref:System.IdentityModel.Selectors.SecurityTokenProvider> a přepíše metodu <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>.</span><span class="sxs-lookup"><span data-stu-id="a4f81-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="a4f81-135">Tato metoda vytvoří a vrátí nový `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="a4f81-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

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

2. <span data-ttu-id="a4f81-136">Napsat vlastního správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a4f81-136">Write custom security token manager.</span></span>

     <span data-ttu-id="a4f81-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>, které jsou předány do `CreateSecurityTokenProvider` metody.</span><span class="sxs-lookup"><span data-stu-id="a4f81-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="a4f81-138">Správce tokenů zabezpečení se používá také k vytváření ověřovatelů tokenů a serializátoru tokenů, ale u těch se tato ukázka nezabývá.</span><span class="sxs-lookup"><span data-stu-id="a4f81-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="a4f81-139">V této ukázce správce vlastního tokenu zabezpečení dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy a přepíše metodu `CreateSecurityTokenProvider` a vrátí vlastnímu poskytovateli tokenů uživatelského jména, když požadavky na předané tokeny označují, že poskytovatel uživatelského jména je požadován.</span><span class="sxs-lookup"><span data-stu-id="a4f81-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

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

3. <span data-ttu-id="a4f81-140">Napište vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-140">Write a custom client credential.</span></span>

     <span data-ttu-id="a4f81-141">Třída pověření klienta slouží k reprezentaci přihlašovacích údajů, které jsou nakonfigurovány pro klienta proxy a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátoru tokenů.</span><span class="sxs-lookup"><span data-stu-id="a4f81-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

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

4. <span data-ttu-id="a4f81-142">Nakonfigurujte klienta tak, aby používal vlastní přihlašovací údaje klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="a4f81-143">Aby klient mohl používat vlastní přihlašovací údaje klienta, vzorek odstraní výchozí třídu přihlašovacích údajů klienta a dodá novou třídu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

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

 <span data-ttu-id="a4f81-144">Chcete-li ve službě zobrazit informace o volajícím, použijte <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="a4f81-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> obsahuje informace o deklaracích aktuálního volajícího.</span><span class="sxs-lookup"><span data-stu-id="a4f81-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="a4f81-146">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="a4f81-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a4f81-147">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="a4f81-148">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="a4f81-148">Setup Batch File</span></span>
 <span data-ttu-id="a4f81-149">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="a4f81-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="a4f81-150">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="a4f81-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="a4f81-151">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="a4f81-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="a4f81-152">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="a4f81-152">Creating the server certificate.</span></span>

     <span data-ttu-id="a4f81-153">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="a4f81-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="a4f81-154">Proměnná `%SERVER_NAME%` Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="a4f81-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="a4f81-155">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="a4f81-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a4f81-156">Výchozí hodnota v tomto dávkovém souboru je localhost.</span><span class="sxs-lookup"><span data-stu-id="a4f81-156">The default value in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a4f81-157">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta:</span><span class="sxs-lookup"><span data-stu-id="a4f81-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="a4f81-158">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a4f81-159">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="a4f81-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a4f81-160">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="a4f81-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="a4f81-161">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a4f81-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="a4f81-162">Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="a4f81-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a4f81-163">Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a4f81-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a4f81-164">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="a4f81-164">To set up and build the sample</span></span>

1. <span data-ttu-id="a4f81-165">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4f81-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a4f81-166">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a4f81-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a4f81-167">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="a4f81-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="a4f81-168">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4f81-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="a4f81-169">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="a4f81-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a4f81-170">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a4f81-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="a4f81-171">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="a4f81-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="a4f81-172">Spustit Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="a4f81-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="a4f81-173">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="a4f81-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a4f81-174">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="a4f81-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="a4f81-175">Do výzvy uživatelské jméno zadejte uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="a4f81-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="a4f81-176">Na výzvu k zadání hesla použijte stejný řetězec, který byl zadán pro výzvu k zadání uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="a4f81-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="a4f81-177">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a4f81-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a4f81-178">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="a4f81-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="a4f81-179">Vytvořte adresář v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="a4f81-180">Zkopírujte programové soubory služby do adresáře služby na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="a4f81-181">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="a4f81-182">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="a4f81-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a4f81-183">Soubor Service. exe. config je třeba aktualizovat, aby odrážel tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a4f81-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="a4f81-184">Certifikát serveru můžete vytvořit úpravou dávkového souboru Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="a4f81-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="a4f81-185">Všimněte si, že soubor Setup. bat musí být spuštěný z Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="a4f81-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="a4f81-186">Musíte nastavit `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, který se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="a4f81-187">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="a4f81-188">Nemusíte to dělat, když certifikát serveru vydává důvěryhodný vydavatel klienta.</span><span class="sxs-lookup"><span data-stu-id="a4f81-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="a4f81-189">V souboru Service. exe. config v počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="a4f81-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="a4f81-190">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="a4f81-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="a4f81-191">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="a4f81-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="a4f81-192">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="a4f81-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="a4f81-193">V klientském počítači spusťte `Client.exe` z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a4f81-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="a4f81-194">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a4f81-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a4f81-195">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="a4f81-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="a4f81-196">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="a4f81-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
