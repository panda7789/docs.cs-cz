---
title: "Podpora tokenů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab728751a01d16c6b3d2d14de4dd09c2d2b0a17a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="supporting-tokens"></a><span data-ttu-id="4bdd9-102">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="4bdd9-102">Supporting Tokens</span></span>
<span data-ttu-id="4bdd9-103">Podpora tokenů ukázka ukazuje, jak přidat další tokeny pro zprávu, která používá WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="4bdd9-104">V příkladu přidá token zabezpečení Binární X.509 kromě token zabezpečení uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="4bdd9-105">Token je předán v hlavičce protokolu WS-zabezpečení zprávy z klienta ke službě a součástí zprávy je podepsaný s privátním klíčem přidružené k tokenu zabezpečení X.509 prokázat u sebe certifikátu X.509 k příjemce.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="4bdd9-106">To je užitečné v případě, pokud je potřeba mít více deklarací identity přidružené k ověřování nebo autorizaci odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="4bdd9-107">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4bdd9-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4bdd9-108">Demonstrates</span></span>  
 <span data-ttu-id="4bdd9-109">Ukázka ukazuje:</span><span class="sxs-lookup"><span data-stu-id="4bdd9-109">The sample demonstrates:</span></span>  
  
-   <span data-ttu-id="4bdd9-110">Jak klient předat tokeny zabezpečení další služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-110">How a client can pass additional security tokens to a service.</span></span>  
  
-   <span data-ttu-id="4bdd9-111">Jak bude server přístup související s tokeny zabezpečení další deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-111">How the server can access claims associated with additional security tokens.</span></span>  
  
-   <span data-ttu-id="4bdd9-112">Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdd9-113">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="4bdd9-114">Klient se ověří pomocí tokenu uživatelské jméno a podpůrné Token zabezpečení X.509</span><span class="sxs-lookup"><span data-stu-id="4bdd9-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>  
 <span data-ttu-id="4bdd9-115">Službu zpřístupní jeden koncový bod pro komunikaci, která je vytvořena programově pomocí `BindingHelper` a `EchoServiceHost` třídy.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="4bdd9-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4bdd9-117">Vazba je nakonfigurována pomocí vlastních vazeb `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="4bdd9-118">Nastaví Tato ukázka `SymmetricSecurityBindingElement` používat certifikát X.509 služby chránit symetrický klíč během přenosu a předávat `UserNameToken` společně s v podporu `X509SecurityToken` v záhlaví zprávy WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="4bdd9-119">Symetrický klíč se používá k šifrování tělo zprávy a token zabezpečení uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="4bdd9-120">Token podpory se předá jako token další binární zabezpečení v záhlaví zprávy WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="4bdd9-121">Pravost token podpory prokázat podepsáním část zprávy s privátním klíčem přidružené podpůrné zabezpečení X.509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
```  
  
 <span data-ttu-id="4bdd9-122">Určuje chování služby přihlašovací údaje, které mají být použita pro ověřování klientů a také informace o certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="4bdd9-123">Příklad používá `CN=localhost` jako název subjektu v certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 <span data-ttu-id="4bdd9-124">Kódu služby:</span><span class="sxs-lookup"><span data-stu-id="4bdd9-124">Service code:</span></span>  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 <span data-ttu-id="4bdd9-125">Koncový bod klient je nakonfigurován podobným způsobem ke koncovému bodu služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="4bdd9-126">Klient používá stejnou `BindingHelper` třída pro vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="4bdd9-127">Zbývající část nastavení se nachází v `Client` třídy.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="4bdd9-128">Klient nastaví informace o tokenu zabezpečení jméno uživatele, token zabezpečení podpory X.509 a informace o certifikátu X.509 služby v kódu instalační program do kolekce chování klienta koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## <a name="displaying-callers-information"></a><span data-ttu-id="4bdd9-129">Zobrazení informací o volající.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-129">Displaying Callers' Information</span></span>  
 <span data-ttu-id="4bdd9-130">Chcete-li zobrazit informace volajícího, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="4bdd9-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje spojené s volajícím aktuální deklarací autorizace.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="4bdd9-132">Tyto deklarace identity jsou automaticky zadány [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro každý token obdržel ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-132">Those claims are supplied automatically by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] for every token received in the message.</span></span>  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="4bdd9-133">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4bdd9-133">Running the Sample</span></span>  
 <span data-ttu-id="4bdd9-134">Při spuštění vzorového klienta nejprve vyzve k zadání uživatelského jména a hesla pro název token uživatele.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="4bdd9-135">Nezapomeňte poskytnout správné hodnoty pro váš účet system, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve službě mapuje hodnoty zadané v název tokenu uživatele do identity poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-135">Be sure to provide correct values for your system account, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="4bdd9-136">Klient se potom zobrazí odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="4bdd9-137">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-137">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="4bdd9-138">Instalační program dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="4bdd9-138">Setup Batch File</span></span>  
 <span data-ttu-id="4bdd9-139">Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění aplikace hostované Internetové informační služby (IIS), která vyžaduje zabezpečení na základě certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4bdd9-140">Tento dávkový soubor je nutné upravit v počítačích nebo pracovat v případě bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="4bdd9-141">Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
