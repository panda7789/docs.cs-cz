---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: de0c5683b081ecebf2168ffb5d6a2768fdd0a1fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975985"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="9ceae-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9ceae-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="9ceae-103">Vzorek ukazuje, jak vytvořit vazbu, která je navržena pro podporu streamování scénáře, když se používá přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9ceae-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ceae-104">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9ceae-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ceae-105">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9ceae-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ceae-106">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9ceae-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ceae-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9ceae-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ceae-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9ceae-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="9ceae-109">Postup vytvoření a konfigurace nové standardní vazby jsou následující.</span><span class="sxs-lookup"><span data-stu-id="9ceae-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1. <span data-ttu-id="9ceae-110">Vytvořte novou vazbu standard</span><span class="sxs-lookup"><span data-stu-id="9ceae-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="9ceae-111">Standardní vazby Windows Communication Foundation (WCF) například basicHttpBinding a netTcpBinding nakonfigurujte základní přenosy a zásobník kanálu pro zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="9ceae-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="9ceae-112">V této ukázce `WSStreamedHttpBinding` nakonfiguruje kanál zásobníku podporovat datový proud.</span><span class="sxs-lookup"><span data-stu-id="9ceae-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="9ceae-113">Ve výchozím nastavení WS-Security a spolehlivé zasílání zpráv nepřidají do zásobníku kanál vzhledem k tomu, že obě funkce nejsou podporovány streamování.</span><span class="sxs-lookup"><span data-stu-id="9ceae-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="9ceae-114">Nová vazba je implementována ve třídě `WSStreamedHttpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="9ceae-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="9ceae-115">`WSStreamedHttpBinding` Obsahuje následující elementy vazby: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="9ceae-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="9ceae-116">Poskytuje třídy `CreateBindingElements()` metoda konfigurace výsledný zásobník vazbu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="9ceae-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
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
  
2. <span data-ttu-id="9ceae-117">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="9ceae-117">Add configuration support</span></span>  
  
     <span data-ttu-id="9ceae-118">K vystavení přenosu prostřednictvím konfigurace implementuje vzorek dvě další třídy –`WSStreamedHttpBindingConfigurationElement` a `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="9ceae-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="9ceae-119">Třída `WSStreamedHttpBindingSection` je <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> , která zveřejní `WSStreamedHttpBinding` k systému konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="9ceae-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="9ceae-120">Hromadné implementace se deleguje na `WSStreamedHttpBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="9ceae-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="9ceae-121">Třída `WSStreamedHttpBindingConfigurationElement` má vlastnosti, které odpovídají vlastnosti `WSStreamedHttpBinding`a funkce pro každý prvek konfigurace mapování na vazbu.</span><span class="sxs-lookup"><span data-stu-id="9ceae-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="9ceae-122">Zaregistrujte obslužné rutiny systém konfigurace, přidáním následujícího oddílu do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="9ceae-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
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
  
     <span data-ttu-id="9ceae-123">Obslužná rutina může pak odkazovat z konfiguračního oddílu serviceModel.</span><span class="sxs-lookup"><span data-stu-id="9ceae-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ceae-124">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9ceae-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9ceae-125">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="9ceae-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="9ceae-126">Ujistěte se, že jste provedli kroky uvedené v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ceae-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="9ceae-127">Ujistěte se, že jste provedli [pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="9ceae-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="9ceae-128">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ceae-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="9ceae-129">Spusťte ukázku v konfiguraci mezi počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ceae-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6. <span data-ttu-id="9ceae-130">Když v okně klienta se zobrazí, zadejte "Ukázka.txt".</span><span class="sxs-lookup"><span data-stu-id="9ceae-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="9ceae-131">Měli byste najít "kopírování z ukázka.txt" ve vašem adresáři.</span><span class="sxs-lookup"><span data-stu-id="9ceae-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="9ceae-132">Ukázka WSStreamedHttpBinding služby</span><span class="sxs-lookup"><span data-stu-id="9ceae-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="9ceae-133">Ukázka služby, který používá `WSStreamedHttpBinding` je umístěný v podadresáři služby.</span><span class="sxs-lookup"><span data-stu-id="9ceae-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="9ceae-134">Provádění `OperationContract` používá `MemoryStream` nejdřív načíst všechna data z příchozího datového proudu před vrácením `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="9ceae-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="9ceae-135">Ukázková služba je hostována Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="9ceae-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="9ceae-136">Ukázka WSStreamedHttpBinding klienta</span><span class="sxs-lookup"><span data-stu-id="9ceae-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="9ceae-137">Klient, který se používá k interakci s použitím služby `WSStreamedHttpBinding` je umístěný v podadresáři klienta.</span><span class="sxs-lookup"><span data-stu-id="9ceae-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="9ceae-138">Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s Makecert.exe, výstrahu zabezpečení se zobrazí při pokusu o přístup k adresu HTTPS v prohlížeči, jako https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="9ceae-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="9ceae-139">Povolit klienta WCF pro práci s testovací certifikát na místě, byla přidána další kód klienta pro potlačení výstrahy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9ceae-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="9ceae-140">Při použití certifikátů produkčního prostředí, kód a související třídy nejsou nutné.</span><span class="sxs-lookup"><span data-stu-id="9ceae-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
