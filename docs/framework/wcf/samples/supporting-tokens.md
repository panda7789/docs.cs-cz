---
title: Podpora tokenů
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 0214479c40e41da64c1cd2ea59837008ffecdb04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656541"
---
# <a name="supporting-tokens"></a><span data-ttu-id="4ecf5-102">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="4ecf5-102">Supporting Tokens</span></span>
<span data-ttu-id="4ecf5-103">Ukázka podporuje tokeny ukazuje, jak přidat další tokeny na zprávu, která používá WS-Security.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="4ecf5-104">V příkladu přidá token zabezpečení Binární X.509 kromě token zabezpečení uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="4ecf5-105">Token je předán do záhlaví zprávy WS-Security z klienta ke službě a část zprávy jsou podepsány pomocí soukromého klíče přidružené k tokenu zabezpečení X.509 prokázat získáním certifikát X.509 příjemci.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="4ecf5-106">To je užitečné v případě, když je potřeba mít více deklarací identity přidružené k zprávy na ověřování nebo autorizaci odesílatele.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="4ecf5-107">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4ecf5-108">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4ecf5-108">Demonstrates</span></span>
 <span data-ttu-id="4ecf5-109">Ukázce:</span><span class="sxs-lookup"><span data-stu-id="4ecf5-109">The sample demonstrates:</span></span>

-   <span data-ttu-id="4ecf5-110">Jak klienta lze předat další bezpečnostní tokeny služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-110">How a client can pass additional security tokens to a service.</span></span>

-   <span data-ttu-id="4ecf5-111">Jak má server přístup související s tokeny zabezpečení další deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-111">How the server can access claims associated with additional security tokens.</span></span>

