---
title: Certifikát zabezpečení zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: be9913c5109f86bf54e69beb58c53c4ddc3fd28e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664876"
---
# <a name="message-security-certificate"></a>Certifikát zabezpečení zprávy
Tento příklad ukazuje, jak implementovat aplikaci, která používá WS-Security X.509 v3 s ověřováním pomocí certifikátu klienta a vyžaduje server ověřování pomocí certifikátu X.509 v3 na server. Tato ukázka používá výchozí nastavení tak, že jsou všechny zprávy aplikace mezi klientem a serverem podepsaný a zašifrovaný. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z programu konzoly klienta a knihovna služby hostované v Internetové informační služby (IIS). Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Vzorek ukazuje řídicí ověřování pomocí konfigurace a jak získat identity volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.  

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
  
 Služba poskytuje jeden koncový bod pro komunikaci s službu a jeden koncový bod pro zveřejnění dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definované pomocí souboru konfigurace (Web.config). Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, který ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka nastaví `clientCredentialType` atributů k certifikátu tak, aby vyžadovala ověření klienta.  
  
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
  
 Určuje chování služby přihlašovací údaje, které se používají při ověřování klienta služby. Je zadaný název subjektu certifikátu serveru v `findValue` atribut [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) elementu.  
  
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
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt. Vazby klienta se nakonfigurují příslušná bezpečnostní režim a režim ověřování. Při spuštění v počítači různé scénáře, zajistěte, adresu koncového bodu služby je odpovídajícím způsobem.  
  
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
  
 Implementace klienta můžete nastavit certifikát, který chcete použít, buď pomocí konfiguračního souboru, nebo prostřednictvím kódu. Následující příklad ukazuje, jak nastavit certifikát, který chcete použít v konfiguračním souboru.  
  
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
  
 Následující příklad ukazuje, jak volat služby v programu.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat součástí Ukázky zabezpečení zpráv umožňuje nakonfigurovat příslušné certifikáty ke spuštění prostředí aplikace, které vyžadují zabezpečení na základě certifikátů klienta a serveru. Dávkový soubor můžete spustit v tří režimů. Ke spuštění v režimu jednoho počítače typu **setup.bat** v příkazový řádek vývojáře pro sadu Visual Studio; pro typ služby režimu **setup.bat služby**; a pro typ režimu klienta **setup.bat klienta**. Při spuštění ukázky mezi počítači, použije se režim klientem a serverem. Zobrazit postup nastavení na konci tohoto tématu, kde podrobnosti. Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:  
  
- Vytváří se certifikát klienta.  
  
     Následující řádek v dávkovém souboru vytvoří certifikát klienta. Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili. Certifikát je uložen v `My` ukládat na `CurrentUser` umístění úložiště.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalaci klientského certifikátu do důvěryhodného úložiště certifikátů serveru.  
  
     Následující řádek v souboru kopie služby batch klientský certifikát do serveru TrustedPeople uložit tak, aby na serveru můžete provádět odpovídající vztah důvěryhodnosti nebo rozhodnutí o důvěryhodnosti č. V objednávku na certifikát nainstalován v úložišti TrustedPeople pro důvěryhodného službou Windows Communication Foundation (WCF), musí být nastaven režim ověřování certifikátu klienta `PeerOrChainTrust` nebo `PeerTrust`. Viz předchozí ukázka konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- Vytváří se certifikát serveru.  
  
     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Proměnná % název_serveru Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud Setup.bat dávkový soubor se spustí s parametrem služby (jako jsou například **setup.bat služby**) název_serveru % obsahuje název plně kvalifikované domény počítače. Jinak je výchozí hodnota je localhost.  
  
- Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udělení oprávnění pro privátní klíč certifikátu.  
  
     Následující řádky do soubor Setup.bat uložené v úložišti LocalMachine přístupné pro certifikát serveru Ujistěte se, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.  
  
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
    >  Pokud používáte mimo USA Anglickou verzi Windows, je nutné pomocí úpravy Setup.bat soubor a nahradit místní ekvivalent názvu účtu "NT AUTHORITY\NETWORK SERVICE".  
  
> [!NOTE]
>  Nástroje používané v tomto souboru batch jsou umístěny v 8\Common7\tools C:\Program Files\Microsoft Visual Studio nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jeden z těchto adresářů musí být v systémové cestě. Pokud máte nainstalovanou sadu Visual Studio, otevřete příkazový řádek vývojáře pro sadu Visual Studio je nejjednodušší způsob, jak získat tento adresář v cestě. Klikněte na tlačítko **Start**a pak vyberte **všechny programy**, **Visual Studio 2012**, **nástroje**. Tento příkazový řádek obsahuje příslušné cesty, které jsou už nakonfigurovaná. Jinak je nutné přidat do příslušného adresáře do cesty ručně.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1. Otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku pro vývojáře pro sadu Visual Studio. To vyžaduje, aby proměnné prostředí path v bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v rámci příkazového řádku pro vývojáře pro sadu Visual Studio (2010).  
  
2. Ověření přístupu ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.  
  
3. Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1. Vytvoření adresáře na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2. Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k počítači služby.  
  
3. Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
4. Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5. Na serveru, spusťte **setup.bat služby** v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění **setup.bat** s **služby** argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravit soubor Web.config tak, aby odrážely nový název certifikátu (v `findValue` atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.  
  
7. Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8. Na straně klienta, spouštění **setup.bat klienta** v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. Spuštění **setup.bat** s **klienta** argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru spusťte ImportClientCert.bat v příkazovém řádku pro vývojáře pro sadu Visual Studio s oprávněními správce. To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
13. Na klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
- Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
