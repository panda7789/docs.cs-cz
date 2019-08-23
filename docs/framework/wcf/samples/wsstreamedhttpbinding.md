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
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="3f826-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f826-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="3f826-103">Ukázka ukazuje, jak vytvořit vazbu, která je navržena pro podporu scénářů streamování při použití přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3f826-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f826-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3f826-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f826-105">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="3f826-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f826-106">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3f826-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3f826-107">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="3f826-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f826-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3f826-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="3f826-109">Následujícím postupem vytvoříte a nakonfigurujete novou standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3f826-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1. <span data-ttu-id="3f826-110">Vytvoří novou standardní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3f826-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="3f826-111">Standardní vazby v Windows Communication Foundation (WCF), jako je basicHttpBinding a netTcpBinding, konfigurují základní přenosy a zásobník kanálů pro konkrétní požadavky.</span><span class="sxs-lookup"><span data-stu-id="3f826-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="3f826-112">V této ukázce `WSStreamedHttpBinding` nakonfiguruje zásobník kanálů pro podporu streamování.</span><span class="sxs-lookup"><span data-stu-id="3f826-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="3f826-113">Ve výchozím nastavení se do zásobníku kanálů nepřidal protokol WS-Security a spolehlivé zasílání zpráv, protože datové proudy nepodporují obě funkce.</span><span class="sxs-lookup"><span data-stu-id="3f826-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="3f826-114">Nová vazba je implementována ve třídě `WSStreamedHttpBinding` , která je odvozena z. <xref:System.ServiceModel.Channels.Binding></span><span class="sxs-lookup"><span data-stu-id="3f826-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="3f826-115"><xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>Obsahuje následující prvky vazby:,, a<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. `WSStreamedHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="3f826-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="3f826-116">Třída poskytuje `CreateBindingElements()` metodu pro konfiguraci výsledného zásobníku vazby, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3f826-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
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
  
2. <span data-ttu-id="3f826-117">Přidat podporu konfigurace</span><span class="sxs-lookup"><span data-stu-id="3f826-117">Add configuration support</span></span>  
  
     <span data-ttu-id="3f826-118">K zveřejnění přenosu prostřednictvím konfigurace ukázka implementuje dvě další třídy –`WSStreamedHttpBindingConfigurationElement` a. `WSStreamedHttpBindingSection`</span><span class="sxs-lookup"><span data-stu-id="3f826-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="3f826-119">Třída `WSStreamedHttpBindingSection` `WSStreamedHttpBinding` je třída, která zpřístupňuje konfiguračnímu systému služby WCF. <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602></span><span class="sxs-lookup"><span data-stu-id="3f826-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="3f826-120">Hromadná implementace je delegována na `WSStreamedHttpBindingConfigurationElement`, což je odvozeno z. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="3f826-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="3f826-121">Třída `WSStreamedHttpBindingConfigurationElement` obsahuje vlastnosti, které odpovídají `WSStreamedHttpBinding`vlastnostem a funkce k namapování jednotlivých elementů konfigurace na vazbu.</span><span class="sxs-lookup"><span data-stu-id="3f826-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="3f826-122">Zaregistrujte obslužnou rutinu pomocí konfiguračního systému přidáním následujícího oddílu do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="3f826-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
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
  
     <span data-ttu-id="3f826-123">Na obslužnou rutinu se pak dá odkazovat z konfiguračního oddílu serviceModel.</span><span class="sxs-lookup"><span data-stu-id="3f826-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f826-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3f826-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3f826-125">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="3f826-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="3f826-126">Ujistěte se, že jste provedli kroky uvedené v [postupu nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="3f826-127">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="3f826-128">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="3f826-129">Pokud chcete ukázku spustit v konfiguraci více počítačů, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6. <span data-ttu-id="3f826-130">Po zobrazení okna klienta zadejte "Sample. txt".</span><span class="sxs-lookup"><span data-stu-id="3f826-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="3f826-131">Ve vašem adresáři byste měli najít kopii Sample. txt.</span><span class="sxs-lookup"><span data-stu-id="3f826-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="3f826-132">Ukázková služba WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f826-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="3f826-133">Ukázková služba, kterou `WSStreamedHttpBinding` používá, se nachází v podadresáři služby.</span><span class="sxs-lookup"><span data-stu-id="3f826-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="3f826-134">Implementace aplikace `OperationContract` `MemoryStream` používá pro první načtení všech dat z `MemoryStream`příchozího datového proudu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="3f826-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="3f826-135">Ukázková služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="3f826-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="3f826-136">Vzorový klient WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3f826-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="3f826-137">Klient, který se používá pro interakci se službou `WSStreamedHttpBinding` , je umístěn v podadresáři klienta.</span><span class="sxs-lookup"><span data-stu-id="3f826-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="3f826-138">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje MakeCert. exe, výstraha zabezpečení se zobrazí při pokusu o přístup k adrese HTTPS v https://localhost/servicemodelsamples/service.svc prohlížeči, jako je například.</span><span class="sxs-lookup"><span data-stu-id="3f826-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="3f826-139">Aby mohl klient služby WCF pracovat s testovacím certifikátem, byl do klienta přidán nějaký další kód, který výstrahu zabezpečení potlačí.</span><span class="sxs-lookup"><span data-stu-id="3f826-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="3f826-140">Kód a doprovodná třída nejsou při použití produkčních certifikátů vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="3f826-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
