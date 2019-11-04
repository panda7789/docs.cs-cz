---
title: Ověřovací data tokenu
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 835a158ba668a3aef749602c73fd9157e8d83a40
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425035"
---
# <a name="token-authenticator"></a><span data-ttu-id="307aa-102">Ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="307aa-102">Token Authenticator</span></span>
<span data-ttu-id="307aa-103">Tato ukázka předvádí, jak implementovat vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="307aa-104">Ověřovací data tokenu v Windows Communication Foundation (WCF) se používají k ověření tokenu, který se používá ve zprávě, ověření, že je samostatný, a ověření identity přidružené k tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="307aa-105">Vlastní ověřovatele tokenů jsou užitečné v nejrůznějších případech, například:</span><span class="sxs-lookup"><span data-stu-id="307aa-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="307aa-106">Pokud chcete přepsat výchozí mechanismus ověřování, který je přidružený k tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="307aa-107">Při vytváření vlastního tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-107">When you are building a custom token.</span></span>

 <span data-ttu-id="307aa-108">Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="307aa-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="307aa-109">Jak se může klient ověřit pomocí dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="307aa-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="307aa-110">Jak může server ověřit přihlašovací údaje klienta pomocí vlastního ověřovatele tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="307aa-111">Způsob, jakým se kód služby WCF přiřazuje k vlastnímu ověřovateli tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="307aa-112">Jak se dá server ověřit pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="307aa-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="307aa-113">Tato ukázka také ukazuje, jak je identita volajícího přístupná z WCF po procesu ověřování pomocí vlastního tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="307aa-114">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="307aa-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="307aa-115">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="307aa-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="307aa-116">Vazba je nakonfigurována se standardním `wsHttpBinding`, s režimem zabezpečení nastaveným na Message – výchozí režim `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="307aa-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="307aa-117">Tato ukázka nastaví standardní `wsHttpBinding` pro použití ověřování uživatelského jména klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="307aa-118">Služba také nakonfiguruje certifikát služby pomocí chování `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="307aa-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="307aa-119">Chování `securityCredentials` umožňuje zadat certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="307aa-120">Certifikát služby používá klient k ověření služby a poskytování ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="307aa-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="307aa-121">Následující konfigurace odkazuje na certifikát localhost nainstalovaný během ukázkové instalace, jak je popsáno v následujících pokynech k instalaci.</span><span class="sxs-lookup"><span data-stu-id="307aa-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
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
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="307aa-122">Konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="307aa-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="307aa-123">Vazba klienta je nakonfigurovaná s příslušnými `Mode` a `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="307aa-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

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

 <span data-ttu-id="307aa-124">Implementace klienta nastaví uživatelské jméno a heslo, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="307aa-124">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="307aa-125">Vlastní ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="307aa-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="307aa-126">Pomocí následujících kroků můžete vytvořit vlastní ověřovací data tokenu:</span><span class="sxs-lookup"><span data-stu-id="307aa-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="307aa-127">Zapište vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="307aa-128">Ukázka implementuje vlastní ověřovací data tokenu, které ověřuje, že uživatelské jméno má platný formát e-mailu.</span><span class="sxs-lookup"><span data-stu-id="307aa-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="307aa-129">Odvozuje <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="307aa-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="307aa-130">Nejdůležitější metoda v této třídě je <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="307aa-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="307aa-131">V této metodě ověřovatel ověří formát uživatelského jména a také, že název hostitele není z neoprávněné domény.</span><span class="sxs-lookup"><span data-stu-id="307aa-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="307aa-132">Pokud jsou splněny obě podmínky, vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí jen pro čtení, která se pak použije k poskytnutí deklarací, které představují informace uložené v tokenu uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="307aa-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="307aa-133">Zadejte zásady autorizace, které vrací vlastní ověřovatel tokenu.</span><span class="sxs-lookup"><span data-stu-id="307aa-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="307aa-134">Tato ukázka poskytuje vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> s názvem `UnconditionalPolicy`, která vrací sadu deklarací identity a identit, které byly předány do svého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="307aa-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="307aa-135">Napište vlastního správce tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="307aa-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="307aa-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou předány do této metody `CreateSecurityTokenAuthenticator`.</span><span class="sxs-lookup"><span data-stu-id="307aa-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="307aa-137">Správce tokenů zabezpečení se používá také k vytváření zprostředkovatelů tokenů a serializátorů tokenů, ale u těch se tato ukázka nezabývá.</span><span class="sxs-lookup"><span data-stu-id="307aa-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="307aa-138">V této ukázce správce vlastního tokenu zabezpečení dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepíše metodu `CreateSecurityTokenAuthenticator`, aby vracela vlastní ověřovací data tokenu uživatelského jména, když požadavky na předané tokeny označují, že se požaduje ověřovací data uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="307aa-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="307aa-139">Napište vlastní přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-139">Write a custom service credential.</span></span>

     <span data-ttu-id="307aa-140">Třída pověření služby se používá k reprezentaci přihlašovacích údajů nakonfigurovaných pro službu a vytvoří Správce tokenů zabezpečení, který se používá k získání ověřovatelů tokenů, poskytovatelů tokenů a serializátorů tokenů.</span><span class="sxs-lookup"><span data-stu-id="307aa-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="307aa-141">Nakonfigurujte službu tak, aby používala vlastní přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="307aa-142">Aby služba používala vlastní přihlašovací údaje služby, odstraníme po zachycení certifikátu služby, který je už předem nakonfigurovaný v přihlašovacích údajích služby, výchozí třídu přihlašovacích údajů služby a nakonfigurujete nové přihlašovací údaje služby. instance pro použití předkonfigurovaných certifikátů služby a přidání této nové instance pověření služby k chování služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="307aa-143">Chcete-li zobrazit informace o volajícím, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="307aa-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="307aa-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> obsahuje informace o deklaracích aktuálního volajícího.</span><span class="sxs-lookup"><span data-stu-id="307aa-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="307aa-145">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="307aa-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="307aa-146">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="307aa-147">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="307aa-147">Setup Batch File</span></span>
 <span data-ttu-id="307aa-148">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="307aa-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="307aa-149">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="307aa-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="307aa-150">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="307aa-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="307aa-151">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="307aa-151">Creating the server certificate.</span></span>

     <span data-ttu-id="307aa-152">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="307aa-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="307aa-153">Proměnná `%SERVER_NAME%` Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="307aa-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="307aa-154">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="307aa-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="307aa-155">Výchozí hodnota v tomto dávkovém souboru je localhost.</span><span class="sxs-lookup"><span data-stu-id="307aa-155">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="307aa-156">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="307aa-157">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="307aa-158">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="307aa-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="307aa-159">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="307aa-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="307aa-160">Instalační dávkový soubor je navržený tak, aby se spouštěl z příkazového řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="307aa-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="307aa-161">Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována.</span><span class="sxs-lookup"><span data-stu-id="307aa-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="307aa-162">Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="307aa-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="307aa-163">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="307aa-163">To set up and build the sample</span></span>

