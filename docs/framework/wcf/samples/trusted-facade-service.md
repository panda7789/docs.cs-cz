---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 40264ee018d3c09d86e1bcd0b8cc96c0610219f9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711880"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="cc4cb-102">Důvěryhodná služba facade</span><span class="sxs-lookup"><span data-stu-id="cc4cb-102">Trusted Facade Service</span></span>
<span data-ttu-id="cc4cb-103">Tato ukázka scénáře ukazuje, jak flowovat informace o identitě volajících z jedné služby do jiné pomocí infrastruktury zabezpečení Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cc4cb-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="cc4cb-104">Jedná se o běžný vzor návrhu k vystavení funkcí poskytovaných službou do veřejné sítě pomocí služby fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="cc4cb-105">Služba fasády se obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná Zone a monitorovaná podsíť) a komunikuje se službou back-end, která implementuje obchodní logiku a má přístup k interním datům.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="cc4cb-106">Komunikační kanál mezi službou fasády a back-end službou prochází přes bránu firewall a je obvykle omezený jenom pro jediný účel.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="cc4cb-107">Tato ukázka se skládá z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="cc4cb-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="cc4cb-108">Klient kalkulačky</span><span class="sxs-lookup"><span data-stu-id="cc4cb-108">Calculator client</span></span>  
  
