---
title: "Validátor certifikátu X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08ccbbf50db089841d2af2205c7a7cb289a8767c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="x509-certificate-validator"></a>Validátor certifikátu X.509
Tento příklad ukazuje, jak implementovat vlastní validátor certifikátu X.509. To je užitečné v případech, kdy se jeden z režimů integrované ověření certifikátu X.509 je vhodné pro požadavky na aplikace. Tento příklad ukazuje služba, která má vlastní validátor, který přijímá samoobslužné vydaných certifikátů. Klient používá tento certifikát k ověření služby.  
  
 Poznámka: jako každý, kdo může vytvořit certifikát vystavený vlastní validátor používá služba je méně bezpečné než výchozí chování poskytované ChainTrust X509CertificateValidationMode. Zabezpečení důsledky tohoto objektu je třeba pečlivě zvážit před použitím této logiku ověření v produkčním kódu.  
  
 V souhrnu tento příklad ukazuje, jak:  
  
-   Klienta můžete ověřit pomocí certifikátu X.509.  
  
-   Server ověřuje pověření klienta proti vlastní X509CertificateValidator.  
  
-   Server byl ověřovaný pomocí certifikátu X.509 serveru.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontraktu. Vazba je nakonfigurována s standard `wsHttpBinding` který ve výchozím nastavení používá `WSSecurity` a ověřování certifikátu klienta. Chování služby určuje vlastní režim pro ověřování klientských certifikátů X.509 společně s typ validátoru třídu. Chování určuje také pomocí elementu serviceCertificate certifikát serveru. Certifikát serveru musí obsahovat stejné hodnoty `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 Konfigurace klienta koncový bod se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazby a kontrakt. Klient vazba je konfigurován s odpovídající režim a zpráva `clientCredentialType`.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Implementace klienta nastaví certifikát klienta, který chcete použít.  
  
```  
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 Tato ukázka používá vlastní X509CertificateValidator k ověření certifikátů. Ukázka implementuje CustomX509CertificateValidator, odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Naleznete v dokumentaci k <xref:System.IdentityModel.Selectors.X509CertificateValidator> Další informace. Tato ukázka konkrétní vlastní validátor implementuje metodu Validate tak, aby přijímal všechny certifikátu X.509, který je vydán samoobslužné, jak je znázorněno v následujícím kódu.  
  
```  
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 Po validátor je implementovaná v kódu služby, hostitele služby musí být informováni o instanci program pro ověření používat. To se provádí pomocí následujícího kódu.  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 Nebo můžete provést totéž v konfiguraci následujícím způsobem.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně by měly volat všechny metody. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
## <a name="setup-batch-file"></a>Instalační program dávkového souboru  
 Dávkový soubor Setup.bat zahrnutá v této ukázce umožňuje nakonfigurovat server se příslušné certifikáty spuštění vlastním hostováním aplikace, která vyžaduje zabezpečení na základě certifikátu serveru. Tento dávkový soubor musí upravit, fungovat na všech počítačích, nebo pro práci v případě bez hostitele.  
  
 Následující poskytuje stručný přehled různých oddílů dávkové soubory, takže může být změněn na spouštění v příslušné konfiguraci:  
  
-   Vytvoření certifikátu serveru:  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který chcete použít. Proměnná % název_serveru % Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota je localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Následující řádky do Setup.bat batch soubor zkopírujte certifikát serveru do důvěryhodných osob klienta úložiště. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou implicitně důvěřují systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Vytvoření certifikátu klienta:  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit klientský certifikát, který se má použít. Proměnná % uživatelské_jméno % Určuje název klienta. Tato hodnota nastavena na "test1", protože je to název, který hledá kódu klienta. Pokud změníte hodnotu % uživatelské_jméno % musíte změnit s odpovídající hodnotou v Client.cs zdrojový soubor a znovu sestavte klienta.  
  
     Certifikát je uložen v tomto úložišti (osobních) v umístění úložiště CurrentUser.  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru:  
  
     Následující řádky v dávkovém souboru, Setup.bat zkopírujte certifikát klienta do úložiště důvěryhodných osob. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému serveru. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu – například certifikát vydaný Microsoft – v tomto kroku naplnění úložišti certifikátů serveru pomocí certifikátu klienta se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Ke spuštění ukázky v jedním - nebo cross-computerconfiguration, postupujte podle následujících pokynů.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spusťte Setup.bat ze složky instalace ukázkové uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!IMPORTANT]
    >  Dávkový soubor Setup.bat slouží ke spouštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavit proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skriptem Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Vytvořte adresář na počítači se službou.  
  
2.  Zkopírujte soubory programu služby z \service\bin do virtuálního adresáře na počítači se službou. Taky zkopírujte soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.  
  
3.  Vytvoření adresáře na klienta počítačeDalší binární soubory klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5.  Na serveru, spusťte `setup.bat service` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s názvem plně kvalifikované domény computerand Exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit Service.exe.config tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače. Taky změnit název počítače v \<služby > /\<baseAddresses > element z localhost pro plně kvalifikovaný název služby počítače.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na klientovi, spusťte `setup.bat client` ve z příkazového řádku Visual Studia otevřen s oprávněními správce. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. To nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce otevřít. Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
13. Na počítači serveru spusťte Service.exe z okna příkazového řádku.  
  
14. Na klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
1.  Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky. Tím se odebere z úložiště certifikátů serveru a klientské certifikáty.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
