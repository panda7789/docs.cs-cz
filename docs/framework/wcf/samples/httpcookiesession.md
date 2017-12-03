---
title: HttpCookieSession
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72d6dcef2ac59fd63706d8d8c843f739575cf5cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="httpcookiesession"></a>HttpCookieSession
Tento příklad znázorňuje, jak vytvořit vlastní protokol kanál používat soubory cookie HTTP pro správu relací. Tento kanál umožňuje komunikaci mezi [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služeb a klientů ASMX nebo mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASMX služby a klienti.  
  
 Když klient volání metody webové v ASMX webové služby, je na základě relace, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modul provede následující akce:  
  
-   Generuje jedinečné ID (ID relace).  
  
-   Generuje objektu session a přidruží ji jedinečný identifikátor.  
  
-   Přidá hlavičku odpovědi Set-Cookie HTTP jedinečné ID a odešle ji do klienta.  
  
-   Identifikuje klienta na následující volání na základě ID relace, že odešle do ní.  
  
 Klient zahrne toto ID relace v jeho následné požadavky na server. Tento server využívá ID relace z klienta k načtení objektu příslušné relace pro aktuální kontext HTTP.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Kanál HttpCookieSession vzorce výměny zpráv  
 Tato ukázka umožňuje relací pro scénáře jako ASMX. V dolní části našich zásobníku kanál, máme přenos HTTP, který podporuje <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>. Je úloha kanálu zajistit relace vyšší úrovně zásobníku kanálu. Ukázka implementuje dva kanály (<xref:System.ServiceModel.Channels.IRequestSessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel>) podporující relací.  
  
## <a name="service-channel"></a>Kanál služby  
 Ukázka poskytuje kanál služby v `HttpCookieReplySessionChannelListener` třídy. Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní a převede <xref:System.ServiceModel.Channels.IReplyChannel> channel z nižší v zásobníku kanál k <xref:System.ServiceModel.Channels.IReplySessionChannel>. Tento proces je možné rozdělit do následujících částí:  
  
-   Po otevření naslouchací proces kanálu nástroje přijme vnitřního kanálu z jeho vnitřní naslouchací proces. Protože vnitřní naslouchací proces je datagram naslouchací proces a doba platnosti přijaté kanálu je odpojená od životnost naslouchací proces, můžeme zavřít vnitřní naslouchací proces a obsahovat pouze vnitřní kanálu  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   Po dokončení procesu otevřete nastavíme smyčku zpráv příjem zpráv z vnitřní kanálu.  
  
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
  
-   Při doručení zprávy kanál služby prozkoumá identifikátor relace a multiplexových kanálu příslušné relace. Naslouchací proces kanálu nástroje udržuje slovník, který se mapuje na kanál instance relace identifikátory relace.  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` Třída implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel>. Vyšší úrovně kanálu zásobníku volání <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu za účelem požadavků na čtení pro tuto relaci. Každý kanál relace má soukromé zprávy fronty, který je naplněn kanál služby.  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 V případě, že když někdo volá <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metoda a nejsou žádné zprávy ve frontě zpráv, kanál čeká na určenou dobu, před ukončením sám sebe. Tím vyčistíte kanály relace vytvořena pro jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů.  
  
 Používáme `channelMapping` sledovat `ReplySessionChannels`, a jsme naše základní nezavírejte `innerChannel` dokud zavřeli přijatých kanálů. Tímto způsobem `HttpCookieReplySessionChannel` může existovat mimo dobu životnosti `HttpCookieReplySessionChannelListener`. Také nemáme si dělat starosti naslouchací proces získávání uvolnění z paměti pod nám, protože přijatých kanálů zachovat odkaz na jejich naslouchací proces prostřednictvím `OnClosed` zpětného volání.  
  
## <a name="client-channel"></a>Kanálem klienta  
 Odpovídající kanálem klienta je v `HttpCookieSessionChannelFactory` třídy. Při vytvoření kanálu, vytváření kanálů zabalí kanál vnitřní žádosti s `HttpCookieRequestSessionChannel`. `HttpCookieRequestSessionChannel` Třída předává volání základní požadavku kanálu. Po ukončení klienta na server proxy, `HttpCookieRequestSessionChannel` odešle zprávu do služby, která určuje, že dochází k uzavření kanál. Proto zásobníku kanál služby můžete řádně vypnutí kanál relace, která je používána.  
  
## <a name="binding-and-binding-element"></a>Vazba a prvku vazby  
 Po vytvoření klienta a služby kanály, dalším krokem je integrovat do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modulu runtime. Kanály jsou viditelné na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prostřednictvím vazby a prvky vazeb. Vazba se skládá z jednoho či více elementů vazby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nabízí několik vazeb definovaných systémem; například BasicHttpBinding nebo WSHttpBinding. `HttpCookieSessionBindingElement` Třída obsahuje implementaci pro prvku vazby. Přepíše naslouchací proces kanálu a kanál factory vytvoření metody, které uděláte nezbytné kanál naslouchání nebo kanál konkretizací objekt pro vytváření.  
  
 Příklad používá výrazy zásad pro popis služby. To umožňuje vzorku, který se publikovat požadavky na jeho kanál pro ostatní klienty, které můžou využívat službu. Tento element vazby například publikuje výrazy zásad umožníte potenciální klienty vědět, že podporuje relací. Vzhledem k tomu ukázka umožňuje `ExchangeTerminateMessage` vlastnost v elementu konfigurace vazeb, přidá nezbytné kontrolní výrazy zobrazit, že služba podporuje akce exchange navíc zprávu o ukončení relace konverzace. Klienti potom můžete pomocí této akce. Následující kód WSDL ukazuje výrazy zásad vytvořené z `HttpCookieSessionBindingElement`.  
  
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
  
 `HttpCookieSessionBinding` Třída je poskytované systémem vazbu, která používá prvku vazby popsané.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Přidání kanál konfigurace systému  
 Ukázka poskytuje dvě třídy, které zveřejňují ukázkový kanál prostřednictvím konfigurace. První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement`. Hromadné implementace je delegovaný jako `HttpCookieSessionBindingConfigurationElement`, která je odvozena z <xref:System.ServiceModel.Configuration.StandardBindingElement>. `HttpCookieSessionBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `HttpCookieSessionBindingElement`.  
  
### <a name="binding-element-extension-section"></a>Vazba oddílu rozšíření – Element  
 V části `HttpCookieSessionBindingElementSection` je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> která zveřejňuje `HttpCookieSessionBindingElement` v konfiguraci systému. S několika přepsání jsou definovány název konfiguračního oddílu, typ elementu vazby a postup vytvoření prvku vazby. Jsme můžete pak zaregistrujte části rozšíření v konfiguračním souboru následujícím způsobem:  
  
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
 Testovacího kódu pro použití přenosu Tato ukázka je dostupná v adresáři pro klienta a služby. Obsahuje dva testy – jeden test používá vazba s `allowCookies` nastavena na `true` na straně klienta. Druhý test umožňuje explicitní vypnutí (s použitím exchange zprávu ukončit) na vazby.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