- <span data-ttu-id="cc4cb-109">Služba na fasádu kalkulačky</span><span class="sxs-lookup"><span data-stu-id="cc4cb-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="cc4cb-110">Back-end služba kalkulačky</span><span class="sxs-lookup"><span data-stu-id="cc4cb-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="cc4cb-111">Služba fasády zodpovídá za ověření žádosti a ověřování volajícího.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="cc4cb-112">Po úspěšném ověření a ověření předá požadavek službě back-end pomocí řízeného komunikačního kanálu z hraniční sítě do interní sítě.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="cc4cb-113">V rámci předávané žádosti služba fasády obsahuje informace o identitě volajícího, aby služba back-end mohla tyto informace použít ve svém zpracování.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="cc4cb-114">Identita volajícího se přenáší pomocí `Username` tokenu zabezpečení uvnitř záhlaví `Security` zprávy.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="cc4cb-115">Ukázka používá infrastrukturu zabezpečení WCF k přenosu a extrakci těchto informací z hlavičky `Security`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cc4cb-116">Back-end služba důvěřuje službě fasády k ověření volajícího.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="cc4cb-117">Proto služba back-end neověřuje volajícího znovu. používá informace o identitě poskytované službou fasády v přesměrovaném požadavku.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="cc4cb-118">Z důvodu tohoto vztahu důvěryhodnosti musí back-end služba ověřit službu fasády, aby se zajistilo, že Předaná zpráva pochází z důvěryhodného zdroje – v tomto případě je to služba fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="cc4cb-119">Implementace</span><span class="sxs-lookup"><span data-stu-id="cc4cb-119">Implementation</span></span>  
 <span data-ttu-id="cc4cb-120">V této ukázce jsou k dispozici dvě cesty komunikace.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="cc4cb-121">První je mezi klientem a službou fasády, druhým je mezi službou fasády a back-end službou.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="cc4cb-122">Komunikační cesta mezi klientem a službou fasády</span><span class="sxs-lookup"><span data-stu-id="cc4cb-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="cc4cb-123">Klient pro komunikační cestu služby fasády používá `wsHttpBinding` s typem přihlašovacích údajů klienta `UserName`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="cc4cb-124">To znamená, že klient nástroje používá uživatelské jméno a heslo k ověření ve službě fasády a služba fasády používá k ověření klienta certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="cc4cb-125">Konfigurace vazby vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-126">Služba fasády ověřuje volajícího pomocí vlastní implementace `UserNamePasswordValidator`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="cc4cb-127">Pro demonstrační účely ověřování zajišťuje pouze uživatelské jméno volajícího, které odpovídá prezentovanému heslu.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="cc4cb-128">V reálném čase se uživatel pravděpodobně ověřuje pomocí služby Active Directory nebo vlastního poskytovatele členství v ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="cc4cb-129">Implementace validátoru se nachází v souboru `FacadeService.cs`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-130">Vlastní validátor je nakonfigurován tak, aby se používal v rámci chování `serviceCredentials` v konfiguračním souboru služby fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="cc4cb-131">Toto chování se používá také ke konfiguraci certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="cc4cb-132">Komunikační cesta mezi službou fasády a back-end službou</span><span class="sxs-lookup"><span data-stu-id="cc4cb-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="cc4cb-133">Služba fasády pro cestu komunikace back-end služby používá `customBinding`, který se skládá z několika prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="cc4cb-134">Tato vazba dosahuje dvou věcí.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-134">This binding accomplishes two things.</span></span> <span data-ttu-id="cc4cb-135">Ověřuje službu fasády a back-end službu, aby bylo zajištěno, že komunikace je zabezpečená a pochází z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="cc4cb-136">Kromě toho také přenáší identitu počátečního volajícího v tokenu zabezpečení `Username`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="cc4cb-137">V takovém případě se do služby back-end přenáší jenom počáteční uživatelské jméno volajícího, heslo není zahrnuté do zprávy.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="cc4cb-138">Důvodem je, že back-end služba důvěřuje službě fasády, aby před předáním žádosti do ní ověřila volajícího.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="cc4cb-139">Vzhledem k tomu, že se služba fasády ověřuje pro back-end službu, může služba back-end důvěřovat informacím obsaženým v přesměrovaném požadavku.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="cc4cb-140">Následuje konfigurace vazby pro tuto cestu komunikace.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-141">Prvek vazby [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) postará o počáteční přenos a extrakci uživatelského jména volajícího.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="cc4cb-142">[\<zabezpečení windowsstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) postarat o ověřování fasády a back-endové služby a ochrany zpráv.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="cc4cb-143">Pro přeposlání žádosti musí implementace služby fasády poskytnout počáteční uživatelské jméno volajícího, aby mohla infrastruktura zabezpečení WCF umístit tuto zprávu do předané zprávy.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="cc4cb-144">Počáteční uživatelské jméno volajícího je k dispozici v implementaci služby fasády tím, že ji nastavíte ve vlastnosti `ClientCredentials` v instanci proxy serveru klienta, kterou služba fasády používá ke komunikaci s back-end službou.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="cc4cb-145">Následující kód ukazuje, jak je metoda `GetCallerIdentity` implementována ve službě fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="cc4cb-146">Jiné metody používají stejný vzor.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-147">Jak je znázorněno v předchozím kódu, heslo není nastaveno na vlastnost `ClientCredentials`, je nastaveno pouze uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="cc4cb-148">Infrastruktura zabezpečení WCF vytvoří v tomto případě token zabezpečení uživatelského jména bez hesla, což je přesně to, co se v tomto scénáři vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="cc4cb-149">V back-end službě musí být ověřené informace obsažené v tokenu zabezpečení uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="cc4cb-150">Ve výchozím nastavení se zabezpečení služby WCF pokusí uživatele mapovat na účet systému Windows pomocí zadaného hesla.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="cc4cb-151">V tomto případě není k dispozici žádné heslo a služba back-end není pro ověření uživatelského jména nutná, protože ověřování již provedla služba fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="cc4cb-152">K implementaci této funkce ve službě WCF je k dispozici vlastní `UserNamePasswordValidator`, která vynutila pouze zadání uživatelského jména v tokenu a neprovádí žádné další ověřování.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-153">Vlastní validátor je nakonfigurován tak, aby se používal v rámci chování `serviceCredentials` v konfiguračním souboru služby fasády.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-154">K extrakci informací o uživatelském jménu a informací o účtu důvěryhodné služby fasády používá implementace back-end služby třídu `ServiceSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="cc4cb-155">Následující kód ukazuje, jak je implementována metoda `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-156">Informace o účtu služby fasády jsou extrahovány pomocí vlastnosti `ServiceSecurityContext.Current.WindowsIdentity`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="cc4cb-157">Chcete-li získat přístup k informacím o počátečním volajícím, služba back-end používá vlastnost `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="cc4cb-158">Vyhledá `Identity` deklarací identity typu `Name`.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="cc4cb-159">Tato deklarace je automaticky generovaná infrastrukturou zabezpečení WCF z informací obsažených v `Username` tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="cc4cb-160">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="cc4cb-160">Running the sample</span></span>  
 <span data-ttu-id="cc4cb-161">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cc4cb-162">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="cc4cb-163">Chcete-li ukončit služby, stiskněte klávesu ENTER ve Windows a v konzole služby back-end Service.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="cc4cb-164">Dávkový soubor Setup. bat, který je součástí ukázky důvěryhodných scénářů průčelí, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění služby fasády, která vyžaduje, aby se k ověřování na klienta vyžadovalo zabezpečení založené na certifikátech.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="cc4cb-165">Podrobnosti najdete v postupu nastavení na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="cc4cb-166">Níže najdete stručný přehled různých částí dávkových souborů.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="cc4cb-167">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="cc4cb-168">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="cc4cb-169">Proměnná `%SERVER_NAME%` Určuje název serveru – výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="cc4cb-170">Certifikát je uložený v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="cc4cb-171">Instalace certifikátu služby fasády do důvěryhodného úložiště certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="cc4cb-172">Následující řádek zkopíruje certifikát služby fasády do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="cc4cb-173">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="cc4cb-174">Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc4cb-175">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="cc4cb-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cc4cb-176">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc4cb-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cc4cb-177">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc4cb-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="cc4cb-178">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="cc4cb-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="cc4cb-179">Ujistěte se, že cesta obsahuje složku, ve které se nachází nástroj Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="cc4cb-180">Z ukázkové instalační složky spusťte Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="cc4cb-181">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="cc4cb-182">Spusťte BackendService. exe z adresáře \BackendService\bin v samostatném okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="cc4cb-183">Spusťte FacadeService. exe z adresáře \FacadeService\bin v samostatném okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="cc4cb-184">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="cc4cb-185">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="cc4cb-186">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="cc4cb-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="cc4cb-187">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="cc4cb-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="cc4cb-188">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cc4cb-189">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc4cb-190">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-190">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cc4cb-191">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc4cb-192">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-192">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
