---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 9b73eea1f51454dd82ba577c4d4d5fd5a1c0efd4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990192"
---
# <a name="authorization-policy"></a><span data-ttu-id="6bf47-102">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="6bf47-102">Authorization Policy</span></span>

<span data-ttu-id="6bf47-103">Tato ukázka předvádí, jak implementovat vlastní zásady autorizace deklarací identity a přidruženého vlastního Správce autorizací služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="6bf47-104">To je užitečné, když služba provádí kontroly přístupu na základě deklarací identity na operace služeb a před kontrolou přístupu uděluje volajícím určitá práva.</span><span class="sxs-lookup"><span data-stu-id="6bf47-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="6bf47-105">V této ukázce se zobrazuje jak proces přidávání deklarací identity, tak i proces pro kontrolu přístupu na finalizaci sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="6bf47-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="6bf47-106">Všechny zprávy aplikací mezi klientem a serverem jsou podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="6bf47-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="6bf47-107">Ve výchozím nastavení s `wsHttpBinding` vazbou se k přihlášení k platnému účtu systému Windows NT používá uživatelské jméno a heslo dodávané klientem.</span><span class="sxs-lookup"><span data-stu-id="6bf47-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="6bf47-108">Tato ukázka předvádí, jak použít vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> pro ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="6bf47-109">Kromě této ukázky se zobrazuje klient ověřující službu pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="6bf47-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="6bf47-110">Tato ukázka předvádí implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a <xref:System.ServiceModel.ServiceAuthorizationManager>, která mezi nimi uděluje přístup ke konkrétním metodám služby pro konkrétní uživatele.</span><span class="sxs-lookup"><span data-stu-id="6bf47-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="6bf47-111">Tato ukázka je založena na [uživatelském jménu zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale ukazuje, jak provést transformaci deklarace před <xref:System.ServiceModel.ServiceAuthorizationManager> voláním.</span><span class="sxs-lookup"><span data-stu-id="6bf47-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="6bf47-112">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="6bf47-113">V souhrnu Tato ukázka předvádí, jak:</span><span class="sxs-lookup"><span data-stu-id="6bf47-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="6bf47-114">Klienta lze ověřit pomocí uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="6bf47-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="6bf47-115">Klienta lze ověřit pomocí certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="6bf47-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="6bf47-116">Server ověří pověření klienta proti vlastnímu `UsernamePassword` validátoru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="6bf47-117">Server je ověřený pomocí certifikátu X. 509 serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="6bf47-118">Server může používat <xref:System.ServiceModel.ServiceAuthorizationManager> k řízení přístupu k určitým metodám ve službě.</span><span class="sxs-lookup"><span data-stu-id="6bf47-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="6bf47-119">Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="6bf47-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="6bf47-120">Služba zpřístupňuje dva koncové body pro komunikaci se službou, které jsou definovány pomocí konfiguračního souboru App. config. Každý koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6bf47-121">Jedna vazba je nakonfigurovaná se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a uživatelské jméno klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="6bf47-122">Druhá vazba je nakonfigurovaná se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="6bf47-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="6bf47-123">Chování > určuje, zda mají být pro ověřování služby použity přihlašovací údaje uživatele. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6bf47-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="6bf47-124">Certifikát serveru musí obsahovat stejnou hodnotu `SubjectName` vlastnosti `findValue` jako atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="6bf47-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="6bf47-125">Každá konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="6bf47-126">Vazba klienta je nakonfigurována s odpovídajícím režimem zabezpečení, jak je uvedeno v tomto případě v [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `clientCredentialType` zabezpečení, jak je uvedeno [ \<ve zprávě >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6bf47-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="6bf47-127">Pro koncový bod uživatelského jména nastaví implementace klienta uživatelské jméno a heslo, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="6bf47-128">Pro koncový bod založený na certifikátu nastaví implementace klienta klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="6bf47-129">Tato ukázka používá vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ověření uživatelských jmen a hesel.</span><span class="sxs-lookup"><span data-stu-id="6bf47-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="6bf47-130">Ukázka implementuje `MyCustomUserNamePasswordValidator`odvozené z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="6bf47-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="6bf47-131">Další informace najdete v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="6bf47-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="6bf47-132">Pro účely demonstrování integrace s nástrojem <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Tato ukázka vlastního validátoru <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> implementuje metodu pro příjem párů uživatelského jména a hesla, kde uživatelské jméno odpovídá heslu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="6bf47-133">Po implementaci ověřovacího modulu v kódu služby musí být hostitel služby informován o instanci validátoru, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="6bf47-134">To se provádí pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6bf47-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="6bf47-135">Nebo můžete stejnou věc provést v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="6bf47-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="6bf47-136">Windows Communication Foundation (WCF) poskytuje bohatý model založený na deklaracích pro provádění kontrol přístupu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="6bf47-137"><xref:System.ServiceModel.ServiceAuthorizationManager> Objekt se používá k provedení kontroly přístupu a určení, zda deklarace přidružené k klientovi splňují požadavky nezbytné pro přístup k metodě služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="6bf47-138">Pro účely ukázky ukazuje Tato ukázka implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> , která <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> implementuje metodu umožňující přístupu uživatele k metodám na základě deklarací typu `http://example.com/claims/allowedoperation` , jejichž hodnota je identifikátor URI akce operace, která je povoleno volání.</span><span class="sxs-lookup"><span data-stu-id="6bf47-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="6bf47-139">Po implementaci vlastního <xref:System.ServiceModel.ServiceAuthorizationManager> uživatelského rozhraní musí být hostitel služby informován <xref:System.ServiceModel.ServiceAuthorizationManager> o tom, jak se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="6bf47-140">To se provádí, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-140">This is done as shown in the following code.</span></span>

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="6bf47-141">Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metoda, která má být implementována, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> je metoda.</span><span class="sxs-lookup"><span data-stu-id="6bf47-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="6bf47-142">Předchozí kód ukazuje, jak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda kontroluje, zda nebyly přidány žádné nové deklarace identity, které mají vliv na zpracování a přidávají konkrétní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6bf47-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="6bf47-143">Deklarace, které jsou povoleny, jsou získány `GetAllowedOpList` z metody, která je implementována k vrácení konkrétního seznamu operací, které může uživatel provést.</span><span class="sxs-lookup"><span data-stu-id="6bf47-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="6bf47-144">Zásady autorizace přidávají deklarace identity pro přístup k určité operaci.</span><span class="sxs-lookup"><span data-stu-id="6bf47-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="6bf47-145">Tato služba <xref:System.ServiceModel.ServiceAuthorizationManager> je později používána k rozhodování o kontrole přístupu.</span><span class="sxs-lookup"><span data-stu-id="6bf47-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="6bf47-146">Po implementaci vlastního <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uživatelského rozhraní musí být hostitel služby informován o zásadách autorizace, které se mají použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="6bf47-147">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6bf47-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6bf47-148">Klient úspěšně volá metodu Add, odečíst a více metod a při pokusu o volání metody dělení Získá zprávu "přístup byl odepřen".</span><span class="sxs-lookup"><span data-stu-id="6bf47-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="6bf47-149">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="6bf47-150">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="6bf47-150">Setup Batch File</span></span>

<span data-ttu-id="6bf47-151">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s příslušnými certifikáty pro spuštění samoobslužné aplikace, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="6bf47-152">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="6bf47-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="6bf47-153">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-153">Creating the server certificate.</span></span>

    <span data-ttu-id="6bf47-154">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="6bf47-155">Proměnná% Název_serveru% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6bf47-156">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="6bf47-157">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="6bf47-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6bf47-158">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="6bf47-159">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6bf47-160">Tento krok je povinný, protože certifikáty generované pomocí nástroje MakeCert. exe pro klientský systém implicitně nedůvěřují.</span><span class="sxs-lookup"><span data-stu-id="6bf47-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6bf47-161">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="6bf47-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="6bf47-162">Vytváří se klientský certifikát.</span><span class="sxs-lookup"><span data-stu-id="6bf47-162">Creating the client certificate.</span></span>

    <span data-ttu-id="6bf47-163">Následující řádky z dávkového souboru Setup. bat vytvoří klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="6bf47-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="6bf47-164">Proměnná% jméno_uživatele% Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6bf47-165">Tato hodnota je nastavená na "test1", protože se jedná o `IAuthorizationPolicy` název, který hledá.</span><span class="sxs-lookup"><span data-stu-id="6bf47-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="6bf47-166">Pokud změníte hodnotu% jméno_uživatele%, je nutné změnit odpovídající hodnotu v `IAuthorizationPolicy.Evaluate` metodě.</span><span class="sxs-lookup"><span data-stu-id="6bf47-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="6bf47-167">Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6bf47-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6bf47-168">Probíhá instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="6bf47-169">Následující řádky v dávkovém souboru Setup. bat kopírují klientský certifikát do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="6bf47-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="6bf47-170">Tento krok je povinný, protože serverové systémy, které jsou vygenerované pomocí nástroje MakeCert. exe, nejsou implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="6bf47-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="6bf47-171">Pokud již máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu, například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů serveru pomocí klientského certifikátu není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="6bf47-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="6bf47-172">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="6bf47-172">To set up and build the sample</span></span>

1. <span data-ttu-id="6bf47-173">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6bf47-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="6bf47-174">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="6bf47-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="6bf47-175">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6bf47-176">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="6bf47-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6bf47-177">Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte *Setup. bat* z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="6bf47-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="6bf47-178">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="6bf47-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6bf47-179">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bf47-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="6bf47-180">Proměnná prostředí PATH nastavená v rámci Developer Command Prompt pro Visual Studio odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript *Setup. bat* .</span><span class="sxs-lookup"><span data-stu-id="6bf47-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="6bf47-181">Spusťte Service. exe z *service\bin*.</span><span class="sxs-lookup"><span data-stu-id="6bf47-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="6bf47-182">Spusťte soubor Client. exe z *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="6bf47-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="6bf47-183">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="6bf47-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="6bf47-184">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6bf47-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6bf47-185">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="6bf47-185">To run the sample across computers</span></span>

1. <span data-ttu-id="6bf47-186">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="6bf47-187">Zkopírujte programové soubory služby z *\service\bin* do adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="6bf47-188">Zkopírujte také soubory Setup. bat, Cleanup. bat, GetComputerName. vbs a ImportClientCert. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="6bf47-189">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="6bf47-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="6bf47-190">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="6bf47-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="6bf47-191">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="6bf47-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="6bf47-192">Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6bf47-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="6bf47-193">Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem *Service. cer*.</span><span class="sxs-lookup"><span data-stu-id="6bf47-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="6bf47-194">Upravte soubor *Service. exe. config* tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="6bf47-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="6bf47-195">Změňte také název **počítače** ve \<službě >/\<adres BaseAddresses > elementu z místního hostitele na plně kvalifikovaný název počítače služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="6bf47-196">Zkopírujte soubor *Service. cer* z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="6bf47-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="6bf47-197">V klientovi spusťte `setup.bat client` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6bf47-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="6bf47-198">Při `setup.bat` spuštění`client` s argumentem se vytvoří klientský certifikát s názvem **test1** a exportuje se klientský certifikát do souboru s názvem *Client. cer*.</span><span class="sxs-lookup"><span data-stu-id="6bf47-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="6bf47-199">V souboru *Client. exe. config* v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="6bf47-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="6bf47-200">Provedete to tak, že nahradíte **localhost** názvem domény, který má plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="6bf47-201">Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="6bf47-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="6bf47-202">Na straně klienta spusťte *ImportServiceCert. bat* v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6bf47-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="6bf47-203">Tím se certifikát služby importuje ze souboru Service. cer do úložiště **CurrentUser-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="6bf47-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="6bf47-204">Na serveru spusťte *ImportClientCert. bat* v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="6bf47-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="6bf47-205">Tím se certifikát klienta importuje ze souboru Client. cer do úložiště **LocalMachine-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="6bf47-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="6bf47-206">V počítači serveru spusťte z okna příkazového řádku Service. exe.</span><span class="sxs-lookup"><span data-stu-id="6bf47-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="6bf47-207">V klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6bf47-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="6bf47-208">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6bf47-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="6bf47-209">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="6bf47-209">Clean up after the sample</span></span>

<span data-ttu-id="6bf47-210">Po dokončení ukázky spusťte *Cleanup. bat* ve složce Samples, až skončíte s jeho spuštěním.</span><span class="sxs-lookup"><span data-stu-id="6bf47-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="6bf47-211">Tím dojde k odebrání certifikátů serveru a klienta z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6bf47-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="6bf47-212">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="6bf47-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="6bf47-213">Pokud jste spustili ukázky WCF, které používají certifikáty napříč počítači, ujistěte se, že jste vymazali certifikáty služby nainstalované v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="6bf47-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6bf47-214">K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="6bf47-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
