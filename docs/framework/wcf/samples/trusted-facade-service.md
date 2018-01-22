---
title: "Důvěryhodná služba facade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c0d1d0473a821510ee70e386058a2b3249221dd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="trusted-facade-service"></a><span data-ttu-id="c68f9-102">Důvěryhodná služba facade</span><span class="sxs-lookup"><span data-stu-id="c68f9-102">Trusted Facade Service</span></span>
<span data-ttu-id="c68f9-103">Tento ukázkový scénář ukazuje, jak přenést informace identitu volajícího jedna služba jiné pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Infrastruktura zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c68f9-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security infrastructure.</span></span>  
  
 <span data-ttu-id="c68f9-104">Je běžné vzoru návrhu ke zveřejnění funkce poskytované službou k veřejné síti pomocí průčelí za služby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="c68f9-105">Služba průčelí za většinou nachází v hraniční síti (označované také jako DMZ, demilitarizovaná zóna a monitorovaná podsíť) a komunikuje se službou back-end, který implementuje obchodní logiky a má přístup k interní data.</span><span class="sxs-lookup"><span data-stu-id="c68f9-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="c68f9-106">Komunikační kanál mezi průčelí za služby a služby back-end přejde přes bránu firewall a je obvykle omezené pro pouze jedinému účelu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="c68f9-107">Tato ukázka se skládá z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="c68f9-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="c68f9-108">Kalkulačky klienta</span><span class="sxs-lookup"><span data-stu-id="c68f9-108">Calculator client</span></span>  
  