### <a name="creating-the-client-certificate"></a><span data-ttu-id="4bdd9-142">Vytvoření certifikátu klienta</span><span class="sxs-lookup"><span data-stu-id="4bdd9-142">Creating the Client Certificate</span></span>  
 <span data-ttu-id="4bdd9-143">Následující řádky z dávkového souboru Setup.bat vytvořit klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="4bdd9-144">`%CLIENT_NAME%` Proměnná Určuje předmětu certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="4bdd9-145">Tato ukázka používá "client.com" jako název předmětu.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-145">This sample uses "client.com" as the subject name.</span></span>  
  
 <span data-ttu-id="4bdd9-146">Certifikát je uložen v tomto úložišti (osobních) v části `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="4bdd9-147">Instalace klientského certifikátu do důvěryhodného úložiště serveru</span><span class="sxs-lookup"><span data-stu-id="4bdd9-147">Installing the Client Certificate into the Server's Trusted Store</span></span>  
 <span data-ttu-id="4bdd9-148">Následující řádek v dávkovém souboru, Setup.bat zkopíruje klientského certifikátu do úložiště důvěryhodných osob serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="4bdd9-149">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="4bdd9-150">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a><span data-ttu-id="4bdd9-151">Vytvoření certifikátu serveru</span><span class="sxs-lookup"><span data-stu-id="4bdd9-151">Creating the Server Certificate</span></span>  
 <span data-ttu-id="4bdd9-152">Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4bdd9-153">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4bdd9-154">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4bdd9-155">V tento dávkový soubor výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-155">The default in this batch file is localhost.</span></span>  
  
 <span data-ttu-id="4bdd9-156">Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="4bdd9-157">Certifikát je uložen v úložišti LocalMachine pro služby hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="4bdd9-158">Pro samoobslužné hostované služby upravte dávkový soubor pro uložení certifikátu serveru v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="4bdd9-159">Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta</span><span class="sxs-lookup"><span data-stu-id="4bdd9-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>  
 <span data-ttu-id="4bdd9-160">Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4bdd9-161">Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4bdd9-162">Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="4bdd9-163">Povolení přístupu k privátnímu klíči certifikátu</span><span class="sxs-lookup"><span data-stu-id="4bdd9-163">Enabling Access to the Certificate's Private Key</span></span>  
 <span data-ttu-id="4bdd9-164">Povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělen příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="4bdd9-165">To lze provést poslední kroky ve skriptu Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-165">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
```  
echo ************  
echo setting privileges on server certificates  
echo ************  
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
iisreset  
```  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4bdd9-166">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4bdd9-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4bdd9-167">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4bdd9-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4bdd9-168">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4bdd9-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4bdd9-169">Spustit ukázku v konfiguraci s jedním nebo mezi počítače, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4bdd9-170">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="4bdd9-170">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="4bdd9-171">Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku spuštěného s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-171">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="4bdd9-172">Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-172">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4bdd9-173">Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-173">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="4bdd9-174">Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-174">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="4bdd9-175">Je nutné certifikáty odebrat spuštěním Cleanup.bat po dokončení se vzorkem.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="4bdd9-176">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-176">Other security samples use the same certificates.</span></span>  
  
2.  <span data-ttu-id="4bdd9-177">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4bdd9-178">Činnost klienta se zobrazí na klientskou aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-178">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="4bdd9-179">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4bdd9-179">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4bdd9-180">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="4bdd9-180">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="4bdd9-181">Vytvoření adresáře na počítač služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-181">Create a directory on the service machine.</span></span> <span data-ttu-id="4bdd9-182">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="4bdd9-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="4bdd9-183">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="4bdd9-184">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="4bdd9-185">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="4bdd9-186">Vytvoření adresáře v klientském počítači pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="4bdd9-187">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="4bdd9-188">Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="4bdd9-189">Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-189">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="4bdd9-190">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="4bdd9-191">Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7.  <span data-ttu-id="4bdd9-192">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="4bdd9-193">Na klientovi, spusťte `setup.bat client` ve z příkazového řádku Visual Studia otevřen s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-193">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="4bdd9-194">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="4bdd9-195">V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="4bdd9-196">To nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="4bdd9-197">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="4bdd9-198">Na klientovi spusťte ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="4bdd9-199">Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="4bdd9-200">Na serveru, spusťte ImportClientCert.bat to naimportuje certifikát klienta ze souboru Client.cer do LocalMachine - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="4bdd9-201">V klientském počítači spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="4bdd9-202">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4bdd9-202">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4bdd9-203">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="4bdd9-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="4bdd9-204">Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdd9-205">Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="4bdd9-206">Pokud jste spustili [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vzorků, které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-206">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4bdd9-207">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4bdd9-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdd9-208">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bdd9-208">See Also</span></span>
