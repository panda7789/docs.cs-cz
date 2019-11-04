---
title: Zabezpečení zpráv s uživatelským jménem
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: cbc24ab20d28e877dd8b1a41d965d9176f15c581
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424084"
---
# <a name="message-security-user-name"></a>Zabezpečení zpráv s uživatelským jménem
Tato ukázka předvádí, jak implementovat aplikaci, která používá protokol WS-Security s ověřováním uživatelského jména pro klienta, a vyžaduje ověření serveru pomocí certifikátu X. 509 v3 serveru. Všechny zprávy aplikací mezi klientem a serverem jsou podepsané a šifrované. Ve výchozím nastavení se k přihlášení k platnému účtu systému Windows používá uživatelské jméno a heslo dodávané klientem. Tato ukázka je založená na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Tato ukázka se skládá z programu klientské konzoly (Client. exe) a knihovny služeb (Service. dll) hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka také ukazuje:  
  
- Výchozí mapování na účty systému Windows, aby bylo možné provést další autorizaci.  
  
- Přístup k informacím o identitě volajícího z kódu služby.  
  
 Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, která je definována pomocí konfiguračního souboru Web. config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurovaná se standardním [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), která standardně používá zabezpečení zpráv. Tato ukázka nastaví standardní [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) pro použití ověřování uživatelského jména klienta. Chování určuje, zda mají být pro ověřování služby použity přihlašovací údaje uživatele. Certifikát serveru musí obsahovat stejnou hodnotu pro název subjektu jako atribut `findValue` [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu. Vazba klienta je nakonfigurovaná s příslušnými `securityMode` a `authenticationMode`. Při spuštění v případě různých počítačů se musí adresa koncového bodu služby odpovídajícím způsobem změnit.  
  
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

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup. bat, který je součástí ukázek MessageSecurity, vám umožní nakonfigurovat server s relevantním certifikátem pro spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátů. Dávkový soubor lze spustit ve dvou režimech. Pokud chcete spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` do příkazového řádku. Pokud ho chcete spustit v režimu služby `setup.bat service`typ. Tento režim použijete při spuštění ukázky v různých počítačích. Podrobnosti najdete v postupu nastavení na konci tohoto tématu.  
  
 Níže najdete stručný přehled různých částí dávkových souborů.  
  
- Vytvoření certifikátu serveru  
  
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
  
     Proměnná% Název_serveru% Určuje název serveru. Certifikát je uložený v úložišti LocalMachine. Pokud se dávkový soubor Setup. bat spustí s argumentem služby (například `setup.bat service`),% název_serveru% obsahuje plně kvalifikovaný název domény počítače.  V opačném případě se použije jako localhost.  
  
- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta  
  
     Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udělení oprávnění k privátnímu klíči certifikátu  
  
     Následující řádky v dávkovém souboru Setup. bat umožňují, aby byl certifikát serveru uložený v úložišti LocalMachine dostupný pro účet pracovního procesu ASP.NET.  
  
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
    > Pokud používáte systém Windows, který není ve verzi U. English, musíte upravit soubor Setup. bat a nahradit název účtu `NT AUTHORITY\NETWORK SERVICE` svým regionálním ekvivalentem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači  
  
1. Ujistěte se, že cesta obsahuje složku, ve které jsou umístěny nástroje MakeCert. exe a FindPrivateKey. exe.  
  
2. Spusťte Setup. bat z ukázkové instalační složky ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z Developer Command Prompt pro Visual Studio. Vyžaduje, aby proměnná prostředí PATH odkazovala na adresář, ve kterém je nainstalována sada SDK. Tato proměnná prostředí se automaticky nastaví v rámci Developer Command Prompt pro Visual Studio.  
  
3. Zadáním adresy `http://localhost/servicemodelsamples/service.svc`ověřte přístup ke službě pomocí prohlížeče.
  
4. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
5. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Vytvořte adresář na počítači služby. Vytvořte virtuální aplikaci s názvem ServiceModelSamples pro tento adresář pomocí nástroje pro správu Internetová informační služba.  
  
2. Zkopírujte programové soubory služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači služby. Ujistěte se, že jste zkopírovali soubory do podadresáře \Bin. Zkopírujte také soubory Setup. bat a Cleanup. bat do počítače služby.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru spusťte `setup.bat service` v Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Web. config tak, aby odrážel nový název certifikátu (v atributu findValue v elementu serviceCertificate), který je stejný jako plně kvalifikovaný název domény počítače`.`  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby.  
  
9. Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
10. V klientském počítači spusťte z příkazového řádku soubor Client. exe. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky Spusťte Cleanup. bat ve složce Samples.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
