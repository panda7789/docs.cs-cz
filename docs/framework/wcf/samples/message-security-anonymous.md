---
title: "Zabezpečení zpráv s anonymní metodou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d6f3ac3ba51939f319d1d0e98265d7867233f2b6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-anonymous"></a>Zabezpečení zpráv s anonymní metodou
Ukázku zprávu zabezpečení anonymní ukazuje, jak implementovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace používající zabezpečení na úrovni zpráv bez jakéhokoli ověřování klienta, ale která vyžaduje server ověřování pomocí certifikátu X.509 serveru. Všechny zprávy aplikace mezi klientem a serverem jsou podepsat a zašifrovat. Tato ukázka je založena na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka. Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka přidá operaci nového kalkulačky rozhraní, které vrátí `True` Pokud klient nebyl ověřen.  
  
```  
public class CalculatorService : ICalculator  
{  
    public bool IsCallerAnonymous()  
    {  
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.  
        return ServiceSecurityContext.Current.IsAnonymous;  
    }  
    ...  
}  
```  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru (Web.config). Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s `wsHttpBinding` vazby. Výchozí režim zabezpečení `wsHttpBinding` vazba je `Message`. `clientCredentialType` Je nastavena na hodnotu `None`.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
     <!--   
     <!--This configuration defines the security mode as Message and-->  
     <!--the clientCredentialType as None. This mode provides -- >  
     <!--server authentication only using the service certificate.-->  
  
     <binding>  
       <security mode="Message">  
         <message clientCredentialType="None" />  
       </security>  
     </binding>  
    </wsHttpBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 Přihlašovací údaje, které má být použit pro ověřování služby jsou určené v [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako zadaná hodnota parametru `findValue` atributu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>  
      <!--   
    The serviceCredentials behavior allows you to define a service certificate.  
    A service certificate is used by a client to authenticate the service and provide message protection.  
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
```  
  
 Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt. Režim zabezpečení klienta `wsHttpBinding` vazba je `Message`. `clientCredentialType` Je nastavena na hodnotu `None`.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
             address="http://localhost/servicemodelsamples/service.svc"   
             binding="wsHttpBinding"   
             behaviorConfiguration="ClientCredentialsBehavior"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--This configuration defines the security mode as -->  
      <!--Message and the clientCredentialType as None. -->  
      <binding name="Binding1">  
        <security mode = "Message">  
          <message clientCredentialType="None"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>   
  ...  
</system.serviceModel>  
```  
  
 Ukázka sady <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pro ověřování certifikátu služby. To se provádí v souboru App.config klienta v `behaviors` oddílu. To znamená, že pokud je certifikát v úložišti důvěryhodných osob uživatele, pak je důvěryhodný bez provedení ověření řetězu vystavitele certifikátu. Toto nastavení je zde slouží pro usnadnění práce, aby ukázce je možné spouštět bez vyžadování certifikátů vystavených certifikační autoritou (CA). Toto nastavení je méně bezpečné než výchozí, ChainTrust. Bezpečnostních důsledcích tohoto nastavení je třeba pečlivě zvážit před použitím `PeerOrChainTrust` v produkčním kódu.  
  
 Implementace klienta přidá volání `IsCallerAnonymous` metoda a jinak neliší od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka.  
  
```  
// Create a client with a client endpoint configuration.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity operation.  
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
...  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
IsCallerAnonymous returned: True  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Dávkový soubor Setup.bat součástí ukázku zprávu zabezpečení anonymní umožňuje nakonfigurovat server se příslušný certifikát spuštění hostované aplikace, která vyžaduje zabezpečení na základě certifikátu. Dávkový soubor lze spustit ve dvou režimech. Chcete-li spustit dávkový soubor v režimu jednoho počítače, zadejte `setup.bat` na příkazovém řádku. Chcete-li spustit v režimu služby, zadejte `setup.bat service`. Tento režim používejte při spuštění ukázky mezi počítači. Přečtěte si postup instalace na konci tohoto tématu podrobnosti.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory:  
  
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
  
     Proměnná % název_serveru % Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Jestli dávkový soubor Instalační program se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače. V opačném případě bude výchozí localhost.  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Udělení oprávnění pro privátní klíč certifikátu.  
  
     Zkontrolujte následující řádky v dávkovém souboru, Setup.bat certifikát serveru, který je uložen v úložišti LocalMachine přístupné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účet pracovního procesu.  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
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
  
2.  Spuštění Setup.bat od vzorku instalační složku v sadě Visual Studio příkazovém řádku spusťte s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Instalační program je určen pro spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]příkazového řádku. To vyžaduje, aby proměnné prostředí path přejděte na adresář, kam nainstalovat sadu SDK. Tato proměnná prostředí bude automaticky nastavena v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]příkazového řádku.  
  
3.  Ověřte přístup ke službě pomocí prohlížeče zadáním adresy http://localhost/servicemodelsamples/service.svc.  
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
5.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou. Vytvořte virtuální aplikaci s názvem servicemodelsamples pro tento adresář pomocí nástroje pro správu Internetové informační služby (IIS).  
  
2.  Zkopírujte soubory programu služby z \inetpub\wwwroot\servicemodelsamples do virtuálního adresáře na počítači se službou. Ujistěte se, že zkopírujete soubory v podadresáři \bin. Taky zkopírujte soubory Setup.bat a Cleanup.bat k počítači služby.  
  
3.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit soubor Web.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), což je stejný jako název plně kvalifikované domény počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.  
  
9. V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
10. Na klientském počítači spusťte z příkazového řádku Client.exe. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`  
  
## <a name="see-also"></a>Viz také
