---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 44e47dd2d291ffc27d1777a04b645d57984919cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591433"
---
# <a name="transport-udp"></a>Přenos: UDP
Ukázka přenosu UDP demonstruje, jak implementovat jednosměrovou vysílání UDP a vícesměrové vysílání jako vlastní přenos Windows Communication Foundation (WCF). Ukázka popisuje doporučený postup pro vytvoření vlastního přenosu ve službě WCF pomocí architektury kanálů a následujících osvědčených postupů pro WCF. Postup vytvoření vlastního přenosu je následující:  
  
1. Rozhodněte, které ze [vzorů výměny zpráv](#MessageExchangePatterns) kanálu (IOutputChannel, IInputChannel, IDuplexChannel, třídu IRequestChannel nebo IReplyChannel) bude vaše třída ChannelFactory a ChannelListener podporovat. Pak se rozhodněte, jestli budete podporovat variace relace těchto rozhraní.  
  
2. Vytvořte objekt pro vytváření a naslouchací proces kanálu, který podporuje váš vzor výměny zpráv.  
  
3. Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na příslušnou odvozenou třídu třídy <xref:System.ServiceModel.CommunicationException> .  
  
4. Přidejte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, který přidá vlastní přenos do zásobníku kanálů. Další informace naleznete v tématu [Přidání prvku vazby](#AddingABindingElement).  
  
5. Přidejte část rozšíření elementu vazby, která zpřístupňuje nový prvek vazby na konfigurační systém.  
  
6. Přidejte rozšíření metadat pro komunikaci s funkcemi do jiných koncových bodů.  
  
7. Přidejte vazbu, která předem nakonfiguruje zásobník prvků vazby podle dobře definovaného profilu. Další informace najdete v tématu [Přidání standardní vazby](#AddingAStandardBinding).  
  
8. Přidáním oddílu vazby a elementu konfigurace vazby zpřístupníte vazbu ke konfiguračnímu systému. Další informace najdete v tématu [Přidání podpory konfigurace](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>Vzorce výměny zpráv  
 Prvním krokem při psaní vlastního přenosu je rozhodování o tom, které vzory výměny zpráv (MEPs) jsou pro přenos povinné. Existují tři MEPsy, ze kterých si můžete vybrat:  
  
- Datagram (IInputChannel/IOutputChannel)  
  
     Při použití dataMEP datagramu pošle klient zprávu s výměnou "Fire and zapomene". Výměna požáru a zapomenutí je taková, která vyžaduje vzdálené potvrzení úspěšného doručení. Zpráva může být ztracena při přenosu a nikdy se nespojit se službou. Pokud se operace odeslání na konci klienta úspěšně dokončí, nezaručuje, že vzdálený koncový bod obdrží zprávu. Datagram je základní stavební blok pro zasílání zpráv, protože můžete sestavovat vlastní protokoly nad ním, včetně spolehlivých protokolů a zabezpečených protokolů. Kanály datagramů klienta implementují rozhraní <xref:System.ServiceModel.Channels.IOutputChannel> a kanály Datagram Service implementující <xref:System.ServiceModel.Channels.IInputChannel> rozhraní.  
  
- Požadavek-odpověď (třídu IRequestChannel/IReplyChannel)  
  
     V tomto MEP zpráva se pošle a odpověď se přijme. Vzor se skládá z párů požadavků a odpovědí. Příklady volání požadavků a odpovědí jsou vzdálená volání procedur (RPC) a prohlížeč. Tento model se také označuje jako poloduplexní. V tomto MEP implementují klientské kanály <xref:System.ServiceModel.Channels.IRequestChannel> a implementuje kanály pro služby <xref:System.ServiceModel.Channels.IReplyChannel> .  
  
- Duplexní přenos (IDuplexChannel)  
  
     Duplexní MEP umožňuje klientovi poslat libovolný počet zpráv a přijatý v libovolném pořadí. Duplexní MEP je jako telefonická konverzace, kde každé mluvené slovo je zpráva. Vzhledem k tomu, že obě strany mohou v tomto MEP odesílat a přijímat, rozhraní implementované kanály klienta a služby je <xref:System.ServiceModel.Channels.IDuplexChannel> .  
  
 Každý z těchto MEPs může také podporovat relace. Přidaná funkce poskytovaná kanálem podporujícím relaci je to, že koreluje všechny zprávy odesílané a přijímané na kanálu. Vzor požadavků a odpovědí je samostatná relace dvou zpráv, protože se jedná o korelační požadavek a odpověď. Oproti tomu vzor požadavek-odpověď, který podporuje relace, implikuje vzájemnou korelaci mezi všemi páry požadavků a odpovědí na daném kanálu. Získáte tak celkem šest MEPs – datagram, požadavek-odpověď, duplexní, datagram s relacemi, požadavek-odpověď s relacemi a duplexní s relacemi – pro výběr z.  
  
> [!NOTE]
> Pro přenos UDP je jedinou podporovanou MEP datagram, protože UDP je ze své podstaty protokolem "oheň a zapomenout".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Životní cyklus objekt ICommunicationObject a objektu WCF  
 WCF má společný Stavový počítač, který se používá ke správě životního cyklu objektů <xref:System.ServiceModel.Channels.IChannel> , jako jsou, <xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener> používané pro komunikaci. Existuje pět stavů, ve kterých tyto komunikační objekty můžou existovat. Tyto stavy jsou reprezentovány <xref:System.ServiceModel.CommunicationState> výčtem a jsou následující:  
  
- Vytvořeno: Jedná se o stav <xref:System.ServiceModel.ICommunicationObject> při prvním vytvoření instance. V tomto stavu se nevyskytují vstupně-výstupní operace (v/v).  
  
- Otevření: objekty přecházejí do tohoto stavu, když <xref:System.ServiceModel.ICommunicationObject.Open%2A> je volána metoda. V tomto okamžiku jsou vlastnosti neměnné a vstupní/výstupní může začít. Tento přechod je platný pouze ze stavu Created (vytvořeno).  
  
- Otevřené: po dokončení otevřeného procesu převede objekty do tohoto stavu. Tento přechod je platný jenom z počátečního stavu. V tomto okamžiku je objekt plně použitelný pro přenos.  
  
- Uzavírání: probíhá přechod objektů do tohoto stavu, když <xref:System.ServiceModel.ICommunicationObject.Close%2A> je volána pro řádné vypnutí. Tento přechod je platný jenom z otevřeného stavu.  
  
- Uzavřeno: objekty uzavřených stavů již nejsou použitelné. Obecně platí, že většina konfigurací je stále k dispozici pro kontrolu, ale nemůžete k tomu dojít k žádné komunikaci. Tento stav je stejný jako vyřazený.  
  
- Došlo k chybě: v chybovém stavu jsou objekty přístupné pro kontrolu, ale již nejsou použitelné. Pokud dojde k neobnovitelné chybě, objekt přejde do tohoto stavu. Jediný platný přechod z tohoto stavu je do `Closed` stavu.  
  
 Existují události, které se aktivují pro každý přechod stavu. <xref:System.ServiceModel.ICommunicationObject.Abort%2A>Metodu lze volat kdykoli a způsobí, že se objekt přenese hned z aktuálního stavu do zavřeného stavu. Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Modul pro vytváření kanálů a naslouchací proces kanálu  
 Dalším krokem při psaní vlastního přenosu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály a <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby. Vrstva kanálu používá model továrny pro vytváření kanálů. WCF poskytuje pomocníky pro základní třídy pro tento proces.  
  
- <xref:System.ServiceModel.Channels.CommunicationObject>Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač dříve popsaný v kroku 2.

- <xref:System.ServiceModel.Channels.ChannelManagerBase>Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje sjednocenou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase> . <xref:System.ServiceModel.Channels.ChannelManagerBase>Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase> , což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel> .  
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase>Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.  
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase>Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener> . Je potřeba se starat o základní správu stavu.  
  
 V této ukázce je implementace továrny obsažena v UdpChannelFactory.cs a implementace naslouchacího procesu je obsažena v UdpChannelListener.cs. <xref:System.ServiceModel.Channels.IChannel>Implementace jsou v UdpOutputChannel.cs a UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Objekt pro vytváření kanálů UDP  
 Je `UdpChannelFactory` odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase> . Vzor přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> , aby poskytoval přístup k verzi zprávy kodéru zpráv. Ukázka také přepisuje, aby bylo <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> možné odtrhnout naši instanci <xref:System.ServiceModel.Channels.BufferManager> při přechodu stavového stroje.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel`Implementuje rozhraní <xref:System.ServiceModel.Channels.IOutputChannel> . Konstruktor ověřuje argumenty a vytvoří cílový <xref:System.Net.EndPoint> objekt na základě <xref:System.ServiceModel.EndpointAddress> předaného objektu.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanál může být řádně uzavřený nebo neřádný. Pokud je kanál řádně uzavřený, soket je uzavřen a volání metody základní třídy je provedeno `OnClose` . Pokud to vyvolá výjimku, zavolá infrastruktura, aby `Abort` zajistila vyčištění kanálu.  
  
```csharp
this.socket.Close(0);  
```  
  
 Následně implementujeme `Send()` a `BeginSend()` / `EndSend()` . Tato část se rozdělí na dvě hlavní části. Nejdřív jsme tuto zprávu serializováni do pole bajtů.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Pak pošleme výsledná data na kabel.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 Rozhraní `UdpChannelListener` , které ukázka implementuje, je odvozena od <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy. K příjmu datagramů používá jeden soket UDP. `OnOpen`Metoda přijímá data pomocí soketu UDP v asynchronní smyčce. Data se pak převedou na zprávy pomocí architektury kódování zpráv.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Vzhledem k tomu, že stejný kanál datagram představuje zprávy, které přicházejí z řady zdrojů, `UdpChannelListener` je naslouchací proces typu singleton. K <xref:System.ServiceModel.Channels.IChannel> tomuto naslouchacímu procesu je v jednu chvíli přidružená maximálně jedna aktivní služba. Ukázka vygeneruje další pouze v případě, že kanál vrácený `AcceptChannel` metodou je následně vyřazen. Po přijetí zprávy se do tohoto kanálu singleton zařazování do fronty.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel`Třída implementuje `IInputChannel` . Skládá se z fronty příchozích zpráv, které jsou vyplněny `UdpChannelListener` soketem. Tyto zprávy jsou odřazeny `IInputChannel.Receive` metodou.  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Teď, když jsou továrny a kanály sestavené, je nutné je vystavit modulu runtime ServiceModel prostřednictvím vazby. Vazba je kolekce elementů vazby, které představují komunikační zásobník přidružený k adrese služby. Každý prvek v zásobníku je reprezentován [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvkem.  
  
 V ukázce je prvek vazby `UdpTransportBindingElement` , který je odvozen z <xref:System.ServiceModel.Channels.TransportBindingElement> . Přepíše následující metody pro sestavení továrn přidružených k naší vazbě.  
  
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
  
 Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (SOAP. UDP).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Přidání podpory metadat pro element transportní vazby  
 Pro integraci našeho přenosu do systému metadat musíme podporovat import i export zásad. To nám umožňuje vygenerovat klienty naší vazby prostřednictvím nástroje pro dodávání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Element vazby přenosu ve vazbě zodpovídá za export a import informací o adresách v metadatech. Při použití vazby SOAP by měl element vazby přenosu také exportovat správný přenosový identifikátor URI v metadatech.  
  
#### <a name="wsdl-export"></a>Export WSDL  
 Chcete-li exportovat informace o adresách, `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní. `ExportEndpoint`Metoda přidá správné informace o adresování do portu WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement`Implementace `ExportEndpoint` metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import WSDL  
 Pro rozšiřování systému importu WSDL pro zpracování importu adres je nutné přidat následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config.  
  
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
  
 Při spuštění Svcutil. exe jsou k dispozici dvě možnosti, jak Svcutil. exe načíst rozšíření importu WSDL:  
  
1. Najeďte Svcutil. exe na náš konfigurační soubor pomocí/SvcutilConfig: \<file> .  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
 `UdpBindingElementImporter`Typ implementuje `IWsdlImportExtension` rozhraní. `ImportEndpoint`Metoda importuje adresu z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory zásad  
 Vlastní element vazby může exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby, aby bylo možné vyjádřit možnosti tohoto prvku vazby.  
  
#### <a name="policy-export"></a>Export zásad  
 `UdpTransportBindingElement`Typ implementuje `IPolicyExportExtension` k přidání podpory pro export zásad. Výsledkem je, že `System.ServiceModel.MetadataExporter` zahrnuje `UdpTransportBindingElement` generování zásad pro všechny vazby, které ji obsahují.  
  
 V nástroji `IPolicyExportExtension.ExportPolicy` přidáme kontrolní výraz pro UDP a jiný kontrolní výraz, pokud je v režimu vícesměrového vysílání. Je to proto, že režim vícesměrového vysílání ovlivňuje způsob, jakým je vytvořen komunikační zásobník, a proto musí být koordinován mezi oběma stranami.  
  
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
  
 Vzhledem k tomu, že vlastní prvky vazby přenosu jsou zodpovědné za zpracování adresování, `IPolicyExportExtension` implementace v `UdpTransportBindingElement` musí také zpracovávat příslušné kontrolní výrazy WS-Addressing, aby označovaly verzi WS-Addressing, která se používá.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásad  
 Pro rozšiřování systému pro import zásad je nutné přidat následující konfiguraci do konfiguračního souboru pro Svcutil. exe, jak je znázorněno v souboru Svcutil. exe. config.  
  
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
  
 Pak implementujeme `IPolicyImporterExtension` z naší registrované třídy ( `UdpBindingElementImporter` ). V nástroji `ImportPolicy()` se podíváme na kontrolní výrazy v našem oboru názvů a zpracujeme je pro generování přenosu a kontrolu, jestli se jedná o vícesměrové vysílání. Je také nutné odebrat kontrolní výrazy, které zpracováváme ze seznamu kontrolních výrazů vazby. Při spuštění Svcutil. exe existují dvě možnosti integrace:  
  
1. Najeďte Svcutil. exe na náš konfigurační soubor pomocí/SvcutilConfig: \<file> .  
  
2. Přidejte konfigurační oddíl do souboru Svcutil. exe. config ve stejném adresáři jako soubor Svcutil. exe.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Přidání standardní vazby  
 Náš element vazby lze použít následujícími dvěma způsoby:  
  
- Pomocí vlastní vazby: vlastní vazba umožňuje uživateli vytvořit vlastní vazbu založenou na libovolné sadě prvků vazby.  
  
- Pomocí systémové vazby, která zahrnuje náš element vazby. WCF poskytuje řadu těchto vazeb definovaných systémem, jako například `BasicHttpBinding` , `NetTcpBinding` a `WsHttpBinding` . Každá z těchto vazeb je přidružená k dobře definovanému profilu.  
  
 Ukázka implementuje vazbu profilu v `SampleProfileUdpBinding` , která je odvozena z <xref:System.ServiceModel.Channels.Binding> . `SampleProfileUdpBinding`Obsahuje až čtyři prvky vazby v rámci něj: `UdpTransportBindingElement` , `TextMessageEncodingBindingElement CompositeDuplexBindingElement` a `ReliableSessionBindingElement` .  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastního programu pro import standardních vazeb  
 Svcutil. exe a `WsdlImporter` typ ve výchozím nastavení rozpoznává a importuje vazby definované systémem. V opačném případě se vazba naimportuje jako `CustomBinding` instance. Chcete-li povolit Svcutil. exe a `WsdlImporter` importovat `SampleProfileUdpBinding` `UdpBindingElementImporter` také jako vlastní import standardních vazeb.  
  
 Vlastní nástroj pro import standardních vazeb implementuje `ImportEndpoint` metodu na `IWsdlImportExtension` rozhraní, aby prověřil `CustomBinding` instanci importovanou z metadat, aby bylo možné zjistit, zda mohla být vygenerována konkrétní standardní vazbou.  
  
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
  
 Obecně implementace vlastního programu pro importování standardní vazby zahrnuje kontrolu vlastností importovaných prvků vazby, aby bylo možné ověřit, zda byly změněny pouze vlastnosti, které by mohly být nastaveny standardní vazbou, a všechny ostatní vlastnosti jsou jejich výchozími hodnotami. Základní strategií pro implementaci importu standardních vazeb je vytvoření instance standardní vazby, šíření vlastností z prvků vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnáním prvků vazby z standardní vazby s importovanými prvky vazby.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Abychom mohli naše přenosy zveřejnit prostřednictvím konfigurace, je nutné implementovat dva konfigurační oddíly. První je `BindingElementExtensionElement` pro `UdpTransportBindingElement` . To je tak proto, že `CustomBinding` implementace mohou odkazovat na náš element vazby. Druhý je `Configuration` pro náš `SampleProfileUdpBinding` .  
  
### <a name="binding-element-extension-element"></a>Element rozšíření elementu vazby  
 Oddíl `UdpTransportElement` `BindingElementExtensionElement` , který zveřejňuje `UdpTransportBindingElement` konfiguračnímu systému. Při několika základních přepsáních definujeme název konfiguračního oddílu, typ našeho prvku vazby a postup vytvoření prvku vazby. Náš oddíl rozšíření můžeme zaregistrovat do konfiguračního souboru, jak je znázorněno v následujícím kódu.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport" />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Na rozšíření se dá odkazovat z vlastních vazeb na použití UDP jako přenosu.  
  
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
  
### <a name="binding-section"></a>Oddíl Binding  
 Oddíl `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` , který zveřejňuje `SampleProfileUdpBinding` konfiguračnímu systému. Hromadná implementace je delegována na `SampleProfileUdpBindingConfigurationElement` , který je odvozen z `StandardBindingElement` . `SampleProfileUdpBindingConfigurationElement`Obsahuje vlastnosti, které odpovídají vlastnostem na `SampleProfileUdpBinding` , a funkce, které mají být mapovány z `ConfigurationElement` vazby. Nakonec přepište `OnApplyConfiguration` metodu v našem `SampleProfileUdpBinding` , jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 K registraci této obslužné rutiny v konfiguračním systému přidáme následující oddíl do příslušného konfiguračního souboru.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Pak na něj můžete odkazovat z oddílu konfigurace serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Testovací služba a klient UDP  
 Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích UdpTestService a UdpTestClient. Kód služby se skládá ze dvou testů – jeden test nastaví vazby a koncové body z kódu a druhý provede konfiguraci. Oba testy používají dva koncové body. Jeden koncový bod používá `SampleUdpProfileBinding` [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) sadu s nastavenou na `true` . Druhý koncový bod používá vlastní vazbu s `UdpTransportBindingElement` . Jedná se o ekvivalent použití `SampleUdpProfileBinding` s [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavením na `false` . Oba testy vytvoří službu, přidejte koncový bod pro každou vazbu, otevřete službu a potom počkejte, než uživatel před zavřením služby zahájí zadání.  
  
 Při spuštění aplikace testování služby by se měl zobrazit následující výstup.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Pak můžete spustit testovací klientskou aplikaci proti publikovaným koncovým bodům. Aplikace test klienta vytvoří klienta pro každý koncový bod a odešle pět zpráv do každého koncového bodu. Následující výstup je na klientovi.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Následuje úplný výstup služby.  
  
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
  
 Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER ve službě a spusťte testovacího klienta znovu. Ve službě by se měl zobrazit následující výstup.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Po opětovném spuštění klienta bude výsledek stejný jako u předchozích výsledků.  
  
 Chcete-li znovu vygenerovat kód klienta a konfiguraci pomocí nástroje Svcutil. exe, spusťte aplikaci služby a spusťte následující soubor Svcutil. exe z kořenového adresáře ukázky.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Všimněte si, že Svcutil. exe negeneruje konfiguraci rozšíření vazby pro `SampleProfileUdpBinding` , takže je potřeba ho přidat ručně.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
3. Přečtěte si předchozí část "testovací služba a klient protokolu UDP".  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
