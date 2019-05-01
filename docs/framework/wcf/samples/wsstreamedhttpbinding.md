---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: de0c5683b081ecebf2168ffb5d6a2768fdd0a1fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007458"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Vzorek ukazuje, jak vytvořit vazbu, která je navržena pro podporu streamování scénáře, když se používá přenos pomocí protokolu HTTP.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Postup vytvoření a konfigurace nové standardní vazby jsou následující.  
  
1. Vytvořte novou vazbu standard  
  
     Standardní vazby Windows Communication Foundation (WCF) například basicHttpBinding a netTcpBinding nakonfigurujte základní přenosy a zásobník kanálu pro zvláštní požadavky. V této ukázce `WSStreamedHttpBinding` nakonfiguruje kanál zásobníku podporovat datový proud. Ve výchozím nastavení WS-Security a spolehlivé zasílání zpráv nepřidají do zásobníku kanál vzhledem k tomu, že obě funkce nejsou podporovány streamování. Nová vazba je implementována ve třídě `WSStreamedHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Obsahuje následující elementy vazby: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Poskytuje třídy `CreateBindingElements()` metoda konfigurace výsledný zásobník vazbu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
2. Přidání podpory konfigurace  
  
     K vystavení přenosu prostřednictvím konfigurace implementuje vzorek dvě další třídy –`WSStreamedHttpBindingConfigurationElement` a `WSStreamedHttpBindingSection`. Třída `WSStreamedHttpBindingSection` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , která zveřejní `WSStreamedHttpBinding` k systému konfigurace WCF. Hromadné implementace se deleguje na `WSStreamedHttpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. Třída `WSStreamedHttpBindingConfigurationElement` má vlastnosti, které odpovídají vlastnosti `WSStreamedHttpBinding`a funkce pro každý prvek konfigurace mapování na vazbu.  
  
     Zaregistrujte obslužné rutiny systém konfigurace, přidáním následujícího oddílu do konfiguračního souboru služby.  
  
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
  
     Obslužná rutina může pak odkazovat z konfiguračního oddílu serviceModel.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli kroky uvedené v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Spusťte ukázku v konfiguraci mezi počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6. Když v okně klienta se zobrazí, zadejte "Ukázka.txt". Měli byste najít "kopírování z ukázka.txt" ve vašem adresáři.  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Ukázka WSStreamedHttpBinding služby  
 Ukázka služby, který používá `WSStreamedHttpBinding` je umístěný v podadresáři služby. Provádění `OperationContract` používá `MemoryStream` nejdřív načíst všechna data z příchozího datového proudu před vrácením `MemoryStream`. Ukázková služba je hostována Internetové informační služby (IIS).  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>Ukázka WSStreamedHttpBinding klienta  
 Klient, který se používá k interakci s použitím služby `WSStreamedHttpBinding` je umístěný v podadresáři klienta. Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, výstrahu zabezpečení se zobrazí při pokusu o přístup k adresu HTTPS v prohlížeči, jako https://localhost/servicemodelsamples/service.svc. Povolit klienta WCF pro práci s testovací certifikát na místě, byla přidána další kód klienta pro potlačení výstrahy zabezpečení. Při použití certifikátů produkčního prostředí, kód a související třídy nejsou nutné.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
