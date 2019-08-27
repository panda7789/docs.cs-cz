---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 496589a0c1a5a0a029e464bfdd87caf8515bb9e3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044871"
---
# <a name="message-security-certificate"></a>Certifikát zabezpečení zprávy
Tato ukázka předvádí, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátů X. 509 v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X. 509 v3 serveru. Tato ukázka používá výchozí nastavení, aby všechny zprávy aplikací mezi klientem a serverem byly podepsané a šifrované. Tato ukázka je založená na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z klientského konzolového programu a knihovny služeb hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka znázorňuje řízení ověřování pomocí konfigurace a způsobu získání identity volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.  

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
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, který je definován pomocí konfiguračního souboru (Web. config). Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována pomocí standardního [ \<prvku WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , který se standardně používá zabezpečení zpráv. Tato ukázka nastaví `clientCredentialType` atribut na certifikát, aby vyžadoval ověření klienta.  
  
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
  
 Chování určuje přihlašovací údaje služby, které se používají, když klient ověřuje službu. Název subjektu certifikátu serveru je zadán v `findValue` atributu [ \<v elementu ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) .  
  
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
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurovaná s příslušným režimem zabezpečení a režimem ověřování. Pokud používáte scénář pro různé počítače, ujistěte se, že se adresa koncového bodu služby odpovídajícím způsobem změnila.  
  
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
  
 Implementace klienta může použít certifikát k použití, a to buď prostřednictvím konfiguračního souboru, nebo prostřednictvím kódu. Následující příklad ukazuje, jak nastavit certifikát pro použití v konfiguračním souboru.  
  
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
  
 Následující příklad ukazuje, jak volat službu v programu.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup. bat, který je součástí ukázek zabezpečení zpráv, vám umožní nakonfigurovat klienta a server s relevantními certifikáty pro spuštění hostované aplikace, která vyžaduje zabezpečení založené na certifikátech. Dávkový soubor lze spustit ve třech režimech. Spuštění v režimu jednoho počítače **Setup. bat** v Developer Command Prompt pro Visual Studio; pro typ Service Mode **Setup. bat service**; a v režimu klienta typ **instalace klient. bat**. Při spuštění ukázky mezi počítači použijte režim klienta a serveru. Podrobnosti najdete v postupu nastavení na konci tohoto tématu. Níže najdete stručný přehled různých částí dávkových souborů, aby je bylo možné upravit tak, aby se spouštěla v příslušné konfiguraci:  
  
- Vytváří se klientský certifikát.  
  
     Následující řádek v dávkovém souboru vytvoří klientský certifikát. Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu. Certifikát je uložený v `My` úložišti `CurrentUser` v umístění úložiště.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.  
  
     Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl učinit příslušná rozhodnutí týkající se vztahu důvěryhodnosti nebo bez vztahu důvěryhodnosti. Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou Windows Communication Foundation (WCF), musí být režim ověřování klientského certifikátu nastaven na `PeerOrChainTrust` nebo. `PeerTrust` V předchozí ukázce konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- Vytváří se certifikát serveru.  
  
     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Proměnná% Název_serveru% Určuje název serveru. Certifikát je uložený v úložišti LocalMachine. Pokud se dávkový soubor Setup. bat spustí s argumentem služby (například **Instalační služba. bat**),% název_serveru% obsahuje plně kvalifikovaný název domény počítače. V opačném případě se použije jako localhost.  
  
- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udělení oprávnění k privátnímu klíči certifikátu.  
  
     Následující řádky v souboru Setup. bat zpřístupní certifikát serveru, který je uložený v úložišti LocalMachine, přístupný pro účet pracovního procesu ASP.NET.  
  
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
    > Pokud používáte jinou než U. S. Anglická edice systému Windows, je nutné upravit soubor Setup. bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE svým regionálním ekvivalentem.  
  
> [!NOTE]
> Nástroje používané v tomto dávkovém souboru jsou umístěné ve složce C:\Program Files\Microsoft Visual Studio 8 \ Common7\tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jeden z těchto adresářů musí být ve vaší systémové cestě. Pokud máte nainstalovanou aplikaci Visual Studio, nejjednodušší způsob, jak získat tento adresář ve vaší cestě, je otevřít Developer Command Prompt pro Visual Studio. Klikněte na tlačítko **Start**a potom na položku **všechny programy**, **Visual Studio 2012**, **nástroje**. Tento příkazový řádek má již nakonfigurovanou odpovídající cesty. V opačném případě musíte do cesty ručně přidat příslušný adresář.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář:  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři:  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači  
  
1. Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio. Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK. Tato proměnná prostředí se automaticky nastaví v rámci Developer Command Prompt pro Visual Studio (2010).  
  
2. Zadáním adresy `http://localhost/servicemodelsamples/service.svc`ověřte přístup ke službě pomocí prohlížeče.  
  
3. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář na počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu služby Internetová informační služba (IIS).  
  
2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin. Zkopírujte také soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru spusťte ve Developer Command Prompt pro Visual Studio **službu Setup. bat** s oprávněními správce. Spuštění souboru **Setup. bat** s argumentem **Služba** vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Web. config tak, aby odrážel nový název certifikátu ( `findValue` v atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. Na straně klienta spusťte **klienta Setup. bat** v Developer Command Prompt pro Visual Studio s oprávněními správce. Spuštěním souboru **Setup. bat** s argumentem **klienta** se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.  
  
9. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.  
  
10. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spusťte ImportServiceCert. bat v Developer Command Prompt pro Visual Studio s oprávněními správce. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
12. Na serveru spusťte ImportClientCert. bat v Developer Command Prompt pro Visual Studio s oprávněními správce. Tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
13. V klientském počítači spusťte soubor Client. exe z okna příkazového řádku. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
