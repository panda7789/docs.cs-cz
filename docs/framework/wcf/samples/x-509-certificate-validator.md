---
title: Validátor certifikátu X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: e54f79046113e5f1a1a1cc065606fd5b706b49ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402349"
---
# <a name="x509-certificate-validator"></a>Validátor certifikátu X.509
Tento příklad ukazuje, jak implementovat vlastní validátor certifikátu X.509. To je užitečné v případech, kdy je vhodné pro požadavky na aplikace žádná z předdefinovaných režimy ověřování certifikátu X.509. Tento příklad ukazuje služba, která má vlastní validátor, který přijímá samostatně vydané certifikáty. Klient používá tento certifikát k ověření ve službě.  
  
 Poznámka: jako kdokoli může vytvořit certifikát vystavený je méně bezpečné než výchozí chování poskytované ChainTrust X509CertificateValidationMode vlastní validátor používané službou. Důsledky zabezpečení tohoto objektu je třeba pečlivě zvážit před použitím této logiky ověřování v produkčním kódu.  
  
 V souhrnu Tato ukázka předvádí, jak:  
  
-   Klient lze ověřit pomocí certifikátu X.509.  
  
-   Server ověří klienta přihlašovacích údajů, kteří vlastní X509CertificateValidator.  
  
-   Server byl ověřovaný pomocí certifikátu X.509 serveru.  
  
 Služba poskytuje jeden koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru App.config. Koncový bod se skládá z adresy, vazby a kontrakt. Je vazba konfigurována se standardní `wsHttpBinding` , která ve výchozím nastavení používá `WSSecurity` a ověření klientského certifikátu. Chování služby určuje vlastní režim ověřování klientských certifikátů X.509 spolu s typem třídy program pro ověření. Chování také Určuje certifikát serveru pomocí serviceCertificate elementu. Certifikát serveru musí obsahovat stejnou hodnotu pro `SubjectName` jako `findValue` v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
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
  
 Konfigurace koncového bodu klienta se skládá z názvu konfigurace absolutní adresu pro koncový bod služby, vazba a kontrakt. Klient vazby je nakonfigurován příslušný režim, zpráva `clientCredentialType`.  
  
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
  
 Implementace klienta nastaví klientský certifikát k použití.  
  
```csharp
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
  
 Tato ukázka používá vlastní X509CertificateValidator ověřování certifikátů. Ukázka implementuje CustomX509CertificateValidator odvozený od <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Najdete v dokumentaci <xref:System.IdentityModel.Selectors.X509CertificateValidator> Další informace. Tato ukázka konkrétní vlastní validátor implementuje metodu Validate tak, aby přijímal libovolný certifikát X.509, která je držitelem vydala, jak je znázorněno v následujícím kódu.  
  
```csharp
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
  
 Jakmile se v kódu služby validátoru, hostitele služby musí být informováni o instance program pro ověření, kterou chcete použít. To se provádí pomocí následujícího kódu.  
  
```csharp
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Klient úspěšně by měly volat všechny metody. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
## <a name="setup-batch-file"></a>Instalační dávkový soubor  
 Dávkový soubor Setup.bat zahrnuté v této ukázce můžete nakonfigurovat server se příslušné certifikáty ke spuštění aplikace v místním prostředí, která vyžaduje zabezpečení na základě certifikátů serveru. Tento dávkový soubor musí být upravena fungovat na všech počítačích nebo pro práci v případě jiných hostované.  
  
 Následující body nabízí stručný přehled o různých částech dávkové soubory tak, aby se lze upravit a spustit v příslušné konfiguraci:  
  
-   Vytváří se certifikát serveru:  
  
     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít. % Proměnná % název_serveru Určuje název serveru. Změňte tuto proměnnou k určení vlastního názvu serveru. Výchozí hodnota je localhost.  
  
    ```bash  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta:  
  
     Uložte následující řádky Setup.bat dávky kopírování souborů certifikát serveru do klienta důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikátů vystavených Microsoftem – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.  
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Vytváří se certifikát klienta:  
  
     Následující řádky z dávkový soubor Setup.bat vytvořit klientský certifikát, který se má použít. % Proměnná % uživatelské_jméno Určuje název klienta. Tato hodnota nastavená na "test1", protože jde o název, který hledá kód klienta. Pokud změníte hodnotu % uživatelské_jméno musíte změnit odpovídající hodnotu ve zdrojovém souboru Client.cs a znovu sestavte klienta.  
  
     Certifikát je uložen v úložišti (osobních) v části CurrentUser umístění úložiště.  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalaci klientského certifikátu do úložiště důvěryhodných certifikátů serveru:  
  
     Následující řádky do dávkový soubor Setup.bat zkopírujte klientský certifikát do úložiště důvěryhodných osob. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje serverového systému. Pokud už máte certifikát, který je integrován v důvěryhodných kořenových certifikátů – například certifikátů vystavených Microsoftem – v tomto kroku naplnění úložiště certifikátů serveru pomocí certifikátu klienta se nevyžaduje.  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Ke spuštění ukázky v jedním - nebo mezi computerconfiguration, použijte následující pokyny.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spustit Setup.bat z instalační složky Ukázky uvnitř [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otevřít příkazový řádek s oprávněními správce. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
    > [!IMPORTANT]
    >  Dávkový soubor Setup.bat slouží ke spuštění z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku. Nastavte proměnné prostředí PATH v rámci [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek odkazuje na adresář, který obsahuje požadované skript Setup.bat spustitelné soubory.  
  
2.  Spusťte Service.exe z service\bin.  
  
3.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře na počítači se službou.  
  
2.  Zkopírujte soubory programu služby z \service\bin do virtuálního adresáře na počítači se službou. Také kopírovat soubory Setup.bat, Cleanup.bat, GetComputerName.vbs a ImportClientCert.bat k počítači služby.  
  
3.  Vytvoření adresáře na klienta počítačeDalší binárních souborů klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5.  Na serveru, spusťte `setup.bat service` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se název plně kvalifikované domény exporty computerand certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit Service.exe.config tak, aby odrážely nový název certifikátu (v `findValue` atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače. Také změnit název počítače \<služby > /\<baseAddresses > element z místního hostitele, plně kvalifikovaný název počítače služby.  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na straně klienta, spouštění `setup.bat client` v příkazovém řádku aplikace Visual Studio otevřené s oprávněními správce. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru spusťte ImportClientCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce. To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
13. Na počítači serveru spusťte Service.exe z okna příkazového řádku.  
  
14. Na klientském počítači spusťte Client.exe z okna příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
1.  Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky. Tím serverových a klientských certifikátů z úložiště certifikátů.  
  
> [!NOTE]
>  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také