-   <span data-ttu-id="4ecf5-112">Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
>  <span data-ttu-id="4ecf5-113">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="4ecf5-114">Klient se ověří pomocí Token uživatelského jména a podpůrné Token zabezpečení X.509</span><span class="sxs-lookup"><span data-stu-id="4ecf5-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="4ecf5-115">Služba poskytuje jeden koncový bod pro komunikaci, která je vytvořena prostřednictvím kódu programu pomocí `BindingHelper` a `EchoServiceHost` třídy.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="4ecf5-116">Koncový bod se skládá z adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4ecf5-117">Je vazba konfigurována s vlastními vazbami pomocí `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="4ecf5-118">Tato ukázka nastaví `SymmetricSecurityBindingElement` chránit symetrický klíč během přenosu a předat pomocí certifikátu X.509 služby `UserNameToken` spolu se podporu `X509SecurityToken` v záhlaví zprávy WS-Security.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="4ecf5-119">Symetrický klíč se používá k šifrování těla zprávy a token zabezpečení uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="4ecf5-120">Podpůrný token je předán jako token další binární zabezpečení v záhlaví zprávy WS-Security.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="4ecf5-121">Pravosti podpůrný token prokázat podepsáním část zprávy s privátním klíčem podpůrné X.509 zabezpečení přidružené k tokenu.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

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

 <span data-ttu-id="4ecf5-122">Chování Určuje přihlašovací údaje služby, které se mají použít pro ověřování klientů a také informace o certifikát služby X.509.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="4ecf5-123">Ukázka používá `CN=localhost` jako název subjektu v certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

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

 <span data-ttu-id="4ecf5-124">Kód služby:</span><span class="sxs-lookup"><span data-stu-id="4ecf5-124">Service code:</span></span>

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

 <span data-ttu-id="4ecf5-125">Podobným způsobem jako do koncového bodu služby je nakonfigurovaný koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="4ecf5-126">Klient používá stejný `BindingHelper` třídy za účelem vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="4ecf5-127">Zbývající část nastavení se nachází v `Client` třídy.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="4ecf5-128">Klient nastaví informace o tokenu zabezpečení jméno uživatele, podpůrný token zabezpečení X.509 a informace o certifikát služby X.509 v kódu instalační program do kolekce chování koncového bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

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

## <a name="displaying-callers-information"></a><span data-ttu-id="4ecf5-129">Zobrazení informací o volajícím.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="4ecf5-130">Chcete-li zobrazit informace volajícího, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="4ecf5-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizaci deklarací identity přidružené k aktuální volajícího.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="4ecf5-132">Tyto deklarace identit se automaticky poskytne Windows Communication Foundation (WCF) pro každý token přijatý ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

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

## <a name="running-the-sample"></a><span data-ttu-id="4ecf5-133">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4ecf5-133">Running the Sample</span></span>
 <span data-ttu-id="4ecf5-134">Při spuštění ukázky, klient nejdřív vás vyzve k zadání uživatelského jména a hesla pro název token uživatele.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="4ecf5-135">Nezapomeňte zadat správné hodnoty pro váš účet systému protože WCF na službu mapuje hodnoty poskytnuté v název tokenu uživatele do identity poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="4ecf5-136">Po tomto klient se zobrazí odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="4ecf5-137">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="4ecf5-138">Instalační dávkový soubor</span><span class="sxs-lookup"><span data-stu-id="4ecf5-138">Setup Batch File</span></span>
 <span data-ttu-id="4ecf5-139">Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace hostované Internetové informační služby (IIS), která vyžaduje zabezpečení na základě certifikátů serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4ecf5-140">Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="4ecf5-141">Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="4ecf5-142">Vytváří se certifikát klienta</span><span class="sxs-lookup"><span data-stu-id="4ecf5-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="4ecf5-143">Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="4ecf5-144">`%CLIENT_NAME%` Proměnná Určuje předmětu certifikátu klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="4ecf5-145">Tato ukázka používá "client.com" jako název subjektu.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="4ecf5-146">Certifikát je uložen v úložišti (osobních) v části `CurrentUser` umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="4ecf5-147">Instalaci klientského certifikátu do důvěryhodného Store na Server</span><span class="sxs-lookup"><span data-stu-id="4ecf5-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="4ecf5-148">Následující řádek v dávkový soubor Setup.bat zkopíruje klientský certifikát do úložiště důvěryhodných osob serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="4ecf5-149">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="4ecf5-150">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="4ecf5-151">Vytváří se certifikát serveru</span><span class="sxs-lookup"><span data-stu-id="4ecf5-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="4ecf5-152">Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4ecf5-153">`%SERVER_NAME%` Proměnné Určuje název serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4ecf5-154">Změňte tuto proměnnou k určení vlastního názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4ecf5-155">V tomto souboru batch výchozí hodnota je localhost.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="4ecf5-156">Certifikát je uložen v úložišti (osobních) v části umístění úložiště LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="4ecf5-157">Certifikát je uložen v úložišti LocalMachine pro služby hostované v IIS.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="4ecf5-158">V místním prostředí služby upravte dávkový soubor pro uložení certifikátu serveru v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="4ecf5-159">Instalace certifikátu serveru do klienta důvěryhodný certifikát Store</span><span class="sxs-lookup"><span data-stu-id="4ecf5-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="4ecf5-160">Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4ecf5-161">Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4ecf5-162">Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="4ecf5-163">Povolení přístupu k privátnímu klíči certifikátu</span><span class="sxs-lookup"><span data-stu-id="4ecf5-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="4ecf5-164">Povolit přístup k privátnímu klíči certifikátu ze služby hostované v IIS, musíte uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělena příslušná oprávnění pro privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="4ecf5-165">Toho lze dosáhnout poslední kroky v skript Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-165">This is accomplished by last steps in the Setup.bat script.</span></span>

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

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ecf5-166">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="4ecf5-166">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="4ecf5-167">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ecf5-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="4ecf5-168">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ecf5-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3.  <span data-ttu-id="4ecf5-169">Ke spuštění ukázky v konfiguraci s jedním nebo více počítačů, použijte následující pokyny.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4ecf5-170">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="4ecf5-170">To run the sample on the same machine</span></span>

1.  <span data-ttu-id="4ecf5-171">Spusťte Setup.bat ve složce instalace ukázkové uvnitř příkazový řádek sady Visual Studio 2012, spusťte s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="4ecf5-172">Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4ecf5-173">Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="4ecf5-174">Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="4ecf5-175">Je potřeba certifikáty odebrat spuštěním Cleanup.bat po dokončení s ukázkou.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="4ecf5-176">Další ukázky zabezpečení použijte stejné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-176">Other security samples use the same certificates.</span></span>  
  
2.  <span data-ttu-id="4ecf5-177">Spusťte Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4ecf5-178">Činnost klienta se zobrazí na klientské aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-178">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="4ecf5-179">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4ecf5-179">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4ecf5-180">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="4ecf5-180">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="4ecf5-181">Vytvoření adresáře v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-181">Create a directory on the service machine.</span></span> <span data-ttu-id="4ecf5-182">Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="4ecf5-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="4ecf5-183">Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="4ecf5-184">Ujistěte se, že zkopírujete soubory v podadresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="4ecf5-185">Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="4ecf5-186">Vytvoření adresáře na klientský počítač určený k binárních souborů klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="4ecf5-187">Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="4ecf5-188">Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="4ecf5-189">Na serveru, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4ecf5-190">Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="4ecf5-191">Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7.  <span data-ttu-id="4ecf5-192">Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="4ecf5-193">Na straně klienta, spouštění `setup.bat client` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4ecf5-194">Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="4ecf5-195">V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="4ecf5-196">Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="4ecf5-197">Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="4ecf5-198">Na straně klienta spouštění ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="4ecf5-199">To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="4ecf5-200">Na serveru, spusťte ImportClientCert.bat to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="4ecf5-201">Na klientském počítači a spusťte Client.exe z okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="4ecf5-202">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="4ecf5-202">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4ecf5-203">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="4ecf5-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="4ecf5-204">Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ecf5-205">Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="4ecf5-206">Pokud jste provedli Ukázky WCF, které certifikáty využívají napříč počítači, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4ecf5-207">Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4ecf5-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ecf5-208">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ecf5-208">See also</span></span>
