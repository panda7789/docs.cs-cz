---
title: Podpora tokenů
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: a8464d7f32b52152b5371ff9edbb396578df6a57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964474"
---
# <a name="supporting-tokens"></a><span data-ttu-id="18540-102">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="18540-102">Supporting Tokens</span></span>
<span data-ttu-id="18540-103">Ukázka pomocných tokenů ukazuje, jak přidat další tokeny do zprávy, která používá WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18540-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="18540-104">V příkladu se kromě tokenu zabezpečení uživatelského jména přidá i binární token zabezpečení X. 509.</span><span class="sxs-lookup"><span data-stu-id="18540-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="18540-105">Token se předává v hlavičce zprávy WS-Security od klienta ke službě a část zprávy je podepsána pomocí privátního klíče přidruženého k tokenu zabezpečení X. 509, aby bylo možné prokázat vlastnictví certifikátu X. 509 pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="18540-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="18540-106">To je užitečné v případě, kdy je potřeba mít k ověření nebo autorizaci odesílatele více deklarací přidružených ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="18540-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="18540-107">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="18540-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="18540-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="18540-108">Demonstrates</span></span>
 <span data-ttu-id="18540-109">Ukázka ukazuje:</span><span class="sxs-lookup"><span data-stu-id="18540-109">The sample demonstrates:</span></span>

- <span data-ttu-id="18540-110">Jak může klient předat službě další tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="18540-110">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="18540-111">Způsob, jakým může server přistupovat k deklaracím přidruženým k dalším tokenům zabezpečení</span><span class="sxs-lookup"><span data-stu-id="18540-111">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="18540-112">Způsob, jakým se používá certifikát X. 509 serveru k ochraně symetrického klíče použitého pro šifrování a podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="18540-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="18540-113">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="18540-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="18540-114">Klient se ověřuje pomocí tokenu uživatelského jména a podporuje token zabezpečení X. 509.</span><span class="sxs-lookup"><span data-stu-id="18540-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="18540-115">Služba zpřístupňuje jeden koncový bod pro komunikaci, která je programově vytvořena pomocí `BindingHelper` tříd `EchoServiceHost` a.</span><span class="sxs-lookup"><span data-stu-id="18540-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="18540-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="18540-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="18540-117">Vazba je nakonfigurována s vlastní vazbou pomocí `SymmetricSecurityBindingElement` a. `HttpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="18540-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="18540-118">Tato ukázka nastaví `SymmetricSecurityBindingElement` použití certifikátu Service X. 509 k ochraně symetrického klíče během přenosu a k `UserNameToken` předání a spolu s podporou `X509SecurityToken` v hlavičce zprávy WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18540-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="18540-119">Symetrický klíč se používá k šifrování textu zprávy a tokenu zabezpečení uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="18540-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="18540-120">Token podpory se předává jako další binární token zabezpečení v hlavičce zprávy WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18540-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="18540-121">Pravost podpůrného tokenu je prokázána tím, že podepisuje část zprávy s privátním klíčem přidruženým k podpůrnému tokenu zabezpečení X. 509.</span><span class="sxs-lookup"><span data-stu-id="18540-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

```csharp
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

 <span data-ttu-id="18540-122">Chování Určuje pověření služby, které se má použít pro ověřování klientů a také informace o certifikátu služby X. 509.</span><span class="sxs-lookup"><span data-stu-id="18540-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="18540-123">Ukázka používá `CN=localhost` jako název subjektu v certifikátu služby X. 509.</span><span class="sxs-lookup"><span data-stu-id="18540-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

```csharp
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

 <span data-ttu-id="18540-124">Kód služby:</span><span class="sxs-lookup"><span data-stu-id="18540-124">Service code:</span></span>

```csharp
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
            return $"Hello {userName}, {certificateSubjectName}";
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
                // Try to find an X500DistinguishedName claim. This will
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

 <span data-ttu-id="18540-125">Koncový bod klienta je nakonfigurován podobným způsobem jako koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="18540-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="18540-126">Klient používá stejnou `BindingHelper` třídu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="18540-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="18540-127">Zbývající část instalace je umístěna ve `Client` třídě.</span><span class="sxs-lookup"><span data-stu-id="18540-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="18540-128">Klient nastaví informace o tokenu zabezpečení uživatelského jména, podpoře tokenu zabezpečení X. 509 a informace o certifikátu X. 509 v instalačním kódu pro kolekci chování koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="18540-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

```csharp
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

## <a name="displaying-callers-information"></a><span data-ttu-id="18540-129">Zobrazení informací o volajícím</span><span class="sxs-lookup"><span data-stu-id="18540-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="18540-130">Chcete-li zobrazit informace o volajícím, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="18540-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="18540-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizační deklarace přidružené k aktuálnímu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="18540-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="18540-132">Tyto deklarace jsou dodány automaticky pomocí Windows Communication Foundation (WCF) pro každý token přijatý ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="18540-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

```csharp
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
            //Try to find an X500DistinguishedName claim.
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

