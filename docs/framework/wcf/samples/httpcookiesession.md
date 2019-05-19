---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 815f6917413afebc71f0ec6e1c81eb1de14547a4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876794"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Tento příklad ukazuje, jak vytvořit vlastní protokol kanál používat soubory cookie protokolu HTTP pro správu relací. Tento kanál umožňuje komunikaci mezi službami Windows Communication Foundation (WCF) a klienti ASMX nebo mezi klienty v WCF a službami ASMX.  
  
 Když klient volá webové metodě v ASMX webová služba, která je založená na relaci, modul ASP.NET provede následující akce:  
  
- Vygeneruje jedinečné ID (ID relace).  
  
- Generuje objekt relace a přidruží ji k jedinečné ID.  
  
- Přidá hlavičku odpovědi Set-Cookie HTTP jedinečné ID a odešle ho klientovi.  
  
- Identifikuje klienta v následných voláních na základě ID relace, že se že odešle do ní.  
  
 Klient zahrne toto ID relace v následných požadavcích na server. Tento server využívá ID relace, od klienta k načtení objektu odpovídající relace pro aktuální kontext HTTP.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Kanál HttpCookieSession vzoru výměny zpráv  
 Tato ukázka umožňuje relací pro ASMX podobné scénáře. V dolní části zásobníku náš kanál, máme přenos pomocí protokolu HTTP, který podporuje <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>. Je úloha kanálu poskytnout relace na vyšší úroveň zásobníku kanálu. Ukázka implementuje dva kanály (<xref:System.ServiceModel.Channels.IRequestSessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel>), která podporují relace.  
  
## <a name="service-channel"></a>Služba kanálu  
 Ukázka poskytuje kanál služby v `HttpCookieReplySessionChannelListener` třídy. Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní a převede <xref:System.ServiceModel.Channels.IReplyChannel> kanál z níže v kanálu zásobník, aby <xref:System.ServiceModel.Channels.IReplySessionChannel>. Tento proces je možné rozdělit do těchto částí:  
  
- Po otevření modul pro naslouchání kanálu přijímá vnitřního kanálu z jeho vnitřní naslouchacího procesu. Protože vnitřní naslouchací proces běží naslouchací proces datagram a životního cyklu přijetí kanálu je oddělený od životnost naslouchací proces, můžeme zavřít vnitřní naslouchací proces a pouze blokovat vnitřního kanálu  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- Po dokončení procesu otevřít nastavíme smyčky zpráv pro příjem zpráv z vnitřního kanálu.  
  
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
  
- Při přijetí e-mailu, kanál služba zkontroluje identifikátor relace a rušit spojuje do kanálu odpovídající relace. Modul pro naslouchání kanálu udržuje slovník, který mapuje identifikátory relace instancí kanálu relace.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Implementuje třída <xref:System.ServiceModel.Channels.IReplySessionChannel>. Vyšší úrovně kanálu zásobníku volání <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu za účelem čtení žádosti pro tuto relaci. Každý kanál relace má soukromou frontu zpráv, který je vyplněn kanálu služby.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 V případě, když někdo volá <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metoda a nejsou žádné zprávy ve frontě zpráv, kanál čeká na určenou dobu, před ukončením samotný. Tím vyčistíte kanálům relace, které jsou vytvořené pro klienty bez WCF.  
  
 Používáme `channelMapping` ke sledování `ReplySessionChannels`, a jsme naše základní nezavírejte `innerChannel` dokud zavřeli přijatých kanálů. Tímto způsobem `HttpCookieReplySessionChannel` může existovat za dobu života `HttpCookieReplySessionChannelListener`. Můžeme také nemusíte starat o naslouchací proces získávání uvolňování paměti shromážděn pod nám, protože přijatých kanálů zachovávat odkaz na jejich naslouchací proces prostřednictvím `OnClosed` zpětného volání.  
  
## <a name="client-channel"></a>Kanálu klienta  
 Probíhá odpovídající kanálu klienta `HttpCookieSessionChannelFactory` třídy. Při vytváření kanálu objekt pro vytváření kanálů zabalí vnitřního požadavku kanálu pomocí `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Třídy předává volání základního kanálu požadavku. Když klient ukončí proxy server, `HttpCookieRequestSessionChannel` odešle zprávu do služby, která označuje, že dochází k uzavření kanálu. Proto kanál zásobník služby můžete řádně vypnutí kanálu relace, která se používá.  
  
## <a name="binding-and-binding-element"></a>Element vazby a vazby  
 Po vytvoření kanálů klienta a služby, dalším krokem je na jejich integraci do modulu runtime WCF. Kanály jsou vystaveny prostřednictvím vazby a prvky vazeb WCF. Vazba se skládá z jednoho nebo více elementů vazby. Nabízí několik systémem definované vazby WCF například tříd BasicHttpBinding a WSHttpBinding. `HttpCookieSessionBindingElement` Třída obsahuje implementaci pro element vazby. Přepíše naslouchací službu kanálu a metod vytváření kanálu objekt pro vytváření provést nezbytné kanálu naslouchacího procesu nebo kanálu objekt pro vytváření instancí.  
  
 Ukázka používá kontrolní výrazy zásad pro popis služby. To umožňuje vzorku publikovat své požadavky na kanál do jiných klientů, které můžete používání této služby. Například tento element vazby publikuje kontrolní výrazy zásad nechte potenciální klienty, kteří vědět, že podporuje relace. Vzhledem k tomu, že umožňuje ukázku `ExchangeTerminateMessage` vlastnost v konfigurace elementu vazby přidá potřebné kontrolní výrazy zobrazíte, že tato služba podporuje další zprávy exchange akci ukončit relaci konverzace. Klienti pak pomocí této akce. Kontrolní výrazy zásad vytvořené z ukazuje následující kód WSDL `HttpCookieSessionBindingElement`.  
  
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
  
 `HttpCookieSessionBinding` Třída je vazeb poskytovaných systémem, který používá element vazby je popsáno výše.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Přidání kanál k systému konfigurace  
 Ukázka poskytuje dvě třídy, která zpřístupňují ukázkový kanál prostřednictvím konfigurace. První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement`. Hromadné implementace se deleguje na `HttpCookieSessionBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnostem v `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Část rozšíření elementu vazby  
 V části `HttpCookieSessionBindingElementSection` je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , která zveřejní `HttpCookieSessionBindingElement` k systému konfigurace. S přepsáními pár název oddílu konfigurace, typ elementu vazby a tom, jak vytvořit element vazby jsou definovány. Můžeme můžete potom zaregistrovat oddílu rozšíření v konfiguračním souboru následujícím způsobem:  
  
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
  
## <a name="test-code"></a>Testování kódu  
 Testovací kód pro tento přenos ukázkový používání je k dispozici v adresářích klienta a služby. Skládá se ze dvou testy – jeden test používá vazbu s `allowCookies` nastavena na `true` na straně klienta. Druhý test umožňuje jednoznačném vypnutí (pomocí serveru exchange zprávu ukončení) v rámci vazby.  
  
 Když spustíte ukázku, byste měli vidět následující výstup:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Instalace technologie ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
