---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990740"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="1fb40-102">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="1fb40-102">Custom Message Interceptor</span></span>
<span data-ttu-id="1fb40-103">Tento příklad ukazuje použití model rozšiřitelnosti kanálu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="1fb40-104">Konkrétně se ukazuje, jak implementovat vlastní prvek vazby, která vytváří objekty pro vytváření kanálů a moduly pro naslouchání kanálů aby se zachytily všechny příchozí a odchozí zprávy v určitém místě v zásobníku za běhu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="1fb40-105">Ukázka zahrnuje také klienta a serveru, které ukazují použití tyto vlastní objekty pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="1fb40-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="1fb40-106">V této ukázce jsou klient a služba konzoly programů (.exe).</span><span class="sxs-lookup"><span data-stu-id="1fb40-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="1fb40-107">Klient a služba, ujistěte se, jak použít společné knihovny (DLL), který obsahuje element vlastní vazby a jejích přidružených objektů za běhu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb40-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fb40-109">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="1fb40-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1fb40-110">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1fb40-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1fb40-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1fb40-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1fb40-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1fb40-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="1fb40-113">Ukázka popisuje doporučený postup pro vytváření vlastních vrstev kanálu ve Windows Communication Foundation (WCF), pomocí architektura kanálů a osvědčených postupů WCF.</span><span class="sxs-lookup"><span data-stu-id="1fb40-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="1fb40-114">Postup vytvoření vlastního kanálu vrstvami jsou následující:</span><span class="sxs-lookup"><span data-stu-id="1fb40-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="1fb40-115">Rozhodněte, které z tvarů kanálu objekt pro vytváření kanálů a modul pro naslouchání kanálu se podporují.</span><span class="sxs-lookup"><span data-stu-id="1fb40-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="1fb40-116">Vytvořte objekt pro vytváření kanálů a naslouchací proces kanálu, které podporují obrazcích kanálu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="1fb40-117">Přidejte prvek vazby, který přidá vlastní vrstvami kanál do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="1fb40-118">Přidání sekce rozšíření elementu vazby vystavit nový element vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="1fb40-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="1fb40-119">Kanál obrazce</span><span class="sxs-lookup"><span data-stu-id="1fb40-119">Channel Shapes</span></span>  
 <span data-ttu-id="1fb40-120">Prvním krokem při psaní vlastního kanálu vrstvami je rozhodnout, jaké tvary jsou požadovány pro kanál.</span><span class="sxs-lookup"><span data-stu-id="1fb40-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="1fb40-121">Pro naše inspektoru zpráva podporujeme žádný obrazec, který podporuje vrstvy pod nám (například pokud vrstvy pod nám můžete vytvářet <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, pak také zveřejňujeme <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="1fb40-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="1fb40-122">Objekt pro vytváření kanálů a Výroba naslouchací služby</span><span class="sxs-lookup"><span data-stu-id="1fb40-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="1fb40-123">Dalším krokem při psaní vlastního kanálu vrstvami je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů a jejich <xref:System.ServiceModel.Channels.IChannelListener> pro kanály service.</span><span class="sxs-lookup"><span data-stu-id="1fb40-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="1fb40-124">Tyto třídy vnitřní objekt pro vytváření a naslouchací proces a delegovat vše kromě na `OnCreateChannel` a `OnAcceptChannel` volání vnitřní objekt pro vytváření a naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="1fb40-125">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="1fb40-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="1fb40-126">Ukázka definuje vlastní prvek vazby: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="1fb40-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="1fb40-127">`InterceptingBindingElement` přijímá `ChannelMessageInterceptor` jako vstup a využívá ji `ChannelMessageInterceptor` k manipulaci s zprávy předávané přes něj.</span><span class="sxs-lookup"><span data-stu-id="1fb40-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="1fb40-128">Toto je pouze třídu, která musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="1fb40-128">This is the only class that must be public.</span></span> <span data-ttu-id="1fb40-129">Objekt pro vytváření, naslouchací proces a kanály můžou být interní implementace veřejné rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="1fb40-130">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="1fb40-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="1fb40-131">K integraci s konfigurací vazby knihovny definuje obslužné rutiny konfiguračního oddílu jako část rozšíření elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="1fb40-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="1fb40-132">Konfiguračních souborů klienta a serveru musí registraci rozšíření elementu vazby v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="1fb40-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="1fb40-133">Implementátory, které chcete je zveřejnit své element vazby na konfigurační systém lze odvodit z této třídy.</span><span class="sxs-lookup"><span data-stu-id="1fb40-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="1fb40-134">Přidání zásad</span><span class="sxs-lookup"><span data-stu-id="1fb40-134">Adding Policy</span></span>  
 <span data-ttu-id="1fb40-135">Integrace s naší systému zásad `InterceptingBindingElement` implementuje IPolicyExportExtension signál, že jsme měli zúčastnit generování zásad.</span><span class="sxs-lookup"><span data-stu-id="1fb40-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="1fb40-136">Podporu importu zásad na generovaného klienta, může uživatel zaregistrovat odvozenou třídu `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() k vygenerování jejich zásady podporou `ChannelMessageInterceptor` třídy.</span><span class="sxs-lookup"><span data-stu-id="1fb40-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="1fb40-137">Příklad: Inspektor droppable zprávy</span><span class="sxs-lookup"><span data-stu-id="1fb40-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="1fb40-138">Ukázka je příklad implementace `ChannelMessageInspector` které zahodí zprávy.</span><span class="sxs-lookup"><span data-stu-id="1fb40-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="1fb40-139">Můžete k němu přístup z konfigurace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1fb40-139">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1fb40-140">Klient a server použijte tento oddíl konfigurace nově vytvořený k vložení vlastní objekty Factory do svých zásobníků kanál za běhu (nad transportní) nejnižší úroveň.</span><span class="sxs-lookup"><span data-stu-id="1fb40-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="1fb40-141">Klient použije `MessageInterceptor` knihovny přidat vlastní hlavičku do i číslované zprávy.</span><span class="sxs-lookup"><span data-stu-id="1fb40-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="1fb40-142">Služba používá na druhé straně `MessageInterceptor` knihovny vyřaďte všechny zprávy, které nemají toto zvláštní záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1fb40-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="1fb40-143">Měli byste vidět následující výstup klienta po spuštění služby a potom klienta.</span><span class="sxs-lookup"><span data-stu-id="1fb40-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="1fb40-144">Klient sestavy 10 rychlost větru jiné službě, ale pouze první z nich s hlavičkou speciální značek.</span><span class="sxs-lookup"><span data-stu-id="1fb40-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="1fb40-145">Ve službě byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1fb40-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1fb40-146">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="1fb40-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1fb40-147">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="1fb40-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="1fb40-148">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb40-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="1fb40-149">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb40-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1fb40-150">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fb40-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="1fb40-151">Nejprve spusťte Service.exe, pak spusťte Client.exe a podívejte se na obě okna konzoly pro výstup.</span><span class="sxs-lookup"><span data-stu-id="1fb40-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
