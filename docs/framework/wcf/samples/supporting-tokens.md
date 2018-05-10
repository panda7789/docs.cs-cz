---
title: Podpora tokenů
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 8d8ff3cf4d5a060d135cbcf40c043681ce72b6e0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="supporting-tokens"></a>Podpora tokenů
Podpora tokenů ukázka ukazuje, jak přidat další tokeny pro zprávu, která používá WS-zabezpečení. V příkladu přidá token zabezpečení Binární X.509 kromě token zabezpečení uživatelské jméno. Token je předán v hlavičce protokolu WS-zabezpečení zprávy z klienta ke službě a součástí zprávy je podepsaný s privátním klíčem přidružené k tokenu zabezpečení X.509 prokázat u sebe certifikátu X.509 k příjemce. To je užitečné v případě, pokud je potřeba mít více deklarací identity přidružené k ověřování nebo autorizaci odesílatele zprávy. Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.  
  
## <a name="demonstrates"></a>Demonstruje  
 Ukázka ukazuje:  
  
-   Jak klient předat tokeny zabezpečení další služby.  
  
-   Jak bude server přístup související s tokeny zabezpečení další deklarace identity.  
  
-   Jak certifikát X.509 serveru slouží k ochraně symetrický klíč použitý k podpisu a šifrování zpráv.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient se ověří pomocí tokenu uživatelské jméno a podpůrné Token zabezpečení X.509  
 Službu zpřístupní jeden koncový bod pro komunikaci, která je vytvořena programově pomocí `BindingHelper` a `EchoServiceHost` třídy. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována pomocí vlastních vazeb `SymmetricSecurityBindingElement` a `HttpTransportBindingElement`. Nastaví Tato ukázka `SymmetricSecurityBindingElement` používat certifikát X.509 služby chránit symetrický klíč během přenosu a předávat `UserNameToken` společně s v podporu `X509SecurityToken` v záhlaví zprávy WS-zabezpečení. Symetrický klíč se používá k šifrování tělo zprávy a token zabezpečení uživatelské jméno. Token podpory se předá jako token další binární zabezpečení v záhlaví zprávy WS-zabezpečení. Pravost token podpory prokázat podepsáním část zprávy s privátním klíčem přidružené podpůrné zabezpečení X.509 tokenu.  
  
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
  
 Určuje chování služby přihlašovací údaje, které mají být použita pro ověřování klientů a také informace o certifikátu X.509 služby. Příklad používá `CN=localhost` jako název subjektu v certifikátu X.509 služby.  
  
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
  
 Kódu služby:  
  
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
  
 Koncový bod klient je nakonfigurován podobným způsobem ke koncovému bodu služby. Klient používá stejnou `BindingHelper` třída pro vytvoření vazby. Zbývající část nastavení se nachází v `Client` třídy. Klient nastaví informace o tokenu zabezpečení jméno uživatele, token zabezpečení podpory X.509 a informace o certifikátu X.509 služby v kódu instalační program do kolekce chování klienta koncový bod.  
  
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
  
## <a name="displaying-callers-information"></a>Zobrazení informací o volající.  
 Chcete-li zobrazit informace volajícího, můžete použít `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak je znázorněno v následujícím kódu. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Obsahuje spojené s volajícím aktuální deklarací autorizace. Tyto deklarace identity se automaticky zadávají ve Windows Communication Foundation (WCF) pro každý token obdržel ve zprávě.  
  
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
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Při spuštění vzorového klienta nejprve vyzve k zadání uživatelského jména a hesla pro název token uživatele. Ujistěte se, zajistit správné hodnoty pro váš účet system, protože ve službě WCF mapuje hodnoty zadané v název tokenu uživatele do identity poskytované systémem. Klient se potom zobrazí odpověď ze služby. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění aplikace hostované Internetové informační služby (IIS), která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor je nutné upravit v počítačích nebo pracovat v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci.  
  
### <a name="creating-the-client-certificate"></a>Vytvoření certifikátu klienta  
 Následující řádky z dávkového souboru Setup.bat vytvořit klientský certifikát, který se má použít. `%CLIENT_NAME%` Proměnná Určuje předmětu certifikátu klienta. Tato ukázka používá "client.com" jako název předmětu.  
  
 Certifikát je uložen v tomto úložišti (osobních) v části `CurrentUser` umístění úložiště.  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalace klientského certifikátu do důvěryhodného úložiště serveru  
 Následující řádek v dávkovém souboru, Setup.bat zkopíruje klientského certifikátu do úložiště důvěryhodných osob serveru. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému serveru. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a>Vytvoření certifikátu serveru  
 Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. `%SERVER_NAME%` Proměnná Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. V tento dávkový soubor výchozí hodnota je localhost.  
  
 Certifikát je uložen v tomto úložišti (osobních) v části LocalMachine umístění úložiště. Certifikát je uložen v úložišti LocalMachine pro služby hostované službou IIS. Pro samoobslužné hostované služby upravte dávkový soubor pro uložení certifikátu serveru v umístění úložiště CurrentUser nahrazením řetězec LocalMachine CurrentUser.  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta  
 Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a>Povolení přístupu k privátnímu klíči certifikátu  
 Povolit přístup k privátnímu klíči certifikátu ze služby hostované službou IIS, musí mít uživatelský účet, pod kterým je spuštěn proces hostované službou IIS udělen příslušná oprávnění pro privátní klíč. To lze provést poslední kroky ve skriptu Setup.bat.  
  
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
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jedním nebo mezi počítače, použijte následující pokyny.  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku spuštěného s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory. Je nutné certifikáty odebrat spuštěním Cleanup.bat po dokončení se vzorkem. Další ukázky zabezpečení použijte stejné certifikáty.  
  
2.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
3.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvoření adresáře na počítač služby. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat k počítači služby.  
  
3.  Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na klientovi, spusťte `setup.bat client` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. To nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na klientovi spusťte ImportServiceCert.bat. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru, spusťte ImportClientCert.bat to naimportuje certifikát klienta ze souboru Client.cer do LocalMachine - TrustedPeople úložiště.  
  
13. V klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud spustíte Ukázky WCF, které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - úložiště TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
