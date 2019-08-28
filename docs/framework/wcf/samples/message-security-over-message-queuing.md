---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 039ec21296392321fec40df2cae7383ccb3be6ea
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039345"
---
# <a name="message-security-over-message-queuing"></a>Zabezpečení zprávy pomocí služby Řízení front zpráv
Tato ukázka předvádí, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátů X. 509 v3 pro klienta, a vyžaduje ověření serveru pomocí certifikátu X. 509 v3 serveru přes službu MSMQ. Zabezpečení zpráv je někdy žádoucí, aby zprávy v úložišti služby MSMQ zůstaly šifrované a aplikace může provádět vlastní ověřování zprávy.

 Tato ukázka je založená na ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . Zprávy jsou zašifrovány a podepsány.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není přítomna, služba ji vytvoří. Službu můžete nejdřív spustit, abyste mohli vytvořit frontu, nebo ji můžete vytvořit pomocí Správce fronty MSMQ. Pomocí těchto kroků vytvořte ve Windows 2008 frontu.

    1. Otevřete Správce serveru v aplikaci Visual Studio 2012.

    2. Rozbalte kartu **funkce** .

    3. Klikněte pravým tlačítkem na **fronty soukromých zpráv**a vyberte **Nový**, **soukromá fronta**.

    4. Zaškrtněte políčko **transakční** .

    5. Jako `ServiceModelSamplesTransacted` název nové fronty zadejte.

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači

1. Ujistěte se, že cesta zahrnuje složku, která obsahuje nástroj Makecert. exe a FindPrivateKey. exe.

2. Z ukázkové instalační složky spusťte Setup. bat. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.

    > [!NOTE]
    > Po dokončení ukázky se ujistěte, že jste odebrali certifikáty spuštěním souboru Cleanup. bat. Další ukázky zabezpečení používají stejné certifikáty.  
  
3. Spustit Service. exe z \service\bin.  
  
4. Spustit soubor Client. exe z \client\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
5. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Zkopírujte soubory Setup. bat, Cleanup. bat a ImportClientCert. bat do počítače služby.  
  
2. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
3. Zkopírujte soubory klientských programů do adresáře klienta v klientském počítači. Zkopírujte také do klienta soubory Setup. bat, Cleanup. bat a ImportServiceCert. bat.  
  
4. Na serveru spusťte `setup.bat service`. Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
5. Upravte Service. exe. config služby, aby odrážela nový název certifikátu (v `findValue` atributu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), který je stejný jako plně kvalifikovaný název domény počítače.  
  
6. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
7. Na straně klienta spusťte `setup.bat client`. Při `setup.bat` spuštění`client` s argumentem se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.  
  
8. V souboru Client. exe. config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. Provedete to tak, že nahradíte localhost názvem domény na plně kvalifikovaném názvu domény serveru.  Také je nutné změnit název certifikátu služby tak, aby byl stejný jako plně kvalifikovaný název domény počítače služby ( `findValue` v atributu `defaultCertificate` v elementu `serviceCertificate` v části `clientCredentials`).  
  
9. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
10. Na straně klienta spusťte `ImportServiceCert.bat`. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
11. Na tomto serveru `ImportClientCert.bat`tento příkaz importuje klientský certifikát ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
12. Na počítači služby spusťte z příkazového řádku Service. exe.  
  
13. V klientském počítači spusťte z příkazového řádku soubor Client. exe. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Požadavky
 Tato ukázka vyžaduje, aby byla služba MSMQ nainstalovaná a spuštěná.

