---
title: Důvěryhodná služba facade
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e7e55cc9d4bc9f0f81ad0570b37d7a749e6fadc2
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332430"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="c7d7b-102">Důvěryhodná služba facade</span><span class="sxs-lookup"><span data-stu-id="c7d7b-102">Trusted Facade Service</span></span>
<span data-ttu-id="c7d7b-103">Tento ukázkový scénář ukazuje, jak tok volajícího informace o identitách z jedné služby do jiného pomocí Windows Communication Foundation (WCF) Infrastruktura zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="c7d7b-104">To je běžný vzor návrhu ke zveřejnění funkce poskytované službou ve veřejné síti pomocí služby průčelí.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="c7d7b-105">Služba průčelí obvykle nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a monitorovaná podsíť) a komunikuje s back-end službu, která implementuje obchodní logiku a má přístup k interní data.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="c7d7b-106">Komunikační kanál mezi službou průčelí a back-end službu prochází přes bránu firewall a je obvykle omezené pouze jedinému účelu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="c7d7b-107">Tento příklad se skládá z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="c7d7b-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="c7d7b-108">Kalkulačka klienta</span><span class="sxs-lookup"><span data-stu-id="c7d7b-108">Calculator client</span></span>  
  
-   <span data-ttu-id="c7d7b-109">Kalkulačka průčelí služby</span><span class="sxs-lookup"><span data-stu-id="c7d7b-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="c7d7b-110">Kalkulačka back-end službou</span><span class="sxs-lookup"><span data-stu-id="c7d7b-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="c7d7b-111">Adaptační vrstva služby zodpovídá za ověření žádosti a ověřování volající.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="c7d7b-112">Po úspěšném ověření a ověření předá požadavek do služby back-end pomocí řízené komunikační kanál z hraniční sítě k interní síti.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="c7d7b-113">Jako součást předaný požadavek průčelí služba obsahuje informace o identitu volajícího tak, aby službě back-end tyto informace můžete použít v jeho zpracování.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="c7d7b-114">Identita volajícího se přenáší prostřednictvím `Username` token zabezpečení ve zprávě `Security` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="c7d7b-115">Ukázka používá k přenosu a získání informací z Infrastruktura zabezpečení WCF `Security` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7d7b-116">Back-end službu vztahy důvěryhodnosti služby průčelí ověřit volající.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="c7d7b-117">Z tohoto důvodu back-end službu neověřuje volající znovu. používá informace o identitě poskytovaný službou průčelí v předaný požadavek.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="c7d7b-118">Díky tomuto vztahu důvěryhodnosti musí back-end službu ověřit službě průčelí a ujistěte se, že přesměrovaná zpráva pochází z důvěryhodného zdroje – v takovém případě adaptační vrstva služby.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="c7d7b-119">Implementace</span><span class="sxs-lookup"><span data-stu-id="c7d7b-119">Implementation</span></span>  
 <span data-ttu-id="c7d7b-120">Existují dvě cesty komunikace v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="c7d7b-121">Nejprve je mezi klientem a službu průčelí, druhá je mezi službou průčelí a back-end službu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="c7d7b-122">Komunikační trasa mezi klientem a službou průčelí</span><span class="sxs-lookup"><span data-stu-id="c7d7b-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="c7d7b-123">Klient do cesty komunikace služby průčelí používá `wsHttpBinding` s `UserName` typu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="c7d7b-124">To znamená, že klient používá uživatelské jméno a heslo k ověření průčelí služba a služba průčelí certifikát X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="c7d7b-125">Konfigurace vazby vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="c7d7b-126">Službu průčelí ověřuje pomocí vlastního volajícího `UserNamePasswordValidator` implementace.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="c7d7b-127">Pro demonstrační účely ověřování pouze zaručí, že uživatelské jméno volajícího odpovídá prezentované heslo.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="c7d7b-128">V reálné situaci pravděpodobně ověření uživatele pomocí služby Active Directory nebo vlastního poskytovatele členství technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="c7d7b-129">Program pro ověření implementace se nachází v `FacadeService.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7d7b-130">Vlastní validátor je nakonfigurován pro použití v `serviceCredentials` chování v konfiguračním souboru služby adaptační vrstva.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="c7d7b-131">Toto chování se také používá ke konfiguraci certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="c7d7b-132">Komunikační trasa mezi službou průčelí a back-end službou</span><span class="sxs-lookup"><span data-stu-id="c7d7b-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="c7d7b-133">Používá službu průčelí komunikační trasa back-end službu `customBinding` , který se skládá z několika elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="c7d7b-134">Tato vazba provede dvě věci.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-134">This binding accomplishes two things.</span></span> <span data-ttu-id="c7d7b-135">Ověří se průčelí služby a back-end službu, aby zajistila, že komunikace je zabezpečená a pochází z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="c7d7b-136">Kromě toho také přenáší identitu volajícího počáteční uvnitř `Username` token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="c7d7b-137">V takovém případě se přenášejí pouze uživatelské jméno volajícího počáteční do back-end službu, heslo není součástí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="c7d7b-138">Je to proto, že back-end službu vztahy důvěryhodnosti služby průčelí ověřit volající před předáním požadavku k němu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="c7d7b-139">Protože průčelí service ověří ve službě back-endu, back-end službu můžete důvěřovat informace obsažené v předaný požadavek.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="c7d7b-140">Následuje konfigurace vazby pro tuto cestu komunikace.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="c7d7b-141">[ \<Zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) postará element vazby přenosu uživatelského jména a extrakce počáteční volající.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="c7d7b-142">[ \<Zabezpečení windowsstreamsecurity iniciuje >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) postará o ověřování fasádu a back-endové služby a zprávu ochrany.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="c7d7b-143">Tento požadavek předá dál, implementace služby průčelí musíte zadat uživatelské jméno počáteční volající tak tuto infrastrukturu zabezpečení WCF to můžete umístit do přesměrovaná zpráva.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="c7d7b-144">Uživatelské jméno počáteční volající je součástí implementace služby průčelí nastavením v `ClientCredentials` vlastnost na instanci proxy serveru klienta služby průčelí používá ke komunikaci s back-end službu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="c7d7b-145">Následující kód ukazuje, jak `GetCallerIdentity` metoda je implementována ve službě adaptační vrstva.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="c7d7b-146">Jiné metody nepoužívají stejným vzorem.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-146">Other methods use the same pattern.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="c7d7b-147">Jak je znázorněno v předchozím kódu, heslo nenastaví na `ClientCredentials` , pouze uživatelské jméno je nastavena.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="c7d7b-148">Infrastruktura zabezpečení WCF vytvoří token zabezpečení uživatelské jméno bez hesla v tomto případě tedy přesně toho, co vyžaduje v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="c7d7b-149">Ve službě back-endu musí být ověřené informace obsažené v tokenu zabezpečení uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="c7d7b-150">Ve výchozím nastavení zabezpečení WCF pokusí mapovat uživatele na Windows účet pomocí zadaného hesla.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="c7d7b-151">V takovém případě není zadáno žádné heslo a k ověření uživatelského jména, protože již bylo provedeno ověření službou průčelí není vyžadována back-end službu.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="c7d7b-152">Pro implementaci této funkce ve službě WCF, vlastní `UserNamePasswordValidator` je k dispozici, pouze vynutí, že uživatelské jméno je zadán v tokenu a nebude provádět žádné další ověřování.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7d7b-153">Vlastní validátor je nakonfigurován pro použití v `serviceCredentials` chování v konfiguračním souboru služby adaptační vrstva.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c7d7b-154">Extrahovat informace uživatelského jména a informace o účtu služby důvěryhodného průčelí, implementace služby back-endu používá `ServiceSecurityContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="c7d7b-155">Následující kód ukazuje jak `GetCallerIdentity` metoda je implementována.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7d7b-156">Informace o účtu služby průčelí se extrahují pomocí `ServiceSecurityContext.Current.WindowsIdentity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="c7d7b-157">Přístup k informacím o počáteční volající back-end služba používá `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="c7d7b-158">Vyhledá `Identity` deklarace identity s typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="c7d7b-159">Tato deklarace identity není automaticky vygenerován pomocí WCF zabezpečení infrastruktury z informací obsažených v `Username` token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="c7d7b-160">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c7d7b-160">Running the sample</span></span>  
 <span data-ttu-id="c7d7b-161">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c7d7b-162">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="c7d7b-163">Stisknutím klávesy ENTER v oknech konzoly služby fasádu a back-endu pro vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7d7b-164">Dávkový soubor Setup.bat součástí ukázkový scénář důvěryhodné Facade umožňuje nakonfigurovat server se příslušný certifikát ke spuštění služby průčelí, které vyžadují zabezpečení na základě certifikátů ke svému ověření ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="c7d7b-165">Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="c7d7b-166">Následující body nabízí stručný přehled o různých částech dávkové soubory.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="c7d7b-167">Vytváří se certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="c7d7b-168">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="c7d7b-169">`%SERVER_NAME%` Proměnné Určuje název serveru – výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="c7d7b-170">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="c7d7b-171">Instalace služby průčelí certifikátu do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="c7d7b-172">Následující řádek certifikát služby průčelí zkopíruje do úložiště důvěryhodných osob klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="c7d7b-173">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c7d7b-174">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7d7b-175">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c7d7b-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c7d7b-176">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7d7b-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c7d7b-177">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c7d7b-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="c7d7b-178">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="c7d7b-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="c7d7b-179">Ujistěte se, že cesta obsahuje složku, kde je umístěn Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="c7d7b-180">Spusťte Setup.bat z instalační složky s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c7d7b-181">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="c7d7b-182">Spuštění BackendService.exe z adresáře \BackendService\bin v okně samostatné konzoly</span><span class="sxs-lookup"><span data-stu-id="c7d7b-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="c7d7b-183">Spuštění FacadeService.exe z adresáře \FacadeService\bin v okně samostatné konzoly</span><span class="sxs-lookup"><span data-stu-id="c7d7b-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="c7d7b-184">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c7d7b-185">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="c7d7b-186">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c7d7b-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c7d7b-187">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="c7d7b-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="c7d7b-188">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7d7b-189">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7d7b-190">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c7d7b-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c7d7b-191">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7d7b-192">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c7d7b-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="c7d7b-193">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7d7b-193">See also</span></span>
