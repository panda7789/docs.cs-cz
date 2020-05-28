---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 663b7921e4e8a66d9b905404bad00f613e2f04cc
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144653"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding

Ukázka ukazuje, jak vytvořit vazbu, která je navržena pro podporu scénářů streamování při použití přenosu HTTP.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 Následujícím postupem vytvoříte a nakonfigurujete novou standardní vazbu.

1. Vytvoří novou standardní vazbu.

    Standardní vazby v Windows Communication Foundation (WCF), jako je basicHttpBinding a netTcpBinding, konfigurují základní přenosy a zásobník kanálů pro konkrétní požadavky. V této ukázce `WSStreamedHttpBinding` nakonfiguruje zásobník kanálů pro podporu streamování. Ve výchozím nastavení se do zásobníku kanálů nepřidal protokol WS-Security a spolehlivé zasílání zpráv, protože datové proudy nepodporují obě funkce. Nová vazba je implementována ve třídě `WSStreamedHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> . `WSStreamedHttpBinding`Obsahuje následující prvky vazby: <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> , <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> . Třída poskytuje `CreateBindingElements()` metodu pro konfiguraci výsledného zásobníku vazby, jak je znázorněno v následujícím ukázkovém kódu.

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. Přidat podporu konfigurace

    K zveřejnění přenosu prostřednictvím konfigurace ukázka implementuje dvě další třídy – `WSStreamedHttpBindingConfigurationElement` a `WSStreamedHttpBindingSection` . Třída `WSStreamedHttpBindingSection` je třída <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , která zpřístupňuje `WSStreamedHttpBinding` konfiguračnímu systému služby WCF. Hromadná implementace je delegována na `WSStreamedHttpBindingConfigurationElement` , což je odvozeno z <xref:System.ServiceModel.Configuration.StandardBindingElement> . Třída `WSStreamedHttpBindingConfigurationElement` obsahuje vlastnosti, které odpovídají vlastnostem `WSStreamedHttpBinding` a funkce k namapování jednotlivých elementů konfigurace na vazbu.

    Zaregistrujte obslužnou rutinu pomocí konfiguračního systému přidáním následujícího oddílu do konfiguračního souboru služby.

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    Na obslužnou rutinu se pak dá odkazovat z konfiguračního oddílu serviceModel.

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli kroky uvedené v [postupu nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).

4. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Pokud chcete ukázku spustit v konfiguraci více počítačů, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

6. Po zobrazení okna klienta zadejte "Sample. txt". Ve vašem adresáři byste měli najít kopii Sample. txt.

## <a name="the-wsstreamedhttpbinding-sample-service"></a>Ukázková služba WSStreamedHttpBinding

Ukázková služba, kterou používá, `WSStreamedHttpBinding` se nachází v podadresáři služby. Implementace aplikace `OperationContract` používá `MemoryStream` pro první načtení všech dat z příchozího datového proudu před vrácením `MemoryStream` . Ukázková služba je hostována službou Internetová informační služba (IIS).

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a>Vzorový klient WSStreamedHttpBinding

Klient, který se používá pro interakci se službou, `WSStreamedHttpBinding` je umístěn v podadresáři klienta. Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, výstraha zabezpečení se zobrazí při pokusu o přístup k adrese HTTPS v prohlížeči, jako je například `https://localhost/servicemodelsamples/service.svc` . Aby mohl klient služby WCF pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód, který výstrahu zabezpečení potlačí. Kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