1. <span data-ttu-id="307aa-164">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="307aa-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="307aa-165">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="307aa-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="307aa-166">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="307aa-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="307aa-167">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="307aa-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="307aa-168">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="307aa-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="307aa-169">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="307aa-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="307aa-170">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="307aa-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="307aa-171">Spustit Service. exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="307aa-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="307aa-172">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="307aa-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="307aa-173">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="307aa-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="307aa-174">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="307aa-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="307aa-175">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="307aa-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="307aa-176">Vytvořte adresář v počítači služby pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="307aa-177">Zkopírujte programové soubory služby do adresáře služby na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="307aa-178">Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="307aa-179">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="307aa-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="307aa-180">Soubor App. config aplikace služby musí být aktualizován, aby odrážel tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="307aa-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="307aa-181">Můžete ji vytvořit pomocí souboru Setup. bat, pokud nastavíte `%SERVER_NAME%` proměnnou na plně kvalifikovaný název hostitele počítače, na kterém bude služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="307aa-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="307aa-182">Všimněte si, že soubor Setup. bat musí být spuštěný z Developer Command Prompt pro Visual Studio, který se otevřel s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="307aa-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="307aa-183">Zkopírujte certifikát serveru do úložiště CurrentUser-TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="307aa-184">Nemusíte to dělat, s výjimkou případů, kdy je certifikát serveru vydán důvěryhodným vystavitelem klienta.</span><span class="sxs-lookup"><span data-stu-id="307aa-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="307aa-185">V souboru App. config na počítači služby změňte hodnotu základní adresy tak, aby místo názvu localhost určovala plně kvalifikovaný název počítače.</span><span class="sxs-lookup"><span data-stu-id="307aa-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="307aa-186">Na počítači služby spusťte z příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="307aa-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="307aa-187">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="307aa-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="307aa-188">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="307aa-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="307aa-189">V klientském počítači spusťte z příkazového řádku soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="307aa-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="307aa-190">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="307aa-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="307aa-191">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="307aa-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="307aa-192">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="307aa-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
