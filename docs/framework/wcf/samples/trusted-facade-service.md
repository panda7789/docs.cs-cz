---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143743"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="94e0a-102">Důvěryhodná služba facade</span><span class="sxs-lookup"><span data-stu-id="94e0a-102">Trusted Facade Service</span></span>
<span data-ttu-id="94e0a-103">Tento scénář ukázka ukazuje, jak tok volajícího informace o identitě z jedné služby do druhé pomocí windows communication foundation (WCF) infrastruktury zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94e0a-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="94e0a-104">Jedná se o běžný návrhový vzor, který poskytuje funkce poskytované službou veřejné síti pomocí služby fasády.</span><span class="sxs-lookup"><span data-stu-id="94e0a-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="94e0a-105">Služba fasády se obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a promítaná podsíť) a komunikuje s back-endovou službou, která implementuje obchodní logiku a má přístup k interním datům.</span><span class="sxs-lookup"><span data-stu-id="94e0a-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="94e0a-106">Komunikační kanál mezi službou fasády a back-endovou službou prochází bránou firewall a je obvykle omezen pouze na jeden účel.</span><span class="sxs-lookup"><span data-stu-id="94e0a-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="94e0a-107">Tento vzorek se skládá z následujících složek:</span><span class="sxs-lookup"><span data-stu-id="94e0a-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="94e0a-108">Klient kalkulačky</span><span class="sxs-lookup"><span data-stu-id="94e0a-108">Calculator client</span></span>  
  
