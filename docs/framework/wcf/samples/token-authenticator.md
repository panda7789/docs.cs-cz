---
title: "Ověřovací data tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7404087117ec45e09495897905094690c01fbaa8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="token-authenticator"></a><span data-ttu-id="e6c54-102">Ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="e6c54-102">Token Authenticator</span></span>
<span data-ttu-id="e6c54-103">Tento příklad ukazuje, jak implementovat vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="e6c54-104">Ověřovací data tokenu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] slouží k ověřování použít se zprávou, že je konzistentní a ověřování identity přidružené k tokenu ověření tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-104">A token authenticator in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>  
  
 <span data-ttu-id="e6c54-105">Vlastní ověřovací data tokenu, jako jsou užitečné v mnoha případech:</span><span class="sxs-lookup"><span data-stu-id="e6c54-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>  
  
-   <span data-ttu-id="e6c54-106">Pokud chcete přepsat výchozí mechanismus ověřování přidružené k tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-106">When you want to override the default authentication mechanism associated with a token.</span></span>  
  
-   <span data-ttu-id="e6c54-107">Když vytváříte vlastní token.</span><span class="sxs-lookup"><span data-stu-id="e6c54-107">When you are building a custom token.</span></span>  
  
 <span data-ttu-id="e6c54-108">Tento příklad znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="e6c54-108">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="e6c54-109">Jak klienta můžete ověřit pomocí pár uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="e6c54-109">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="e6c54-110">Jak server můžete ověřit pomocí vlastního ověřovacího modulu tokenu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-110">How the server can validate the client credentials using a custom token authenticator.</span></span>  
  
-   <span data-ttu-id="e6c54-111">Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kódu služby sváže pomocí vlastního ověřovacího modulu tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-111">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code ties in with the custom token authenticator.</span></span>  
  
