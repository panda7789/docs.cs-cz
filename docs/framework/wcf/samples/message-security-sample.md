---
title: Ukázka zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 85108e7d1a04f39ea9e0402b0e22e9d3f609f19e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424095"
---
# <a name="message-security-sample"></a>Ukázka zabezpečení zpráv
Tato ukázka předvádí, jak implementovat aplikaci, která používá `basicHttpBinding` a zabezpečení zpráv. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Režim zabezpečení `basicHttpBinding` lze nastavit na následující hodnoty: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` a `None`. V následujícím ukázkovém souboru App. config služby, definice koncového bodu určuje `basicHttpBinding` a odkazuje na konfiguraci vazby s názvem `Binding1`, jak je znázorněno v následující ukázkové konfiguraci:  
  
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
  
 Konfigurace vazby nastaví atribut `mode` [\<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message` a nastaví atribut `clientCredentialType`\<[zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) > na `Certificate`, jak je znázorněno v následující ukázkové konfiguraci:  
  
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
  
 Certifikát, který služba používá ke vzájemnému ověření pro klienta, je nastaven v oddílu chování konfiguračního souboru pod prvkem `serviceCredentials`. Režim ověřování, který se vztahuje na certifikát, který klient používá k ověření ve službě, je také nastaven v oddílu chování pod prvkem `clientCertificate`.  
  
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
  
 V konfiguračním souboru klienta jsou zadány stejné podrobnosti o vazbě a zabezpečení.  
  
 Identita volajícího se zobrazí v okně konzoly služby pomocí následujícího kódu:  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači  
  
1. Z ukázkové instalační složky spusťte Setup. bat. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    > Dávkový soubor Setup. bat je navržený tak, aby se spouštěl z příkazového řádku Windows SDK. Vyžaduje, aby proměnná prostředí MSSDK odkazovala na adresář, ve kterém je sada SDK nainstalována. Tato proměnná prostředí se automaticky nastaví v rámci Windows SDK příkazového řádku.  
  
2. Spuštění aplikace služby z \service\bin.  
  
3. Spuštění klientské aplikace z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Po dokončení s ukázkou odeberte certifikáty spuštěním souboru Cleanup. bat. Další ukázky zabezpečení používají stejné certifikáty.  
  
### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Vytvořte adresář na počítači služby pro binární soubory služby.  
  
2. Zkopírujte programové soubory služby do adresáře služby na serveru. Zkopírujte také soubory Setup. bat, Cleanup. bat a ImportClientCert. bat na server.  
  
3. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
4. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
5. Na serveru spusťte `setup.bat service`. Spuštění `setup.bat` s argumentem `service` vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
6. Upravte soubor Service. exe. config tak, aby odrážel nový název certifikátu (v atributu `findValue` v elementu [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), který je stejný jako plně kvalifikovaný název domény počítače. Změňte také hodnotu základní adresy a zadejte plně kvalifikovaný název počítače, nikoli localhost`.`  
  
7. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
8. Na straně klienta spusťte `setup.bat client`. Spuštění `setup.bat` s argumentem `client` vytvoří klientský certifikát s názvem client.com a vyexportuje klientský certifikát do souboru s názvem Client. cer.  
  
9. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. To provedete tak, že nahradíte localhost názvem domény pro plně kvalifikovaný název domény serveru. Změňte také atribut `findValue` [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nový název certifikátu služby, který je plně kvalifikovaný název domény serveru.  
  
10. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
11. Na straně klienta spusťte ImportServiceCert. bat. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
12. Na serveru spusťte ImportClientCert. bat. tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
13. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
14. Na klientském počítači spusťte soubor Client. exe z okna příkazového řádku.  
  
    1. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
