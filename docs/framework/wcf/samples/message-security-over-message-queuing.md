---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 9e9067c38d86bb74c569b6d648d84c7c9ff6fac6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770786"
---
# <a name="message-security-over-message-queuing"></a>Zabezpečení zprávy pomocí služby Řízení front zpráv
Tento příklad ukazuje, jak implementovat aplikaci, která používá WS-Security x.509 v3 s ověřováním pomocí certifikátu klienta a vyžaduje ověření serveru pomocí služby MSMQ na server certifikát x.509 v3. Zpráva, že zabezpečení je někdy další žádoucí, ujistěte se, že zprávy v úložišti služby MSMQ zůstanou šifrovaná a aplikací můžete provést vlastní ověřování zprávy.

 Tato ukázka je založena na [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Zprávy jsou zašifrovaná a podepsaná.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna první, zkontroluje se tak, aby byl do fronty k dispozici. Pokud fronta neexistuje, služba ho vytvoří. Můžete spustit služba nejdřív vytvořte frontu nebo můžete vytvořit prostřednictvím Správce fronty MSMQ. Postupujte podle těchto kroků můžete vytvořit frontu Windows 2008.

    1.  Otevřete správce serveru v sadě Visual Studio 2012.

    2.  Rozbalte **funkce** kartu.

    3.  Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **nový**, **soukromou frontu**.

    4.  Zkontrolujte, **transakční** pole.

    5.  Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači

1. Ujistěte se, že cesta obsahuje složku obsahující Makecert.exe a FindPrivateKey.exe.

2. Spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.

    > [!NOTE]
    >  Ujistěte se odebrat certifikáty spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
3. Spusťte Service.exe z \service\bin.  
  
4. Spusťte Client.exe z \client\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
5. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1. Zkopírujte soubory Setup.bat Cleanup.bat a ImportClientCert.bat k počítači služby.  
  
2. Vytvoření adresáře v klientském počítači pro binární soubory klienta.  
  
3. Zkopírujte soubory programu klienta k adresáři klienta v klientském počítači. Také kopírovat soubory Setup.bat Cleanup.bat a ImportServiceCert.bat do klienta.  
  
4. Na serveru, spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
5. Upravit service.exe.config služby tak, aby odrážely nový název certifikátu (v `findValue` atribut v [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) která je stejná jako plně kvalifikovaný název domény počítače.  
  
6. Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
7. Na straně klienta, spouštění `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adresu služby. Proveďte to nahrazením localhost plně kvalifikovaný název domény serveru.  Musíte taky změnit název certifikátu služby být stejné jako plně kvalifikovaný název domény počítače, služby (v `findValue` atribut `defaultCertificate` prvek `serviceCertificate` pod `clientCredentials`).  
  
9. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
10. Na straně klienta, spouštění `ImportServiceCert.bat`. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
11. Na serveru, spusťte `ImportClientCert.bat`, to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
12. Na počítači se službou spusťte z příkazového řádku Service.exe.  
  
13. Na klientském počítači spusťte Client.exe z příkazového řádku. Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty na počítačích, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Požadavky
 Tato ukázka vyžaduje, že je služba MSMQ nainstalovaná a spuštěná.

## <a name="demonstrates"></a>Demonstruje
 Klient zašifruje pomocí veřejného klíče služby zprávu a podepíše zprávy pomocí vlastní certifikát. Čtení zprávy z fronty služby ověřování klientského certifikátu pomocí certifikátu v úložišti důvěryhodných osob. Potom zprávu dešifruje a odešle zprávu, která se operace služby.

 Protože zpráv Windows Communication Foundation (WCF) provádí jako datovou část, která je v textu zprávy služby MSMQ, zůstanou v úložišti služby MSMQ šifrovaného textu. To zajišťuje zabezpečení zprávy z nežádoucí zpřístupnění zprávy. Všimněte si, že MSMQ samotný není vědět, jestli je zašifrovaný zprávu, kterou je provádění.

 Vzorek ukazuje, jak vzájemného ověřování zprávy úroveň je možné pomocí služby MSMQ. Certifikáty jsou výměně out-of-band. To platí vždy s frontové aplikace služby a klient nemají být spuštěné ve stejnou dobu.

## <a name="description"></a>Popis
 Vzorový kód klienta a služby jsou stejné jako [nepodporuje transakce vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) ukázku s jedním z rozdílů. Kontrakt je opatřen poznámkou úroveň ochrany, což naznačuje, že zpráva musí podepsat a zašifrovat.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Aby bylo zajištěno, že je zpráva zabezpečena pomocí požadovaný token k identifikaci klienta a služby, App.config obsahuje přihlašovací údaje.

 Konfigurace klienta určuje služby certifikát k ověřování. Používá jeho úložiště LocalMachine jako důvěryhodné úložiště přináší setrvávání u platnosti této služby. Určuje také klientský certifikát, který je připojen se zprávou pro ověřování služby klienta.

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

 Všimněte si, že je režim zabezpečení nastavený na zprávu a nebyl typ ClientCredentialType nastaven na certifikátu.

 Konfigurace služby obsahuje chování služby, který určuje přihlašovací údaje služby, které se používají při ověřování klienta služby. Je zadaný název subjektu certifikátu serveru v `findValue` atribut [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 Ukázka demonstruje řídící ověřování pomocí konfigurace a jak získat identity volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:

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

 Při spuštění kódu služby zobrazí identifikaci klienta. Tady je ukázkový výstup z kódu služby:

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

-   Vytváří se certifikát klienta.

     Následující řádek v dávkovém souboru vytvoří certifikát klienta. Zadaný název klienta se používá v názvu subjektu certifikátu vytvořili. Certifikát je uložen v `My` ukládat na `CurrentUser` umístění úložiště.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   Instalaci klientského certifikátu do úložiště důvěryhodných certifikátů serveru.

     Následující řádek v souboru kopie služby batch klientský certifikát do serveru TrustedPeople uložit tak, aby na serveru můžete provádět odpovídající vztah důvěryhodnosti nebo rozhodnutí o důvěryhodnosti č. Pro certifikát nainstalován v úložišti TrustedPeople pro důvěryhodného službou Windows Communication Foundation (WCF), režim ověřování certifikátu klienta musí být nastavena na `PeerOrChainTrust` nebo `PeerTrust` hodnotu. Viz předchozí ukázka konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

-   Vytváří se certifikát serveru.

     Následující řádky z dávkový soubor Setup.bat vytvořte certifikát serveru, který se má použít:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % Proměnná % název_serveru Určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud instalační dávkový soubor se spustí s parametrem služby (jako je třeba `setup.bat service`) název_serveru % obsahuje název plně kvalifikované domény počítače. Jinak je výchozí hodnotou na místního hostitele

-   Instalace certifikátu serveru do úložiště důvěryhodných certifikátů klienta.

     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je nutný, protože certifikáty generované infrastrukturou Makecert.exe implicitně nedůvěřuje systému klienta. Pokud už máte certifikát, který je integrován důvěryhodného kořenového certifikátu klienta, například certifikát vydaný společností Microsoft – naplnění úložiště certifikátů klienta pomocí certifikátu serveru v tomto kroku se nevyžaduje.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Pokud používáte mimo USA Anglickou verzi Microsoft Windows, je nutné pomocí úpravy Setup.bat soubor a nahradit místní ekvivalent názvu účtu "NT AUTHORITY\NETWORK SERVICE".

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