-   <span data-ttu-id="c68f9-109">Kalkulačky průčelí za služby</span><span class="sxs-lookup"><span data-stu-id="c68f9-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="c68f9-110">Back-end službu kalkulačky</span><span class="sxs-lookup"><span data-stu-id="c68f9-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="c68f9-111">Službu průčelí za zodpovídá za ověření žádosti a ověřování volající.</span><span class="sxs-lookup"><span data-stu-id="c68f9-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="c68f9-112">Po úspěšném ověření a ověření se předá požadavek back-end službu pomocí řízené komunikační kanál z hraniční sítě k interní síti.</span><span class="sxs-lookup"><span data-stu-id="c68f9-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="c68f9-113">Jako součást předaný požadavek službu průčelí za obsahuje informace o identitu volajícího, aby službě back-end tyto informace můžete použít v jeho zpracování.</span><span class="sxs-lookup"><span data-stu-id="c68f9-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="c68f9-114">Identitu volajícího se přenášejí pomocí `Username` token zabezpečení uvnitř zprávu `Security` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c68f9-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="c68f9-115">Ukázce se používá [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpečení k přenosu a získání informací z `Security` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c68f9-115">The sample uses the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c68f9-116">Back-end službu důvěřuje průčelí za službu, kterou chcete ověřit volající.</span><span class="sxs-lookup"><span data-stu-id="c68f9-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="c68f9-117">Z toho důvodu back-end službu neověřuje volající znovu; používá informace o identitě poskytovaný službou průčelí za v přesměrovaná žádosti.</span><span class="sxs-lookup"><span data-stu-id="c68f9-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="c68f9-118">Díky tomuto vztahu důvěryhodnosti musí ověřit službě back-end službu průčelí za tak, aby zajistila, že přesměrovaná zpráva pochází z důvěryhodného zdroje – v takovém případě průčelí za službu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="c68f9-119">Implementace</span><span class="sxs-lookup"><span data-stu-id="c68f9-119">Implementation</span></span>  
 <span data-ttu-id="c68f9-120">Existují dva komunikační cesty v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c68f9-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="c68f9-121">Nejprve je mezi klientem a službu průčelí za sekundu je mezi průčelí za služby a služby back-end.</span><span class="sxs-lookup"><span data-stu-id="c68f9-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="c68f9-122">Komunikační trasa mezi klientem a službou průčelí za</span><span class="sxs-lookup"><span data-stu-id="c68f9-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="c68f9-123">Klient k cestě komunikace služby průčelí za používá `wsHttpBinding` s `UserName` typu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="c68f9-124">To znamená, že klient použije uživatelské jméno a heslo k ověření průčelí za služby a služby průčelí za používá certifikát X.509 k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="c68f9-125">Konfigurace vazeb vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-126">Službu průčelí za ověří volajícího pomocí vlastní `UserNamePasswordValidator` implementace.</span><span class="sxs-lookup"><span data-stu-id="c68f9-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="c68f9-127">Pro demonstrační účely ověřování jenom zaručí, že uživatelské jméno volajícího odpovídá vidění heslo.</span><span class="sxs-lookup"><span data-stu-id="c68f9-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="c68f9-128">V případě skutečných pravděpodobně ověření uživatele pomocí služby Active Directory nebo vlastního zprostředkovatele členství technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c68f9-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="c68f9-129">Implementace validátoru se nachází v `FacadeService.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="c68f9-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-130">Vlastní validátor je nakonfigurována pro používání uvnitř `serviceCredentials` chování v konfiguračním souboru průčelí za služby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="c68f9-131">Toto chování je také použít ke konfiguraci služby certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="c68f9-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="c68f9-132">Komunikační trasa mezi službou průčelí za a back-end službu</span><span class="sxs-lookup"><span data-stu-id="c68f9-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="c68f9-133">Používá službu průčelí za cestu komunikace služby back-end `customBinding` který se skládá z několika součástí vazby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="c68f9-134">Tato vazba má dvě věci.</span><span class="sxs-lookup"><span data-stu-id="c68f9-134">This binding accomplishes two things.</span></span> <span data-ttu-id="c68f9-135">Ověřuje průčelí za služby a back-end službu zajistěte, aby komunikace zabezpečená a pochází z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="c68f9-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="c68f9-136">Kromě toho také přenášení počáteční volajícího identity uvnitř `Username` tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c68f9-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="c68f9-137">V tomto případě se přenáší pouze uživatelské jméno počáteční volajícího na službě back-end, heslo není součástí zprávy.</span><span class="sxs-lookup"><span data-stu-id="c68f9-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="c68f9-138">Je to proto, že back-end službu důvěřuje průčelí za službu, kterou chcete ověřit volající před předáním požadavku na ni.</span><span class="sxs-lookup"><span data-stu-id="c68f9-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="c68f9-139">Protože průčelí za služby se ověří na službě back-end, můžete informace obsažené v předaný požadavek důvěřovat back-end službu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="c68f9-140">Zde je konfigurace vazeb pro tuto cestu komunikace.</span><span class="sxs-lookup"><span data-stu-id="c68f9-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-141">[ \<Zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku vazby má na starosti přenosu uživatelského jména a extrakce počáteční volajícího.</span><span class="sxs-lookup"><span data-stu-id="c68f9-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="c68f9-142">[ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) a [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) postará o ověřování průčelí za a back-end služby a zpráv ochrany.</span><span class="sxs-lookup"><span data-stu-id="c68f9-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="c68f9-143">Předání žádosti, musí implementace služby průčelí za zadat uživatelské jméno počáteční volajícího, aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Tato infrastruktura zabezpečení můžete umístit do přesměrovaná zpráva.</span><span class="sxs-lookup"><span data-stu-id="c68f9-143">To forward the request, the façade service implementation must provide the initial caller's username so that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="c68f9-144">Počáteční volajícího uživatelské jméno je součástí implementace služby průčelí za nastavením v `ClientCredentials` vlastnost na instanci proxy serveru klienta služby průčelí za používá ke komunikaci s back-end službu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="c68f9-145">Následující kód ukazuje, jak `GetCallerIdentity` metoda se implementuje na průčelí za službu.</span><span class="sxs-lookup"><span data-stu-id="c68f9-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="c68f9-146">Ostatní metody pomocí stejného vzoru.</span><span class="sxs-lookup"><span data-stu-id="c68f9-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-147">Jak ukazuje předchozí kód, heslo není nastaven na `ClientCredentials` , pouze uživatelské jméno je nastavena.</span><span class="sxs-lookup"><span data-stu-id="c68f9-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c68f9-148">Infrastruktura zabezpečení vytvoří token zabezpečení uživatelské jméno bez zadání hesla v tomto případě tedy přesně co je nutné v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="c68f9-148"> security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="c68f9-149">Na službě back-end musí být ověřeny informací obsažených v tokenu zabezpečení, uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="c68f9-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="c68f9-150">Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení se pokouší mapovat uživatele na účet systému Windows pomocí zadaného hesla.</span><span class="sxs-lookup"><span data-stu-id="c68f9-150">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="c68f9-151">V takovém případě není zadané heslo a back-end službu není nutné k ověření uživatelského jména, protože již bylo provedeno ověření službou průčelí za.</span><span class="sxs-lookup"><span data-stu-id="c68f9-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="c68f9-152">K implementaci tuto funkci v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vlastní `UserNamePasswordValidator` je k dispozici, pouze vynucuje, uživatelské jméno je zadána v tokenu a nebude provádět žádné další ověřování.</span><span class="sxs-lookup"><span data-stu-id="c68f9-152">To implement this functionality in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-153">Vlastní validátor je nakonfigurována pro používání uvnitř `serviceCredentials` chování v konfiguračním souboru průčelí za služby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-154">Extrahovat informace uživatelského jména a informace o účtu služby průčelí za důvěryhodné, používá implementace služby back-end `ServiceSecurityContext` třídy.</span><span class="sxs-lookup"><span data-stu-id="c68f9-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="c68f9-155">Následující kód ukazuje jak `GetCallerIdentity` metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="c68f9-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-156">Informace o účtu služby průčelí za je extrahována pomocí `ServiceSecurityContext.Current.WindowsIdentity` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c68f9-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="c68f9-157">Pro přístup k informacím o počáteční volající používá služba back-end `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c68f9-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="c68f9-158">Hledá `Identity` deklarace identity s typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="c68f9-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="c68f9-159">Tento požadavek je automaticky generován [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpečení z informací obsažených v `Username` tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c68f9-159">This claim is automatically generated by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="c68f9-160">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c68f9-160">Running the sample</span></span>  
 <span data-ttu-id="c68f9-161">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c68f9-162">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="c68f9-163">Můžete stisknutím klávesy ENTER v oknech konzoly služby průčelí za a back-end vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="c68f9-164">Dávkový soubor Setup.bat součástí ukázkový scénář důvěryhodné Facade umožňuje nakonfigurovat server se příslušný certifikát ke spuštění průčelí za služby, která vyžaduje zabezpečení na základě certifikátu k vlastnímu ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="c68f9-165">Přečtěte si postup instalace na konci tohoto tématu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c68f9-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="c68f9-166">Následující poskytuje stručný přehled různých oddílů dávkové soubory.</span><span class="sxs-lookup"><span data-stu-id="c68f9-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="c68f9-167">Vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="c68f9-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="c68f9-168">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c68f9-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="c68f9-169">`%SERVER_NAME%` Proměnná Určuje název serveru – výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="c68f9-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="c68f9-170">Certifikát je uložen v úložišti LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c68f9-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="c68f9-171">Instalace služby průčelí za certifikátu do úložiště důvěryhodných certifikátů klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="c68f9-172">Následující řádek zkopíruje do úložiště důvěryhodných osob na klientský certifikát průčelí za služby.</span><span class="sxs-lookup"><span data-stu-id="c68f9-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="c68f9-173">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="c68f9-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c68f9-174">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c68f9-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c68f9-175">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="c68f9-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c68f9-176">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c68f9-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c68f9-177">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c68f9-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="c68f9-178">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="c68f9-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="c68f9-179">Ujistěte se, že cesta obsahuje složku, kde je umístěna Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="c68f9-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="c68f9-180">Spuštění Setup.bat od vzorku instalační složku.</span><span class="sxs-lookup"><span data-stu-id="c68f9-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c68f9-181">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="c68f9-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="c68f9-182">Spusťte BackendService.exe z adresáře \BackendService\bin v okně samostatné konzoly</span><span class="sxs-lookup"><span data-stu-id="c68f9-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="c68f9-183">Spusťte FacadeService.exe z adresáře \FacadeService\bin v okně samostatné konzoly</span><span class="sxs-lookup"><span data-stu-id="c68f9-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="c68f9-184">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="c68f9-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c68f9-185">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="c68f9-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="c68f9-186">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="c68f9-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c68f9-187">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="c68f9-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="c68f9-188">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="c68f9-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c68f9-189">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="c68f9-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c68f9-190">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c68f9-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c68f9-191">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c68f9-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c68f9-192">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c68f9-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="c68f9-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="c68f9-193">See Also</span></span>
