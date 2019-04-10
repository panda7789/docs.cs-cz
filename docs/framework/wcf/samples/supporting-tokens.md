---
title: Podpora tokenů
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 5f2b1500f54f8ade3c4924e3eb22cd022c6800c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334182"
---
# <a name="supporting-tokens"></a>Podpora tokenů
Ukázka podporuje tokeny ukazuje, jak přidat další tokeny na zprávu, která používá WS-Security. V příkladu přidá token zabezpečení Binární X.509 kromě token zabezpečení uživatelské jméno. Token je předán do záhlaví zprávy WS-Security z klienta ke službě a část zprávy jsou podepsány pomocí soukromého klíče přidružené k tokenu zabezpečení X.509 prokázat získáním certifikát X.509 příjemci. To je užitečné v případě, když je potřeba mít více deklarací identity přidružené k zprávy na ověřování nebo autorizaci odesílatele. Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.

## <a name="demonstrates"></a>Demonstruje
 Ukázce:

-   Jak klienta lze předat další bezpečnostní tokeny služby.

-   Jak má server přístup související s tokeny zabezpečení další deklarace identity.

-   Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.

> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient se ověří pomocí Token uživatelského jména a podpůrné Token zabezpečení X.509
 Služba poskytuje jeden koncový bod pro komunikaci, která je vytvořena prostřednictvím kódu programu pomocí `BindingHelper` a `EchoServiceHost` třídy. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována s vlastními vazbami pomocí `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`. Tato ukázka nastaví `SymmetricSecurityBindingElement` chránit symetrický klíč během přenosu a předat pomocí certifikátu X.509 služby `UserNameToken` spolu se podporu `X509SecurityToken` v záhlaví zprávy WS-Security. Symetrický klíč se používá k šifrování těla zprávy a token zabezpečení uživatelské jméno. Podpůrný token je předán jako token další binární zabezpečení v záhlaví zprávy WS-Security. Pravosti podpůrný token prokázat podepsáním část zprávy s privátním klíčem podpůrné X.509 zabezpečení přidružené k tokenu.

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

 Chování Určuje přihlašovací údaje služby, které se mají použít pro ověřování klientů a také informace o certifikát služby X.509. Ukázka používá `CN=localhost` jako název subjektu v certifikátu X.509 služby.

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

 Kód služby:

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

 Podobným způsobem jako do koncového bodu služby je nakonfigurovaný koncový bod klienta. Klient používá stejný `BindingHelper` třídy za účelem vytvoření vazby. Zbývající část nastavení se nachází v `Client` třídy. Klient nastaví informace o tokenu zabezpečení jméno uživatele, podpůrný token zabezpečení X.509 a informace o certifikát služby X.509 v kódu instalační program do kolekce chování koncového bodu klienta.

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

## <a name="displaying-callers-information"></a>Zobrazení informací o volajícím.
 Chcete-li zobrazit informace volajícího, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje autorizaci deklarací identity přidružené k aktuální volajícího. Tyto deklarace identit se automaticky poskytne Windows Communication Foundation (WCF) pro každý token přijatý ve zprávě.

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

## <a name="running-the-sample"></a>Spuštění ukázky
 Při spuštění ukázky, klient nejdřív vás vyzve k zadání uživatelského jména a hesla pro název token uživatele. Nezapomeňte zadat správné hodnoty pro váš účet systému protože WCF na službu mapuje hodnoty poskytnuté v název tokenu uživatele do identity poskytované systémem. Po tomto klient se zobrazí odpověď ze služby. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

## <a name="setup-batch-file"></a>Instalační dávkový soubor
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace hostované Internetové informační služby (IIS), která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.

 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v odpovídající konfiguraci.

### <a name="creating-the-client-certificate"></a>Vytváří se certifikát klienta
 Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít. `%CLIENT_NAME%` Proměnná Určuje předmětu certifikátu klienta. Tato ukázka používá "client.com" jako název subjektu.

 Certifikát je uložen v úložišti (osobních) v části `CurrentUser` umístění úložiště.

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalaci klientského certifikátu do důvěryhodného Store na Server
 Následující řádek v dávkový soubor Setup.bat zkopíruje klientský certifikát do úložiště důvěryhodných osob serveru. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému serveru. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Vytváří se certifikát serveru
 Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. `%SERVER_NAME%` Proměnné Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tomto souboru batch výchozí hodnota je localhost.

 Certifikát je uložen v úložišti (osobních) v části umístění úložiště LocalMachine. Certifikát je uložen v úložišti LocalMachine pro služby hostované v IIS. V místním prostředí služby upravte dávkový soubor pro uložení certifikátu serveru v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalace certifikátu serveru do klienta důvěryhodný certifikát Store
 Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Povolení přístupu k privátnímu klíči certifikátu
 Povolit přístup k privátnímu klíči certifikátu ze služby hostované v IIS, musíte uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělena příslušná oprávnění pro privátní klíč. Toho lze dosáhnout poslední kroky v skript Setup.bat.

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

##### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Ke spuštění ukázky v konfiguraci s jedním nebo více počítačů, použijte následující pokyny.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači

1. Spusťte Setup.bat ve složce instalace ukázkové uvnitř příkazový řádek sady Visual Studio 2012, spusťte s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio 2012 příkazový řádek. Proměnné prostředí PATH v nastavení v rámci body příkazový řádek sady Visual Studio 2012 k adresáři, který obsahuje požadované skript Setup.bat spustitelné soubory. Je potřeba certifikáty odebrat spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
2. Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
3. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1. Vytvoření adresáře v počítači služby. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2. Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k počítači služby.  
  
3. Vytvoření adresáře na klientský počítač určený k binárních souborů klienta.  
  
4. Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5. Na serveru, spusťte `setup.bat service` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8. Na straně klienta, spouštění `setup.bat client` otevřeného v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spouštění ImportServiceCert.bat. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru, spusťte ImportClientCert.bat to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
13. Na klientském počítači a spusťte Client.exe z okna příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky napříč počítači. Pokud jste provedli Ukázky WCF, které certifikáty využívají napříč počítači, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
