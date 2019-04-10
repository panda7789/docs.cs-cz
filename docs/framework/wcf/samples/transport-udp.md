---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 8d72ab5c7d8c461cd2ce4d4003d449ac9fe7e807
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334663"
---
# <a name="transport-udp"></a>Přenos: UDP
Přenos UDP ukázka ukazuje, jak implementovat jednosměrového vysílání UDP a vícesměrového vysílání jako vlastní přenosu Windows Communication Foundation (WCF). Ukázka popisuje doporučený postup pro vytvoření vlastní přenos ve službě WCF, pomocí architektura kanálů a osvědčených postupů WCF. Postup vytvoření vlastní přenosu jsou následující:  
  
1. Rozhodnout, které z kanálu [zpráv Exchange vzory](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) budou podporovat třídu ChannelFactory a ChannelListener. Následně se rozhodnete, zda bude podporovat s relacemi varianty těchto rozhraní.  
  
2. Vytvoření postupu kanálu a posluchače, které podporují vaše vzorce výměny zpráv.  
  
3. Ujistěte se, že všechny výjimky pro konkrétní sítě jsou normalizovány na příslušné třídy odvozené z <xref:System.ServiceModel.CommunicationException>.  
  
4. Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) element, který přidá vlastní přenosu do zásobníku kanálu. Další informace najdete v tématu [přidání prvku vazby](#AddingABindingElement).  
  
5. Přidání sekce rozšíření elementu vazby vystavit nový element vazby na konfigurační systém.  
  
6. Přidejte rozšíření metadat pro komunikaci funkce pro další koncové body.  
  
7. Přidáte vazbu, která předem nakonfiguruje sady elementů vazby podle přesně definovaného profilu. Další informace najdete v tématu [přidání standardní vazby](#AddingAStandardBinding).  
  
8. Přidáte vazbu oddíl a vazeb konfiguračního prvku vystavit vazby na konfigurační systém. Další informace najdete v tématu [přidání podpory konfigurace](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Vzorky serveru Exchange zprávu  
 Prvním krokem v psaní vlastních přenosu je rozhodnout, jaké zprávy Exchange vzory (MEPs) jsou požadovány pro přenos. Existují tři MEPs lze vybírat:  
  
-   Datagram (IInputChannel/IOutputChannel)  
  
     Při použití datagram MEP, klient odešle zprávu pomocí exchange "vypal a zapomeň". A vypal a zapomeň exchange je ten, který vyžaduje out-of-band potvrzení úspěšné dodání. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí služby. Pokud se operace odeslání se úspěšně dokončí na straně klienta, není zaručeno, že vzdálený koncový bod přijal zprávu. Datagram je základním stavebním blokem pro zasílání zpráv, jak můžete vytvářet vlastní protokoly, dojde k jeho zvýraznění – včetně protokolů spolehlivé a zabezpečené protokoly. Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.  
  
-   Request-Response (třídu IRequestChannel/IReplyChannel)  
  
     V tomto MEP je odeslána zpráva a přijetí odpovědi. Vzor se skládá z dvojice žádost odpověď. Odpověď na požadavek volání příklady vzdálených volání procedur (RPC) a prohlížeče získá. Tento model se také označuje jako poloduplexní. V tomto MEP kanály klientů implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementují kanály service <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplexní režim (IDuplexChannel)  
  
     Duplexní MEP umožňuje libovolný počet zpráv pro klientem odesílat a přijímat v libovolném pořadí. Duplexní MEP je jako je telefonní hovor, kde je zpráva každého slova, se kterým se mluví. Vzhledem k tomu, že obě strany můžete odesílat a přijímat v tomto MEP, rozhraní implementované pomocí kanálů klient a služba je <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Každá z těchto MEPs může také podporovat relace. Přidání funkce poskytované službou s ohledem na relaci kanálu je, že souvisí všechny zprávy odeslané a přijaté v kanálu. Vzor typu žádost-odpověď je samostatné relace dvě zprávy, jako jsou korelována žádost a odpověď. Vzor typu žádost-odpověď, která podporuje relací naproti tomu znamená, že všechny páry žádostí a odpovědí v tomto kanálu jsou korelována mezi sebou. To vám dává celkem šest MEPs – Datagram typu žádost-odpověď, duplexní, Datagram s relacemi, odpověď na požadavek s relacemi a duplexní s relacemi – lze vybírat.  
  
> [!NOTE]
>  Pro přenos UDP pouze MEP, který je podporovaný totiž Datagram, UDP je ze své podstaty protokol "vypal a zapomeň".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Objekt ICommunicationObject a životního cyklu objektu WCF  
 WCF obsahuje běžné stavového stroje, který se používá pro správu životního cyklu objektů, jako jsou <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, a <xref:System.ServiceModel.Channels.IChannelListener> , která se používají ke komunikaci. Existuje pět stavy, ve kterých lze tyto komunikace objekty existují. Tyto stavy jsou reprezentovány <xref:System.ServiceModel.CommunicationState> výčtu a jsou následujícím způsobem:  
  
-   Vytvořit: Toto je stav <xref:System.ServiceModel.ICommunicationObject> kdy je poprvé vytvořena. Vyvolá se v tomto stavu žádný vstup/výstup (vstupně-výstupní operace).  
  
-   Otevřít: Objekty přechodu na tento stav, kdy <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána. V tomto okamžiku byly neměnné vlastnosti a začít vstupu a výstupu. Tento převod je platný pouze ze stavu vytvořen.  
  
-   Otevřít: Objekty přechod do tohoto stavu po dokončení procesu otevřít. Tento převod je platný pouze ze stavu otevření. V tomto okamžiku objektu je plně použitelné pro přenos.  
  
-   Uzavření: Objekty přechodu na tento stav, kdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> se volá pro řádné vypnutí. Tento převod je platný pouze ze stavu otevřen.  
  
-   Zavřít: V poli Uzavřeno stavu objekty už nejsou použitelné. Obecně platí je pořád přístupný pro kontrolu největší konfiguraci, ale žádná komunikace může dojít. Tento stav je ekvivalentní vyřazována.  
  
-   Došlo k chybě: Objekty v chybovém stavu, jsou přístupné pro kontrolu, ale už nebude použitelná. Pokud dojde k nezotavitelné chybě, objekt přejde do tohoto stavu. Je platné pouze přechod z tohoto stavu do `Closed` stavu.  
  
 Existují události, které se aktivují pro každý přechod stavu. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metoda může být volána v každém okamžiku a způsobí, že objekt přechod okamžitě v jejím aktuálním stavu do uzavřeného stavu. Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Objekt pro vytváření kanálů a modul pro naslouchání kanálu  
 Dalším krokem při psaní vlastních přenosu je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů a jejich <xref:System.ServiceModel.Channels.IChannelListener> pro kanály service. Vrstvy kanálu používá vzor factory pro vytváření kanálů. WCF poskytuje pomocné rutiny základní třídy pro tento proces.  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Implementuje třída <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavového stroje výše popsaný v kroku 2. 

-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Implementuje třída <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotné základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třídy funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídy, která implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   <xref:System.ServiceModel.Channels.ChannelFactoryBase> Implementuje třída <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a slučuje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Implementuje třída <xref:System.ServiceModel.Channels.IChannelListener>. Postará se o správu základního stavu.  
  
 V této ukázce je implementace objektu factory součástí UdpChannelFactory.cs a naslouchací proces implementace je obsažený v UdpChannelListener.cs. <xref:System.ServiceModel.Channels.IChannel> Implementace jsou v UdpOutputChannel.cs a UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Objekt pro vytváření kanálů UDP  
 `UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pro poskytnutí přístupu k verze kodér zprávy. Ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby můžete odstraňujeme naše instanci <xref:System.ServiceModel.Channels.BufferManager> když změní stav stavového stroje.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor ověří argumenty a vytvoří cíl <xref:System.Net.EndPoint> objektu na základě <xref:System.ServiceModel.EndpointAddress> , který je předán.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanál můžete zavřít, bez výpadku nebo ungracefully. Pokud kanál je uzavřen řádně soketu se zavře a základní třídy je provedeno volání `OnClose` metoda. Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěn.  
  
```csharp
this.socket.Close(0);  
```  
  
 Pak implementovat `Send()` a `BeginSend()` / `EndSend()`. Tím je prolomen na dvě hlavní části. Nejprve můžeme serializovat zprávu do bajtového pole.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Potom pošleme Výsledná data na lince.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 `UdpChannelListener` , Že implementuje vzorek je odvozen od <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy. Pro příjem datagramy používá pro jediný soket UDP. `OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčka. Data se pak převedeno do zprávy pomocí rozhraní kódování zprávy.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Vzhledem k tomu, že představuje stejný kanálu datagramu zprávy přicházející z mnoha různých zdrojů, `UdpChannelListener` běží naslouchací proces typu singleton. Existuje na většině, jednu aktivní <xref:System.ServiceModel.Channels.IChannel> spojené s tímto naslouchacím procesem najednou. Ukázka generuje jiný pouze v případě, že kanál, který je vrácený `AcceptChannel` metoda následně uvolněn. Při doručení zprávy do je zařazených do fronty do tohoto kanálu typu singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Implementuje třída `IInputChannel`. Skládá se z front příchozích zpráv, které je vyplněn `UdpChannelListener`uživatele soketu. Tyto zprávy jsou odstraněné z fronty podle `IInputChannel.Receive` metody.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Teď, když jsou vytvořeny objekty pro vytváření a kanály, jsme musí vystavit do modulu runtime ServiceModel prostřednictvím vazby. Vazba je kolekce elementů vazby, který představuje komunikační balík přidružené k adrese služby. Každý prvek v zásobníku je reprezentována [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu.  
  
 V ukázce je element vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Přepíše následujících metod k vytváření továrny spojené s využitím naší vazby.  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Přidání podpory metadat pro Element vazby přenosu  
 K integraci naší přenosu do metadat systému, musí Podporujeme import a export zásad. Díky tomu můžeme ke generování klientů prostřednictvím našich vazby [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě je zodpovědná za export a import informací o adresách v metadatech. Při použití vazby protokolu SOAP, element vazby přenosu by měl také exportovat správné přepravy identifikátoru URI v metadatech.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat informace o adresách `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní. `ExportEndpoint` Metoda přidá správné informace o adresování na WSDL port.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Provádění `ExportEndpoint` metoda zároveň exportuje přepravy identifikátoru URI při používá koncový bod vazbou SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Rozšíření systému importu WSDL pro zpracování importu adres, jsme musíte přidat následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Při spuštění Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe k načítání rozšíření importu WSDL:  
  
1. Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.  
  
2. Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` rozhraní. `ImportEndpoint` Metoda importuje adresu z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory pro zásady  
 Vlastní prvek vazby můžete export kontrolních výrazů zásad Vazba WSDL pro koncový bod služby vyjádřit možnosti daného prvku vazby.  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` přidává funkce pro export zásad. V důsledku toho `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` při generování zásad pro všechny vazby, který ji obsahuje.  
  
 V `IPolicyExportExtension.ExportPolicy`, můžeme přidat kontrolní výraz pro UDP a další kontrolní výraz Pokud se nám v režimu vícesměrového vysílání. Jak komunikačního balíku je vytvořen a proto musí být koordinovaní mezi obě strany jde vzhledem k tomu, že má vliv na režimu vícesměrového vysílání.  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Protože jsou zodpovědného za obsluhu adresování elementů přenosové vlastní vazby `IPolicyExportExtension` implementace v prostředí `UdpTransportBindingElement` musí také zpracovat export odpovídající WS-Addressing kontrolní výrazy zásad označující verzi elementu WS-Addressing používá.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásady  
 Rozšíření importu zásady systému jsme musíte přidat následující konfigurace do konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Pak můžeme implementovat `IPolicyImporterExtension` z našich registrované třídy (`UdpBindingElementImporter`). V `ImportPolicy()`, jsme v našem oboru názvů, prohlédněte si kontrolní výrazy a zpracovat pro generování přenos a zkontrolujte, zda je vícesměrového vysílání. Také musíte Odebereme kontrolní výrazy, které My se postaráme ze seznamu vazby kontrolní výrazy. Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:  
  
1. Bod Svcutil.exe k naší konfiguračního souboru pomocí /SvcutilConfig:\<soubor >.  
  
2. Přidáte konfigurační oddíl pro Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Přidání standardní vazbu  
 Naše element vazby lze použít v následujících dvou způsobů:  
  
-   Prostřednictvím vlastní vazby: Vlastní vazba umožňuje uživateli vytvořit své vlastní vazbu na základě libovolného sady elementů vazby.  
  
-   S použitím vazeb poskytovaných systémem, který zahrnuje naše element vazby. WCF poskytuje několik z těchto vazeb definovaných systémem, jako `BasicHttpBinding`, `NetTcpBinding`, a `WsHttpBinding`. Každá z těchto vazeb souvisí s dobře definovaného profilu.  
  
 Ukázka implementuje vazba profilu v `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Obsahuje až čtyři elementy vazby v něm: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastní standardní vazby programu pro import  
 Svcutil.exe a `WsdlImporter` typ, ve výchozím nastavení, rozpozná a importuje systémem definované vazby. V opačném případě získá importovat, protože vazba `CustomBinding` instance. Povolit Svcutil.exe a `WsdlImporter` import `SampleProfileUdpBinding` `UdpBindingElementImporter` taky pracuje jako import standardní vlastní vazby.  
  
 Implementuje programu pro import standardní vlastní vazby `ImportEndpoint` metodu na `IWsdlImportExtension` rozhraní k prozkoumání `CustomBinding` instance naimportované z metadat najdete v článku, zda ho může být vygenerováno konkrétní standardní vazbu.  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Obecně platí implementace programu pro import vlastních vazeb standard zahrnuje ověření vlastností elementů importované vazby k ověření, že jste změnili pouze vlastnosti, které může nastavit standardní vazbou a všechny ostatní vlastnosti se jejich výchozích hodnotách. Základní strategií pro implementaci standardní vazbu Importér je vytvoření instance standardní vazbu, rozšíří vlastnosti z elementů vazby instanci standardní vazbu, která podporuje standardní vazbu, a porovnat vazby elementy ze standardní vazba s prvky importované vazby.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Pokud chcete zpřístupnit naše přenosu prostřednictvím konfigurace, musíme implementovat dvě konfigurační oddíly funkce. První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`. Toto je tak, aby `CustomBinding` implementace může odkazovat na naše element vazby. Druhým je `Configuration` pro naše `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Element rozšíření elementu vazby  
 V části `UdpTransportElement` je `BindingElementExtensionElement` , která zveřejní `UdpTransportBindingElement` k systému konfigurace. S několika základní přepsání definujeme naše název oddílu konfigurace, typ naše element vazby a vytvoření naší element vazby. Naše rozšíření části jsme pak můžete zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Rozšíření můžete odkazovat z vlastní vazby pro použití jako přenos UDP.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a>Část vazby  
 V části `SampleProfileUdpBindingCollectionElement` je `StandardBindingCollectionElement` , která zveřejní `SampleProfileUdpBinding` k systému konfigurace. Hromadné implementace se deleguje na `SampleProfileUdpBindingConfigurationElement`, která je odvozena z `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnostem v `SampleProfileUdpBinding`a funkce mapování `ConfigurationElement` vazby. Nakonec přepsání `OnApplyConfiguration` metoda v našich `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 K registraci této obslužné rutiny konfigurace systému, přidáme do příslušných konfigurační soubor v následující části.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Poté jej lze odkazovat z konfiguračního oddílu serviceModel.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a>Služba testovacího UDP a klienta  
 Testovací kód pro tento přenos ukázkový používání je k dispozici v adresářích UdpTestService a UdpTestClient. Kódu služby se skládá ze dvou testy – jeden test nastaví vazby a koncových bodů z kódu a druhý se prostřednictvím konfigurace. Oba testy použít dva koncové body. Použije jeden koncový bod `SampleUdpProfileBinding` s [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `true`. Jiný koncový bod používá vlastní vazby s `UdpTransportBindingElement`. To je ekvivalentní k použití `SampleUdpProfileBinding` s [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `false`. Oba testy vytvoření služby, přidat koncový bod pro každou vazbu, otevřete službu a potom počkejte uživateli před jeho zavřením službu stiskněte ENTER.  
  
 Při spuštění testu aplikace službu byste měli vidět následující výstup.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Test klientská aplikace může potom spuštěním příkazu publikované koncových bodů. Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odesílá pět zprávy pro každý koncový bod. Následující výstup je na klientovi.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Následuje úplný výstup ve službě.  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 Ke spuštění klientské aplikace publikované pomocí konfigurace koncových bodů, stiskněte ENTER na službu a poté znovu spusťte testovací klient. Ve službě byste měli vidět následující výstup.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Spuštění klienta znovu provede stejné jako předchozí výsledky.  
  
 Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující Svcutil.exe z kořenového adresáře vzorku.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Všimněte si, že Svcutil.exe negeneruje pro konfiguraci rozšíření vazby `SampleProfileUdpBinding`, takže je třeba přidat ji ručně.  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Přečtěte si předchozí část "The UDP testu a klient služby".  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
