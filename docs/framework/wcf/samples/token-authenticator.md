---
title: Ověřovací data tokenu
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 501f1801c1cb475a87c586f8bbc14146b9141047
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779168"
---
# <a name="token-authenticator"></a><span data-ttu-id="23f62-102">Ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="23f62-102">Token Authenticator</span></span>
<span data-ttu-id="23f62-103">Tento příklad ukazuje, jak implementovat vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="23f62-104">Ve Windows Communication Foundation (WCF) ověřovací data tokenu se používá k ověření tokenu používaného se zprávou, ověření, že je konzistentní a ověření identity přidružené k tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="23f62-105">Vlastní ověřovací data tokenu jsou užitečné v mnoha případech, jako je například:</span><span class="sxs-lookup"><span data-stu-id="23f62-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="23f62-106">Pokud chcete přepsat výchozí mechanismus ověřování přidružené k tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="23f62-107">Pokud vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="23f62-107">When you are building a custom token.</span></span>

 <span data-ttu-id="23f62-108">Tato ukázka demonstruje následující:</span><span class="sxs-lookup"><span data-stu-id="23f62-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="23f62-109">Jak klient může ověřit pomocí dvojice uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="23f62-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="23f62-110">Jak na serveru můžete ověřit přihlašovací údaje klienta pomocí vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="23f62-111">Jak kód služby WCF spojují se pomocí vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="23f62-112">Jak na serveru je možné ověřit pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="23f62-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="23f62-113">Tento příklad také ukazuje, jak identitu volajícího, jež je přístupný z WCF po dokončení procesu vlastních tokenů ověřování.</span><span class="sxs-lookup"><span data-stu-id="23f62-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="23f62-114">Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="23f62-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="23f62-115">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="23f62-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="23f62-116">Je vazba konfigurována se standardní `wsHttpBinding`, s režimem zabezpečení nastavit ke zprávě – výchozí režim `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="23f62-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="23f62-117">Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="23f62-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="23f62-118">Služba také nakonfiguruje pomocí certifikátu služby `serviceCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="23f62-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="23f62-119">`securityCredentials` Chování umožňuje určit certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="23f62-120">Certifikát služby se používá pro klienta k ověření služby a zajistit ochranu zprávy.</span><span class="sxs-lookup"><span data-stu-id="23f62-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="23f62-121">Následující konfigurace odkazuje nainstalovat během instalace ukázka, jak je popsáno v následující pokyny k instalaci certifikátu localhost.</span><span class="sxs-lookup"><span data-stu-id="23f62-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

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

 <span data-ttu-id="23f62-122">Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="23f62-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="23f62-123">Klient vazby je nakonfigurovaný s příslušnou `Mode` a `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="23f62-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

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

 <span data-ttu-id="23f62-124">Implementace klienta nastaví uživatelské jméno a heslo pro použití.</span><span class="sxs-lookup"><span data-stu-id="23f62-124">The client implementation sets the user name and password to use.</span></span>

```
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="23f62-125">Vlastní ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="23f62-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="23f62-126">Použijte následující postup k vytvoření vlastního ověřovacího modulu tokenu:</span><span class="sxs-lookup"><span data-stu-id="23f62-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="23f62-127">Napište vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="23f62-128">Ukázka implementuje vlastní ověřovací data tokenu, který ověřuje, že uživatelské jméno je ve formátu platné e-mailu.</span><span class="sxs-lookup"><span data-stu-id="23f62-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="23f62-129">Se odvozuje <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="23f62-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="23f62-130">Metoda nejdůležitější v této třídě <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="23f62-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="23f62-131">V této metodě ověřovacích ověří formát uživatelského jména a také, že název hostitele není kompatibilní se z podvodného domény.</span><span class="sxs-lookup"><span data-stu-id="23f62-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="23f62-132">Pokud jsou splněny obě podmínky a pak vrátí kolekci jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které se pak použije k poskytovat deklarace identity, které představují informací uložených uvnitř tokenu uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="23f62-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```
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

2. <span data-ttu-id="23f62-133">Zadejte zásadu autorizace, který je vrácen vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="23f62-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="23f62-134">Tato ukázka poskytuje vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> volá `UnconditionalPolicy` , která vrací sadu deklarací identity a identity, které bylo předáno 've svém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="23f62-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```
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

3. <span data-ttu-id="23f62-135">Správce tokenů zabezpečení vlastního zápisu.</span><span class="sxs-lookup"><span data-stu-id="23f62-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="23f62-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Slouží k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou do ní předán v `CreateSecurityTokenAuthenticator` metody.</span><span class="sxs-lookup"><span data-stu-id="23f62-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="23f62-137">Správce tokenů zabezpečení se také používá k vytvoření poskytovatele tokenů a serializátorů tokenu, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="23f62-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="23f62-138">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenAuthenticator` požadovaná metoda vrátí uživatelské jméno vlastní ověřovací data tokenu při úspěšné požadavky tokenu označení authenticator tohoto uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="23f62-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```
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

