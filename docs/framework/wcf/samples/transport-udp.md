---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 51f445d7f53f70fa206c53835b107da68749e3c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="transport-udp"></a>Přenos: UDP
Ukázka přenosu UDP ukazuje, jak implementovat jednosměrového vysílání UDP a vícesměrového vysílání jako vlastní přenosu Windows Communication Foundation (WCF). Ukázka popisuje doporučený postup pro vytvoření vlastní přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pomocí rozhraní kanálu a následující [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] osvědčené postupy. Postup vytvoření vlastního přenosu jsou následující:  
  
1.  Rozhodněte, které kanálu [zpráva Exchange vzory](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) ChannelFactory a ChannelListener bude podporovat. Rozhodněte se, zda bude podporovat relacemi variace tato rozhraní.  
  
2.  Vytvoření postupu kanálu a naslouchací proces, který podporují vaše vzorce výměny zpráv.  
  
3.  Ujistěte se, že jsou všechny výjimky sítě normalizovány na příslušné odvozené třídy z <xref:System.ServiceModel.CommunicationException>.  
  
4.  Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) element, který přidá vlastní přenos do zásobníku kanálu. Další informace najdete v tématu [přidání Element vazby](#AddingABindingElement).  
  
5.  Přidáte oddíl rozšíření element vazby ke zveřejnění nového elementu vazby v konfiguraci systému.  
  
6.  Přidejte rozšíření metadata pro komunikaci funkce pro ostatní koncové body.  
  
7.  Přidejte vazbu, která předem nakonfiguruje zásobníku elementů vazby podle dobře definovaný profil. Další informace najdete v tématu [přidání standardní vazbu](#AddingAStandardBinding).  
  
8.  Přidáte oddíl vazby a konfigurace prvku vazby ke zveřejnění vazby ke konfiguraci systému. Další informace najdete v tématu [přidání podpory konfigurace](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 První krok v zápisu vlastní přenosu je rozhodnout, jaké zprávy Exchange vzory (MEPs) jsou požadovány pro přenos. Existují tři MEPs zvolit:  
  
-   Datagram (IInputChannel/IOutputChannel)  
  
     Pokud používáte datagram MEP, klient odešle zprávu pomocí systému exchange "fire a zapomněli". A fire a zapomněli exchange je ten, který vyžaduje out-of-band potvrzení úspěšné doručení. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí službu. Operaci odeslání po úspěšném dokončení na konci klienta, nezaručuje to, že vzdálený koncový bod se zobrazila zpráva. Datagram je základní stavební blok pro zasílání zpráv, jak můžete vytvořit vlastní protokoly nad jeho – včetně protokoly spolehlivé a bezpečné protokoly. Implementace klienta datagram kanály <xref:System.ServiceModel.Channels.IOutputChannel> implementovat rozhraní a služba datagramu kanály <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.  
  
-   Požadavků a odpovědí (třídu IRequestChannel/IReplyChannel)  
  
     V této MEP je odeslána zpráva a odpoví. Vzor se skládá z dvojice požadavků a odpovědí. Volání požadavků a odpovědí příklady vzdálených volání procedur (RPC) a prohlížeč získá. Tento vzor se také označuje jako poloduplexní. V této MEP klienta kanály implementovat <xref:System.ServiceModel.Channels.IRequestChannel> a implementaci služby kanály <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplexní režim (IDuplexChannel)  
  
     Duplexní MEP umožňuje libovolný počet zpráv, které mají být odeslány klientem a přijaté v libovolném pořadí. Duplexní MEP je třeba je telefonní hovor, kde je jednotlivých slov použitém zprávu. Vzhledem k tomu, že na obou stranách můžete odesílat a přijímat v této MEP, rozhraní implementované kanály klienta a služby je <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Každý z těchto MEPs může také podporovat relací. Přidané funkce poskytované službou deklaracemi relace kanál je, že ho korelaci všechny zprávy odeslané a přijaté v kanálu. Vzor požadavků a odpovědí je samostatné relaci dvě zprávy, jako jsou korelační požadavku a odpovědi. Naproti tomu vzor požadavků a odpovědí, který podporuje relací znamená, že všechny páry požadavků a odpovědí v tomto kanálu jsou korelační mezi sebou. To vám dává celkem šest MEPs – Datagram, požadavků a odpovědí, duplexní režim, Datagram s relací, požadavků a odpovědí s relací a duplexní s relací – lze vybírat.  
  
> [!NOTE]
>  Pro přenosu UDP pouze MEP, která je podporována je Datagram, protože UDP je ze své podstaty protokol "fire a zapomněli".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject a životního cyklu objekt WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsahuje běžné stavu počítače, který se používá pro správu životního cyklu objekty jako <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, a <xref:System.ServiceModel.Channels.IChannelListener> používané pro komunikaci. Nejsou k dispozici pět stavy, při kterých může existovat tyto objekty komunikace. Tyto stavy jsou reprezentované pomocí <xref:System.ServiceModel.CommunicationState> výčet a jsou následujícím způsobem:  
  
-   Vytvoří: Toto je stav <xref:System.ServiceModel.ICommunicationObject> při prvním vytvoření instance. V tomto stavu dojde k žádné vstupní a výstupní (I/O).  
  
-   Otevírání: Přechod objekty do tohoto stavu, kdy <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána. Vlastnosti jsou vytvářeny v tomto okamžiku nezměnitelná a můžete začít vstupu a výstupu. Tento přechod je platný pouze z stavu vytvořen.  
  
-   Otevřené: Přechod objekty do tohoto stavu po dokončení procesu otevřete. Tento přechod je platný pouze z otevírání stavu. Objekt je nyní plně použitelné pro přenos.  
  
-   Ukončovací: Přechod objekty do tohoto stavu, kdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána pro řádné vypnutí. Tento přechod je platný pouze z stavu otevřeno.  
  
-   Uzavřené: V poli Uzavřeno stavu objektů již nejsou použitelné. Obecně platí většina konfigurace je stále přístupné pro kontrolu, ale může nastat žádná komunikace. Tento stav je ekvivalentní vyřazována.  
  
-   Faulted: V chybném stavu, jsou objekty přístupné pro kontrolu, ale již není použitelná. Když dojde k nezotavitelnou chybu, objekt přechází do tohoto stavu. Je platné pouze přechod z tohoto stavu do `Closed` stavu.  
  
 Nejsou události, které budou spuštěny pro každý přechod stavu. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metodu lze volat kdykoli a způsobí, že objekt přecházení mezi okamžitě z jeho aktuální stav v uzavřeném stavu. Volání metody <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechna nedokončené práce.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Postup kanálu a naslouchací proces kanálu  
 Dalším krokem při psaní vlastních přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klienta a z <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby. Vrstvy kanálu využívá vzor objekt factory pro vytváření kanálů. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Poskytuje pomocné rutiny základní třídy pro tento proces.  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stav stavového stroje výše popsané v kroku 2. 

-   ''<xref:System.ServiceModel.Channels.ChannelManagerBase> Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídu, která implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a dojde ke konsolidaci `CreateChannel` přetížení do jednoho `OnCreateChannel` abstraktní metodu.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Se má na starosti správu základních stavu.  
  
 V této ukázce implementace objektu factory, je součástí UdpChannelFactory.cs a implementace naslouchací proces je obsažený v UdpChannelListener.cs. <xref:System.ServiceModel.Channels.IChannel> Implementace jsou UdpOutputChannel.cs a UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>UDP kanálu  
 `UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> k poskytování přístupu k zpráva verzi kodér zpráv. Ukázka také přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby jsme přerušit naše instanci <xref:System.ServiceModel.Channels.BufferManager> když přejde stav stavového stroje.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Ověří argumenty konstruktoru a vytvoří cíl <xref:System.Net.EndPoint> na základě objektu <xref:System.ServiceModel.EndpointAddress> , je předaná.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanál je možné uzavřít řádně nebo ungracefully. Pokud je kanál řádně uzavřen soketu se zavře a je volána v základní třídě `OnClose` metoda. Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěna.  
  
```csharp
this.socket.Close(0);  
```  
  
 Potom implementovat `Send()` a `BeginSend()` / `EndSend()`. To rozdělí na dvě hlavní části. Nejprve jsme serializovat zprávy do bajtového pole.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Potom pošleme Výsledná data v drátové síti.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 '' UdpChannelListener, který implementuje ukázce je odvozena z <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy. Pro jediný soket UDP používá pro příjem datagramy. `OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčce. Data jsou potom převedou do zprávy pomocí rozhraní kódování zprávy.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Protože stejné kanálu datagramu představuje zprávy, které přicházejí z mnoha zdrojů, `UdpChannelListener` naslouchací proces typu singleton. Není ve většině, jednu aktivní <xref:System.ServiceModel.Channels.IChannel>'' přidružené k této naslouchací proces najednou. Ukázka generuje jiný pouze v případě, že kanál, který je vrácen rutinou `AcceptChannel` metoda je následně zlikvidován. Při příjmu zprávy je zařazených do fronty do tohoto kanálu, typu singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Třída implementuje `IInputChannel`. Skládá se z fronty příchozích zpráv, které se nacházejí `UdpChannelListener`je soketu. Tyto zprávy jsou vyjmutou pomocí `IInputChannel.Receive` metoda.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Teď, když jsou vytvořeny objekty pro vytváření a kanály, jsme musí vystavit modulu runtime ServiceModel prostřednictvím vazbu. Vazba je kolekci elementů vazby, která reprezentuje komunikačního balíku přidružená adresa služby. Každý prvek v zásobníku je reprezentována [ \<vazby >](../../../../docs/framework/misc/binding.md) element.  
  
 V ukázce je prvku vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Přepíše následující metody pro vytvoření objektů Factory související s naše vazby.  
  
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
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Přidání podpory Metadata pro přenos vazby – Element  
 Při integraci naše přenosu do systému metadata, jsme musí podporovat import a export zásad. To umožňuje vygenerovat klienti naše vazby prostřednictvím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě zodpovídá pro export a import informací o adresách v metadatech. Při použití vazby protokolu SOAP, element vazby přenosu by také exportovat správné přenosu URI v metadatech.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat informace o přidělování `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní. `ExportEndpoint` Metoda přidá správné informace o přidělování do portu WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementace `ExportEndpoint` metoda zároveň exportuje přenos identifikátor URI, pokud koncový bod používá vazbu protokolu SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import schématu WSDL  
 Rozšíření systému importu WSDL pro zpracování importu adres, nemůžeme přidat následující konfigurace konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.  
  
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
  
 Když spustíte Svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst import rozšíření schématu WSDL:  
  
1.  Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.  
  
2.  Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 `UdpBindingElementImporter` Zadejte implementuje `IWsdlImportExtension` rozhraní. `ImportEndpoint` Metoda importuje adresu z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání zásady podpory  
 Vlastní vazby element můžete exportovat zásady kontrolní výrazy ve vazbě WSDL pro koncový bod služby do express možnosti tohoto prvku vazby.  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement` Zadejte implementuje `IPolicyExportExtension` přidání podpory pro export zásad. V důsledku toho `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` při generování zásad u všech vazby, která ji obsahuje.  
  
 V `IPolicyExportExtension.ExportPolicy`, přidáme kontrolní výrazy pro UDP a jiné assertion Pokud Snažíme se v režimu vícesměrového vysílání. Toto je vzhledem k tomu, že má vliv na režimu vícesměrového vysílání jak komunikačního balíku je vytvořený a proto musí být koordinované mezi na obou stranách.  
  
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
  
 Protože elementů přenosové vlastní vazby je zodpovědná za zpracování adresy, `IPolicyExportExtension` implementace na `UdpTransportBindingElement` musí také zpracovat export příslušné WS-Addressing kontrolních výrazů zásad označující verzi adresování WS používá.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásady  
 Rozšířit systém Import zásady, nemůžeme přidat následující konfigurace konfiguračního souboru pro Svcutil.exe jak je znázorněno v souboru Svcutil.exe.config.  
  
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
  
 Pak můžeme implementovat `IPolicyImporterExtension` z našich registrované třídy (`UdpBindingElementImporter`). V `ImportPolicy()`, jsme Projděte kontrolní výrazy v našem oboru názvů a zpracovat těm, které jsou pro generování přenosu a zkontrolujte, zda je vícesměrového vysílání. Také jsme musí odebrat příslušné kontrolní výrazy, které jsme zpracovat ze seznamu vazby kontrolní výrazy. Znovu když spustíte Svcutil.exe, existují dvě možnosti pro integraci:  
  
1.  Bod Svcutil.exe pro naše konfiguračního souboru pomocí /SvcutilConfig:\<souboru >.  
  
2.  Přidejte konfigurační oddíl k Svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Přidání standardní vazby  
 Naše prvku vazby lze použít v následujících dvou způsobů:  
  
-   Prostřednictvím vlastní vazby: vlastní vazby umožňuje uživateli vytvoření vlastní vazby založené na libovolnou sadu elementů vazby.  
  
-   Pomocí vazby poskytované systémem, který zahrnuje naše prvku vazby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje několik z těchto vazeb definovaná systémem, jako `BasicHttpBinding`, `NetTcpBinding`, a `WsHttpBinding`. Každá z těchto vazeb je přidružen k profilu dobře definovaný.  
  
 Ukázka implementuje vazba profilu v `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Obsahuje až čtyři prvky vazeb v něm: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastních standardní vazby – Importér  
 Svcutil.exe a `WsdlImporter` typu, ve výchozím nastavení, rozpozná a importuje definovaná systémem vazby. Jinak získává importovat, protože vazba `CustomBinding` instance. Chcete-li povolit Svcutil.exe a `WsdlImporter` k importu `SampleProfileUdpBinding` `UdpBindingElementImporter` taky funguje jako – Importér vlastní standardní vazby.  
  
 Implementuje – Importér vlastní standardní vazby `ImportEndpoint` metodu `IWsdlImportExtension` rozhraní prozkoumat `CustomBinding` instance importovat z metadat zobrazíte, zda se může vygenerovat konkrétní standardní vazby.  
  
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
  
 Obecně platí implementace – Importér vlastní standardní vazby zahrnuje kontrolu vlastnosti prvky importované vazby pro ověření, že pouze vlastnosti, které by mohly být nastaveny standardní vazbou změnily a všechny ostatní vlastnosti jsou jejich výchozí hodnoty. Základní strategii pro implementaci – Importér standardní vazba je vytvoření instance standardní vazby, rozšířit vlastnosti z elementů vazby standardní vazby instanci, která podporuje standardní vazby a porovnání vazby elementy ze standardní vazba s prvky importované vazby.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Ke zveřejnění naše přenosu prostřednictvím konfigurace, musíme implementovat dvě konfigurační oddíly. První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`. Toto je tak, aby `CustomBinding` implementace může odkazovat naše prvku vazby. Druhý `Configuration` pro naše `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Rozšíření elementu vazby  
 V části `UdpTransportElement` je `BindingElementExtensionElement` která zveřejňuje `UdpTransportBindingElement` v konfiguraci systému. S několika základní přepsání jsme definovali naše název konfiguračního oddílu, typ elementu naše vazby a postup vytvoření naše prvku vazby. Naše oddílu rozšíření jsme pak můžete zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.  
  
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
  
 Rozšíření můžete odkazovat z vlastních vazeb, používat UDP jako přenosu.  
  
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
 V části `SampleProfileUdpBindingCollectionElement` je `StandardBindingCollectionElement` která zveřejňuje `SampleProfileUdpBinding` v konfiguraci systému. Hromadné implementace je delegovaný jako `SampleProfileUdpBindingConfigurationElement`, která je odvozena z `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Má vlastnosti, které odpovídají vlastnosti na `SampleProfileUdpBinding`a funkce pro mapování z `ConfigurationElement` vazby. Nakonec přepsání `OnApplyConfiguration` metoda v našem `SampleProfileUdpBinding`, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 K registraci této obslužné rutiny konfigurace systému, přidáme v následující části relevantní konfiguračního souboru.  
  
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
  
 Potom může být odkaz z serviceModel konfigurační oddíl.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Služba Test UDP a klienta  
 Testovacího kódu pro použití přenosu Tato ukázka je dostupná v adresáři UdpTestService a UdpTestClient. Kód služby se skládá ze dvou testy – jeden test nastaví vazby a koncových bodů z kódu a dalších nemá prostřednictvím konfigurace. Oba testy používají dva koncové body. Používá jeden koncový bod `SampleUdpProfileBinding` s [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) nastavena na `true`. Jiný koncový bod používá vlastní vazby s `UdpTransportBindingElement`. Jde o ekvivalent pomocí `SampleUdpProfileBinding` s [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) nastavena na `false`. Oba testy vytvoření služby, přidat koncový bod pro každou vazbu, otevřete službu a potom počkejte uživatelům před jeho zavřením službu stiskněte ENTER.  
  
 Když spustíte testovací aplikaci služby byste měli vidět následující výstup.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Když pak spustíte test klientská aplikace proti publikované koncových bodů. Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odesílá zprávy pět na každý koncový bod. Následující výstup je v klientovi.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Níže je úplný výstup ve službě.  
  
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
  
 Ke spouštění klientskou aplikaci publikovat pomocí konfigurace koncových bodů, stiskněte ENTER na službu a poté znovu spusťte testovacího klienta. Měli byste vidět následující výstup ve službě.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Znovu spustit klienta vypočítá stejný jako předchozí výsledky.  
  
 Znovu vygenerovat kód klienta a konfigurace pomocí Svcutil.exe, spusťte aplikaci služby a pak spusťte následující Svcutil.exe z kořenového adresáře vzorku.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Všimněte si, že Svcutil.exe negeneruje vazby konfigurace rozšíření pro `SampleProfileUdpBinding`, takže je třeba přidat ji ručně.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Naleznete v předchozí části "UDP testovací služby a klient".  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
