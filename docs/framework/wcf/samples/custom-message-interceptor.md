---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145083"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="06830-102">Vlastní zachycování zpráv</span><span class="sxs-lookup"><span data-stu-id="06830-102">Custom Message Interceptor</span></span>
<span data-ttu-id="06830-103">Tato ukázka ukazuje použití modelu rozšiřitelnosti kanálu.</span><span class="sxs-lookup"><span data-stu-id="06830-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="06830-104">Zejména ukazuje, jak implementovat vlastní element vazby, který vytváří továrny kanálu a naslouchací procesy kanálu zachytit všechny příchozí a odchozí zprávy v určitém bodě v zásobníku za běhu.</span><span class="sxs-lookup"><span data-stu-id="06830-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="06830-105">Ukázka také obsahuje klienta a server, které ukazují použití těchto vlastních továren.</span><span class="sxs-lookup"><span data-stu-id="06830-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="06830-106">V této ukázce jsou klient a služba konzolové programy (.exe).</span><span class="sxs-lookup"><span data-stu-id="06830-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="06830-107">Klient i služba využívají společnou knihovnu (.dll), která obsahuje vlastní element vazby a jeho přidružené objekty run-time.</span><span class="sxs-lookup"><span data-stu-id="06830-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06830-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="06830-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="06830-109">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="06830-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06830-110">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="06830-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="06830-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="06830-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06830-112">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="06830-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="06830-113">Ukázka popisuje doporučený postup pro vytvoření vlastního vrstveného kanálu v systému Windows Communication Foundation (WCF), pomocí rozhraní kanálu a podle doporučených postupů WCF.</span><span class="sxs-lookup"><span data-stu-id="06830-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="06830-114">Postup vytvoření vlastního vrstveného kanálu je následující:</span><span class="sxs-lookup"><span data-stu-id="06830-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="06830-115">Rozhodněte, který z obrazců kanálu bude podporovat váš kanál a naslouchací proces kanálu.</span><span class="sxs-lookup"><span data-stu-id="06830-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="06830-116">Vytvořte továrnu kanálu a naslouchací proces kanálu, které podporují obrazce kanálu.</span><span class="sxs-lookup"><span data-stu-id="06830-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="06830-117">Přidejte element vazby, který přidá vlastní vrstvený kanál do zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="06830-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="06830-118">Přidejte oddíl rozšíření elementu vazby, který zpřístupní nový element vazby do konfiguračního systému.</span><span class="sxs-lookup"><span data-stu-id="06830-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="06830-119">Obrazce kanálů</span><span class="sxs-lookup"><span data-stu-id="06830-119">Channel Shapes</span></span>  
 <span data-ttu-id="06830-120">Prvním krokem při psaní vlastního vrstveného kanálu je rozhodnutí, které obrazce jsou pro kanál vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="06830-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="06830-121">Pro naše zprávy inspektor, podporujeme jakýkoli tvar, který vrstva pod námi <xref:System.ServiceModel.Channels.IOutputChannel> podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel>(například <xref:System.ServiceModel.Channels.IOutputChannel> v <xref:System.ServiceModel.Channels.IDuplexSessionChannel>případě, že vrstva pod námi může stavět a , pak jsme také vystavit a ).</span><span class="sxs-lookup"><span data-stu-id="06830-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="06830-122">Továrna kanálu a naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="06830-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="06830-123">Dalším krokem při psaní vlastního vrstveného kanálu <xref:System.ServiceModel.Channels.IChannelFactory> je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro klientské kanály a pro kanály služeb.</span><span class="sxs-lookup"><span data-stu-id="06830-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="06830-124">Tyto třídy trvat vnitřní factory a `OnCreateChannel` naslouchací proces a delegovat všechny, ale a `OnAcceptChannel` volání vnitřní factory a naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="06830-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
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
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="06830-125">Přidání prvku vazby</span><span class="sxs-lookup"><span data-stu-id="06830-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="06830-126">Ukázka definuje vlastní prvek `InterceptingBindingElement`vazby: .</span><span class="sxs-lookup"><span data-stu-id="06830-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="06830-127">`InterceptingBindingElement`bere `ChannelMessageInterceptor` jako vstup a používá `ChannelMessageInterceptor` jej k manipulaci se zprávami, které procházejí.</span><span class="sxs-lookup"><span data-stu-id="06830-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="06830-128">Tohle je jediná třída, která musí být veřejná.</span><span class="sxs-lookup"><span data-stu-id="06830-128">This is the only class that must be public.</span></span> <span data-ttu-id="06830-129">Factory, naslouchací proces a kanály mohou být interní implementace veřejných rozhraní run-time.</span><span class="sxs-lookup"><span data-stu-id="06830-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="06830-130">Přidání podpory konfigurace</span><span class="sxs-lookup"><span data-stu-id="06830-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="06830-131">Chcete-li integrovat s konfigurací vazby, knihovna definuje obslužnou rutinu oddílu konfigurace jako oddíl rozšíření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="06830-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="06830-132">Konfigurační soubory klienta a serveru musí zaregistrovat příponu elementu vazby s konfiguračním systémem.</span><span class="sxs-lookup"><span data-stu-id="06830-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="06830-133">Implementátory, které chtějí vystavit jejich element vazby konfiguračního systému můžete odvodit z této třídy.</span><span class="sxs-lookup"><span data-stu-id="06830-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="06830-134">Přidání zásad</span><span class="sxs-lookup"><span data-stu-id="06830-134">Adding Policy</span></span>  
 <span data-ttu-id="06830-135">Chcete-li integrovat s `InterceptingBindingElement` naším systémem zásad, implementuje IPolicyExportExtension signál, že bychom se měli podílet na generování politiky.</span><span class="sxs-lookup"><span data-stu-id="06830-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="06830-136">Pro podporu importu zásad na generovaném klientovi může uživatel `InterceptingBindingElementImporter` zaregistrovat `CreateMessageInterceptor`odvozenou třídu a `ChannelMessageInterceptor` přepsat () a vygenerovat třídu s povoleným zásadami.</span><span class="sxs-lookup"><span data-stu-id="06830-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="06830-137">Příklad: Inspektor zasahovavých zpráv</span><span class="sxs-lookup"><span data-stu-id="06830-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="06830-138">Součástí ukázky je příklad `ChannelMessageInspector` implementace, která kapky zprávy.</span><span class="sxs-lookup"><span data-stu-id="06830-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="06830-139">Můžete k němu přistupovat z konfigurace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="06830-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="06830-140">Klient i server používají tuto nově vytvořenou část konfigurace k vložení vlastních továren do nejnižší úrovně jejich zásobníků kanálu za běhu (nad úrovní přenosu).</span><span class="sxs-lookup"><span data-stu-id="06830-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="06830-141">Klient používá `MessageInterceptor` knihovnu k přidání vlastní hlavičky do sudých číslovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="06830-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="06830-142">Služba na druhé straně `MessageInterceptor` používá knihovnu k přetažení všech zpráv, které nemají tuto speciální hlavičku.</span><span class="sxs-lookup"><span data-stu-id="06830-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="06830-143">Po spuštění služby a potom na straně klienta byste měli vidět následující výstup klienta.</span><span class="sxs-lookup"><span data-stu-id="06830-143">You should see the following client output after running the service and then the client.</span></span>  
  
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
  
 <span data-ttu-id="06830-144">Klient hlásí službě 10 různých rychlostí větru, ale polovinu z nich označí pouze speciální hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="06830-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="06830-145">Ve službě byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="06830-145">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06830-146">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="06830-146">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="06830-147">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="06830-147">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="06830-148">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06830-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="06830-149">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06830-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="06830-150">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06830-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="06830-151">Nejprve spusťte soubor Service.exe, poté spusťte soubor Client.exe a sledujte výstup obou oken konzoly.</span><span class="sxs-lookup"><span data-stu-id="06830-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
