---
title: "Certifikát zabezpečení zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
caps.latest.revision: "51"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0587883a7f354ec03e3fd47ea362b93f006028ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-certificate"></a>Certifikát zabezpečení zprávy
Tento příklad znázorňuje implementaci aplikace, která používá WS-zabezpečení X.509 v3 s ověřováním pomocí certifikátu pro klienta a vyžaduje ověření serveru pomocí serveru certifikát X.509 v3. Tato ukázka používá výchozí nastavení tak, aby všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) a skládá se z konzoly programu klienta knihovnu služby hostované Internetové informační služby (IIS). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
 Službu zpřístupní jeden koncový bod pro komunikaci s službu a jeden koncový bod pro vystavení dokumentu WSDL služby pomocí protokolu WS-MetadataExchange, definované za použití konfiguračního souboru (Web.config). Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standard [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, který ve výchozím nastavení používá zabezpečení zpráv. Tato ukázka se nastaví `clientCredentialType` atribut certifikát tak, aby vyžadovala ověření klienta.  
  
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
  
 Chování Určuje přihlašovací údaje služby, které se používají, když klient se ověří službu. Název subjektu certifikátu serveru je zadán v `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.  
  
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
  
 Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient pro vazby nastavena příslušná bezpečnostní režim a režim ověřování. Při spuštění ve scénáři mezi počítači, ujistěte se, že adresa koncového bodu služby se změní odpovídajícím způsobem.  
  
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
  
 Implementace klienta můžete nastavit certifikát, který chcete použít, prostřednictvím konfiguračního souboru nebo prostřednictvím kódu. Následující příklad ukazuje, jak nastavit certifikát, který chcete použít v konfiguračním souboru.  
  
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
  
 Následující příklad ukazuje způsob volání služby v programu.  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat součástí Ukázky zabezpečení zpráv umožňuje nakonfigurovat příslušné certifikáty spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu klienta a serveru. Dávkový soubor se může spouštět ve tři režimy. Ke spuštění v režimu jednoho počítače typu **setup.bat** v Visual Studio – příkazový řádek; pro typ služby režimu **setup.bat služby**; a pro typ režimu klienta **setup.bat klienta** . Režim klienta a serveru použijte při spuštění ukázky pro počítače. Přečtěte si postup instalace na konci tohoto tématu podrobnosti. Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v odpovídající konfiguraci:  
  
-   Vytvoření certifikátu klienta.  
  
     Následující řádek v dávkovém souboru, vytvoří certifikát klienta. Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili. Certifikát je uložen v `My` uložit na `CurrentUser` umístění úložiště.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru.  
  
     Následující řádek v kopie souborů batch certifikát klienta do serveru TrustedPeople úložiště tak, aby server můžete provést příslušné důvěryhodnosti nebo ne důvěryhodnosti rozhodnutí. V pořadí pro certifikát nainstalovaný v úložišti TrustedPeople být důvěryhodný [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, režim ověření certifikátu klienta musí být nastavená na `PeerOrChainTrust` nebo `PeerTrust`. Viz předchozí ukázka konfigurace služby se dozvíte, jak to můžete provést pomocí konfiguračního souboru.  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   Vytvoření certifikátu serveru.  
  
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
  
     Proměnná % název_serveru % Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud dávkový soubor Setup.bat spuštění s argumentem služby (například **setup.bat služby**) název_serveru % obsahuje plně kvalifikovaný název domény počítače. V opačném případě bude výchozí localhost.  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Udělení oprávnění pro privátní klíč certifikátu.  
  
     Zkontrolujte následující řádky v souboru Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.  
  
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
    >  Pokud používáte jiný USA Anglickou verzi systému Windows, je nutné upravit Setup.bat souboru a název účtu "Služba NT AUTHORITY\NETWORK" nahraďte vaše místní ekvivalent.  
  
> [!NOTE]
>  Nástroje používané v tomto souboru batch jsou umístěny v sadě Visual Studio C:\Program Files\Microsoft 8\Common7\tools nebo C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jedna z těchto adresářů musí být v systémové cestě. Pokud máte nainstalovanou sadu Visual Studio, otevřete příkazový řádek sady Visual Studio je nejjednodušší způsob, jak získat tento adresář v cestě. Klikněte na tlačítko **spustit**a potom vyberte **všechny programy**, **Visual Studio 2012**, **nástroje**. Tento příkaz má odpovídající cesty již nakonfigurována. V opačném případě je nutné přidat do příslušného adresáře pro vaši cestu ručně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete příkazový řádek Visual Studio s oprávněními správce a spusťte Setup.bat z ukázkové složky instalace. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat slouží ke spuštění z Visual Studio – příkazový řádek. To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v rámci Visual Studio – příkazový řádek (2010).  
  
2.  Ověřte přístup ke službě pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat k počítači služby.  
  
3.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte **setup.bat služby** v sadě Visual Studio příkazový řádek s oprávněními správce. Spuštění **setup.bat** s **služby** argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na klientovi, spusťte **setup.bat klienta** v sadě Visual Studio příkazový řádek s oprávněními správce. Spuštění **setup.bat** s **klienta** argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. To nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na klientovi spusťte ImportServiceCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce. Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
13. Na klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
