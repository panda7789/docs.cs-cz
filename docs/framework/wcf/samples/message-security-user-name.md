---
title: Zabezpečení zpráv s uživatelským jménem
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183502"
---
# <a name="message-security-user-name"></a>Zabezpečení zpráv s uživatelským jménem
Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním uživatelského jména pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509v3 serveru. Všechny zprávy aplikace mezi klientem a serverem jsou podepsány a šifrovány. Ve výchozím nastavení se uživatelské jméno a heslo zadané klientem používají k přihlášení k platnému účtu systému Windows. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Tato ukázka se skládá z programu klientské konzole (Client.exe) a knihovny služeb (Service.dll) hostované Internetovou informační službou (IIS). Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tento vzorek také ukazuje:  
  
- Výchozí mapování na účty systému Windows, aby bylo možné provést další autorizaci.  
  
- Jak získat přístup k informacím o identitě volajícího z kódu služby.  
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a smlouvy. Vazba je nakonfigurována se standardním [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), který ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka nastaví standardní [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) pro použití ověřování uživatelského jména klienta. Chování určuje, že pověření uživatele mají být použita pro ověřování služby. Certifikát serveru musí obsahovat stejnou hodnotu `findValue` pro název subjektu jako atribut v [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu. Vazby klienta je `securityMode` nakonfigurován s příslušnou a `authenticationMode`. Při spuštění ve scénáři mezi počítači musí být odpovídajícím způsobem změněna adresa koncového bodu služby.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Implementace klienta nastaví uživatelské jméno a heslo, které se má použít.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat, který je součástí ukázek MessageSecurity, umožňuje nakonfigurovat server s příslušným certifikátem tak, aby spouštěl hostovnu, která vyžaduje zabezpečení založené na certifikátu. Dávkový soubor lze spustit ve dvou režimech. Chcete-li dávkový soubor spustit v `setup.bat` režimu jednoho počítače, zadejte příkaz na příkazovém řádku. Chcete-li jej spustit `setup.bat service`v servisním režimu typu . Tento režim se používá při spuštění ukázky v počítačích. Podrobnosti naleznete v postupu nastavení na konci tohoto tématu.  
  
 Následující text poskytuje stručný přehled různých částí dávkových souborů.  
  
- Vytvoření certifikátu serveru  
  
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
  
     Proměnná %SERVER_NAME% určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud je dávkový soubor Setup.bat spuštěn s `setup.bat service`argumentem služby (například) % SERVER_NAME% obsahuje plně kvalifikovaný název domény počítače.  V opačném případě je výchozí localhost.  
  
- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udělení oprávnění k soukromému klíči certifikátu  
  
     Následující řádky v dávkovém souboru Setup.bat zpřístupní certifikát serveru uložený v úložišti LocalMachine ASP.NET účtu pracovního procesu.  
  
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
    > Pokud používáte edici systému Windows, která není v USA, je `NT AUTHORITY\NETWORK SERVICE` nutné upravit soubor Setup.bat a nahradit název účtu místním ekvivalentem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, kde jsou umístěny Makecert.exe a FindPrivateKey.exe.  
  
2. Spusťte soubor Setup.bat z ukázkové instalační složky v příkazovém řádku pro vývojáře pro sady Visual Studio otevřeného s oprávněními správce. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup.bat je navržen tak, aby byl spuštěn z příkazového řádku pro vývojáře sady Visual Studio. Vyžaduje, aby proměnná prostředí cesty přecškovala do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je automaticky nastavena v příkazovém řádku pro vývojáře pro sadu Visual Studio.  
  
3. Ověřte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním adresy .
  
4. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
5. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích  
  
1. Vytvořte adresář v počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby.  
  
2. Zkopírujte soubory servisních programů ze vzorků \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře v počítači služby. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Zkopírujte také soubory Setup.bat a Cleanup.bat do servisního počítače.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5. Na serveru spusťte `setup.bat service` v příkazovém řádku pro vývojáře pro Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Úprava souboru Web.config tak, aby odrážel nový název certifikátu (v atributu findValue v elementu serviceCertificate), který je stejný jako plně kvalifikovaný název domény počítače`.`  
  
7. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. Na straně klienta spusťte soubor ImportServiceCert.bat v příkazovém řádku pro vývojáře pro sady Visual Studio otevřeného s oprávněními správce. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
10. V klientském počítači spusťte soubor Client.exe z příkazového řádku. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Spusťte cleanup.bat ve složce ukázky po dokončení spuštění ukázky.  
  
    > [!NOTE]
    > Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .  