## <a name="demonstrates"></a>Demonstruje
 Klient šifruje zprávu pomocí veřejného klíče služby a podepíše zprávu pomocí vlastního certifikátu. Služba, která čte zprávu z fronty ověřuje certifikát klienta s certifikátem v úložišti důvěryhodných osob. Poté dešifruje zprávu a odešle zprávu do operace služby.

 Vzhledem k tomu, že se zpráva Windows Communication Foundation (WCF) přenese jako datová část v těle zprávy služby MSMQ, text zůstane zašifrovaný v úložišti MSMQ. Tím se zpráva zabezpečí ze nechtěného zveřejnění zprávy. Mějte na paměti, že samotný služba MSMQ nezáleží na tom, zda je zpráva, kterou přepravuje, šifrovaná.

 Ukázka předvádí, jak se vzájemné ověřování na úrovni zpráv dá použít u služby MSMQ. Certifikáty se vyměňují mimo IP síť. To je vždycky u aplikace zařazené do fronty, protože služba a klient nemusí být ve stejnou dobu spuštěný.

## <a name="description"></a>Popis
 Ukázkový klient a kód služby jsou stejné jako v transakční ukázce s [transakčními vazbami služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) s jedním rozdílem. Kontrakt operace je opatřen poznámkou s úrovní ochrany, která naznačuje, že musí být zpráva podepsána a zašifrována.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Aby bylo zajištěno, že je zpráva zabezpečená pomocí požadovaného tokenu k identifikaci služby a klienta, obsahuje soubor App. config informace o přihlašovacích údajích.

 Konfigurace klienta Určuje certifikát služby pro ověření služby. Používá své LocalMachine úložiště jako důvěryhodné úložiště k tomu, aby se spoléhala na platnost služby. Určuje také klientský certifikát, který je připojen ke zprávě pro ověření služby klienta.

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

 Všimněte si, že režim zabezpečení je nastavený na Message a ClientCredentialType je nastavené na certifikát.

 Konfigurace služby zahrnuje chování služby, které určuje přihlašovací údaje služby, které se používají, když klient ověřuje službu. Název subjektu certifikátu serveru je zadán v `findValue` atributu [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 Ukázka znázorňuje řízení ověřování pomocí konfigurace a jak získat identitu volajícího z kontextu zabezpečení, jak je znázorněno v následujícím ukázkovém kódu:

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

 Při spuštění zobrazí kód služby identifikaci klienta. Následuje ukázkový výstup z kódu služby:

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

- Vytváří se klientský certifikát.

     Následující řádek v dávkovém souboru vytvoří klientský certifikát. Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu. Certifikát je uložený v `My` úložišti `CurrentUser` v umístění úložiště.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Probíhá instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.

     Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl učinit příslušná rozhodnutí týkající se vztahu důvěryhodnosti nebo bez vztahu důvěryhodnosti. Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou Windows Communication Foundation (WCF), musí být režim ověřování klientského certifikátu nastaven na `PeerOrChainTrust` hodnotu nebo. `PeerTrust` V předchozí ukázce konfigurace služby se dozvíte, jak to lze provést pomocí konfiguračního souboru.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Vytváří se certifikát serveru.

     Následující řádky z dávkového souboru Setup. bat vytvoří certifikát serveru, který se má použít:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Proměnná% Název_serveru% Určuje název serveru. Certifikát je uložený v úložišti LocalMachine. Pokud je instalační dávkový soubor spuštěn s argumentem služby (například, `setup.bat service`),% název_serveru% obsahuje plně kvalifikovaný název domény počítače. V opačném případě se použije jako localhost

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

     Následující řádek zkopíruje certifikát serveru do úložiště Důvěryhodné osoby z klienta. Tento krok je povinný, protože certifikáty vygenerované pomocí nástroje MakeCert. exe nejsou implicitně důvěryhodné klientským systémem. Pokud už máte certifikát, který je rootem v důvěryhodném kořenovém certifikátu klienta – například certifikát vydaný společností Microsoft – tento krok naplnění úložiště certifikátů klienta s certifikátem serveru není vyžadován.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Pokud používáte jinou než U. S. Anglická edice Microsoft Windows je potřeba upravit soubor Setup. bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE svým regionálním ekvivalentem.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