-   <span data-ttu-id="e6c54-112">Jak server lze ověřit pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-112">How the server can be authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="e6c54-113">Tento příklad také ukazuje, jak je přístupná ze identitu volajícího [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] po dokončení procesu vlastních tokenů ověřování.</span><span class="sxs-lookup"><span data-stu-id="e6c54-113">This sample also shows how the caller's identity is accessible from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="e6c54-114">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config.</span><span class="sxs-lookup"><span data-stu-id="e6c54-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="e6c54-115">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e6c54-116">Vazba je nakonfigurována s standard `wsHttpBinding`, s režimem zabezpečení nastavena na zprávy - výchozí režim `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="e6c54-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="e6c54-117">Tato ukázka nastaví standardní `wsHttpBinding` používat uživatelské jméno ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="e6c54-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="e6c54-118">Služba nakonfiguruje taky certifikát služby pomocí `serviceCredentials` chování.</span><span class="sxs-lookup"><span data-stu-id="e6c54-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="e6c54-119">`securityCredentials` Chování umožňuje určit certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="e6c54-120">Certifikát služby se používá klient k ověření služby a zajištění ochrany zprávy.</span><span class="sxs-lookup"><span data-stu-id="e6c54-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="e6c54-121">Následující konfigurace odkazuje localhost certifikát nainstalovat během instalace ukázka, jak je popsáno v následujících pokynů pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="e6c54-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
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
  
 <span data-ttu-id="e6c54-122">Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e6c54-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="e6c54-123">Klient vazba je konfigurován s odpovídající `Mode` a `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="e6c54-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="e6c54-124">Implementace klienta nastaví uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="e6c54-124">The client implementation sets the user name and password to use.</span></span>  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a><span data-ttu-id="e6c54-125">Vlastní ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="e6c54-125">Custom Token Authenticator</span></span>  
 <span data-ttu-id="e6c54-126">Použijte následující postup k vytvoření vlastního ověřovacího modulu tokenu:</span><span class="sxs-lookup"><span data-stu-id="e6c54-126">Use the following steps to create a custom token authenticator:</span></span>  
  
1.  <span data-ttu-id="e6c54-127">Zápis vlastního ověřovacího modulu tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-127">Write a custom token authenticator.</span></span>  
  
     <span data-ttu-id="e6c54-128">Ukázka implementuje vlastní ověřovací token, která ověřuje, že je uživatelské jméno ve formátu platné e-mailu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="e6c54-129">Je odvozen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="e6c54-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="e6c54-130">Je nejdůležitější metoda v této třídě <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="e6c54-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="e6c54-131">Tato metoda ověří ověřovacích formát uživatelského jména a také, že název hostitele není z podvodného domény.</span><span class="sxs-lookup"><span data-stu-id="e6c54-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="e6c54-132">Pokud jsou splněny obě podmínky, pak vrátí kolekci jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které se pak použije k poskytovat deklarace identity, které představují informace uložené uvnitř tokenu uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="e6c54-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>  
  
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
  
2.  <span data-ttu-id="e6c54-133">Zadejte zásad autorizace, který je vrácen vlastní ověřovací data tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>  
  
     <span data-ttu-id="e6c54-134">Tato ukázka poskytuje svou vlastní implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> názvem `UnconditionalPolicy` , který vrací sadu deklarací identity a identity, které bylo předáno v jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>  
  
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
  
3.  <span data-ttu-id="e6c54-135">Zápis tokenu správce vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e6c54-135">Write a custom security token manager.</span></span>  
  
     <span data-ttu-id="e6c54-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Se používá k vytvoření <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pro konkrétní <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objekty, které jsou do ní předán v `CreateSecurityTokenAuthenticator` metoda.</span><span class="sxs-lookup"><span data-stu-id="e6c54-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="e6c54-137">Správce tokenu zabezpečení se také používá k vytvoření poskytovatele tokenů a serializátorů tokenu, ale nejsou uvedené v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="e6c54-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="e6c54-138">V této ukázce Správce tokenů zabezpečení vlastní dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy a přepsání `CreateSecurityTokenAuthenticator` metoda vrátí ověřovací data tokenu vlastní uživatelské jméno v případě předaný tokenu požadavky znamenat, že ověřovací uživatelské jméno je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="e6c54-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>  
  
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
  
4.  <span data-ttu-id="e6c54-139">Přihlašovací údaje vlastní služby zápisu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-139">Write a custom service credential.</span></span>  
  
     <span data-ttu-id="e6c54-140">Třída přihlašovací údaje služby se používá k reprezentování přihlašovací údaje, které jsou nakonfigurované pro službu a vytvoří token správce, který slouží k získání tokenu ověřovací data, poskytovatele tokenů a serializátorů tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e6c54-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
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
  
5.  <span data-ttu-id="e6c54-141">Nakonfigurujte službu, která používá přihlašovací údaje vlastní služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-141">Configure the service to use the custom service credential.</span></span>  
  
     <span data-ttu-id="e6c54-142">V pořadí pro službu, která používá přihlašovací údaje vlastní služby jsme odstranit výchozí třídu přihlašovacích údajů služby po zaznamenání službu certifikát, který je už předem nakonfigurované výchozí pověření služby a konfiguraci nových přihlašovacích údajů služby instance použít certifikáty předem nakonfigurované služby a přidejte tuto novou instanci služby přihlašovacích údajů do chování služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 <span data-ttu-id="e6c54-143">Chcete-li zobrazit informace volajícího, můžete použít <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="e6c54-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Obsahuje deklarace identity informace o aktuální volajícího.</span><span class="sxs-lookup"><span data-stu-id="e6c54-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 <span data-ttu-id="e6c54-145">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e6c54-146">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-146">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="e6c54-147">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="e6c54-147">Setup Batch File</span></span>  
 <span data-ttu-id="e6c54-148">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje server zabezpečení na základě certifikátů.</span><span class="sxs-lookup"><span data-stu-id="e6c54-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="e6c54-149">Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="e6c54-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="e6c54-150">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e6c54-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
-   <span data-ttu-id="e6c54-151">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-151">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="e6c54-152">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="e6c54-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e6c54-153">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e6c54-154">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e6c54-155">V tento dávkový soubor výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="e6c54-155">The default in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="e6c54-156">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-156">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="e6c54-157">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="e6c54-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e6c54-158">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e6c54-159">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e6c54-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e6c54-160">Instalační program dávkový soubor slouží ke spuštění z Windows příkazový řádek SDK.</span><span class="sxs-lookup"><span data-stu-id="e6c54-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="e6c54-161">Se vyžaduje, aby proměnné prostředí MSSDK bodu na adresář, kam nainstalovat sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="e6c54-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="e6c54-162">Tato proměnná prostředí bude automaticky nastavena v příkazovém řádku Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="e6c54-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e6c54-163">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="e6c54-163">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="e6c54-164">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6c54-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e6c54-165">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e6c54-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e6c54-166">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e6c54-166">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="e6c54-167">Spustit Setup.bat z instalační složky ukázka uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e6c54-167">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="e6c54-168">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e6c54-168">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e6c54-169">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e6c54-169">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="e6c54-170">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="e6c54-170">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="e6c54-171">Spusťte service.exe z service\bin.</span><span class="sxs-lookup"><span data-stu-id="e6c54-171">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="e6c54-172">Spusťte client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e6c54-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="e6c54-173">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="e6c54-173">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="e6c54-174">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="e6c54-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e6c54-175">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="e6c54-175">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="e6c54-176">Vytvořte adresář na počítači se službou pro binární soubory služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="e6c54-177">Zkopírujte soubory programu služby do adresáře služby na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="e6c54-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="e6c54-178">Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="e6c54-179">Musíte mít certifikát serveru s názvem subjektu, který obsahuje plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="e6c54-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e6c54-180">Soubor App.config služby musí být aktualizovány tak, aby odrážela tento nový název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e6c54-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="e6c54-181">Můžete ji vytvořit pomocí Setup.bat, pokud jste nastavili `%SERVER_NAME%` proměnnou hostitele plně kvalifikovaný název počítače, na kterém je spuštěna služba.</span><span class="sxs-lookup"><span data-stu-id="e6c54-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="e6c54-182">Všimněte si, že soubor setup.bat musí spouštět z příkazového řádku Visual Studia, otevřít s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e6c54-182">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="e6c54-183">Zkopírujte certifikát serveru do úložiště CurrentUser TrustedPeople klienta.</span><span class="sxs-lookup"><span data-stu-id="e6c54-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="e6c54-184">Není nutné k tomu kromě při vydání klienta důvěryhodného vystavitele certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="e6c54-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="e6c54-185">V souboru App.config na počítači se službou změňte hodnotu z bázové adresy k zadání názvu počítače plně kvalifikovaný místo localhost.</span><span class="sxs-lookup"><span data-stu-id="e6c54-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="e6c54-186">Na počítači se službou spusťte z příkazového řádku service.exe.</span><span class="sxs-lookup"><span data-stu-id="e6c54-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="e6c54-187">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="e6c54-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="e6c54-188">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e6c54-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="e6c54-189">Na klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="e6c54-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="e6c54-190">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="e6c54-190">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e6c54-191">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="e6c54-191">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="e6c54-192">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="e6c54-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c54-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6c54-193">See Also</span></span>
