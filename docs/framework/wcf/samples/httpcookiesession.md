---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: af624305e4ab4678938b7f63c4e4056404de0bc9
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393134"
---
# <a name="httpcookiesession"></a><span data-ttu-id="44f5e-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="44f5e-102">HttpCookieSession</span></span>
<span data-ttu-id="44f5e-103">Tato ukázka předvádí, jak vytvořit vlastní kanál protokolu pro použití souborů cookie protokolu HTTP pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="44f5e-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="44f5e-104">Tento kanál umožňuje komunikaci mezi službami Windows Communication Foundation (WCF) a klienty ASMX nebo mezi klienty WCF a službami ASMX.</span><span class="sxs-lookup"><span data-stu-id="44f5e-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="44f5e-105">Když klient zavolá webovou metodu ve webové službě ASMX, která je založená na relaci, modul ASP.NET provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="44f5e-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="44f5e-106">Vygeneruje jedinečné ID (ID relace).</span><span class="sxs-lookup"><span data-stu-id="44f5e-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="44f5e-107">Vygeneruje objekt relace a přidruží ho k jedinečnému ID.</span><span class="sxs-lookup"><span data-stu-id="44f5e-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="44f5e-108">Přidá jedinečné ID do hlavičky odpovědi HTTP Set-cookie a pošle je klientovi.</span><span class="sxs-lookup"><span data-stu-id="44f5e-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="44f5e-109">Identifikuje klienta při následných voláních na základě ID relace, kterou do něj pošle.</span><span class="sxs-lookup"><span data-stu-id="44f5e-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="44f5e-110">Klient zahrnuje toto ID relace v následných požadavcích na server.</span><span class="sxs-lookup"><span data-stu-id="44f5e-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="44f5e-111">Server používá ID relace z klienta k načtení vhodného objektu relace pro aktuální kontext HTTP.</span><span class="sxs-lookup"><span data-stu-id="44f5e-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44f5e-112">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="44f5e-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44f5e-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="44f5e-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="44f5e-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="44f5e-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44f5e-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="44f5e-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="44f5e-116">Vzor výměny zpráv kanálu HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="44f5e-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="44f5e-117">V této ukázce jsou povoleny relace pro scénáře podobné ASMX.</span><span class="sxs-lookup"><span data-stu-id="44f5e-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="44f5e-118">V dolní části zásobníku kanálů máme přenos HTTP, který podporuje <xref:System.ServiceModel.Channels.IRequestChannel> a. <xref:System.ServiceModel.Channels.IReplyChannel></span><span class="sxs-lookup"><span data-stu-id="44f5e-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="44f5e-119">Jedná se o úlohu kanálu, která poskytuje relace na vyšší úrovně zásobníku kanálu.</span><span class="sxs-lookup"><span data-stu-id="44f5e-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="44f5e-120">Ukázka implementuje dva kanály (<xref:System.ServiceModel.Channels.IRequestSessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel>), které podporují relace.</span><span class="sxs-lookup"><span data-stu-id="44f5e-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="44f5e-121">Kanál služby</span><span class="sxs-lookup"><span data-stu-id="44f5e-121">Service Channel</span></span>  
 <span data-ttu-id="44f5e-122">Ukázka poskytuje kanál služby ve `HttpCookieReplySessionChannelListener` třídě.</span><span class="sxs-lookup"><span data-stu-id="44f5e-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="44f5e-123">Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní a <xref:System.ServiceModel.Channels.IReplyChannel> převede kanál z nižší úrovně v zásobníku kanálů na <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="44f5e-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="44f5e-124">Tento proces může být rozdělen do následujících částí:</span><span class="sxs-lookup"><span data-stu-id="44f5e-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="44f5e-125">Při otevření naslouchacího procesu kanálu přijímá interní kanál z jeho vnitřního naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="44f5e-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="44f5e-126">Vzhledem k tomu, že vnitřní naslouchací proces je naslouchací proces datagram a životnost přijímaného kanálu je oddělená od doby životnosti naslouchacího procesu, můžeme vnitřní naslouchací proces zavřít a použít ho jenom na interním kanálu.</span><span class="sxs-lookup"><span data-stu-id="44f5e-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="44f5e-127">Po dokončení otevřeného procesu nastavíme smyčku zpráv pro příjem zpráv z vnitřního kanálu.</span><span class="sxs-lookup"><span data-stu-id="44f5e-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="44f5e-128">Po přijetí zprávy kanál služby prověřuje identifikátor relace a demultiplexy na příslušný kanál relace.</span><span class="sxs-lookup"><span data-stu-id="44f5e-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="44f5e-129">Naslouchací proces kanálu uchovává slovník, který mapuje identifikátory relací na instance kanálů relací.</span><span class="sxs-lookup"><span data-stu-id="44f5e-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="44f5e-130">`HttpCookieReplySessionChannel` Třída implementuje<xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="44f5e-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="44f5e-131">Vyšší úrovně zásobníku kanálu volají <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu pro čtení požadavků pro tuto relaci.</span><span class="sxs-lookup"><span data-stu-id="44f5e-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="44f5e-132">Každý kanál relace má soukromou frontu zpráv, která je vyplněna kanálem služby.</span><span class="sxs-lookup"><span data-stu-id="44f5e-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="44f5e-133">V případě, že někdo volá <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu a ve frontě zpráv nejsou žádné zprávy, kanál počká zadanou dobu, než se ukončí.</span><span class="sxs-lookup"><span data-stu-id="44f5e-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="44f5e-134">Tím se vyčistí kanály relací vytvořené pro klienty jiného typu než WCF.</span><span class="sxs-lookup"><span data-stu-id="44f5e-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="44f5e-135">Používáme `channelMapping` ke `ReplySessionChannels`sledování a my neukončíme naši podklady `innerChannel` , dokud se všechny přijaté kanály nezavřou.</span><span class="sxs-lookup"><span data-stu-id="44f5e-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="44f5e-136">Tento způsob `HttpCookieReplySessionChannel` může existovat i po `HttpCookieReplySessionChannelListener`dobu životnosti.</span><span class="sxs-lookup"><span data-stu-id="44f5e-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="44f5e-137">Nemusíme se starat o naslouchací proces získávání paměti, který se nachází pod námi, protože přijímané kanály udržují odkaz na jejich naslouchací `OnClosed` proces prostřednictvím zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="44f5e-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="44f5e-138">Kanál klienta</span><span class="sxs-lookup"><span data-stu-id="44f5e-138">Client channel</span></span>  
 <span data-ttu-id="44f5e-139">Odpovídající kanál klienta je ve `HttpCookieSessionChannelFactory` třídě.</span><span class="sxs-lookup"><span data-stu-id="44f5e-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="44f5e-140">Při vytváření kanálu zabalí objekt pro vytváření kanálů kanál interních požadavků s `HttpCookieRequestSessionChannel`příponou.</span><span class="sxs-lookup"><span data-stu-id="44f5e-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="44f5e-141">`HttpCookieRequestSessionChannel` Třída přesměruje volání do podkladového kanálu požadavků.</span><span class="sxs-lookup"><span data-stu-id="44f5e-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="44f5e-142">Když klient zavře proxy server, `HttpCookieRequestSessionChannel` pošle zprávu službě, která indikuje, že kanál je právě uzavřený.</span><span class="sxs-lookup"><span data-stu-id="44f5e-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="44f5e-143">Proto zásobník kanálu služby může řádně vypnout kanál relace, který se používá.</span><span class="sxs-lookup"><span data-stu-id="44f5e-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="44f5e-144">Vazba a element vazby</span><span class="sxs-lookup"><span data-stu-id="44f5e-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="44f5e-145">Po vytvoření kanálů služby a klienta je dalším krokem jejich integrace do modulu runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="44f5e-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="44f5e-146">Kanály se zveřejňují pro WCF prostřednictvím vazeb a elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="44f5e-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="44f5e-147">Vazba se skládá z jednoho nebo mnoha prvků vazby.</span><span class="sxs-lookup"><span data-stu-id="44f5e-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="44f5e-148">WCF nabízí několik uživatelsky definovaných vazeb. například BasicHttpBinding nebo WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="44f5e-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="44f5e-149">`HttpCookieSessionBindingElement` Třída obsahuje implementaci elementu vazby.</span><span class="sxs-lookup"><span data-stu-id="44f5e-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="44f5e-150">Potlačí naslouchací proces kanálu a metody vytváření továrny kanálů, aby bylo možné provést potřebné naslouchací proces kanálu nebo vytváření instancí kanálu.</span><span class="sxs-lookup"><span data-stu-id="44f5e-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="44f5e-151">Ukázka používá pro popis služby kontrolní výrazy zásad.</span><span class="sxs-lookup"><span data-stu-id="44f5e-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="44f5e-152">Tato možnost umožňuje, aby ukázka publikovala požadavky kanálu na jiné klienty, kteří můžou službu spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="44f5e-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="44f5e-153">Například tento prvek vazby publikuje kontrolní výrazy zásad, aby potenciální klienti věděli, že podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="44f5e-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="44f5e-154">Vzhledem k tomu, že `ExchangeTerminateMessage` ukázka povoluje vlastnost v konfiguraci elementu vazby, přidává potřebné kontrolní výrazy k tomu, aby bylo možné Ukázat, že služba podporuje pro ukončení konverzace relace dodatečnou akci výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="44f5e-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="44f5e-155">Klienti pak mohou tuto akci použít.</span><span class="sxs-lookup"><span data-stu-id="44f5e-155">Clients can then use this action.</span></span> <span data-ttu-id="44f5e-156">Následující kód WSDL ukazuje kontrolní výrazy zásad vytvořené z `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="44f5e-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="44f5e-157">`HttpCookieSessionBinding` Třída je systémem poskytnutá vazba, která používá element vazby popsaný dříve.</span><span class="sxs-lookup"><span data-stu-id="44f5e-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="44f5e-158">Přidání kanálu do konfiguračního systému</span><span class="sxs-lookup"><span data-stu-id="44f5e-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="44f5e-159">Ukázka poskytuje dvě třídy, které zpřístupňují vzorový kanál prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="44f5e-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="44f5e-160">První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement`pro.</span><span class="sxs-lookup"><span data-stu-id="44f5e-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="44f5e-161">Hromadná implementace je delegována na `HttpCookieSessionBindingConfigurationElement`, který je odvozen z. <xref:System.ServiceModel.Configuration.StandardBindingElement></span><span class="sxs-lookup"><span data-stu-id="44f5e-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="44f5e-162">Obsahuje vlastnosti, které odpovídají vlastnostem na `HttpCookieSessionBindingElement`. `HttpCookieSessionBindingConfigurationElement`</span><span class="sxs-lookup"><span data-stu-id="44f5e-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="44f5e-163">Oddíl rozšíření vazby element</span><span class="sxs-lookup"><span data-stu-id="44f5e-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="44f5e-164">`HttpCookieSessionBindingElement` Oddíl `HttpCookieSessionBindingElementSection` ,kterýzveřejňujekonfiguračnímusystému<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="44f5e-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="44f5e-165">S několika potlačením název konfiguračního oddílu, typ prvku vazby a způsob vytvoření prvku vazby jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="44f5e-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="44f5e-166">Oddíl rozšíření pak můžeme zaregistrovat v konfiguračním souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="44f5e-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="44f5e-167">Testovací kód</span><span class="sxs-lookup"><span data-stu-id="44f5e-167">Test Code</span></span>  
 <span data-ttu-id="44f5e-168">Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích klientů a služeb.</span><span class="sxs-lookup"><span data-stu-id="44f5e-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="44f5e-169">Skládá se ze dvou testů – jeden test používá vazbu s `allowCookies` `true` nastavením na na klienta.</span><span class="sxs-lookup"><span data-stu-id="44f5e-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="44f5e-170">Druhý test umožňuje explicitní vypnutí (pomocí výměny ukončovacích zpráv) ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="44f5e-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="44f5e-171">Při spuštění ukázky by se měl zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44f5e-171">When you run the sample, you should see the following output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="44f5e-172">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="44f5e-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="44f5e-173">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="44f5e-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="44f5e-174">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44f5e-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="44f5e-175">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44f5e-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="44f5e-176">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="44f5e-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
