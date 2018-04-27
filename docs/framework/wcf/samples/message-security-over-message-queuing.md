---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: 22
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: aeb0e66c5bad2b2d03a08560e1021b57e793ad55
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="message-security-over-message-queuing"></a>Zabezpečení zprávy pomocí služby Řízení front zpráv
Tento příklad znázorňuje implementaci aplikace, která využívá WS-zabezpečení x.509 v3 s ověřováním pomocí certifikátu pro klienta a vyžaduje server ověřování pomocí certifikátu x.509 v3 serveru přes služby MSMQ. Zpráva, že zabezpečení je někdy další žádoucí zajistit, že zůstat šifrovaných zpráv v úložišti služby MSMQ a aplikace můžete provádět vlastní ověřování zprávy.  
  
 Tato ukázka je založena na [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázka. Zprávy jsou šifrovaný a podepsaný.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud je služba spuštěna první, zkontroluje Ujistěte se, zda je k dispozici fronty. Pokud fronta neexistuje, vytvoří služba jeden. Můžete spustit služby nejprve vytvořit frontu, nebo můžete vytvořit jeden prostřednictvím správce front služby MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu v systému Windows 2008.  
  
    1.  Otevřete správce serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozbalte **funkce** kartě.  
  
    3.  Klikněte pravým tlačítkem na **soukromé fronty zpráv**a vyberte **nový**, **soukromou frontu**.  
  
    4.  Zkontrolujte **transakcí** pole.  
  
    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe a FindPrivateKey.exe.  
  
2.  Spuštění Setup.bat od vzorku instalační složku. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
    > [!NOTE]
    >  Ujistěte se, spuštěním Cleanup.bat po dokončení s ukázkou certifikáty odebrat. Další ukázky zabezpečení použijte stejné certifikáty.  
  
3.  Spusťte Service.exe z \service\bin.  
  
4.  Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
5.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat na počítač služby.  
  
2.  Vytvořte adresář na klientském počítači pro binární soubory klienta.  
  
3.  Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Taky zkopírujte soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
4.  Na serveru, spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
5.  Upravit service.exe.config služby tak, aby odrážely novou název certifikátu (v `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) což je stejný jako název plně kvalifikované domény počítače.  
  
6.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
7.  Na klientovi, spusťte `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
8.  V souboru Client.exe.config na klientský počítač změňte hodnotu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. To nahrazením localhost plně kvalifikovaný název domény serveru.  Musíte taky změnit název certifikátu služby být stejné jako plně kvalifikovaný název domény počítače, služby (v `findValue` atribut `defaultCertificate` element `serviceCertificate` pod `clientCredentials`).  
  
9. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
10. Na klientovi, spusťte `ImportServiceCert.bat`. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
11. Na serveru, spusťte `ImportClientCert.bat`, tento klientský certifikát naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
12. Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
13. Na klientském počítači spusťte z příkazového řádku Client.exe. Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vzorků, které používají certifikáty na počítačích, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="requirements"></a>Požadavky  
 Tato ukázka vyžaduje, aby služby MSMQ nainstalovaná a spuštěná.  
  
## <a name="demonstrates"></a>Demonstruje  
 Klient zašifruje pomocí veřejného klíče služby zprávu a podepisuje zprávy pomocí svůj vlastní certifikát. Čtení zprávy z fronty služby ověřuje klientský certifikát s certifikátem v úložišti důvěryhodných osob. Potom zprávu dešifruje a odešle zprávu, která se operace služby.  
  
 Protože [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zpráva Probíhá jako datovou část v těle zprávy služby MSMQ, text zůstávají šifrovaná v úložišti služby MSMQ. To zabezpečuje zprávu od nežádoucí zpřístupnění zprávy. Modul služby MSMQ, samotné není vědět jestli se šifrují zprávy, které je provedení.  
  
 Ukázka ukazuje, jak vzájemné ověřování na zprávu úroveň lze použít s služby MSMQ. Certifikáty jsou výměně out-of-band. To je vždy tomu u aplikace ve frontě, protože služba a klient nemusí být spuštěná ve stejnou dobu.  
  
## <a name="description"></a>Popis  
 Ukázkový kód klienta a služby jsou stejné jako [transakční vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázku s jedním rozdílem. Kontrakt operaci je označena úroveň ochrany, což naznačuje, že zprávy musí být podepsat a zašifrovat.  

```csharp
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 Aby se zajistilo, že je zpráva zabezpečené pomocí požadovaný token k identifikaci klienta a služby, souboru App.config obsahuje přihlašovací údaje.  
  
 Konfigurace klienta Určuje certifikát služby k ověřování. Jeho LocalMachine úložiště jako důvěryhodné úložiště používá moct spolehnout na platnosti služby. Určuje také klientský certifikát, který je připojen se zprávou pro ověřování služby klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"   
                binding="netMsmqBinding"   
                bindingConfiguration="messageSecurityBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"  
                behaviorConfiguration="ClientCertificateBehavior" />  
    </client>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate"/>  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 Všimněte si, že režim zabezpečení je nastaven na zprávu a ClientCredentialType nastavena na certifikát.  
  
 Konfigurace služby obsahuje chování služby, který určuje pověření služby, které se používají, když klient se ověří službu. Název subjektu certifikátu serveru je zadán v `findValue` atribut [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
          behaviorConfiguration="PurchaseOrderServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="messageSecurityBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="PurchaseOrderServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!--   
               The serviceCredentials behavior allows one to define a service certificate.  
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
               This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
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
  
</configuration>  
```  
  
 Ukázka ukazuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:  
  
```csharp
// Service class which implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    private string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  //…  
}  
```
  
 Při spuštění kódu služby zobrazí identifikaci klienta. Následuje příklad výstupu z kódu služby:  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C  
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
## <a name="comments"></a>Komentáře  
  
-   Vytvoření certifikátu klienta.  
  
     Následující řádek v dávkovém souboru, vytvoří certifikát klienta. Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili. Certifikát je uložen v `My` uložit na `CurrentUser` umístění úložiště.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalace klientského certifikátu do úložiště důvěryhodných certifikátů serveru.  
  
     Následující řádek v kopie souborů batch certifikát klienta do serveru TrustedPeople úložiště tak, aby server můžete provést příslušné důvěryhodnosti nebo ne důvěryhodnosti rozhodnutí. Pro certifikát nainstalovaný v úložišti TrustedPeople k být důvěryhodný [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, režim ověření certifikátu klienta musí být nastavená na `PeerOrChainTrust` nebo `PeerTrust` hodnotu. Viz předchozí ukázka konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Vytvoření certifikátu serveru.  
  
     Následující řádky z dávkového souboru Setup.bat vytvořit certifikát serveru, který se má použít:  
  
    ```bat  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Proměnná % název_serveru % Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Jestli dávkový soubor Instalační program se spustí s parametrem služby (například `setup.bat service`) název_serveru % obsahuje plně kvalifikovaný název domény počítače. V opačném případě je standardně nastavena na místního hostitele  
  
-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.  
  
     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob na klienta. Tento krok je povinný, protože certifikáty generované infrastrukturou Makecert.exe nejsou důvěryhodný implicitně systému klienta. Pokud již máte certifikát, který je integrován do důvěryhodného kořenového certifikátu klienta – například certifikát vystavený Microsoft – v tomto kroku naplnění úložišti certifikátů klienta s certifikátem serveru se nevyžaduje.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Pokud používáte jiný USA Anglickou edici systému Microsoft Windows, je nutné upravit Setup.bat a nahraďte název účtu "Služba NT AUTHORITY\NETWORK" vaše místní ekvivalent.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a>Viz také
