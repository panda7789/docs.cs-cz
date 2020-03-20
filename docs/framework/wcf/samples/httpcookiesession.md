---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183620"
---
# <a name="httpcookiesession"></a><span data-ttu-id="33c1e-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="33c1e-102">HttpCookieSession</span></span>
<span data-ttu-id="33c1e-103">Tato ukázka ukazuje, jak vytvořit vlastní kanál protokolu pro použití souborů cookie HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="33c1e-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="33c1e-104">Tento kanál umožňuje komunikaci mezi službami WCF (Windows Communication Foundation) a klienty ASMX nebo mezi klienty WCF a službami ASMX.</span><span class="sxs-lookup"><span data-stu-id="33c1e-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="33c1e-105">Když klient volá webovou metodu ve webové službě ASMX, která je založena na relacích, ASP.NET engine provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="33c1e-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="33c1e-106">Generuje jedinečné ID (ID relace).</span><span class="sxs-lookup"><span data-stu-id="33c1e-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="33c1e-107">Generuje objekt relace a přidruží jej k jedinečnému ID.</span><span class="sxs-lookup"><span data-stu-id="33c1e-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="33c1e-108">Přidá jedinečné ID do hlavičky odpovědi HTTP set-cookie a odešle jej klientovi.</span><span class="sxs-lookup"><span data-stu-id="33c1e-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="33c1e-109">Identifikuje klienta při následných voláních na základě ID relace, které mu odešle.</span><span class="sxs-lookup"><span data-stu-id="33c1e-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="33c1e-110">Klient zahrne toto ID relace do následných požadavků na server.</span><span class="sxs-lookup"><span data-stu-id="33c1e-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="33c1e-111">Server používá ID relace z klienta k načtení příslušného objektu relace pro aktuální kontext PROTOKOLU HTTP.</span><span class="sxs-lookup"><span data-stu-id="33c1e-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33c1e-112">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="33c1e-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33c1e-113">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="33c1e-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="33c1e-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="33c1e-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33c1e-115">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="33c1e-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="33c1e-116">Vzor výměny zpráv kanálu HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="33c1e-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="33c1e-117">Tato ukázka umožňuje relace pro scénáře podobné ASMX.</span><span class="sxs-lookup"><span data-stu-id="33c1e-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="33c1e-118">V dolní části zásobníku kanálů máme přenos <xref:System.ServiceModel.Channels.IRequestChannel> HTTP, který podporuje a <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="33c1e-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="33c1e-119">Je úlohou kanálu poskytovat relace na vyšší úrovně zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="33c1e-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="33c1e-120">Ukázka implementuje dva<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>kanály ( a ), které podporují relace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="33c1e-121">Servisní kanál</span><span class="sxs-lookup"><span data-stu-id="33c1e-121">Service Channel</span></span>  
 <span data-ttu-id="33c1e-122">Ukázka poskytuje kanál služby ve `HttpCookieReplySessionChannelListener` třídě.</span><span class="sxs-lookup"><span data-stu-id="33c1e-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="33c1e-123">Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní <xref:System.ServiceModel.Channels.IReplyChannel> a převádí kanál <xref:System.ServiceModel.Channels.IReplySessionChannel>z nižší v zásobníku kanálu na .</span><span class="sxs-lookup"><span data-stu-id="33c1e-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="33c1e-124">Tento proces lze rozdělit do následujících částí:</span><span class="sxs-lookup"><span data-stu-id="33c1e-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="33c1e-125">Při otevření naslouchací proces kanálu přijímá vnitřní kanál z jeho vnitřní naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="33c1e-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="33c1e-126">Vzhledem k tomu, že vnitřní naslouchací proces je naslouchací proces datagramu a životnost přijatého kanálu je oddělena od životnosti posluchače, můžeme zavřít vnitřní naslouchací proces a pouze držet vnitřní kanál</span><span class="sxs-lookup"><span data-stu-id="33c1e-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="33c1e-127">Po dokončení otevřeného procesu nastavíme smyčku zpráv pro příjem zpráv z vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="33c1e-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="33c1e-128">Když přijde zpráva, kanál služby zkontroluje identifikátor relace a de-multiplexy na příslušný kanál relace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="33c1e-129">Naslouchací proces kanálu udržuje slovník, který mapuje identifikátory relací na instance kanálu relace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="33c1e-130">Třída `HttpCookieReplySessionChannel` implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="33c1e-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="33c1e-131">Vyšší úrovně zásobníku kanálu <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> volání metody číst požadavky pro tuto relaci.</span><span class="sxs-lookup"><span data-stu-id="33c1e-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="33c1e-132">Každý kanál relace má frontu soukromých zpráv, která je naplněna kanálem služby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="33c1e-133">V případě, že <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> někdo volá metodu a nejsou žádné zprávy ve frontě zpráv, kanál čeká na zadanou dobu před vypnutím sám.</span><span class="sxs-lookup"><span data-stu-id="33c1e-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="33c1e-134">Tím vyčistíte kanály relace vytvořené pro klienty bez WCF.</span><span class="sxs-lookup"><span data-stu-id="33c1e-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="33c1e-135">Používáme `channelMapping` ke sledování `ReplySessionChannels`, a nebudeme `innerChannel` zavírat naše základní, dokud všechny přijaté kanály byly uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="33c1e-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="33c1e-136">Tímto `HttpCookieReplySessionChannel` způsobem může existovat `HttpCookieReplySessionChannelListener`i po dobu životnosti .</span><span class="sxs-lookup"><span data-stu-id="33c1e-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="33c1e-137">Také se nemusíme starat o posluchače, který pod námi získává odpadky, `OnClosed` protože přijaté kanály udržují odkaz na jejich posluchače prostřednictvím zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="33c1e-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="33c1e-138">Kanál klienta</span><span class="sxs-lookup"><span data-stu-id="33c1e-138">Client channel</span></span>  
 <span data-ttu-id="33c1e-139">Odpovídající kanál klienta `HttpCookieSessionChannelFactory` je ve třídě.</span><span class="sxs-lookup"><span data-stu-id="33c1e-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="33c1e-140">Během vytváření kanálu factory zabalí vnitřní požadavek `HttpCookieRequestSessionChannel`kanál s .</span><span class="sxs-lookup"><span data-stu-id="33c1e-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="33c1e-141">Třída `HttpCookieRequestSessionChannel` předává volání do kanálu základní požadavek.</span><span class="sxs-lookup"><span data-stu-id="33c1e-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="33c1e-142">Když klient zavře proxy `HttpCookieRequestSessionChannel` server, odešle zprávu službě, která označuje, že kanál je právě uzavřen.</span><span class="sxs-lookup"><span data-stu-id="33c1e-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="33c1e-143">Proto zásobník kanálu služby můžete řádně vypnout kanál relace, který je používán.</span><span class="sxs-lookup"><span data-stu-id="33c1e-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="33c1e-144">Vazba a element vazby</span><span class="sxs-lookup"><span data-stu-id="33c1e-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="33c1e-145">Po vytvoření služby a klientských kanálů je dalším krokem jejich integrace do runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="33c1e-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="33c1e-146">Kanály jsou vystaveny WCF prostřednictvím vazby a elementy vazby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="33c1e-147">Vazba se skládá z jednoho nebo více elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="33c1e-148">WCF nabízí několik systémově definovaných vazeb; například BasicHttpBinding nebo WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="33c1e-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="33c1e-149">Třída `HttpCookieSessionBindingElement` obsahuje implementaci prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="33c1e-150">Přepíše naslouchací proces kanálu a metody vytváření kanálu k vytvoření potřebné houstnoucí proces kanálu nebo innastanci kanálu factory.</span><span class="sxs-lookup"><span data-stu-id="33c1e-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="33c1e-151">Ukázka používá kontrolní výrazy zásad pro popis služby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="33c1e-152">To umožňuje ukázku publikovat požadavky na kanál pro ostatní klienty, kteří mohou využívat službu.</span><span class="sxs-lookup"><span data-stu-id="33c1e-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="33c1e-153">Například tento element vazby publikuje kontrolní výrazy zásad, aby potenciální klienti věděli, že podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="33c1e-154">Vzhledem k `ExchangeTerminateMessage` tomu, že ukázka umožňuje vlastnost v konfiguraci elementu vazby, přidá nezbytné kontrolní výrazy, které ukazují, že služba podporuje další akci výměny zpráv k ukončení konverzace relace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="33c1e-155">Klienti pak mohou tuto akci použít.</span><span class="sxs-lookup"><span data-stu-id="33c1e-155">Clients can then use this action.</span></span> <span data-ttu-id="33c1e-156">Následující kód WSDL zobrazuje kontrolní výrazy `HttpCookieSessionBindingElement`zásad vytvořené z .</span><span class="sxs-lookup"><span data-stu-id="33c1e-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="33c1e-157">Třída `HttpCookieSessionBinding` je systémem za předpokladu, vazby, která používá prvek vazby popsané výše.</span><span class="sxs-lookup"><span data-stu-id="33c1e-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="33c1e-158">Přidání kanálu do konfiguračního systému</span><span class="sxs-lookup"><span data-stu-id="33c1e-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="33c1e-159">Ukázka poskytuje dvě třídy, které zveřejňují ukázkový kanál prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="33c1e-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="33c1e-160">První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="33c1e-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="33c1e-161">Převážná část implementace je delegována `HttpCookieSessionBindingConfigurationElement`na <xref:System.ServiceModel.Configuration.StandardBindingElement>, který je odvozen z .</span><span class="sxs-lookup"><span data-stu-id="33c1e-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="33c1e-162">Má `HttpCookieSessionBindingConfigurationElement` vlastnosti, které odpovídají `HttpCookieSessionBindingElement`vlastnosti na .</span><span class="sxs-lookup"><span data-stu-id="33c1e-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="33c1e-163">Oddíl rozšíření prvku vazby</span><span class="sxs-lookup"><span data-stu-id="33c1e-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="33c1e-164">Sekce `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> je, která `HttpCookieSessionBindingElement` zpřístupňuje konfiguračnísystém.</span><span class="sxs-lookup"><span data-stu-id="33c1e-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="33c1e-165">S několika přepsání název oddílu konfigurace, typ elementu vazby a jak vytvořit element vazby jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="33c1e-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="33c1e-166">Oddíl rozšíření pak můžeme zaregistrovat v konfiguračním souboru takto:</span><span class="sxs-lookup"><span data-stu-id="33c1e-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="33c1e-167">Testovací kód</span><span class="sxs-lookup"><span data-stu-id="33c1e-167">Test Code</span></span>  
 <span data-ttu-id="33c1e-168">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="33c1e-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="33c1e-169">Skládá se ze dvou testů – jeden `allowCookies` test `true` používá vazbu s nastavenou na klienta.</span><span class="sxs-lookup"><span data-stu-id="33c1e-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="33c1e-170">Druhý test umožňuje explicitní vypnutí (pomocí výměny zpráv ukončení) na vazbě.</span><span class="sxs-lookup"><span data-stu-id="33c1e-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="33c1e-171">Při spuštění ukázky, měli byste vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="33c1e-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33c1e-172">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="33c1e-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="33c1e-173">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="33c1e-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="33c1e-174">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33c1e-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="33c1e-175">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33c1e-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="33c1e-176">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33c1e-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