## <a name="running-the-sample"></a><span data-ttu-id="18540-133">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="18540-133">Running the Sample</span></span>
 <span data-ttu-id="18540-134">Při spuštění ukázky se klient poprvé vyzve k zadání uživatelského jména a hesla pro token uživatelského jména.</span><span class="sxs-lookup"><span data-stu-id="18540-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="18540-135">Nezapomeňte zadat správné hodnoty pro systémový účet, protože služba WCF ve službě mapuje hodnoty zadané v tokenu uživatelského jména do identity poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="18540-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="18540-136">Potom klient zobrazí odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="18540-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="18540-137">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="18540-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="18540-138">Nastavení dávkového souboru</span><span class="sxs-lookup"><span data-stu-id="18540-138">Setup Batch File</span></span>
 <span data-ttu-id="18540-139">Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantními certifikáty pro spuštění aplikace hostované v Internetová informační služba (IIS), která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="18540-140">Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.</span><span class="sxs-lookup"><span data-stu-id="18540-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="18540-141">Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="18540-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="18540-142">Vytváření klientského certifikátu</span><span class="sxs-lookup"><span data-stu-id="18540-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="18540-143">Následující řádky z dávkového souboru Setup. bat vytvoří klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="18540-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="18540-144">`%CLIENT_NAME%` Proměnná Určuje předmět klientského certifikátu.</span><span class="sxs-lookup"><span data-stu-id="18540-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="18540-145">V této ukázce se jako název předmětu používá "client.com".</span><span class="sxs-lookup"><span data-stu-id="18540-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="18540-146">Certifikát je uložený v osobním úložišti (osobní) v `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="18540-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="18540-147">Instalace klientského certifikátu do důvěryhodného úložiště serveru</span><span class="sxs-lookup"><span data-stu-id="18540-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="18540-148">Následující řádek v dávkovém souboru Setup. bat kopíruje klientský certifikát do úložiště důvěryhodných osob serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="18540-149">Tento krok je povinný, protože pro systém serveru nejsou implicitně důvěryhodné certifikáty vygenerované pomocí nástroje MakeCert. exe.</span><span class="sxs-lookup"><span data-stu-id="18540-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="18540-150">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="18540-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="18540-151">Vytvoření certifikátu serveru</span><span class="sxs-lookup"><span data-stu-id="18540-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="18540-152">Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="18540-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="18540-153">`%SERVER_NAME%` Proměnná Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="18540-154">Změňte tuto proměnnou tak, aby určovala vlastní název serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="18540-155">Výchozí hodnota v tomto dávkovém souboru je localhost.</span><span class="sxs-lookup"><span data-stu-id="18540-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="18540-156">Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="18540-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="18540-157">Certifikát je uložený v úložišti LocalMachine pro služby hostované službou IIS.</span><span class="sxs-lookup"><span data-stu-id="18540-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="18540-158">Pro samoobslužné služby byste měli soubor Batch upravit tak, aby ukládal certifikát serveru do umístění úložiště CurrentUser, a to tak, že nahradíte řetězec LocalMachine řetězcem CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="18540-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="18540-159">Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta</span><span class="sxs-lookup"><span data-stu-id="18540-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="18540-160">Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta.</span><span class="sxs-lookup"><span data-stu-id="18540-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="18540-161">Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem.</span><span class="sxs-lookup"><span data-stu-id="18540-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="18540-162">Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="18540-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="18540-163">Povoluje se přístup k privátnímu klíči certifikátu.</span><span class="sxs-lookup"><span data-stu-id="18540-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="18540-164">Aby bylo možné povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěný proces hostovaný službou IIS, udělena příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="18540-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="18540-165">To se provádí v posledních krocích skriptu Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="18540-165">This is accomplished by last steps in the Setup.bat script.</span></span>

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

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18540-166">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="18540-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="18540-167">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18540-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="18540-168">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18540-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="18540-169">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="18540-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="18540-170">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="18540-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="18540-171">Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 spustit s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="18540-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="18540-172">Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="18540-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="18540-173">Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="18540-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="18540-174">Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="18540-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="18540-175">Nezapomeňte odebrat certifikáty spuštěním souboru Cleanup. bat po dokončení ukázky.</span><span class="sxs-lookup"><span data-stu-id="18540-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="18540-176">Další ukázky zabezpečení používají stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="18540-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="18540-177">Spustit soubor Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="18540-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="18540-178">Aktivita klienta se zobrazí v klientské aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="18540-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="18540-179">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="18540-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="18540-180">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="18540-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="18540-181">Vytvořte adresář na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="18540-181">Create a directory on the service machine.</span></span> <span data-ttu-id="18540-182">Pomocí nástroje pro správu služby Internetová informační služba (IIS) vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář.</span><span class="sxs-lookup"><span data-stu-id="18540-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="18540-183">Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="18540-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="18540-184">Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="18540-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="18540-185">Zkopírujte také soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.</span><span class="sxs-lookup"><span data-stu-id="18540-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="18540-186">Vytvořte v klientském počítači adresář pro binární soubory klienta.</span><span class="sxs-lookup"><span data-stu-id="18540-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="18540-187">Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="18540-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="18540-188">Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="18540-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="18540-189">Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="18540-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="18540-190">Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.</span><span class="sxs-lookup"><span data-stu-id="18540-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="18540-191">Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="18540-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="18540-192">Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="18540-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="18540-193">Na straně klienta spusťte `setup.bat client` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="18540-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="18540-194">Při `setup.bat` spuštění`client` s argumentem se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.</span><span class="sxs-lookup"><span data-stu-id="18540-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="18540-195">V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="18540-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="18540-196">Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="18540-197">Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="18540-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="18540-198">Na straně klienta spusťte ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="18540-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="18540-199">Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="18540-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="18540-200">Na serveru spusťte ImportClientCert. bat. tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="18540-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="18540-201">Na klientském počítači spusťte soubor Client. exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="18540-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="18540-202">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="18540-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="18540-203">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="18540-203">To clean up after the sample</span></span>  
  
- <span data-ttu-id="18540-204">Po dokončení ukázky spusťte na složce Samples Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="18540-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18540-205">Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi.</span><span class="sxs-lookup"><span data-stu-id="18540-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="18540-206">Pokud jste spustili ukázky WCF, které používají certifikáty napříč počítači, ujistěte se, že jste vymazali certifikáty služby nainstalované v úložišti CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="18540-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="18540-207">K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="18540-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
