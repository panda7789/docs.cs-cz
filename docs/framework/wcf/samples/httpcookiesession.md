---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 8dba147ace7ada221b5d274cd233e4b9618835d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585127"
---
# <a name="httpcookiesession"></a>HttpCookieSession
Tato ukázka předvádí, jak vytvořit vlastní kanál protokolu pro použití souborů cookie protokolu HTTP pro správu relací. Tento kanál umožňuje komunikaci mezi službami Windows Communication Foundation (WCF) a klienty ASMX nebo mezi klienty WCF a službami ASMX.  
  
 Když klient zavolá webovou metodu ve webové službě ASMX, která je založená na relaci, modul ASP.NET provede následující akce:  
  
- Vygeneruje jedinečné ID (ID relace).  
  
- Vygeneruje objekt relace a přidruží ho k jedinečnému ID.  
  
- Přidá jedinečné ID do hlavičky odpovědi HTTP Set-cookie a pošle je klientovi.  
  
- Identifikuje klienta při následných voláních na základě ID relace, kterou do něj pošle.  
  
 Klient zahrnuje toto ID relace v následných požadavcích na server. Server používá ID relace z klienta k načtení vhodného objektu relace pro aktuální kontext HTTP.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>Vzor výměny zpráv kanálu HttpCookieSession  
 V této ukázce jsou povoleny relace pro scénáře podobné ASMX. V dolní části zásobníku kanálů máme přenos HTTP, který podporuje <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel> . Jedná se o úlohu kanálu, která poskytuje relace na vyšší úrovně zásobníku kanálu. Ukázka implementuje dva kanály ( <xref:System.ServiceModel.Channels.IRequestSessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel> ), které podporují relace.  
  
## <a name="service-channel"></a>Kanál služby  
 Ukázka poskytuje kanál služby ve `HttpCookieReplySessionChannelListener` třídě. Tato třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> rozhraní a převede <xref:System.ServiceModel.Channels.IReplyChannel> kanál z nižší úrovně v zásobníku kanálů na <xref:System.ServiceModel.Channels.IReplySessionChannel> . Tento proces může být rozdělen do následujících částí:  
  
- Při otevření naslouchacího procesu kanálu přijímá interní kanál z jeho vnitřního naslouchacího procesu. Vzhledem k tomu, že vnitřní naslouchací proces je naslouchací proces datagram a životnost přijímaného kanálu je oddělená od doby životnosti naslouchacího procesu, můžeme vnitřní naslouchací proces zavřít a použít ho jenom na interním kanálu.  
  
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
  
- Po přijetí zprávy kanál služby prověřuje identifikátor relace a demultiplexy na příslušný kanál relace. Naslouchací proces kanálu uchovává slovník, který mapuje identifikátory relací na instance kanálů relací.  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel`Třída implementuje <xref:System.ServiceModel.Channels.IReplySessionChannel> . Vyšší úrovně zásobníku kanálu volají <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu pro čtení požadavků pro tuto relaci. Každý kanál relace má soukromou frontu zpráv, která je vyplněna kanálem služby.  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 V případě, že někdo volá <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> metodu a ve frontě zpráv nejsou žádné zprávy, kanál počká zadanou dobu, než se ukončí. Tím se vyčistí kanály relací vytvořené pro klienty jiného typu než WCF.  
  
 Používáme `channelMapping` ke sledování `ReplySessionChannels` a my neukončíme naši podklady, `innerChannel` dokud se všechny přijaté kanály nezavřou. Tento způsob `HttpCookieReplySessionChannel` může existovat i po dobu životnosti `HttpCookieReplySessionChannelListener` . Nemusíme se starat o naslouchací proces získávání paměti, který se nachází pod námi, protože přijímané kanály udržují odkaz na jejich naslouchací proces prostřednictvím `OnClosed` zpětného volání.  
  
## <a name="client-channel"></a>Kanál klienta  
 Odpovídající kanál klienta je ve `HttpCookieSessionChannelFactory` třídě. Při vytváření kanálu zabalí objekt pro vytváření kanálů kanál interních požadavků s `HttpCookieRequestSessionChannel` příponou. `HttpCookieRequestSessionChannel`Třída přesměruje volání do podkladového kanálu požadavků. Když klient zavře proxy server, `HttpCookieRequestSessionChannel` pošle zprávu službě, která indikuje, že kanál je právě uzavřený. Proto zásobník kanálu služby může řádně vypnout kanál relace, který se používá.  
  
## <a name="binding-and-binding-element"></a>Vazba a element vazby  
 Po vytvoření kanálů služby a klienta je dalším krokem jejich integrace do modulu runtime WCF. Kanály se zveřejňují pro WCF prostřednictvím vazeb a elementů vazby. Vazba se skládá z jednoho nebo mnoha prvků vazby. WCF nabízí několik uživatelsky definovaných vazeb. například BasicHttpBinding nebo WSHttpBinding. `HttpCookieSessionBindingElement`Třída obsahuje implementaci elementu vazby. Potlačí naslouchací proces kanálu a metody vytváření továrny kanálů, aby bylo možné provést potřebné naslouchací proces kanálu nebo vytváření instancí kanálu.  
  
 Ukázka používá pro popis služby kontrolní výrazy zásad. Tato možnost umožňuje, aby ukázka publikovala požadavky kanálu na jiné klienty, kteří můžou službu spotřebovat. Například tento prvek vazby publikuje kontrolní výrazy zásad, aby potenciální klienti věděli, že podporuje relace. Vzhledem k tomu, že ukázka povoluje `ExchangeTerminateMessage` vlastnost v konfiguraci elementu vazby, přidává potřebné kontrolní výrazy k tomu, aby bylo možné Ukázat, že služba podporuje pro ukončení konverzace relace dodatečnou akci výměny zpráv. Klienti pak mohou tuto akci použít. Následující kód WSDL ukazuje kontrolní výrazy zásad vytvořené z `HttpCookieSessionBindingElement` .  
  
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
  
 `HttpCookieSessionBinding`Třída je systémem poskytnutá vazba, která používá element vazby popsaný dříve.  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>Přidání kanálu do konfiguračního systému  
 Ukázka poskytuje dvě třídy, které zpřístupňují vzorový kanál prostřednictvím konfigurace. První je <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pro `HttpCookieSessionBindingElement` . Hromadná implementace je delegována na `HttpCookieSessionBindingConfigurationElement` , který je odvozen z <xref:System.ServiceModel.Configuration.StandardBindingElement> . `HttpCookieSessionBindingConfigurationElement`Obsahuje vlastnosti, které odpovídají vlastnostem na `HttpCookieSessionBindingElement` .  
  
### <a name="binding-element-extension-section"></a>Oddíl rozšíření vazby element  
 Oddíl `HttpCookieSessionBindingElementSection` <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , který zveřejňuje `HttpCookieSessionBindingElement` konfiguračnímu systému. S několika potlačením název konfiguračního oddílu, typ prvku vazby a způsob vytvoření prvku vazby jsou definovány. Oddíl rozšíření pak můžeme zaregistrovat v konfiguračním souboru následujícím způsobem:  
  
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
 Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích klientů a služeb. Skládá se ze dvou testů – jeden test používá vazbu s `allowCookies` nastavením na `true` na klienta. Druhý test umožňuje explicitní vypnutí (pomocí výměny ukončovacích zpráv) ve vazbě.  
  
 Při spuštění ukázky by se měl zobrazit následující výstup:  
  
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
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
