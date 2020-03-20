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
# <a name="httpcookiesession"></a>HttpCookieSession
Tato ukázka ukazuje, jak vytvořit vlastní kanál protokolu pro použití souborů cookie HTTP pro správu relací. Tento kanál umožňuje komunikaci mezi službami WCF (Windows Communication Foundation) a klienty ASMX nebo mezi klienty WCF a službami ASMX.  
  
 Když klient volá webovou metodu ve webové službě ASMX, která je založena na relacích, ASP.NET engine provádí následující akce:  
  
- Generuje jedinečné ID (ID relace).  
  
- Generuje objekt relace a přidruží jej k jedinečnému ID.  
  
- Přidá jedinečné ID do hlavičky odpovědi HTTP set-cookie a odešle jej klientovi.  
  
- Identifikuje klienta při následných voláních na základě ID relace, které mu odešle.  
  
 Klient zahrne toto ID relace do následných požadavků na server. Server používá ID relace z klienta k načtení příslušného objektu relace pro aktuální kontext PROTOKOLU HTTP.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Vzor výměny zpráv kanálu HttpCookieSession  
 Tato ukázka umožňuje relace pro scénáře podobné ASMX. V dolní části zásobníku kanálů máme přenos <xref:System.ServiceModel.Channels.IRequestChannel> HTTP, který podporuje a <xref:System.ServiceModel.Channels.IReplyChannel>. Je úlohou kanálu poskytovat relace na vyšší úrovně zásobníku kanálu. Ukázka implementuje dva<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>kanály ( a ), které podporují relace.  
  
## <a name="service-channel"></a>Servisní kanál  
 Ukázka poskytuje kanál služby ve `HttpCookieReplySessionChannelListener` třídě. Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní <xref:System.ServiceModel.Channels.IReplyChannel> a převádí kanál <xref:System.ServiceModel.Channels.IReplySessionChannel>z nižší v zásobníku kanálu na . Tento proces lze rozdělit do následujících částí:  
  
- Při otevření naslouchací proces kanálu přijímá vnitřní kanál z jeho vnitřní naslouchací proces. Vzhledem k tomu, že vnitřní naslouchací proces je naslouchací proces datagramu a životnost přijatého kanálu je oddělena od životnosti posluchače, můžeme zavřít vnitřní naslouchací proces a pouze držet vnitřní kanál  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Po dokončení otevřeného procesu nastavíme smyčku zpráv pro příjem zpráv z vnitřního kanálu.  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- Když přijde zpráva, kanál služby zkontroluje identifikátor relace a de-multiplexy na příslušný kanál relace. Naslouchací proces kanálu udržuje slovník, který mapuje identifikátory relací na instance kanálu relace.  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 Třída `HttpCookieReplySessionChannel` implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>. Vyšší úrovně zásobníku kanálu <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> volání metody číst požadavky pro tuto relaci. Každý kanál relace má frontu soukromých zpráv, která je naplněna kanálem služby.  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 V případě, že <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> někdo volá metodu a nejsou žádné zprávy ve frontě zpráv, kanál čeká na zadanou dobu před vypnutím sám. Tím vyčistíte kanály relace vytvořené pro klienty bez WCF.  
  
 Používáme `channelMapping` ke sledování `ReplySessionChannels`, a nebudeme `innerChannel` zavírat naše základní, dokud všechny přijaté kanály byly uzavřeny. Tímto `HttpCookieReplySessionChannel` způsobem může existovat `HttpCookieReplySessionChannelListener`i po dobu životnosti . Také se nemusíme starat o posluchače, který pod námi získává odpadky, `OnClosed` protože přijaté kanály udržují odkaz na jejich posluchače prostřednictvím zpětného volání.  
  
## <a name="client-channel"></a>Kanál klienta  
 Odpovídající kanál klienta `HttpCookieSessionChannelFactory` je ve třídě. Během vytváření kanálu factory zabalí vnitřní požadavek `HttpCookieRequestSessionChannel`kanál s . Třída `HttpCookieRequestSessionChannel` předává volání do kanálu základní požadavek. Když klient zavře proxy `HttpCookieRequestSessionChannel` server, odešle zprávu službě, která označuje, že kanál je právě uzavřen. Proto zásobník kanálu služby můžete řádně vypnout kanál relace, který je používán.  
  
## <a name="binding-and-binding-element"></a>Vazba a element vazby  
 Po vytvoření služby a klientských kanálů je dalším krokem jejich integrace do runtime WCF. Kanály jsou vystaveny WCF prostřednictvím vazby a elementy vazby. Vazba se skládá z jednoho nebo více elementů vazby. WCF nabízí několik systémově definovaných vazeb; například BasicHttpBinding nebo WSHttpBinding. Třída `HttpCookieSessionBindingElement` obsahuje implementaci prvku vazby. Přepíše naslouchací proces kanálu a metody vytváření kanálu k vytvoření potřebné houstnoucí proces kanálu nebo innastanci kanálu factory.  
  
 Ukázka používá kontrolní výrazy zásad pro popis služby. To umožňuje ukázku publikovat požadavky na kanál pro ostatní klienty, kteří mohou využívat službu. Například tento element vazby publikuje kontrolní výrazy zásad, aby potenciální klienti věděli, že podporuje relace. Vzhledem k `ExchangeTerminateMessage` tomu, že ukázka umožňuje vlastnost v konfiguraci elementu vazby, přidá nezbytné kontrolní výrazy, které ukazují, že služba podporuje další akci výměny zpráv k ukončení konverzace relace. Klienti pak mohou tuto akci použít. Následující kód WSDL zobrazuje kontrolní výrazy `HttpCookieSessionBindingElement`zásad vytvořené z .  
  
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
  
 Třída `HttpCookieSessionBinding` je systémem za předpokladu, vazby, která používá prvek vazby popsané výše.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Přidání kanálu do konfiguračního systému  
 Ukázka poskytuje dvě třídy, které zveřejňují ukázkový kanál prostřednictvím konfigurace. První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement`. Převážná část implementace je delegována `HttpCookieSessionBindingConfigurationElement`na <xref:System.ServiceModel.Configuration.StandardBindingElement>, který je odvozen z . Má `HttpCookieSessionBindingConfigurationElement` vlastnosti, které odpovídají `HttpCookieSessionBindingElement`vlastnosti na .  
  
### <a name="binding-element-extension-section"></a>Oddíl rozšíření prvku vazby  
 Sekce `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> je, která `HttpCookieSessionBindingElement` zpřístupňuje konfiguračnísystém. S několika přepsání název oddílu konfigurace, typ elementu vazby a jak vytvořit element vazby jsou definovány. Oddíl rozšíření pak můžeme zaregistrovat v konfiguračním souboru takto:  
  
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
  
## <a name="test-code"></a>Testovací kód  
 Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích klienta a služby. Skládá se ze dvou testů – jeden `allowCookies` test `true` používá vazbu s nastavenou na klienta. Druhý test umožňuje explicitní vypnutí (pomocí výměny zpráv ukončení) na vazbě.  
  
 Při spuštění ukázky, měli byste vidět následující výstup:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
