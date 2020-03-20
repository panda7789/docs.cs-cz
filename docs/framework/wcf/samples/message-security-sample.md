---
title: Ukázka zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 43e1a9104bdd44509d86bd198559c5e7477a9964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183521"
---
# <a name="message-security-sample"></a>Ukázka zabezpečení zpráv
Tato ukázka ukazuje, jak implementovat `basicHttpBinding` aplikaci, která používá zabezpečení a zprávy. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Režim zabezpečení `basicHttpBinding` lze nastavit na následující `Message`hodnoty: `TransportWithMessageCredential` `TransportCredentialOnly` , `None` `Transport`, a . V následujícím ukázkovém souboru App.config určuje `basicHttpBinding` definice koncového bodu `Binding1`a odkazuje na konfiguraci vazby s názvem , jak je znázorněno v následující ukázkové konfiguraci:  
  
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
  </services>  
  ...  
</system.serviceModel>  
```  
  
 Konfigurace vazby `mode` nastaví atribut [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `clientCredentialType` `Message` a nastaví atribut `Certificate` [ \<>zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) tak, jak je znázorněno v následující ukázkové konfiguraci:  
  
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
  
 Certifikát, který služba používá k ověření sám klientovi je nastavena v `serviceCredentials` části chování konfiguračního souboru pod elementem. Ověřovací režim, který se vztahuje k certifikátu, který klient používá k ověření sám `clientCertificate` služby je také nastavena v části chování pod element.  
  
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
  
 Stejné podrobnosti o vazbě a zabezpečení jsou určeny v konfiguračním souboru klienta.  
  
 Identita volajícího se zobrazí v okně konzoly služby pomocí následujícího kódu:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky ve stejném počítači  
  
1. Spusťte soubor Setup.bat z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup.bat je určen ke spuštění z příkazového řádku sady Windows SDK. Vyžaduje, aby proměnná prostředí sady MSSDK přecšuje do adresáře, ve kterém je sada SDK nainstalována. Tato proměnná prostředí je automaticky nastavena v příkazovém řádku sady Windows SDK.  
  
2. Spusťte aplikaci služby z \service\bin.  
  
3. Spusťte klientskou aplikaci z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
4. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Po dokončení ukázky odeberte certifikáty spuštěním souboru Cleanup.bat. Jiné ukázky zabezpečení používají stejné certifikáty.  
  
### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Vytvořte adresář na servisním počítači pro binární soubory služby.  
  
2. Zkopírujte soubory programu služby do adresáře služby na serveru. Na server také zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat.  
  
3. Vytvořte adresář v klientském počítači pro binární soubory klienta.  
  
4. Zkopírujte soubory klientského programu do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
5. Na serveru spusťte . `setup.bat service` Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
6. Upravte service.exe.config tak, aby odrážel `findValue` nový název certifikátu (v atributu [ \<v prvku serviceCertificate>),](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) který je stejný jako plně kvalifikovaný název domény počítače. Změňte také hodnotu základní adresy a zadejte plně kvalifikovaný název počítače namísto localhost`.`  
  
7. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
8. Na straně klienta spusťte `setup.bat client`. Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.  
  
9. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Provést nahrazením localhost plně kvalifikovaný název domény serveru. Změňte `findValue` také atribut [ \<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nový název certifikátu služby, který je plně kvalifikovaným názvem domény serveru.  
  
10. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spusťte ImportServiceCert.bat. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
12. Na serveru spusťte ImportClientCert.bat, Importuje to klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.  
  
13. Na servisním počítači spusťte service.exe z příkazového řádku.  
  
14. V klientském počítači spusťte soubor Client.exe z okna příkazového řádku.  
  
    1. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.  
  
    > [!NOTE]
    > Tento skript neodebere certifikáty služeb na straně klienta při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující příkaz: Například:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
