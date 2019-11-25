---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 61f9bae24f5edb70430f4f3eaa16e42da221a7b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978301"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="3b13f-102">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="3b13f-102">Custom Message Interceptor</span></span>
<span data-ttu-id="3b13f-103">Tato ukázka demonstruje použití modelu rozšiřitelnosti kanálu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="3b13f-104">Konkrétně ukazuje, jak implementovat vlastní prvek vazby, který vytváří objekty pro vytváření kanálů a naslouchací procesy kanálu pro zachycení všech příchozích a odchozích zpráv v určitém bodě v zásobníku běhu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="3b13f-105">Ukázka zahrnuje také klienta a server, který předvádí použití těchto vlastních továrn.</span><span class="sxs-lookup"><span data-stu-id="3b13f-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="3b13f-106">V této ukázce jsou klientem i služba konzolové programy (. exe).</span><span class="sxs-lookup"><span data-stu-id="3b13f-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="3b13f-107">Klient a služba obě využívají společnou knihovnu (. dll), která obsahuje vlastní prvek vazby a příslušné objekty modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3b13f-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b13f-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3b13f-109">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="3b13f-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3b13f-110">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3b13f-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3b13f-111">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="3b13f-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b13f-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3b13f-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="3b13f-113">Ukázka popisuje doporučený postup pro vytvoření vlastního vrstveného kanálu v Windows Communication Foundation (WCF) pomocí architektury kanálů a následujících osvědčených postupů pro WCF.</span><span class="sxs-lookup"><span data-stu-id="3b13f-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="3b13f-114">Postup vytvoření vlastního vrstveného kanálu je následující:</span><span class="sxs-lookup"><span data-stu-id="3b13f-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="3b13f-115">Rozhodněte, které z obrazců kanálů bude podporovat objekt pro vytváření kanálů a naslouchací proces kanálu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="3b13f-116">Vytvořte objekt pro vytváření kanálů a naslouchací proces kanálu, který podporuje obrazce kanálu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="3b13f-117">Přidejte prvek vazby, který přidá vlastní vrstvený kanál do zásobníku kanálů.</span><span class="sxs-lookup"><span data-stu-id="3b13f-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="3b13f-118">Přidejte část rozšíření elementu vazby, která zpřístupňuje nový prvek vazby na konfigurační systém.</span><span class="sxs-lookup"><span data-stu-id="3b13f-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="3b13f-119">Obrazce kanálu</span><span class="sxs-lookup"><span data-stu-id="3b13f-119">Channel Shapes</span></span>  
 <span data-ttu-id="3b13f-120">Prvním krokem při psaní vlastního vrstveného kanálu je rozhodování o tom, které obrazce jsou pro kanál vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="3b13f-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="3b13f-121">Pro náš inspektor zpráv podporujeme jakýkoliv tvar, který podporuje vrstva níže (například pokud je možné, že vrstva níže může sestavovat <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, a také zveřejňuje <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="3b13f-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="3b13f-122">Továrna kanálu a továrna naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="3b13f-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="3b13f-123">Dalším krokem při psaní vlastního vrstveného kanálu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály a <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.</span><span class="sxs-lookup"><span data-stu-id="3b13f-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="3b13f-124">Tyto třídy přebírají interní továrnu a naslouchací proces a deleguje všechny kromě `OnCreateChannel` a `OnAcceptChannel` volání interní továrny a naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ 
    //... 
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ 
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="3b13f-125">Přidání elementu vazby</span><span class="sxs-lookup"><span data-stu-id="3b13f-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="3b13f-126">Ukázka definuje vlastní element vazby: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3b13f-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="3b13f-127">`InterceptingBindingElement` přebírá `ChannelMessageInterceptor` jako vstup a používá tento `ChannelMessageInterceptor` k manipulaci se zprávami, které projde.</span><span class="sxs-lookup"><span data-stu-id="3b13f-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="3b13f-128">Toto je jediná třída, která musí být veřejná.</span><span class="sxs-lookup"><span data-stu-id="3b13f-128">This is the only class that must be public.</span></span> <span data-ttu-id="3b13f-129">Továrny, naslouchací proces a kanály můžou být interními implementacemi pro veřejná rozhraní za běhu.</span><span class="sxs-lookup"><span data-stu-id="3b13f-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="3b13f-130">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="3b13f-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="3b13f-131">Pro integraci s konfigurací vazby knihovna definuje obslužnou rutinu konfiguračního oddílu jako rozšíření elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="3b13f-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="3b13f-132">Konfigurační soubory klienta a serveru musí registrovat rozšíření elementu vazby s konfiguračním systémem.</span><span class="sxs-lookup"><span data-stu-id="3b13f-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="3b13f-133">Implementátori, kteří chtějí zveřejnit svůj element vazby do konfiguračního systému, lze odvodit z této třídy.</span><span class="sxs-lookup"><span data-stu-id="3b13f-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="3b13f-134">Přidávání zásad</span><span class="sxs-lookup"><span data-stu-id="3b13f-134">Adding Policy</span></span>  
 <span data-ttu-id="3b13f-135">Pro integraci s naším systémem zásad `InterceptingBindingElement` implementuje IPolicyExportExtension k signalizaci, že by se měl zúčastnit generování zásad.</span><span class="sxs-lookup"><span data-stu-id="3b13f-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="3b13f-136">Pro podporu importu zásad na vygenerovaného klienta může uživatel zaregistrovat odvozenou třídu `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() pro vygenerování své třídy `ChannelMessageInterceptor` s povolenými zásadami.</span><span class="sxs-lookup"><span data-stu-id="3b13f-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="3b13f-137">Příklad: Droppable Message Inspector</span><span class="sxs-lookup"><span data-stu-id="3b13f-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="3b13f-138">Součástí ukázky je příklad implementace `ChannelMessageInspector`, která vyřazuje zprávy.</span><span class="sxs-lookup"><span data-stu-id="3b13f-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="3b13f-139">K němu můžete přistupovat z konfigurace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3b13f-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="3b13f-140">Klient a server používají tento nově vytvořený konfigurační oddíl k vložení vlastních továren do nejnižší úrovně jejich zásobníků kanálů za běhu (nad úroveň transportu).</span><span class="sxs-lookup"><span data-stu-id="3b13f-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="3b13f-141">Klient nástroje používá knihovnu `MessageInterceptor` k přidání vlastní hlavičky k sudému číslování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b13f-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="3b13f-142">Služba na druhé straně používá knihovnu `MessageInterceptor` k vyřazení všech zpráv, které nemají toto speciální hlavičku.</span><span class="sxs-lookup"><span data-stu-id="3b13f-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="3b13f-143">Po spuštění služby a poté klientovi by se měl zobrazit následující výstup klienta.</span><span class="sxs-lookup"><span data-stu-id="3b13f-143">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
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
  
 <span data-ttu-id="3b13f-144">Klient oznamuje službě 10 různých rychlostí větru, ale pouze ty, které jsou ve stejném záhlaví, pouze se speciální hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="3b13f-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="3b13f-145">Ve službě by se měl zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3b13f-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3b13f-146">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3b13f-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3b13f-147">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="3b13f-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="3b13f-148">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b13f-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="3b13f-149">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b13f-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3b13f-150">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b13f-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="3b13f-151">Nejprve spusťte Service. exe a spusťte soubor Client. exe a Sledujte výstup okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="3b13f-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
