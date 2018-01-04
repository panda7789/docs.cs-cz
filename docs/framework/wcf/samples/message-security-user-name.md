---
title: "Zabezpečení zpráv s uživatelským jménem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4df9b3d5c1f073b1b2348220ac1a77efbe797311
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-user-name"></a>Zabezpečení zpráv s uživatelským jménem
Tento příklad znázorňuje implementaci aplikace, která využívá WS-zabezpečení pomocí uživatelského jména ověřování klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru. Všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat. Ve výchozím nastavení, uživatelské jméno a heslo, které poskytl klient, se používají k přihlašování platný účet systému Windows. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Tato ukázka se skládá z konzoly programu klienta (Client.exe) a knihovna service (Service.dll) hostované Internetové informační služby (IIS). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tento příklad také ukazuje:  
  
-   Výchozí mapování na účty v systému Windows tak, že lze provést další autorizace.  
  
-   Jak pro přístup k informacím identitu volajícího z kódu služby.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, která je definovaná pomocí konfiguračního souboru Web.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standard [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), který používá ve výchozím nastavení zabezpečení zpráv. Tato ukázka nastaví standardní [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) používat uživatelské jméno ověřování klientů. Chování Určuje, zda má být použit pro ověřování služby jsou pověření uživatele. Certifikát serveru musí obsahovat stejnou hodnotu pro název subjektu, jako `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient vazba je konfigurován s odpovídající `securityMode` a `authenticationMode`. Při spuštění ve scénáři mezi počítači, musíte změnit odpovídajícím způsobem adresa koncového bodu služby.  
  
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
  
 Implementace klienta nastaví uživatelské jméno a heslo.  
  
```  
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
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat součástí ukázky MessageSecurity umožňuje nakonfigurovat server se příslušný certifikát spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu. Dávkový soubor lze spustit ve dvou režimech. Chcete-li spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku. Chcete-li používat typ režim služby `setup.bat service`. Můžete použít tento režim při spuštění ukázky pro počítače. Přečtěte si postup instalace na konci tohoto tématu podrobnosti.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory.  
  
-   Vytvoření certifikátu serveru  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Proměnná % název_serveru % Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud dávkový soubor Setup.bat spuštění s argumentem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače.  V opačném případě bude výchozí localhost.  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Udělení oprávnění pro privátní klíč certifikátu  
  
     Zkontrolujte následující řádky v dávkovém souboru, Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.  
  
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
  
    > [!NOTE]
    >  Pokud používáte jiný USA Anglickou verzi systému Windows, musíte upravit soubor Setup.bat a nahraďte `NT AUTHORITY\NETWORK SERVICE` název účtu s vaší místní ekvivalent.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, kde jsou umístěny Makecert.exe a FindPrivateKey.exe.  
  
2.  Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazový řádek s oprávněními správce otevřít. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio – příkazový řádek. To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio – příkazový řádek.  
  
3.  Ověřte přístup ke službě pomocí prohlížeče zadáním adresy http://localhost/servicemodelsamples/service.svc.  
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
5.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu služby IIS.  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážela nový název certifikátu (v atributu findValue v elementu serviceCertificate), která je stejná jako plně kvalifikovaný název domény počítače`.`  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte z příkazového řádku Client.exe. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
