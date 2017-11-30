---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8238ede6fd43cc5cca2df1f8c7f9162f9c4a1302
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
Ukázka ukazuje, jak vytvořit vazbu, která je určená pro podporu streamování scénářů, při použití přenosového protokolu HTTP.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 Takto vypadají kroky k vytvoření a konfiguraci nové standardní vazby.  
  
1.  Vytvořte novou vazbu standardní  
  
     Standardní vazeb v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , jako je basicHttpBinding a netTcpBinding nakonfigurovat základní přenosy a zásobníku kanálu pro zvláštní požadavky. V této ukázce `WSStreamedHttpBinding` nakonfiguruje kanál zásobníku pro podporu streamování. Ve výchozím nastavení, WS-zabezpečení a spolehlivé zasílání zpráv nebyly přidány do zásobníku kanál vzhledem k tomu, jak funkce nepodporuje vysílání datového proudu. Novou vazbu je implementována ve třídě `WSStreamedHttpBinding` která je odvozena od <xref:System.ServiceModel.Channels.Binding>. `WSStreamedHttpBinding` Obsahuje následující prvky vazby: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Poskytuje třídy `CreateBindingElements()` metoda konfigurace výsledný zásobník vazby, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
2.  Přidat podporu konfigurace  
  
     Ke zveřejnění přenos prostřednictvím konfigurace ukázku implementuje dva další třídy –`WSStreamedHttpBindingConfigurationElement` a `WSStreamedHttpBindingSection`. Třída `WSStreamedHttpBindingSection` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> která zveřejňuje `WSStreamedHttpBinding` k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurační systém. Hromadné implementace je delegovaný jako `WSStreamedHttpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. Třída `WSStreamedHttpBindingConfigurationElement` má vlastnosti, které odpovídají vlastnosti `WSStreamedHttpBinding`a funkce pro mapování každý prvek konfigurace pro vazbu.  
  
     Obslužná rutina se konfigurační systém zaregistrujte přidáním následující části do konfiguračního souboru služby.  
  
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
  
     Obslužná rutina může pak odkazovat z serviceModel konfigurační oddíl.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli kroky uvedené v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
4.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spustit ukázku v konfiguraci s počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
6.  Když v okně klienta se zobrazí, zadejte "Ukázka.txt". Ve vašem adresáři by měl zjistit "kopírování z ukázka.txt".  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>Ukázka WSStreamedHttpBinding služby  
 Ukázka službu, která používá `WSStreamedHttpBinding` se nachází v podadresáři služby. Implementace `OperationContract` používá `MemoryStream` nejdřív načíst všechna data z příchozího datového proudu před vrácením `MemoryStream`. Ukázka služba hostována Internetové informační služby (IIS).  
  
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
 Pro klienta, který se používá k interakci s používáním služby `WSStreamedHttpBinding` se nachází v podadresáři klienta. Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, zobrazí se výstraha zabezpečení při pokusu o přístup k adresou protokolu HTTPS v prohlížeči například https://localhost/servicemodelsamples/service.svc. Chcete-li povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pro práci s testovací certifikát na místě, některé další kód byl přidán do klienta pro potlačení výstrahy zabezpečení. Kód a doprovodné třídy nejsou vyžadovány, při použití provozní certifikáty.  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>Viz také
