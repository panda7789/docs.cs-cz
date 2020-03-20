---
title: Zabezpečení zprávy pomocí služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144432"
---
# <a name="message-security-over-message-queuing"></a>Zabezpečení zprávy pomocí služby Řízení front zpráv
Tato ukázka ukazuje, jak implementovat aplikaci, která používá WS-Security s ověřováním certifikátu X.509v3 pro klienta a vyžaduje ověření serveru pomocí certifikátu X.509v3 serveru přes službu MSMQ. Zabezpečení zpráv je někdy více žádoucí zajistit, aby zprávy v úložišti služby MSMQ zůstat šifrované a aplikace může provádět vlastní ověřování zprávy.

 Tato ukázka je založena na [transacted MSMQ binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku. Zprávy jsou zašifrovány a podepsány.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud je služba spuštěna jako první, zkontroluje, zda je fronta k dispozici. Pokud fronta není k dispozici, služba ji vytvoří. Nejprve můžete spustit službu a vytvořit frontu, nebo ji můžete vytvořit pomocí Správce front služby MSMQ. Vytvořenífronty v systému Windows 2008 postupujte takto.

    1. Otevřete Správce serveru v sadě Visual Studio 2012.

    2. Rozbalte kartu **Funkce.**

    3. Klepněte pravým tlačítkem myši na **položku Fronty soukromých zpráv**a vyberte příkaz **Nová**, **Soukromá fronta**.

    4. Zaškrtněte políčko **Transakční** transakce.

    5. Zadejte `ServiceModelSamplesTransacted` jako název nové fronty.

3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači

1. Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe a FindPrivateKey.exe.

2. Spusťte soubor Setup.bat z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky.

    > [!NOTE]
    > Ujistěte se, že odeberete certifikáty spuštěním souboru Cleanup.bat po dokončení ukázky. Jiné ukázky zabezpečení používají stejné certifikáty.  
  
3. Spusťte soubor Service.exe z \service\bin.  
  
4. Spusťte soubor Client.exe z \client\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
5. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích  
  
1. Zkopírujte soubory Setup.bat, Cleanup.bat a ImportClientCert.bat do servisního počítače.  
  
2. Vytvořte v klientském počítači adresář pro binární soubory klienta.  
  
3. Zkopírujte soubory klientských programů do klientského adresáře v klientském počítači. Zkopírujte také soubory Setup.bat, Cleanup.bat a ImportServiceCert.bat klientovi.  
  
4. Na serveru spusťte . `setup.bat service` Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
5. Upravte soubor service.exe.config služby tak, aby `findValue` odrážel nový název certifikátu (v atributu [ \<v serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)který je stejný jako plně kvalifikovaný název domény počítače.  
  
6. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
7. Na straně klienta spusťte `setup.bat client`. Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem client.com a exportuje klientský certifikát do souboru s názvem Client.cer.  
  
8. V souboru Client.exe.config v klientském počítači změňte hodnotu adresy koncového bodu tak, aby odpovídala nové adrese vaší služby. To provést nahrazením localhost plně kvalifikovaný název domény serveru.  Je také nutné změnit název certifikátu služby tak, aby byl stejný jako plně `findValue` kvalifikovaný `defaultCertificate` název `serviceCertificate` domény `clientCredentials`počítače služby (v atributu v prvku under ).  
  
9. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
10. Na straně klienta spusťte `ImportServiceCert.bat`. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
11. Na serveru, `ImportClientCert.bat`spustit , To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.  
  
12. V servisním počítači spusťte program Service.exe z příkazového řádku.  
  
13. V klientském počítači spusťte soubor Client.exe z příkazového řádku. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.  
  
    > [!NOTE]
    > Tento skript neodebere certifikáty služeb v klientovi při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty v počítačích, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` použijte následující `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`příkaz: Například: .

## <a name="requirements"></a>Požadavky
 Tato ukázka vyžaduje, aby byla služba MSMQ nainstalována a spuštěna.

## <a name="demonstrates"></a>Demonstruje
 Klient zašifruje zprávu pomocí veřejného klíče služby a podepíše zprávu pomocí vlastního certifikátu. Služba, která čte zprávu z fronty, ověří klientský certifikát s certifikátem v úložišti důvěryhodných osob. Potom dešifruje zprávu a odešle zprávu do operace služby.

 Vzhledem k tomu, že zpráva WCF (Windows Communication Foundation) je přenášena jako datová část v těle zprávy služby MSMQ, tělo zůstane šifrované v úložišti služby MSMQ. Tím se zpráva zabezpečí před nežádoucím zveřejněním zprávy. Všimněte si, že služba MSMQ sama o sobě neví, zda je zpráva, kterou nese, šifrována.

 Ukázka ukazuje, jak lze s msmq používat vzájemné ověřování na úrovni zprávy. Certifikáty jsou vyměňovány mimo pásmo. To je vždy případ s aplikací ve frontě, protože služba a klient nemusí být spuštěna současně.

## <a name="description"></a>Popis
 Ukázkový kód klienta a služby jsou stejné jako [transacted msmq vazby](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) vzorku s jedním rozdílem. Smlouva o operaci je anotována s úrovní ochrany, což naznačuje, že zpráva musí být podepsána a zašifrována.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Chcete-li zajistit, že zpráva je zabezpečena pomocí požadovaného tokenu k identifikaci služby a klienta, App.config obsahuje informace o pověření.

 Konfigurace klienta určuje certifikát služby pro ověření služby. Používá úložiště LocalMachine jako důvěryhodné úložiště k spoléhání se na platnost služby. Určuje také klientský certifikát, který je připojen ke zprávě pro ověřování služby klienta.

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

 Všimněte si, že režim zabezpečení je nastaven na Message a ClientCredentialType je nastavena na certifikát.

 Konfigurace služby zahrnuje chování služby, které určuje pověření služby, které se používají při ověření služby klientem. Název subjektu certifikátu serveru `findValue` je uveden v atributu v [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 Při spuštění kód služby zobrazí identifikaci klienta. Následuje ukázkový výstup z kódu služby:

```console
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

- Vytvoření klientského certifikátu.

     Následující řádek v dávkovém souboru vytvoří klientský certifikát. Zadaný název klienta se používá v názvu subjektu vytvořeného certifikátu. Certifikát je uložen `My` v `CurrentUser` úložišti v umístění úložiště.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalace klientského certifikátu do důvěryhodného úložiště certifikátů serveru.

     Následující řádek v dávkovém souboru zkopíruje klientský certifikát do úložiště TrustedPeople serveru, aby server mohl činit příslušná rozhodnutí o důvěryhodnosti nebo nedůvěryhodnosti. Aby byl certifikát nainstalovaný v úložišti TrustedPeople důvěryhodný službou WCF (Windows Communication Foundation), `PeerOrChainTrust` `PeerTrust` musí být režim ověření klientského certifikátu nastaven na hodnotu nebo hodnotu. Podívejte se na předchozí ukázku konfigurace služby, kde se dozvíte, jak to lze provést pomocí konfiguračního souboru.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Vytvoření certifikátu serveru.

     Následující řádky z dávkového souboru Setup.bat vytvářejí certifikát serveru, který má být použit:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Proměnná %SERVER_NAME% určuje název serveru. Certifikát je uložen v úložišti LocalMachine. Pokud je dávkový soubor instalace spuštěn s argumentem služby `setup.bat service`(například) %SERVER_NAME% obsahuje plně kvalifikovaný název domény počítače. V opačném případě je výchozí localhost

- Instalace certifikátu serveru do důvěryhodného úložiště certifikátů klienta.

     Následující řádek zkopíruje certifikát serveru do úložiště důvěryhodných osob klienta. Tento krok je vyžadován, protože certifikáty generované programem Makecert.exe nejsou klientským systémem implicitně důvěryhodné. Pokud již máte certifikát, který je zakořeněný v důvěryhodném kořenovém certifikátu klienta – například certifikát emitovaný společností Microsoft – tento krok naplnění úložiště klientských certifikátů certifikátem certifikátem serveru není vyžadován.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Pokud používáte edici systému Microsoft Windows, která není v USA, je nutné upravit soubor Setup.bat a nahradit název účtu NT AUTHORITY\NETWORK SERVICE místním ekvivalentem.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
