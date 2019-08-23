---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: aad89924b371d9d5032f32f29aac83fae445f253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959782"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Ukázka ukazuje, jak vytvořit vazbu, která je navržena pro podporu scénářů streamování při použití přenosu HTTP.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Následujícím postupem vytvoříte a nakonfigurujete novou standardní vazbu.  
  
1. Vytvoří novou standardní vazbu.  
  
     Standardní vazby v Windows Communication Foundation (WCF), jako je basicHttpBinding a netTcpBinding, konfigurují základní přenosy a zásobník kanálů pro konkrétní požadavky. V této ukázce `WSStreamedHttpBinding` nakonfiguruje zásobník kanálů pro podporu streamování. Ve výchozím nastavení se do zásobníku kanálů nepřidal protokol WS-Security a spolehlivé zasílání zpráv, protože datové proudy nepodporují obě funkce. Nová vazba je implementována ve třídě `WSStreamedHttpBinding` , která je odvozena z. <xref:System.ServiceModel.Channels.Binding> <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>Obsahuje následující prvky vazby:,, a<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. `WSStreamedHttpBinding` Třída poskytuje `CreateBindingElements()` metodu pro konfiguraci výsledného zásobníku vazby, jak je znázorněno v následujícím ukázkovém kódu.  
  
    ```  
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
  
     K zveřejnění přenosu prostřednictvím konfigurace ukázka implementuje dvě další třídy –`WSStreamedHttpBindingConfigurationElement` a. `WSStreamedHttpBindingSection` Třída `WSStreamedHttpBindingSection` `WSStreamedHttpBinding` je třída, která zpřístupňuje konfiguračnímu systému služby WCF. <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> Hromadná implementace je delegována na `WSStreamedHttpBindingConfigurationElement`, což je odvozeno z. <xref:System.ServiceModel.Configuration.StandardBindingElement> Třída `WSStreamedHttpBindingConfigurationElement` obsahuje vlastnosti, které odpovídají `WSStreamedHttpBinding`vlastnostem a funkce k namapování jednotlivých elementů konfigurace na vazbu.  
  
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
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli kroky uvedené v [postupu nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Pokud chcete ukázku spustit v konfiguraci více počítačů, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6. Po zobrazení okna klienta zadejte "Sample. txt". Ve vašem adresáři byste měli najít kopii Sample. txt.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Ukázková služba WSStreamedHttpBinding  
 Ukázková služba, kterou `WSStreamedHttpBinding` používá, se nachází v podadresáři služby. Implementace aplikace `OperationContract` `MemoryStream` používá pro první načtení všech dat z `MemoryStream`příchozího datového proudu před vrácením. Ukázková služba je hostována službou Internetová informační služba (IIS).  
  
```  
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
 Klient, který se používá pro interakci se službou `WSStreamedHttpBinding` , je umístěn v podadresáři klienta. Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, výstraha zabezpečení se zobrazí při pokusu o přístup k adrese HTTPS v https://localhost/servicemodelsamples/service.svc prohlížeči, jako je například. Aby mohl klient služby WCF pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód, který výstrahu zabezpečení potlačí. Kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
