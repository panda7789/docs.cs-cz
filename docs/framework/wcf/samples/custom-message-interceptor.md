---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: a59b2075473e2ca4c8cb8751fd6cb733f282238b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="53220-102">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="53220-102">Custom Message Interceptor</span></span>
<span data-ttu-id="53220-103">Tento příklad znázorňuje použití model rozšiřitelnosti kanálu.</span><span class="sxs-lookup"><span data-stu-id="53220-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="53220-104">Konkrétně ukazuje, jak implementovat vlastní vazby element, který vytváří objekty factory kanálu a naslouchací procesy kanál zachytávat všechny příchozí a odchozí zprávy na určitém místě v zásobníku spuštění.</span><span class="sxs-lookup"><span data-stu-id="53220-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="53220-105">Ukázka zahrnuje také klienta a serveru, která ukazují použití tyto vlastní objekty pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="53220-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="53220-106">V této ukázce klienta a služby jsou programy konzoly (.exe).</span><span class="sxs-lookup"><span data-stu-id="53220-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="53220-107">Klient a služba i použití běžné knihovny (DLL.dll), která obsahuje element vlastní vazby a jejích přidružených objektů běhu.</span><span class="sxs-lookup"><span data-stu-id="53220-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53220-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="53220-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53220-109">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="53220-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53220-110">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="53220-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="53220-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="53220-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53220-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="53220-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="53220-113">Ukázka popisuje doporučený postup pro vytvoření vlastní vrstveného kanál ve Windows Communication Foundation (WCF), pomocí rozhraní kanálu a následující osvědčené postupy WCF.</span><span class="sxs-lookup"><span data-stu-id="53220-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="53220-114">Postup vytvoření vlastní vrstveného kanál jsou následující:</span><span class="sxs-lookup"><span data-stu-id="53220-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="53220-115">Rozhodnete, které tvarů kanál bude podporovat kanálu a naslouchací proces kanálu.</span><span class="sxs-lookup"><span data-stu-id="53220-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="53220-116">Vytvoření postupu kanálu a kanál naslouchací proces, který podporují obrazců kanálu.</span><span class="sxs-lookup"><span data-stu-id="53220-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="53220-117">Přidáte element vazby, který přidá do kanálu zásobníku vlastním vrstveného kanálu.</span><span class="sxs-lookup"><span data-stu-id="53220-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="53220-118">Přidáte oddíl rozšíření element vazby ke zveřejnění nového elementu vazby v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="53220-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="53220-119">Kanál tvarů</span><span class="sxs-lookup"><span data-stu-id="53220-119">Channel Shapes</span></span>  
 <span data-ttu-id="53220-120">Prvním krokem při psaní vlastních vrstveného kanál je rozhodněte, které obrazce jsou nutné pro kanál.</span><span class="sxs-lookup"><span data-stu-id="53220-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="53220-121">Pro naše inspector zpráva podporujeme jakýkoli tvar, který podporuje vrstvu pod nám (například v případě, že můžete vytvořit vrstvu pod nám <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, pak taky zveřejňujeme <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="53220-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="53220-122">Postup kanálu a objektu pro vytváření naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="53220-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="53220-123">Dalším krokem při psaní vlastních vrstveného kanál je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klienta a z <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.</span><span class="sxs-lookup"><span data-stu-id="53220-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="53220-124">Tyto třídy vnitřní objekt pro vytváření a naslouchací proces a delegovat všechny ale na `OnCreateChannel` a `OnAcceptChannel` volání vnitřní objekt pro vytváření a naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="53220-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="53220-125">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="53220-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="53220-126">Ukázka definuje element vlastní vazby: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="53220-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="53220-127">`InterceptingBindingElement` trvá `ChannelMessageInterceptor` jako vstup a to pomocí `ChannelMessageInterceptor` k manipulaci s zprávy, které předáte ji.</span><span class="sxs-lookup"><span data-stu-id="53220-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="53220-128">Toto je jediná třída, která musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="53220-128">This is the only class that must be public.</span></span> <span data-ttu-id="53220-129">Objekt pro vytváření, naslouchací proces a kanály mohou být interních implementací veřejné rozhraní běhu.</span><span class="sxs-lookup"><span data-stu-id="53220-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="53220-130">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="53220-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="53220-131">K integraci s Konfigurace vazeb, knihovny definuje obslužnou rutinu oddílu konfigurace jako oddíl rozšíření element vazby.</span><span class="sxs-lookup"><span data-stu-id="53220-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="53220-132">Konfigurační soubory, které klient a server musí registraci rozšíření elementu vazby v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="53220-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="53220-133">Implementátory informačních technologií, které chcete zpřístupnit jejich prvku vazby do konfiguračního systému lze odvozovat z této třídy.</span><span class="sxs-lookup"><span data-stu-id="53220-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="53220-134">Přidání zásady</span><span class="sxs-lookup"><span data-stu-id="53220-134">Adding Policy</span></span>  
 <span data-ttu-id="53220-135">K integraci s naše systému zásad `InterceptingBindingElement` implementuje IPolicyExportExtension signál, že jsme by se měly podílet generování zásad.</span><span class="sxs-lookup"><span data-stu-id="53220-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="53220-136">Pro podporu Import zásady generovaného klienta, můžete uživatele zaregistrovat třídu odvozenou z `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() k vygenerování jejich zásady povoleným `ChannelMessageInterceptor` třídy.</span><span class="sxs-lookup"><span data-stu-id="53220-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="53220-137">Příklad: Droppable zpráva Inspector</span><span class="sxs-lookup"><span data-stu-id="53220-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="53220-138">Příklad implementace je zahrnuta v ukázce `ChannelMessageInspector` který zahodí zprávy.</span><span class="sxs-lookup"><span data-stu-id="53220-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="53220-139">Můžete k němu přístup z konfigurace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="53220-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="53220-140">Klient a server použít tento nově vytvořený konfigurační oddíl vložení vlastní objekty Factory do jejich spuštění kanálu zásobníky (nad transportní) nejnižší úroveň.</span><span class="sxs-lookup"><span data-stu-id="53220-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="53220-141">Klient použije `MessageInterceptor` knihovny a přidat vlastní hlavičku do i číslované zprávy.</span><span class="sxs-lookup"><span data-stu-id="53220-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="53220-142">Služba na druhé straně používá `MessageInterceptor` knihovny vyřaďte všechny zprávy, které nemají speciální hlavičku.</span><span class="sxs-lookup"><span data-stu-id="53220-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="53220-143">Měli byste vidět následující výstup klienta po spuštění služby a potom klienta.</span><span class="sxs-lookup"><span data-stu-id="53220-143">You should see the following client output after running the service and then the client.</span></span>  
  
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
  
 <span data-ttu-id="53220-144">Klient sestavy 10 rychlosti větru jiné službě, ale pouze polovinu je speciální hlavičky značky.</span><span class="sxs-lookup"><span data-stu-id="53220-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="53220-145">Ve službě byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53220-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53220-146">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="53220-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="53220-147">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="53220-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="53220-148">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53220-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="53220-149">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53220-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="53220-150">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53220-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="53220-151">Nejprve spusťte Service.exe potom spustit Client.exe a podívejte se na obě okna konzoly pro výstup.</span><span class="sxs-lookup"><span data-stu-id="53220-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53220-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="53220-152">See Also</span></span>
