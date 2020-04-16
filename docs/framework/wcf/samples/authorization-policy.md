---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463952"
---
# <a name="authorization-policy"></a><span data-ttu-id="da8f3-102">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="da8f3-102">Authorization Policy</span></span>

<span data-ttu-id="da8f3-103">Tato ukázka ukazuje, jak implementovat vlastní zásady autorizace deklarací a přidruženého správce autorizací vlastních služeb.</span><span class="sxs-lookup"><span data-stu-id="da8f3-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="da8f3-104">To je užitečné, když služba provádí kontroly přístupu na základě deklarací nároku k operacím služby a před kontrolami přístupu uděluje volajícímu určitá práva.</span><span class="sxs-lookup"><span data-stu-id="da8f3-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="da8f3-105">Tato ukázka ukazuje proces přidávání deklarací identity i proces pro provedení kontroly přístupu proti dokončené sadě deklarací.</span><span class="sxs-lookup"><span data-stu-id="da8f3-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="da8f3-106">Všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány.</span><span class="sxs-lookup"><span data-stu-id="da8f3-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="da8f3-107">Ve výchozím `wsHttpBinding` nastavení s vazbou se uživatelské jméno a heslo zadané klientem používají k přihlášení k platnému účtu systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="da8f3-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="da8f3-108">Tato ukázka ukazuje, jak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> využít vlastní k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="da8f3-109">Kromě toho tato ukázka ukazuje ověření klienta pro službu pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="da8f3-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="da8f3-110">Tento příklad ukazuje <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementaci <xref:System.ServiceModel.ServiceAuthorizationManager>a , která mezi nimi udělují přístup ke konkrétním metodám služby pro konkrétní uživatele.</span><span class="sxs-lookup"><span data-stu-id="da8f3-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="da8f3-111">Tato ukázka je založena na [uživatelské jméno zabezpečení zprávy](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale <xref:System.ServiceModel.ServiceAuthorizationManager> ukazuje, jak provést transformaci deklarace před voláním.</span><span class="sxs-lookup"><span data-stu-id="da8f3-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="da8f3-112">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="da8f3-113">V souhrnu tento vzorek ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="da8f3-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="da8f3-114">Klient může být ověřen pomocí uživatelského jména-hesla.</span><span class="sxs-lookup"><span data-stu-id="da8f3-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="da8f3-115">Klienta lze ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="da8f3-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="da8f3-116">Server ověří pověření klienta proti `UsernamePassword` vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="da8f3-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="da8f3-117">Server je ověřen pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="da8f3-118">Server může <xref:System.ServiceModel.ServiceAuthorizationManager> řídit přístup k určitým metodám ve službě.</span><span class="sxs-lookup"><span data-stu-id="da8f3-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="da8f3-119">Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="da8f3-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="da8f3-120">Služba zpřístupňuje dva koncové body pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="da8f3-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="da8f3-121">Jedna vazba je `wsHttpBinding` konfigurována se standardní vazbou, která používá ověřování ws-security a uživatelského jména klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="da8f3-122">Druhá vazba je konfigurována se standardní `wsHttpBinding` vazbou, která používá ověřování WS-Security a client certificate.</span><span class="sxs-lookup"><span data-stu-id="da8f3-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="da8f3-123">Chování [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) určuje, že pověření uživatele mají být použita pro ověřování služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="da8f3-124">Certifikát serveru musí obsahovat stejnou `SubjectName` hodnotu `findValue` vlastnosti jako atribut v [ \<>serviceCertificate ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="da8f3-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="da8f3-125">Každá konfigurace koncového bodu klienta se skládá z názvu konfigurace, absolutní adresy pro koncový bod služby, vazby a smlouvy.</span><span class="sxs-lookup"><span data-stu-id="da8f3-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="da8f3-126">Vazby klienta jsou konfigurovány s příslušným režimem zabezpečení, `clientCredentialType` jak je v tomto případě specifikováno v [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a jak je uvedeno ve [ \<zprávě>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="da8f3-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="da8f3-127">Pro koncový bod založený na uživatelském jménu implementací klienta nastaví uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="da8f3-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="da8f3-128">Pro koncový bod založený na certifikátu implementace klienta nastaví klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="da8f3-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="da8f3-129">Tato ukázka <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> používá vlastní ověření uživatelských jmen a hesel.</span><span class="sxs-lookup"><span data-stu-id="da8f3-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="da8f3-130">Ukázka implementuje `MyCustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>odvozené z .</span><span class="sxs-lookup"><span data-stu-id="da8f3-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="da8f3-131">Další informace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="da8f3-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="da8f3-132">Pro účely prokázání integrace <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>s , tento vlastní validátor <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> ukázka implementuje metodu přijmout uživatelské jméno a heslo dvojice, kde uživatelské jméno odpovídá heslo, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="da8f3-133">Jakmile je validátor implementován v kódu služby, musí být hostitel služby informován o instanci validátoru, která má být používána.</span><span class="sxs-lookup"><span data-stu-id="da8f3-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="da8f3-134">To se provádí pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="da8f3-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="da8f3-135">Nebo můžete udělat totéž v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="da8f3-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="da8f3-136">Windows Communication Foundation (WCF) poskytuje bohatý model založený na deklaracích identity pro provádění kontrol přístupu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="da8f3-137">Objekt <xref:System.ServiceModel.ServiceAuthorizationManager> se používá k provedení kontroly přístupu a určení, zda deklarace přidružené ke klientovi splňují požadavky nezbytné pro přístup k metodě služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="da8f3-138">Pro účely demonstrace tato ukázka ukazuje <xref:System.ServiceModel.ServiceAuthorizationManager> implementaci, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> která implementuje metodu, která umožňuje uživateli přístup k metodám založeným na deklaracích typu, `http://example.com/claims/allowedoperation` jehož hodnota je identifikátor URI akce operace, která může být volána.</span><span class="sxs-lookup"><span data-stu-id="da8f3-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="da8f3-139">Jakmile je <xref:System.ServiceModel.ServiceAuthorizationManager> vlastní implementována, hostitel služby musí být informován o <xref:System.ServiceModel.ServiceAuthorizationManager> použití.</span><span class="sxs-lookup"><span data-stu-id="da8f3-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="da8f3-140">To se provádí tak, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="da8f3-141">Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metodou k implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> je metoda.</span><span class="sxs-lookup"><span data-stu-id="da8f3-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="da8f3-142">Předchozí kód ukazuje, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> jak metoda kontroluje, že nebyly přidány žádné nové deklarace identity, které ovlivňují zpracování a přidá konkrétní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="da8f3-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="da8f3-143">Deklarace, které jsou povoleny jsou získány z `GetAllowedOpList` metody, která je implementována vrátit konkrétní seznam operací, které uživatel může provádět.</span><span class="sxs-lookup"><span data-stu-id="da8f3-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="da8f3-144">Zásady autorizace přidá deklarace identity pro přístup k určité operaci.</span><span class="sxs-lookup"><span data-stu-id="da8f3-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="da8f3-145">To se později <xref:System.ServiceModel.ServiceAuthorizationManager> používá k provedení rozhodnutí o kontrole přístupu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="da8f3-146">Jakmile je <xref:System.IdentityModel.Policy.IAuthorizationPolicy> vlastní implementována, hostitel služby musí být informován o zásadách autorizace použít.</span><span class="sxs-lookup"><span data-stu-id="da8f3-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="da8f3-147">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="da8f3-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="da8f3-148">Klient úspěšně volá Add, Odečíst a Více metod a získá zprávu "Přístup je odepřen" při pokusu o volání Divide metoda.</span><span class="sxs-lookup"><span data-stu-id="da8f3-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="da8f3-149">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="da8f3-150">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="da8f3-150">Setup Batch File</span></span>

<span data-ttu-id="da8f3-151">Dávkový soubor Setup.bat, který je součástí této ukázky, umožňuje nakonfigurovat server s příslušnými certifikáty tak, aby spouštěl samoobslužnou aplikaci, která vyžaduje zabezpečení založené na certifikátech serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="da8f3-152">Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="da8f3-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="da8f3-153">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-153">Creating the server certificate.</span></span>

    <span data-ttu-id="da8f3-154">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="da8f3-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="da8f3-155">Proměnná %SERVER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="da8f3-156">Změňte tuto proměnnou a zadejte vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="da8f3-157">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="da8f3-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="da8f3-158">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="da8f3-159">Následující řádky v dávkovém souboru Setup.bat zkopírují certifikát serveru do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="da8f3-160">Tento krok je vyžadován, protože certifikáty, které jsou generovány programem Makecert.exe, nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="da8f3-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="da8f3-161">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="da8f3-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="da8f3-162">Vytvoření klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="da8f3-162">Creating the client certificate.</span></span>

    <span data-ttu-id="da8f3-163">Následující řádky z dávkového souboru Setup.bat vytvoří klientský certifikát, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="da8f3-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="da8f3-164">Proměnná %USER_NAME% určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="da8f3-165">Tato hodnota je nastavena na "test1", protože toto je název `IAuthorizationPolicy` hledá.</span><span class="sxs-lookup"><span data-stu-id="da8f3-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="da8f3-166">Pokud změníte hodnotu %USER_NAME%, musíte změnit `IAuthorizationPolicy.Evaluate` odpovídající hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="da8f3-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="da8f3-167">Certifikát je uložen v úložišti Moje (osobní) pod umístěním úložiště CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="da8f3-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="da8f3-168">Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="da8f3-169">Následující řádky v dávkovém souboru Setup.bat zkopírují klientský certifikát do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="da8f3-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="da8f3-170">Tento krok je vyžadován, protože certifikáty, které jsou generovány programem Makecert.exe, nejsou serverovým systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="da8f3-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="da8f3-171">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu – například certifikát emitovaný společností Microsoft – není tento krok naplnění úložiště certifikátů serveru klientským certifikátem vyžadován.</span><span class="sxs-lookup"><span data-stu-id="da8f3-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="da8f3-172">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="da8f3-172">To set up and build the sample</span></span>

1. <span data-ttu-id="da8f3-173">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="da8f3-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="da8f3-174">Chcete-li vzorek spustit v konfiguraci jednoho nebo mezi počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="da8f3-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="da8f3-175">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="da8f3-176">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="da8f3-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="da8f3-177">Otevřete příkazový řádek pro vývojáře pro Visual Studio s oprávněními správce a spusťte *soubor Setup.bat* z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="da8f3-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="da8f3-178">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="da8f3-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="da8f3-179">Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře pro sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da8f3-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="da8f3-180">Proměnná prostředí PATH nastavená v příkazovém řádku vývojáře pro sadu Visual Studio odkazuje na adresář, který obsahuje spustitelné soubory vyžadované skriptem *Setup.bat.*</span><span class="sxs-lookup"><span data-stu-id="da8f3-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="da8f3-181">Spusťte soubor Service.exe ze *služby\bin*.</span><span class="sxs-lookup"><span data-stu-id="da8f3-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="da8f3-182">Spusťte soubor Client.exe z *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="da8f3-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="da8f3-183">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="da8f3-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="da8f3-184">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="da8f3-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="da8f3-185">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="da8f3-185">To run the sample across computers</span></span>

1. <span data-ttu-id="da8f3-186">Vytvořte adresář v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="da8f3-187">Zkopírujte soubory servisních programů z *\service\bin* do adresáře v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="da8f3-188">Do servisního počítače zkopírujte také soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat.</span><span class="sxs-lookup"><span data-stu-id="da8f3-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="da8f3-189">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="da8f3-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="da8f3-190">Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="da8f3-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="da8f3-191">Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="da8f3-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="da8f3-192">Na serveru spusťte `setup.bat service` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="da8f3-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="da8f3-193">Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem *Service.cer*.</span><span class="sxs-lookup"><span data-stu-id="da8f3-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="da8f3-194">Upravte *service.exe.config* tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v>serviceCertificate), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="da8f3-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="da8f3-195">Změňte také **název** \<počítače ve\<službě>/ baseAddresses> element z localhost na plně kvalifikovaný název počítače služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="da8f3-196">Zkopírujte soubor *Service.cer* z adresáře služby do klientského adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="da8f3-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="da8f3-197">Na straně klienta spusťte `setup.bat client` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="da8f3-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="da8f3-198">Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem **test1** a exportuje klientský certifikát do souboru s názvem *Client.cer*.</span><span class="sxs-lookup"><span data-stu-id="da8f3-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="da8f3-199">V souboru *Client.exe.config* v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="da8f3-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="da8f3-200">To provést nahrazením **localhost** plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="da8f3-201">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="da8f3-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="da8f3-202">Na straně klienta spusťte *soubor ImportServiceCert.bat* v příkazovém řádku pro vývojáře pro aplikaci Visual Studio otevřenou s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="da8f3-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="da8f3-203">Tím se importuje certifikát služby ze souboru Service.cer do úložiště **CurrentUser - TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="da8f3-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="da8f3-204">Na serveru spusťte *soubor ImportClientCert.bat* v příkazovém řádku pro vývojáře pro aplikaci Visual Studio otevřenou s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="da8f3-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="da8f3-205">Tím se klientský certifikát importuje ze souboru Client.cer do úložiště **LocalMachine - TrustedPeople.**</span><span class="sxs-lookup"><span data-stu-id="da8f3-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="da8f3-206">V počítači serveru spusťte service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="da8f3-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="da8f3-207">V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="da8f3-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="da8f3-208">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="da8f3-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="da8f3-209">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="da8f3-209">Clean up after the sample</span></span>

<span data-ttu-id="da8f3-210">Chcete-li vyčistit po vzorku, spusťte *Cleanup.bat* ve složce ukázky po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="da8f3-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="da8f3-211">Tím odeberete certifikáty serveru a klienta z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="da8f3-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="da8f3-212">Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích.</span><span class="sxs-lookup"><span data-stu-id="da8f3-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="da8f3-213">Pokud jste schovali ukázky WCF, které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="da8f3-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="da8f3-214">Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .</span><span class="sxs-lookup"><span data-stu-id="da8f3-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