- <span data-ttu-id="94e0a-109">Kalkulačka fasádní služba</span><span class="sxs-lookup"><span data-stu-id="94e0a-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="94e0a-110">Služba back-end kalkulačky</span><span class="sxs-lookup"><span data-stu-id="94e0a-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="94e0a-111">Služba fasády je zodpovědná za ověření požadavku a ověření volajícího.</span><span class="sxs-lookup"><span data-stu-id="94e0a-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="94e0a-112">Po úspěšném ověření a ověření předá požadavek back-endové službě pomocí řízeného komunikačního kanálu z hraniční sítě do interní sítě.</span><span class="sxs-lookup"><span data-stu-id="94e0a-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="94e0a-113">Jako součást předané žádosti fasádní služba obsahuje informace o identitě volajícího tak, aby back-endová služba mohla tyto informace použít při zpracování.</span><span class="sxs-lookup"><span data-stu-id="94e0a-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="94e0a-114">Identita volajícího je přenášena `Username` pomocí tokenu `Security` zabezpečení uvnitř záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="94e0a-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="94e0a-115">Ukázka používá infrastrukturu zabezpečení WCF k přenosu `Security` a extrahování těchto informací z hlavičky.</span><span class="sxs-lookup"><span data-stu-id="94e0a-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="94e0a-116">Back-endová služba důvěřuje službě fasády k ověření volajícího.</span><span class="sxs-lookup"><span data-stu-id="94e0a-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="94e0a-117">Z tohoto důvodu back-endová služba neověřuje volajícího znovu; používá informace o totožnosti poskytnuté službou fasády v předaných požadavcích.</span><span class="sxs-lookup"><span data-stu-id="94e0a-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="94e0a-118">Z důvodu tohoto vztahu důvěryhodnosti musí služba back-end ověřit službu fasády, aby bylo zajištěno, že předávaná zpráva pochází z důvěryhodného zdroje - v tomto případě z fasádní služby.</span><span class="sxs-lookup"><span data-stu-id="94e0a-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="94e0a-119">Implementace</span><span class="sxs-lookup"><span data-stu-id="94e0a-119">Implementation</span></span>  
 <span data-ttu-id="94e0a-120">V této ukázce jsou dvě komunikační cesty.</span><span class="sxs-lookup"><span data-stu-id="94e0a-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="94e0a-121">První je mezi klientem a fasádní službou, druhá je mezi fasádní službou a back-endovou službou.</span><span class="sxs-lookup"><span data-stu-id="94e0a-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="94e0a-122">Komunikační cesta mezi klientem a fasádní službou</span><span class="sxs-lookup"><span data-stu-id="94e0a-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="94e0a-123">Klient komunikační cesty služby fasády `wsHttpBinding` používá `UserName` s typem pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="94e0a-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="94e0a-124">To znamená, že klient používá uživatelské jméno a heslo k ověření služby fasády a služba fasády používá certifikát X.509 k ověření klientovi.</span><span class="sxs-lookup"><span data-stu-id="94e0a-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="94e0a-125">Konfigurace vazby vypadá jako následující příklad.</span><span class="sxs-lookup"><span data-stu-id="94e0a-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="94e0a-126">Služba fasády ověřuje volajícího `UserNamePasswordValidator` pomocí vlastní implementace.</span><span class="sxs-lookup"><span data-stu-id="94e0a-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="94e0a-127">Pro demonstrační účely ověřování pouze zajišťuje, že uživatelské jméno volajícího odpovídá prezentované heslo.</span><span class="sxs-lookup"><span data-stu-id="94e0a-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="94e0a-128">V reálné situaci je uživatel pravděpodobně ověřen pomocí služby Active Directory nebo vlastního poskytovatele členství ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94e0a-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="94e0a-129">Implementace validátoru je `FacadeService.cs` umístěna v souboru.</span><span class="sxs-lookup"><span data-stu-id="94e0a-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="94e0a-130">Vlastní validátor je nakonfigurován tak, `serviceCredentials` aby byl použit uvnitř chování v konfiguračním souboru služby fasády.</span><span class="sxs-lookup"><span data-stu-id="94e0a-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="94e0a-131">Toto chování se také používá ke konfiguraci certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="94e0a-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="94e0a-132">Komunikační cesta mezi službou Fasáda a Backend Service</span><span class="sxs-lookup"><span data-stu-id="94e0a-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="94e0a-133">Služba fasády pro komunikační cestu back-endové `customBinding` služby používá a, která se skládá z několika elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="94e0a-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="94e0a-134">Tato vazba dosahuje dvě věci.</span><span class="sxs-lookup"><span data-stu-id="94e0a-134">This binding accomplishes two things.</span></span> <span data-ttu-id="94e0a-135">Ověřuje službu fasády a back-endovou službu, aby bylo zajištěno, že komunikace je zabezpečená a pochází z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="94e0a-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="94e0a-136">Navíc také přenáší identitu počátečního volajícího uvnitř `Username` tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94e0a-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="94e0a-137">V tomto případě pouze počáteční volajícího uživatelské jméno je přenesena do back-endové služby, heslo není součástí zprávy.</span><span class="sxs-lookup"><span data-stu-id="94e0a-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="94e0a-138">Důvodem je, že back-endová služba důvěřuje službě fasády k ověření volajícího před předáním požadavku.</span><span class="sxs-lookup"><span data-stu-id="94e0a-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="94e0a-139">Vzhledem k tomu, že služba fasády se ověřuje samo službě back-end, může back-endová služba důvěřovat informacím obsaženým v předaný požadavek.</span><span class="sxs-lookup"><span data-stu-id="94e0a-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="94e0a-140">Následuje konfigurace vazby pro tuto komunikační cestu.</span><span class="sxs-lookup"><span data-stu-id="94e0a-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="94e0a-141">[ \<Prvek vazby>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) se postará o přenos a extrakci uživatelského jména volajícího.</span><span class="sxs-lookup"><span data-stu-id="94e0a-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="94e0a-142">[ \<WindowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) starat o ověřování fasády a back-endové služby a ochranu zpráv.</span><span class="sxs-lookup"><span data-stu-id="94e0a-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="94e0a-143">Chcete-li předat požadavek, implementace služby fasády musí poskytnout počáteční volajícího uživatelské jméno tak, aby wcf infrastruktury zabezpečení můžete umístit do předané zprávy.</span><span class="sxs-lookup"><span data-stu-id="94e0a-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="94e0a-144">Uživatelské jméno počátečního volajícího je k dispozici v implementaci služby `ClientCredentials` fasády nastavením ve vlastnosti instance proxy klienta, kterou služba fasády používá ke komunikaci se službou back-end.</span><span class="sxs-lookup"><span data-stu-id="94e0a-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="94e0a-145">Následující kód ukazuje, jak `GetCallerIdentity` je metoda implementována ve službě fasády.</span><span class="sxs-lookup"><span data-stu-id="94e0a-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="94e0a-146">Jiné metody používají stejný vzor.</span><span class="sxs-lookup"><span data-stu-id="94e0a-146">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="94e0a-147">Jak je znázorněno v předchozím kódu, `ClientCredentials` heslo není nastaveno na vlastnost, je nastaveno pouze uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="94e0a-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="94e0a-148">WCF infrastruktury zabezpečení vytvoří token zabezpečení uživatelského jména bez hesla v tomto případě, což je přesně to, co je požadováno v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="94e0a-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="94e0a-149">V back-endové službě musí být ověřeny informace obsažené v tokenu zabezpečení uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="94e0a-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="94e0a-150">Ve výchozím nastavení se zabezpečení WCF pokusí namapovat uživatele na účet systému Windows pomocí poskytnutého hesla.</span><span class="sxs-lookup"><span data-stu-id="94e0a-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="94e0a-151">V tomto případě není k dispozici žádné heslo a back-endová služba není vyžadována k ověření uživatelského jména, protože ověřování již bylo provedeno službou fasády.</span><span class="sxs-lookup"><span data-stu-id="94e0a-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="94e0a-152">Chcete-li implementovat tuto funkci `UserNamePasswordValidator` v WCF, vlastní je za předpokladu, že pouze vynucuje, že uživatelské jméno je zadán v tokenu a neprovádí žádné další ověřování.</span><span class="sxs-lookup"><span data-stu-id="94e0a-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="94e0a-153">Vlastní validátor je nakonfigurován tak, `serviceCredentials` aby byl použit uvnitř chování v konfiguračním souboru služby fasády.</span><span class="sxs-lookup"><span data-stu-id="94e0a-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="94e0a-154">Chcete-li extrahovat informace o uživatelském jménu a informace o účtu `ServiceSecurityContext` služby důvěryhodné fasády, používá implementace back-endové služby třídu.</span><span class="sxs-lookup"><span data-stu-id="94e0a-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="94e0a-155">Následující kód ukazuje, `GetCallerIdentity` jak je metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="94e0a-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="94e0a-156">Informace o účtu služby fasády jsou `ServiceSecurityContext.Current.WindowsIdentity` extrahovány pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="94e0a-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="94e0a-157">Pro přístup k informacím o počátečním `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` volajícím používá back-endová služba vlastnost.</span><span class="sxs-lookup"><span data-stu-id="94e0a-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="94e0a-158">Hledá `Identity` nárok s typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="94e0a-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="94e0a-159">Tato deklarace je automaticky generována infrastrukturou zabezpečení WCF z informací obsažených v tokenu `Username` zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94e0a-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="94e0a-160">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="94e0a-160">Running the sample</span></span>  
 <span data-ttu-id="94e0a-161">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="94e0a-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="94e0a-162">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="94e0a-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="94e0a-163">Chcete-li služby vypnout stisknutím klávesy ENTER v oknech konzoly služby a back-end.</span><span class="sxs-lookup"><span data-stu-id="94e0a-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="94e0a-164">Dávkový soubor Setup.bat, který je součástí ukázky scénáře Trusted Facade, umožňuje nakonfigurovat server s příslušným certifikátem tak, aby spouštěl službu fasády, která vyžaduje zabezpečení založené na certifikátu k ověření klientovi.</span><span class="sxs-lookup"><span data-stu-id="94e0a-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="94e0a-165">Podrobnosti naleznete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="94e0a-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="94e0a-166">Následující text poskytuje stručný přehled různých částí dávkových souborů.</span><span class="sxs-lookup"><span data-stu-id="94e0a-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="94e0a-167">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="94e0a-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="94e0a-168">Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="94e0a-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="94e0a-169">Proměnná `%SERVER_NAME%` určuje název serveru - výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="94e0a-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="94e0a-170">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="94e0a-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="94e0a-171">Instalace certifikátu fasádní služby do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="94e0a-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="94e0a-172">Následující řádek zkopíruje certifikát fasádní služby do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="94e0a-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="94e0a-173">Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="94e0a-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="94e0a-174">Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="94e0a-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94e0a-175">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="94e0a-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="94e0a-176">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94e0a-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="94e0a-177">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="94e0a-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="94e0a-178">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="94e0a-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="94e0a-179">Ujistěte se, že cesta obsahuje složku, kde je umístěn makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="94e0a-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="94e0a-180">Spusťte soubor Setup.bat z ukázkové instalační složky.</span><span class="sxs-lookup"><span data-stu-id="94e0a-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="94e0a-181">Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="94e0a-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="94e0a-182">Spuštění nástroje BackendService.exe z adresáře \BackendService\bin v samostatném okně konzoly</span><span class="sxs-lookup"><span data-stu-id="94e0a-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="94e0a-183">Spuštění nástroje FacadeService.exe z adresáře \FacadeService\bin v samostatném okně konzoly</span><span class="sxs-lookup"><span data-stu-id="94e0a-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="94e0a-184">Spusťte soubor Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="94e0a-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="94e0a-185">Aktivita klienta je zobrazena v aplikaci klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="94e0a-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="94e0a-186">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="94e0a-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="94e0a-187">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="94e0a-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="94e0a-188">Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.</span><span class="sxs-lookup"><span data-stu-id="94e0a-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="94e0a-189">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="94e0a-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="94e0a-190">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="94e0a-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="94e0a-191">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="94e0a-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94e0a-192">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="94e0a-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
