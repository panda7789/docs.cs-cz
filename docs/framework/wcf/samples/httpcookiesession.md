---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="httpcookiesession"></a><span data-ttu-id="3d8ea-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="3d8ea-102">HttpCookieSession</span></span>
<span data-ttu-id="3d8ea-103">Tento příklad znázorňuje, jak vytvořit vlastní protokol kanál používat soubory cookie HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="3d8ea-104">Tento kanál umožňuje komunikaci mezi služby Windows Communication Foundation (WCF) a klienti ASMX nebo ASMX služby a klienti WCF.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="3d8ea-105">Když klient volání metody webové v ASMX webové služby, je na základě relace, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modul provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="3d8ea-105">When a client calls a Web method in an ASMX Web service that is session-based, the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] engine does the following:</span></span>  
  
-   <span data-ttu-id="3d8ea-106">Generuje jedinečné ID (ID relace).</span><span class="sxs-lookup"><span data-stu-id="3d8ea-106">Generates a unique ID (session ID).</span></span>  
  
-   <span data-ttu-id="3d8ea-107">Generuje objektu session a přidruží ji jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-107">Generates the session object and associates it with the unique ID.</span></span>  
  
-   <span data-ttu-id="3d8ea-108">Přidá hlavičku odpovědi Set-Cookie HTTP jedinečné ID a odešle ji do klienta.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
-   <span data-ttu-id="3d8ea-109">Identifikuje klienta na následující volání na základě ID relace, že odešle do ní.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="3d8ea-110">Klient zahrne toto ID relace v jeho následné požadavky na server.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="3d8ea-111">Tento server využívá ID relace z klienta k načtení objektu příslušné relace pro aktuální kontext HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d8ea-112">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d8ea-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3d8ea-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d8ea-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d8ea-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="3d8ea-116">Kanál HttpCookieSession vzorce výměny zpráv</span><span class="sxs-lookup"><span data-stu-id="3d8ea-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="3d8ea-117">Tato ukázka umožňuje relací pro scénáře jako ASMX.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="3d8ea-118">V dolní části našich zásobníku kanál, máme přenos HTTP, který podporuje <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="3d8ea-119">Je úloha kanálu zajistit relace vyšší úrovně zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="3d8ea-120">Ukázka implementuje dva kanály (<xref:System.ServiceModel.Channels.IRequestSessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel>) podporující relací.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="3d8ea-121">Kanál služby</span><span class="sxs-lookup"><span data-stu-id="3d8ea-121">Service Channel</span></span>  
 <span data-ttu-id="3d8ea-122">Ukázka poskytuje kanál služby v `HttpCookieReplySessionChannelListener` třídy.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="3d8ea-123">Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní a převede <xref:System.ServiceModel.Channels.IReplyChannel> channel z nižší v zásobníku kanál k <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3d8ea-124">Tento proces je možné rozdělit do následujících částí:</span><span class="sxs-lookup"><span data-stu-id="3d8ea-124">This process can be divided into the following parts:</span></span>  
  
