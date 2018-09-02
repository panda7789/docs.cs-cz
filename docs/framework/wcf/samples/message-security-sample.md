---
title: Ukázka zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7de6670043e6ff8862d611e987ef7b4191b3ba8d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397810"
---
# <a name="message-security-sample"></a>Ukázka zabezpečení zpráv
Tato ukázka předvádí, jak implementovat aplikaci, která se používá `basicHttpBinding` a zabezpečení zpráv. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Režim zabezpečení `basicHttpBinding` můžete nastavit následující hodnoty: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` a `None`. V následující ukázka service souboru App.config, určuje definice koncového bodu `basicHttpBinding` a odkazuje na vazbu konfigurace s názvem `Binding1`, jak je znázorněno v následující ukázkové konfiguraci:  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 Nastaví konfiguraci vazby `mode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) k `Message` a nastaví `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)k `Certificate` jak je znázorněno v následující ukázková konfigurace:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Certifikát, který službu používá ke svému ověření ke klientovi je nastavena v sekci chování konfiguračního souboru v rámci `serviceCredentials` elementu. Režim ověřování, který se vztahuje na certifikát, který klient použije ke svému ověření ke službě je také nastavena v sekci chování v rámci `clientCertificate` elementu.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Stejné informace pro vazby a zabezpečení jsou uvedeny v souboru konfigurace klienta.  
  
 Identita volajícího se zobrazí v okně konzoly služby pomocí následujícího kódu:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
    > [!NOTE]
    >  Dávkový soubor Setup.bat je navržena pro spouštění na příkazovém řádku sady SDK Windows. To vyžaduje, aby proměnné prostředí MSSDK bodu do adresáře, ve kterém je nainstalována sada SDK. Tato proměnná prostředí je nastavena automaticky v příkazovém řádku Windows SDK.  
  
2.  Spusťte aplikaci služby z \service\bin.  
  
3.  Spuštění klientské aplikace z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Odeberte certifikáty spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1.  Vytvoření adresáře v počítači služby pro binární soubory služby.  
  
2.  Programové soubory nástroje služby zkopírujte do adresáře služby na serveru. Také kopírovat soubory Setup.bat Cleanup.bat a ImportClientCert.bat k serveru.  
  
3.  Vytvoření adresáře na klientský počítač určený k binárních souborů klienta.  
  
4.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
5.  Na serveru, spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6.  Upravit Service.exe.config tak, aby odrážely nový název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) která je stejná jako plně kvalifikovaný název domény počítače. Také změňte hodnotu základní adresa pro zadejte název počítače plně kvalifikovaný místo localhost`.`  
  
7.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
8.  Na straně klienta, spouštění `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači. Změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Provedete to nahrazením localhost plně kvalifikovaný název domény serveru. Také změnit `findValue` atribut [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nový název certifikátu služby, který je plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spouštění ImportServiceCert.bat. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
12. Na serveru, spusťte ImportClientCert.bat to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
13. Na počítači služby spusťte Service.exe z příkazového řádku.  
  
14. Na klientském počítači a spusťte Client.exe z okna příkazového řádku.  
  
    1.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky napříč počítači. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty mezi počítači, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a>Viz také