4. <span data-ttu-id="23f62-139">Zápis přihlašovacích údajů pro vlastní služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-139">Write a custom service credential.</span></span>

     <span data-ttu-id="23f62-140">Třída přihlašovací údaje služby se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro službu a vytvoří Správce tokenů, který se používá k získání ověřovací data tokenu, poskytovatele tokenů a serializátorů tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="23f62-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```
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

5. <span data-ttu-id="23f62-141">Nakonfigurujte službu, aby pomocí přihlašovacích údajů pro vlastní služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="23f62-142">V pořadí pro službu, aby používala vlastní službu přihlašovacích údajů jsme odstranit výchozí třídu přihlašovacích údajů služby po zachycení, který už je předem nakonfigurovaný v přihlašovacích údajích služby výchozí certifikát služby a konfiguraci nových přihlašovacích údajů služby instance používat certifikáty předem nakonfigurované služby a přidejte tato nová pověření instance služby do chování služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="23f62-143">Chcete-li zobrazit informace volajícího, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="23f62-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="23f62-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícím.</span><span class="sxs-lookup"><span data-stu-id="23f62-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="23f62-145">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="23f62-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="23f62-146">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="23f62-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="23f62-147">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="23f62-147">Setup Batch File</span></span>
 <span data-ttu-id="23f62-148">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje server zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="23f62-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="23f62-149">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="23f62-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="23f62-150">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="23f62-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="23f62-151">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="23f62-151">Creating the server certificate.</span></span>

     <span data-ttu-id="23f62-152">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="23f62-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="23f62-153">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="23f62-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="23f62-154">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="23f62-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="23f62-155">V tomto souboru batch výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="23f62-155">The default in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="23f62-156">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="23f62-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="23f62-157">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="23f62-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="23f62-158">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="23f62-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="23f62-159">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="23f62-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="23f62-160">Instalační dávkový soubor je navržena pro spouštění na příkazovém řádku sady SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="23f62-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="23f62-161">To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK.</span><span class="sxs-lookup"><span data-stu-id="23f62-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="23f62-162">Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="23f62-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="23f62-163">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="23f62-163">To set up and build the sample</span></span>

1. <span data-ttu-id="23f62-164">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23f62-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="23f62-165">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23f62-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="23f62-166">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="23f62-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="23f62-167">Spusťte Setup.bat z instalační složky s ukázkou v příkazovém řádku aplikace Visual Studio 2012 otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="23f62-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="23f62-168">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="23f62-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23f62-169">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="23f62-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="23f62-170">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="23f62-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="23f62-171">Spusťte service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="23f62-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="23f62-172">Spusťte client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="23f62-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="23f62-173">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="23f62-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="23f62-174">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="23f62-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="23f62-175">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="23f62-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="23f62-176">Vytvoření adresáře na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="23f62-177">Programové soubory nástroje služby zkopírujte do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="23f62-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="23f62-178">Také kopírovat soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="23f62-179">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="23f62-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="23f62-180">Soubor App.config služby musí být aktualizovány tak, aby odrážely tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="23f62-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="23f62-181">Můžete vytvořit pomocí Setup.bat, pokud jste nastavili `%SERVER_NAME%` proměnných hostitele plně kvalifikovaný název počítače, na kterém je spuštěna služba.</span><span class="sxs-lookup"><span data-stu-id="23f62-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="23f62-182">Všimněte si, že se soubor setup.bat musí spustit na příkazovém řádku pro vývojáře pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="23f62-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="23f62-183">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="23f62-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="23f62-184">Nemusíte to dělat s výjimkou případů, kdy certifikátu serveru vydanému klienta důvěryhodného vystavitele.</span><span class="sxs-lookup"><span data-stu-id="23f62-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="23f62-185">V souboru App.config na počítači se službou změňte hodnotu z bázové adresy pro zadejte název počítače plně kvalifikovaný, místo localhost.</span><span class="sxs-lookup"><span data-stu-id="23f62-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="23f62-186">Na počítači se službou spusťte z příkazového řádku service.exe.</span><span class="sxs-lookup"><span data-stu-id="23f62-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="23f62-187">Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="23f62-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="23f62-188">V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="23f62-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="23f62-189">Na klientském počítači spusťte Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="23f62-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="23f62-190">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="23f62-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="23f62-191">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="23f62-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="23f62-192">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="23f62-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