-   <span data-ttu-id="3d8ea-125">Po otevření naslouchací proces kanálu nástroje přijme vnitřního kanálu z jeho vnitřní naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="3d8ea-126">Protože vnitřní naslouchací proces je datagram naslouchací proces a doba platnosti přijaté kanálu je odpojená od životnost naslouchací proces, můžeme zavřít vnitřní naslouchací proces a obsahovat pouze vnitřní kanálu</span><span class="sxs-lookup"><span data-stu-id="3d8ea-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   <span data-ttu-id="3d8ea-127">Po dokončení procesu otevřete nastavíme smyčku zpráv příjem zpráv z vnitřní kanálu.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   <span data-ttu-id="3d8ea-128">Při doručení zprávy kanál služby prozkoumá identifikátor relace a multiplexových kanálu příslušné relace.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="3d8ea-129">Naslouchací proces kanálu nástroje udržuje slovník, který se mapuje na kanál instance relace identifikátory relace.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="3d8ea-130">`HttpCookieReplySessionChannel` Třída implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="3d8ea-131">Vyšší úrovně kanálu zásobníku volání <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu za účelem požadavků na čtení pro tuto relaci.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="3d8ea-132">Každý kanál relace má soukromé zprávy fronty, který je naplněn kanál služby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="3d8ea-133">V případě, že když někdo volá <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metoda a nejsou žádné zprávy ve frontě zpráv, kanál čeká na určenou dobu, před ukončením sám sebe.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="3d8ea-134">Vyčistí relaci kanály pro klienty bez WCF vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="3d8ea-135">Používáme `channelMapping` sledovat `ReplySessionChannels`, a jsme naše základní nezavírejte `innerChannel` dokud zavřeli přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="3d8ea-136">Tímto způsobem `HttpCookieReplySessionChannel` může existovat mimo dobu životnosti `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="3d8ea-137">Také nemáme si dělat starosti naslouchací proces získávání uvolnění z paměti pod nám, protože přijatých kanálů zachovat odkaz na jejich naslouchací proces prostřednictvím `OnClosed` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="3d8ea-138">Kanálem klienta</span><span class="sxs-lookup"><span data-stu-id="3d8ea-138">Client channel</span></span>  
 <span data-ttu-id="3d8ea-139">Odpovídající kanálem klienta je v `HttpCookieSessionChannelFactory` třídy.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="3d8ea-140">Při vytvoření kanálu, vytváření kanálů zabalí kanál vnitřní žádosti s `HttpCookieRequestSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="3d8ea-141">`HttpCookieRequestSessionChannel` Třída předává volání základní požadavku kanálu.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="3d8ea-142">Po ukončení klienta na server proxy, `HttpCookieRequestSessionChannel` odešle zprávu do služby, která určuje, že dochází k uzavření kanál.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="3d8ea-143">Proto zásobníku kanál služby můžete řádně vypnutí kanál relace, která je používána.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="3d8ea-144">Vazba a prvku vazby</span><span class="sxs-lookup"><span data-stu-id="3d8ea-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="3d8ea-145">Po vytvoření kanálů klienta a služby, je dalším krokem je na jejich integraci do modulu runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="3d8ea-146">Kanály jsou vystaveny prostřednictvím vazby a prvky vazeb WCF.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="3d8ea-147">Vazba se skládá z jednoho či více elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="3d8ea-148">WCF nabízí několik vazeb definovaných systémem; například BasicHttpBinding nebo WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="3d8ea-149">`HttpCookieSessionBindingElement` Třída obsahuje implementaci pro prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="3d8ea-150">Přepíše naslouchací proces kanálu a kanál factory vytvoření metody, které uděláte nezbytné kanál naslouchání nebo kanál konkretizací objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="3d8ea-151">Příklad používá výrazy zásad pro popis služby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="3d8ea-152">To umožňuje vzorku, který se publikovat požadavky na jeho kanál pro ostatní klienty, které můžou využívat službu.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="3d8ea-153">Tento element vazby například publikuje výrazy zásad umožníte potenciální klienty vědět, že podporuje relací.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="3d8ea-154">Vzhledem k tomu ukázka umožňuje `ExchangeTerminateMessage` vlastnost v elementu konfigurace vazeb, přidá nezbytné kontrolní výrazy zobrazit, že služba podporuje akce exchange navíc zprávu o ukončení relace konverzace.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="3d8ea-155">Klienti potom můžete pomocí této akce.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-155">Clients can then use this action.</span></span> <span data-ttu-id="3d8ea-156">Následující kód WSDL ukazuje výrazy zásad vytvořené z `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="3d8ea-157">`HttpCookieSessionBinding` Třída je poskytované systémem vazbu, která používá prvku vazby popsané.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="3d8ea-158">Přidání kanál konfigurace systému</span><span class="sxs-lookup"><span data-stu-id="3d8ea-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="3d8ea-159">Ukázka poskytuje dvě třídy, které zveřejňují ukázkový kanál prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="3d8ea-160">První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="3d8ea-161">Hromadné implementace je delegovaný jako `HttpCookieSessionBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="3d8ea-162">`HttpCookieSessionBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="3d8ea-163">Vazba oddílu rozšíření – Element</span><span class="sxs-lookup"><span data-stu-id="3d8ea-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="3d8ea-164">V části `HttpCookieSessionBindingElementSection` je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> která zveřejňuje `HttpCookieSessionBindingElement` v konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="3d8ea-165">S několika přepsání jsou definovány název konfiguračního oddílu, typ elementu vazby a postup vytvoření prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="3d8ea-166">Jsme můžete pak zaregistrujte části rozšíření v konfiguračním souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3d8ea-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="3d8ea-167">Testování kódu</span><span class="sxs-lookup"><span data-stu-id="3d8ea-167">Test Code</span></span>  
 <span data-ttu-id="3d8ea-168">Testovacího kódu pro použití přenosu Tato ukázka je dostupná v adresáři pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="3d8ea-169">Obsahuje dva testy – jeden test používá vazba s `allowCookies` nastavena na `true` na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="3d8ea-170">Druhý test umožňuje explicitní vypnutí (s použitím exchange zprávu ukončit) na vazby.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="3d8ea-171">Když spustíte ukázku, byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3d8ea-171">When you run the sample, you should see the following output:</span></span>  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d8ea-172">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3d8ea-172">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3d8ea-173">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="3d8ea-173">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="3d8ea-174">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8ea-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="3d8ea-175">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8ea-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3d8ea-176">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8ea-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8ea-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d8ea-177">See Also</span></span>
