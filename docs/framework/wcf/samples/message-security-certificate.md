---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183538"
---
# <a name="message-security-certificate"></a>Certifikát zabezpečení zprávy
Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátu X.509 v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509 v3 serveru. Tato ukázka používá výchozí nastavení tak, aby všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány. Tato ukázka je založena na [wshttpbinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z programu konzoly klienta a knihovny služeb hostované Internetovou informační službou (IIS). Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definovaného pomocí konfiguračního souboru (Web.config). Koncový bod se skládá z adresy, vazby a smlouvy. Vazba je nakonfigurována se standardním [ \<prvkem wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) který ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka `clientCredentialType` nastaví atribut na certifikát tak, aby vyžadoval ověření klienta.  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Chování určuje pověření služby, které se používají při ověření služby klientem. Název subjektu certifikátu serveru `findValue` je určen v atributu v elementu [ \<serviceCredentials>.](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu. Vazba klienta je konfigurována s příslušným režimem zabezpečení a režimem ověřování. Při spuštění ve scénáři mezi počítači se ujistěte, že je odpovídajícím způsobem změněna adresa koncového bodu služby.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 Implementace klienta můžete nastavit certifikát použít, a to buď prostřednictvím konfiguračního souboru nebo prostřednictvím kódu. Následující ukázka ukazuje, jak nastavit certifikát pro použití v konfiguračním souboru.  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 Následující ukázka ukazuje, jak volat službu v programu.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat, který je součástí ukázek Zabezpečení zpráv, umožňuje nakonfigurovat klienta a server s příslušnými certifikáty tak, aby spouštěly hostovnu, která vyžaduje zabezpečení založené na certifikátu. Dávkový soubor lze spustit ve třech režimech. Chcete-li spustit v režimu jednoho počítače, zadejte **setup.bat** v příkazovém řádku pro vývojáře pro sady Visual Studio ; pro službu typu service type **setup.bat**; a pro klientský režim typu **setup.bat klienta**. Při spuštění ukázky v počítačích použijte režim klienta a serveru. Podrobnosti naleznete v postupu nastavení na konci tohoto tématu. Následující text poskytuje stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby byly spuštěny v odpovídající konfiguraci:  
  
- Vytvoření klientského certifikátu.  
  
     Následující řádek v dávkovém souboru vytvoří klientský certifikát. Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu. Certifikát je uložen `My` v `CurrentUser` úložišti v umístění úložiště.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.  
  
     Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl činit příslušná rozhodnutí o důvěryhodnosti nebo nedůvěryhodnosti. Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou WCF (Windows Communication Foundation), musí `PeerOrChainTrust` `PeerTrust`být režim ověření klientského certifikátu nastaven na nebo . Podívejte se na předchozí ukázku konfigurace služby, kde se dozvíte, jak toho lze provést pomocí konfiguračního souboru.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvoří certifikát serveru, který má být použit.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Proměnná %SERVER_NAME% určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud je dávkový soubor Setup.bat spuštěn s argumentem služby (například **služba setup.bat),** obsahuje %SERVER_NAME% plně kvalifikovaný název domény počítače. V opačném případě je výchozí localhost.  
  
- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udělení oprávnění k soukromému klíči certifikátu.  
  
     Následující řádky v souboru Setup.bat zpřístupní certifikát serveru uložený v úložišti LocalMachine ASP.NET účtu pracovního procesu.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > Pokud používáte edici systému Windows, která není v USA, je nutné upravit soubor Setup.bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE místním ekvivalentem.  
  
> [!NOTE]
> Nástroje použité v tomto dávkovém souboru jsou umístěny buď v souborech C:\Program Files\Microsoft Visual Studio 8\Common7\Tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin. Jeden z těchto adresářů musí být v cestě systému. Pokud máte nainstalovanou aplikaci Visual Studio, nejjednodušší způsob, jak tento adresář získat do cesty, je otevřít příkazový řádek pro vývojáře pro sady Visual Studio. Klepněte na tlačítko **Start**a vyberte možnost **Všechny programy**, **Visual Studio 2012**, **Nástroje**. Tento příkazový řádek má již nakonfigurované příslušné cesty. V opačném případě je nutné přidat příslušný adresář do cesty ručně.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář:  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři:  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači  
  
1. Otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor Setup.bat z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře sady Visual Studio. Vyžaduje, aby proměnná prostředí cesty přecškovala do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je automaticky nastavena v rámci příkazového řádku pro vývojáře pro sadu Visual Studio (2010).  
  
2. Ověřte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním adresy .  
  
3. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
4. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích  
  
1. Vytvořte adresář v počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2. Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportClientCert.bat do servisního počítače.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5. Na serveru spusťte **službu setup.bat** v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce. **Spuštěnísouboru setup.bat** s argumentem **služby** vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravte web.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
8. V klientovi klienta **setup.bat** spusťte v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce. **Spuštěnísouboru setup.bat** s argumentem **klienta** vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. To provést nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spusťte soubor ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
12. Na serveru spusťte soubor ImportClientCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio s oprávněními správce. Tím se klientský certifikát importuje ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.  
  
13. V klientském počítači spusťte soubor Client.exe z okna příkazového řádku. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.  
  
    > [!NOTE]
    > Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .  
