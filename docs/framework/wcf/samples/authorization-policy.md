---
title: Zásada autorizace
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: eaf4dfc6e1f02a1cd98d9ab48af70426e8ba6151
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674362"
---
# <a name="authorization-policy"></a><span data-ttu-id="1e130-102">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="1e130-102">Authorization Policy</span></span>

<span data-ttu-id="1e130-103">Tento příklad ukazuje, jak implementovat zásady autorizace vlastních deklarací identity a přidružená služba vlastního Správce autorizací.</span><span class="sxs-lookup"><span data-stu-id="1e130-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="1e130-104">To je užitečné, když služba usnadňující kontroly přístupu podle deklarací identity k operacím služby a před kontroly přístupu udělí volajícímu určitá práva.</span><span class="sxs-lookup"><span data-stu-id="1e130-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="1e130-105">Tento příklad ukazuje obě proces přidávání deklarací identity, stejně jako proces pro provádění kontroly přístupu pro dokončené sadu deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="1e130-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="1e130-106">Všechny zprávy aplikace mezi klientem a serverem jsou podepsaný a zašifrovaný.</span><span class="sxs-lookup"><span data-stu-id="1e130-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="1e130-107">Ve výchozím nastavení se `wsHttpBinding` vazby, uživatelské jméno a heslo, které poskytl klient, slouží k přihlášení k platný účet systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="1e130-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="1e130-108">Tato ukázka předvádí, jak využívat vlastní <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-108">This sample demonstrates how to utilize a custom <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` to authenticate the client.</span></span> <span data-ttu-id="1e130-109">Kromě toho tento příklad ukazuje ověřování do služby pomocí certifikátu X.509 klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="1e130-110">Tento příklad ukazuje implementaci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a <xref:System.ServiceModel.ServiceAuthorizationManager>, která mezi nimi udělit přístup na konkrétní metody služby pro konkrétní uživatele.</span><span class="sxs-lookup"><span data-stu-id="1e130-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="1e130-111">Tato ukázka je založena na [zabezpečení zpráv s uživatelským jménem](../../../../docs/framework/wcf/samples/message-security-user-name.md), ale ukazuje, jak provádět transformace deklarací identity před verzí <xref:System.ServiceModel.ServiceAuthorizationManager> volána.</span><span class="sxs-lookup"><span data-stu-id="1e130-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="1e130-112">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1e130-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="1e130-113">Stručně řečeno, tento příklad ukazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="1e130-113">In summary, this sample demonstrates how:</span></span>

-   <span data-ttu-id="1e130-114">Klient lze ověřit pomocí uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="1e130-114">The client can be authenticated using a user name-password.</span></span>

-   <span data-ttu-id="1e130-115">Klient lze ověřit pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="1e130-115">The client can be authenticated using an X.509 certificate.</span></span>

-   <span data-ttu-id="1e130-116">Server ověří klienta přihlašovacích údajů, kteří vlastní `UsernamePassword` program pro ověření.</span><span class="sxs-lookup"><span data-stu-id="1e130-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

-   <span data-ttu-id="1e130-117">Server byl ověřovaný pomocí certifikátu X.509 serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-117">The server is authenticated using the server's X.509 certificate.</span></span>

-   <span data-ttu-id="1e130-118">Server můžete použít <xref:System.ServiceModel.ServiceAuthorizationManager> pro řízení přístupu k určité metody ve službě.</span><span class="sxs-lookup"><span data-stu-id="1e130-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

-   <span data-ttu-id="1e130-119">Jak implementovat <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="1e130-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="1e130-120">Služba poskytuje dva koncové body služby pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Každý koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1e130-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="1e130-121">Jedna vazba konfigurována se standardní `wsHttpBinding` vazby, která používá ověřování uživatelským jménem WS-Security a klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="1e130-122">Druhé vazby má nakonfigurovanou standardní `wsHttpBinding` vazby, která používá ověřování certifikátem WS-Security a klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="1e130-123">[ \<Chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Určuje, že má být použit pro ověřování služby jsou přihlašovací údaje uživatele.</span><span class="sxs-lookup"><span data-stu-id="1e130-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="1e130-124">Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` vlastnost jako `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="1e130-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="1e130-125">Konfigurace koncového bodu každá klient se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1e130-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="1e130-126">Vazba je klient nakonfigurovaný s režimem zabezpečení uvedené v tomto případě v [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a `clientCredentialType` podle [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1e130-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="1e130-127">Implementace klienta pro uživatele na základě názvu koncového bodu, nastaví uživatelské jméno a heslo pro použití.</span><span class="sxs-lookup"><span data-stu-id="1e130-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="1e130-128">Implementace klienta pro koncový bod pomocí certifikátu, nastaví klientský certifikát k použití.</span><span class="sxs-lookup"><span data-stu-id="1e130-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="1e130-129">Tato ukázka používá vlastní <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> k ověření uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="1e130-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="1e130-130">Implementuje vzorek `MyCustomUserNamePasswordValidator`odvozenou z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="1e130-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="1e130-131">V dokumentaci <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> Další informace.</span><span class="sxs-lookup"><span data-stu-id="1e130-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="1e130-132">Pro účely integrace s představením toho, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, tato ukázka vlastní validátor implementuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu tak, aby přijímal párů jméno/heslo uživatele kde uživatelské jméno odpovídá heslu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1e130-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="1e130-133">Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1e130-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="1e130-134">To se provádí pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="1e130-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="1e130-135">Nebo můžete provést totéž v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="1e130-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="1e130-136">Windows Communication Foundation (WCF) poskytuje bohaté možnosti založené na deklaracích model pro provádění kontroly přístupu.</span><span class="sxs-lookup"><span data-stu-id="1e130-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="1e130-137"><xref:System.ServiceModel.ServiceAuthorizationManager> Objekt se používá k provádění kontroly přístupu a určit, jestli deklarace identity přidružené ke klientovi splňují požadavky potřebné pro přístup k metodě služby.</span><span class="sxs-lookup"><span data-stu-id="1e130-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="1e130-138">Pro demonstrační účely, tento příklad ukazuje implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> , který implementuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda umožňující uživateli přístup k metodám založené na deklaracích identity typu http://example.com/claims/allowedoperation jehož hodnota je identifikátor URI akce, která je operace mohou být volána.</span><span class="sxs-lookup"><span data-stu-id="1e130-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type http://example.com/claims/allowedoperation whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="1e130-139">Jednou vlastní <xref:System.ServiceModel.ServiceAuthorizationManager> je implementováno, hostitele služby musí být informováni o <xref:System.ServiceModel.ServiceAuthorizationManager> používat.</span><span class="sxs-lookup"><span data-stu-id="1e130-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="1e130-140">Důvodem je, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1e130-140">This is done as shown in the following code.</span></span>

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="1e130-141">Primární <xref:System.IdentityModel.Policy.IAuthorizationPolicy> metody k implementaci je <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody.</span><span class="sxs-lookup"><span data-stu-id="1e130-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="1e130-142">Předchozí kód ukazuje jak <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda zkontroluje, že byly přidány žádné nové deklarace identity, která ovlivňují zpracování a přidává deklarace identity specifické pro.</span><span class="sxs-lookup"><span data-stu-id="1e130-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="1e130-143">Deklarace identity, které jsou povoleny jsou získávány z `GetAllowedOpList` metodu, která je implementováno s cílem vrátit konkrétní seznam operací, které uživatel může provádět.</span><span class="sxs-lookup"><span data-stu-id="1e130-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="1e130-144">Zásady autorizace přidá deklarace identity pro přístup k určité operace.</span><span class="sxs-lookup"><span data-stu-id="1e130-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="1e130-145">Používá se později pomocí <xref:System.ServiceModel.ServiceAuthorizationManager> k provedení rozhodnutí o kontrolu přístupu.</span><span class="sxs-lookup"><span data-stu-id="1e130-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="1e130-146">Jednou vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementované, hostitele služby musí být informováni o zásad autorizace tak, aby používat.</span><span class="sxs-lookup"><span data-stu-id="1e130-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="1e130-147">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1e130-148">Klient úspěšně volá přidat, rozdílového a několik metod a získá zprávu "Přístup byl odepřen" při pokusu o volání metody dělení.</span><span class="sxs-lookup"><span data-stu-id="1e130-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="1e130-149">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="1e130-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="1e130-150">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="1e130-150">Setup Batch File</span></span>

<span data-ttu-id="1e130-151">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="1e130-152">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="1e130-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

-   <span data-ttu-id="1e130-153">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-153">Creating the server certificate.</span></span>

     <span data-ttu-id="1e130-154">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1e130-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="1e130-155">% Proměnná % název_serveru Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="1e130-156">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="1e130-157">Výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="1e130-157">The default value is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="1e130-158">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-158">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="1e130-159">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="1e130-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="1e130-160">Tento krok je vyžadován, protože certifikáty, které jsou generovány Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="1e130-161">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="1e130-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="1e130-162">Vytváří se certifikát klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-162">Creating the client certificate.</span></span>

     <span data-ttu-id="1e130-163">Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="1e130-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="1e130-164">% Proměnná % uživatelské_jméno Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="1e130-165">Tato hodnota nastavená na "test1", protože jde o název `IAuthorizationPolicy` hledá.</span><span class="sxs-lookup"><span data-stu-id="1e130-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="1e130-166">Pokud změníte hodnotu % uživatelské_jméno musíte změnit odpovídající hodnotu v `IAuthorizationPolicy.Evaluate` metody.</span><span class="sxs-lookup"><span data-stu-id="1e130-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

     <span data-ttu-id="1e130-167">Certifikát je uložen v úložišti (osobních) v části CurrentUser umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="1e130-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="1e130-168">Instalaci klientského certifikátu do úložiště důvěryhodných certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-168">Installing the client certificate into server's trusted certificate store.</span></span>

     <span data-ttu-id="1e130-169">Následující řádky do dávkový soubor Setup.bat zkopírujte klientský certifikát do úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="1e130-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="1e130-170">Tento krok je nutný, protože certifikáty, které jsou generovány Makecert.exe implicitně nedůvěřuje serverového systému.</span><span class="sxs-lookup"><span data-stu-id="1e130-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="1e130-171">Pokud už máte certifikát, který je integrován v důvěryhodných kořenových certifikátů – například certifikátů vystavených Microsoftem – v tomto kroku naplnění úložiště certifikátů serveru pomocí certifikátu klienta se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="1e130-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="1e130-172">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="1e130-172">To set up and build the sample</span></span>

1. <span data-ttu-id="1e130-173">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e130-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="1e130-174">Ke spuštění ukázky v konfiguraci s jedním nebo více počítači, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="1e130-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="1e130-175">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="1e130-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="1e130-176">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="1e130-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="1e130-177">Otevřete Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spusťte *Setup.bat* z instalační složky vzorku.</span><span class="sxs-lookup"><span data-stu-id="1e130-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="1e130-178">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="1e130-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1e130-179">Dávkový soubor Setup.bat slouží ke spuštění z příkazového řádku pro vývojáře pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e130-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="1e130-180">Proměnné prostředí PATH v nastavení v rámci příkazového řádku pro vývojáře pro Visual Studio odkazuje na adresář obsahující spustitelné soubory, které jsou vyžadované *Setup.bat* skriptu.</span><span class="sxs-lookup"><span data-stu-id="1e130-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="1e130-181">Spuštění Service.exe z *service\bin*.</span><span class="sxs-lookup"><span data-stu-id="1e130-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="1e130-182">Spusťte Client.exe z *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="1e130-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="1e130-183">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="1e130-183">Client activity is displayed on the client console application.</span></span>

  <span data-ttu-id="1e130-184">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1e130-184">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1e130-185">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="1e130-185">To run the sample across computers</span></span>

1. <span data-ttu-id="1e130-186">Vytvoření adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="1e130-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="1e130-187">Kopírování souborů program služby *\service\bin* do adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="1e130-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="1e130-188">Také kopírovat soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="1e130-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="1e130-189">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="1e130-190">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="1e130-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="1e130-191">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="1e130-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="1e130-192">Na serveru, spusťte `setup.bat service` v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1e130-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="1e130-193">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem *Service.cer*.</span><span class="sxs-lookup"><span data-stu-id="1e130-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="1e130-194">Upravit *Service.exe.config* tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="1e130-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="1e130-195">Také změnit **computername** v \<služby > /\<baseAddresses > element z místního hostitele, plně kvalifikovaný název počítače služby.</span><span class="sxs-lookup"><span data-stu-id="1e130-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="1e130-196">Kopírovat *Service.cer* soubor z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="1e130-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="1e130-197">Na straně klienta, spouštění `setup.bat client` v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1e130-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="1e130-198">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem **test1** a exportuje certifikát klienta do souboru s názvem *Client.cer*.</span><span class="sxs-lookup"><span data-stu-id="1e130-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="1e130-199">V *Client.exe.config* souborů v klientském počítači, změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="1e130-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="1e130-200">To udělat tak, že nahradíte **localhost** s plně kvalifikovaný název serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="1e130-201">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="1e130-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="1e130-202">Na straně klienta, spouštění *ImportServiceCert.bat* v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1e130-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="1e130-203">Tento postup importuje certifikát služby ze souboru Service.cer do **CurrentUser - TrustedPeople** ukládat.</span><span class="sxs-lookup"><span data-stu-id="1e130-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="1e130-204">Na serveru, spusťte *ImportClientCert.bat* v Developer Command Prompt pro sadu Visual Studio otevřeného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1e130-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

   <span data-ttu-id="1e130-205">Tento postup importuje klientský certifikát ze souboru Client.cer do **LocalMachine - TrustedPeople** ukládat.</span><span class="sxs-lookup"><span data-stu-id="1e130-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="1e130-206">Na počítači serveru spusťte Service.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1e130-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="1e130-207">Na klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1e130-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

   <span data-ttu-id="1e130-208">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="1e130-208">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="1e130-209">Vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="1e130-209">Clean up after the sample</span></span>

<span data-ttu-id="1e130-210">Chcete-li vyčistit po ukázce, spusťte *Cleanup.bat* ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="1e130-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="1e130-211">Tím serverových a klientských certifikátů z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1e130-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="1e130-212">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích.</span><span class="sxs-lookup"><span data-stu-id="1e130-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="1e130-213">Pokud jste spustili Ukázky WCF, které používají certifikáty na počítačích, je nutné vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople uložit.</span><span class="sxs-lookup"><span data-stu-id="1e130-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="1e130-214">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="1e130-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>