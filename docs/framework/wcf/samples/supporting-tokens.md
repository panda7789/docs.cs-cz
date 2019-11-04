---
title: Podpora tokenů
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 9d665c82f4af969204e1c87f982c6398b55cda01
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421377"
---
# <a name="supporting-tokens"></a>Podpora tokenů
Ukázka pomocných tokenů ukazuje, jak přidat další tokeny do zprávy, která používá WS-Security. V příkladu se kromě tokenu zabezpečení uživatelského jména přidá i binární token zabezpečení X. 509. Token se předává v hlavičce zprávy WS-Security od klienta ke službě a část zprávy je podepsána pomocí privátního klíče přidruženého k tokenu zabezpečení X. 509, aby bylo možné prokázat vlastnictví certifikátu X. 509 pro příjemce. To je užitečné v případě, kdy je potřeba mít k ověření nebo autorizaci odesílatele více deklarací přidružených ke zprávě. Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.

## <a name="demonstrates"></a>Demonstruje
 Ukázka ukazuje:

- Jak může klient předat službě další tokeny zabezpečení.

- Způsob, jakým může server přistupovat k deklaracím přidruženým k dalším tokenům zabezpečení

- Způsob, jakým se používá certifikát X. 509 serveru k ochraně symetrického klíče použitého pro šifrování a podpis zprávy.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient se ověřuje pomocí tokenu uživatelského jména a podporuje token zabezpečení X. 509.
 Služba zpřístupňuje jeden koncový bod pro komunikaci, která je programově vytvořena pomocí tříd `BindingHelper` a `EchoServiceHost`. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s vlastní vazbou pomocí `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`. Tato ukázka nastaví `SymmetricSecurityBindingElement` pro použití certifikátu Service X. 509 k ochraně symetrického klíče během přenosu a k předávání `UserNameToken` spolu s podpůrnými `X509SecurityToken` v hlavičce zprávy WS-Security. Symetrický klíč se používá k šifrování textu zprávy a tokenu zabezpečení uživatelského jména. Token podpory se předává jako další binární token zabezpečení v hlavičce zprávy WS-Security. Pravost podpůrného tokenu je prokázána tím, že podepisuje část zprávy s privátním klíčem přidruženým k podpůrnému tokenu zabezpečení X. 509.

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

 Chování Určuje pověření služby, které se má použít pro ověřování klientů a také informace o certifikátu služby X. 509. Ukázka používá `CN=localhost` jako název subjektu v certifikátu Service X. 509.

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

 Koncový bod klienta je nakonfigurován podobným způsobem jako koncový bod služby. Klient používá stejnou třídu `BindingHelper` k vytvoření vazby. Zbývající část instalace je umístěna v `Client` třídy. Klient nastaví informace o tokenu zabezpečení uživatelského jména, podpoře tokenu zabezpečení X. 509 a informace o certifikátu X. 509 v instalačním kódu pro kolekci chování koncového bodu klienta.

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

## <a name="displaying-callers-information"></a>Zobrazení informací o volajícím
 Chcete-li zobrazit informace o volajícím, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, jak je znázorněno v následujícím kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` obsahuje autorizační deklarace přidružené k aktuálnímu volajícímu. Tyto deklarace jsou dodány automaticky pomocí Windows Communication Foundation (WCF) pro každý token přijatý ve zprávě.

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

## <a name="running-the-sample"></a>Spuštění ukázky
 Při spuštění ukázky se klient poprvé vyzve k zadání uživatelského jména a hesla pro token uživatelského jména. Nezapomeňte zadat správné hodnoty pro systémový účet, protože služba WCF ve službě mapuje hodnoty zadané v tokenu uživatelského jména do identity poskytnuté systémem. Potom klient zobrazí odpověď ze služby. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

## <a name="setup-batch-file"></a>Nastavení dávkového souboru
 Dávkový soubor Setup. bat, který je součástí této ukázky, vám umožní nakonfigurovat server s relevantními certifikáty pro spuštění aplikace hostované v Internetová informační služba (IIS), která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upraven pro práci napříč počítači nebo pro práci v nehostovaném případě.

 Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci.

### <a name="creating-the-client-certificate"></a>Vytváření klientského certifikátu
 Následující řádky z dávkového souboru Setup. bat vytvoří klientský certifikát, který se má použít. Proměnná `%CLIENT_NAME%` určuje předmět klientského certifikátu. V této ukázce se jako název předmětu používá "client.com".

 Certifikát je uložený v osobním úložišti úložiště v umístění `CurrentUser` Store.

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalace klientského certifikátu do důvěryhodného úložiště serveru
 Následující řádek v dávkovém souboru Setup. bat kopíruje klientský certifikát do úložiště důvěryhodných osob serveru. Tento krok je povinný, protože pro systém serveru nejsou implicitně důvěryhodné certifikáty vygenerované pomocí nástroje MakeCert. exe. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Vytvoření certifikátu serveru
 Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít. Proměnná `%SERVER_NAME%` Určuje název serveru. Změňte tuto proměnnou tak, aby určovala vlastní název serveru. Výchozí hodnota v tomto dávkovém souboru je localhost.

 Certifikát je uložený v osobním úložišti (osobní) v umístění úložiště LocalMachine. Certifikát je uložený v úložišti LocalMachine pro služby hostované službou IIS. Pro samoobslužné služby byste měli soubor Batch upravit tak, aby ukládal certifikát serveru do umístění úložiště CurrentUser, a to tak, že nahradíte řetězec LocalMachine řetězcem CurrentUser.

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta
 Následující řádky v dávkovém souboru Setup. bat kopírují certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem klienta důvěryhodných kořenových certifikátů, například certifikát vydaný společností Microsoft – tento krok naplnění klientského úložiště certifikátů pomocí certifikátu serveru není vyžadován.

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Povoluje se přístup k privátnímu klíči certifikátu.
 Aby bylo možné povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěný proces hostovaný službou IIS, udělena příslušná oprávnění pro privátní klíč. To se provádí v posledních krocích skriptu Setup. bat.

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle následujících pokynů.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači

1. Spusťte Setup. bat z ukázkové instalační složky v příkazovém řádku sady Visual Studio 2012 spustit s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku sady Visual Studio 2012. Proměnná prostředí PATH nastavená v příkazovém řádku sady Visual Studio 2012 odkazuje na adresář, který obsahuje spustitelné soubory, které vyžaduje skript Setup. bat. Nezapomeňte odebrat certifikáty spuštěním souboru Cleanup. bat po dokončení ukázky. Další ukázky zabezpečení používají stejné certifikáty.  
  
2. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
3. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Vytvořte adresář na počítači služby. Pomocí nástroje pro správu služby Internetová informační služba (IIS) vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář.  
  
2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin. Zkopírujte také soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Web. config tak, aby odrážel nový název certifikátu (v atributu `findValue` v [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. Na straně klienta spusťte `setup.bat client` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s argumentem `client` vytvoří klientský certifikát s názvem client.com a vyexportuje klientský certifikát do souboru s názvem Client. cer.  
  
9. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.  
  
10. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spusťte ImportServiceCert. bat. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
12. Na serveru spusťte ImportClientCert. bat. tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
13. Na klientském počítači spusťte soubor Client. exe z okna příkazového řádku. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
> [!NOTE]
> Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky WCF, které používají certifikáty napříč počítači, ujistěte se, že jste vymazali certifikáty služby nainstalované v úložišti CurrentUser-TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
