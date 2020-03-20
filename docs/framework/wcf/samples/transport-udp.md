---
title: 'Přenos: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143769"
---
# <a name="transport-udp"></a>Přenos: UDP
Ukázka přenosu UDP ukazuje, jak implementovat jednosměrové a vícesměrové vysílání UDP jako vlastní přenos Windows Communication Foundation (WCF). Ukázka popisuje doporučený postup pro vytvoření vlastní přenos v WCF pomocí rozhraní kanálu a následující WCF osvědčené postupy. Kroky k vytvoření vlastní přenos jsou následující:  
  
1. Rozhodněte, který z kanálu [Vzorky výměny zpráv](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel nebo IReplyChannel) bude podporovat vaše ChannelFactory a ChannelListener. Pak se rozhodněte, zda budete podporovat relace varianty těchto rozhraní.  
  
2. Vytvořte továrnu kanálu a naslouchací proces, který podporuje váš vzor výměny zpráv.  
  
3. Ujistěte se, že všechny výjimky specifické pro síť <xref:System.ServiceModel.CommunicationException>jsou normalizovány na příslušnou odvozenou třídu .  
  
4. Přidejte element [ \<>vazby,](../../configure-apps/file-schema/wcf/bindings.md) který přidá vlastní přenos do zásobníku kanálu. Další informace naleznete [v tématu Přidání elementu vazby](#AddingABindingElement).  
  
5. Přidejte oddíl rozšíření elementu vazby, který zpřístupní nový element vazby do konfiguračního systému.  
  
6. Přidejte rozšíření metadat pro komunikaci schopností s jinými koncovými body.  
  
7. Přidejte vazbu, která předem konfiguruje zásobník prvků vazby podle dobře definovaného profilu. Další informace naleznete [v tématu Přidání standardní vazby](#AddingAStandardBinding).  
  
8. Přidejte oddíl vazby a prvek konfigurace vazby, abyste zpřístupní vazbu konfiguračnímu systému. Další informace naleznete [v tématu Adding Configuration Support](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>Vzory výměny zpráv  
 Prvním krokem při psaní vlastní přenos je rozhodnout, které vzory výměny zpráv (MEPs) jsou požadovány pro přenos. Na výběr jsou tři poslanci:  
  
- Datagram (IInputChannel/IOutputChannel)  
  
     Při použití datagram MEP, klient odešle zprávu pomocí "fire and forget" exchange. Výměna ohně a zapomenout je ten, který vyžaduje mimo-of-band potvrzení úspěšnédodávky. Zpráva může být při přenosu ztracena a nikdy se nedostanete ke službě. Pokud operace odeslání úspěšně dokončena na konci klienta, nezaručuje, že vzdálený koncový bod přijal zprávu. Datagram je základním stavebním kamenem pro zasílání zpráv, protože můžete vytvořit vlastní protokoly na vrcholu - včetně spolehlivých protokolů a zabezpečených protokolů. Kanály datagramu <xref:System.ServiceModel.Channels.IOutputChannel> klienta implementují <xref:System.ServiceModel.Channels.IInputChannel> rozhraní a kanály datagramů služeb implementují rozhraní.  
  
- Požadavek-odpověď (iRequestChannel/iReplyChannel)  
  
     V tomto poslanci EP je odeslána zpráva a je přijata odpověď. Vzor se skládá z dvojice požadavek odpověď. Příklady volání požadavek odpověď jsou vzdálená volání procedur (RPC) a prohlížeče GETs. Tento vzor je také známý jako Half-Duplex. V tomto MEP klientské kanály implementují <xref:System.ServiceModel.Channels.IRequestChannel> a služby implementují <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Duplex (iduplexchannel)  
  
     Duplexní MEP umožňuje libovolný počet zpráv, které mají být odeslány klientem a přijaty v libovolném pořadí. Duplexní europoslanec je jako telefonní rozhovor, kde každé slovo, které se mluví, je zpráva. Vzhledem k tomu, že obě strany mohou odesílat a <xref:System.ServiceModel.Channels.IDuplexChannel>přijímat v tomto MEP, rozhraní implementované klientem a kanály služeb je .  
  
 Každý z těchto poslanců evropského parlamentu může rovněž podpořit zasedání. Přidané funkce poskytované relace podporující kanál je, že koreluje všechny zprávy odeslané a přijaté na kanálu. Vzor požadavek odpověď je samostatná relace dvou zpráv, jako požadavek a odpověď jsou korelovány. Naproti tomu vzor požadavku a odpovědi, který podporuje relace znamená, že všechny páry požadavků a odpovědí na tomto kanálu jsou vzájemně korelovány. Získáte tak celkem šest poslanců – Datagram, Požadavek na odpověď, Oboustranný tisk, Datagram s relacemi, Požadavek na odpověď s relacemi a Oboustranný tisk s relacemi – ze kterých si můžete vybrat.  
  
> [!NOTE]
> Pro přenos UDP je jediným podporovaným mep datagramem, protože Protokol UDP je ze své podstaty protokol "fire and forget".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Životní cyklus objektu ICommunicationObject a objektu WCF  
 WCF má společný stavový počítač, který se používá <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory>pro <xref:System.ServiceModel.Channels.IChannelListener> správu životního cyklu objektů, jako je , a které se používají pro komunikaci. Existuje pět stavů, ve kterých mohou existovat tyto komunikační objekty. Tyto stavy jsou <xref:System.ServiceModel.CommunicationState> reprezentovány výčtu a jsou následující:  
  
- Vytvořeno: Toto je <xref:System.ServiceModel.ICommunicationObject> stav, kdy je první instance. V tomto stavu se nevyskytuje žádný vstup/výstup (V/V).  
  
- Otevření: Objekty přechod <xref:System.ServiceModel.ICommunicationObject.Open%2A> do tohoto stavu, když je volána. V tomto okamžiku jsou vlastnosti neměnné a vstup/výstup může začít. Tento přechod je platný pouze ze stavu Vytvořeno.  
  
- Otevřeno: Objekty přecházejí do tohoto stavu po dokončení otevřeného procesu. Tento přechod je platný pouze ze stavu Otevření. V tomto okamžiku je objekt plně použitelný pro přenos.  
  
- Uzávěrka: Objekty <xref:System.ServiceModel.ICommunicationObject.Close%2A> přechod do tohoto stavu, když se nazývá pro řádné vypnutí. Tento přechod je platný pouze ze stavu Otevřeno.  
  
- Uzavřeno: V uzavřeném stavu objekty již nejsou použitelné. Obecně platí, že většina konfigurace je stále přístupná pro kontrolu, ale nemůže dojít k žádné komunikaci. Tento stav je ekvivalentní vyřazení.  
  
- Chyba: V chybovaném stavu jsou objekty přístupné kontrole, ale již nejsou použitelné. Dojde-li k neobnovitelné chybě, objekt přejde do tohoto stavu. Jediný platný přechod z tohoto `Closed` stavu je do stavu.  
  
 Existují události, které požár u každého přechodu stavu. Metoda <xref:System.ServiceModel.ICommunicationObject.Abort%2A> může být volána kdykoli a způsobí, že objekt přechod okamžitě z aktuálního stavu do stavu Uzavřeno. Volání <xref:System.ServiceModel.ICommunicationObject.Abort%2A> ukončí všechny nedokončené práce.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Factory kanálu a naslouchací proces kanálu  
 Dalším krokem při psaní vlastní přenos je <xref:System.ServiceModel.Channels.IChannelFactory> vytvořit implementaci pro <xref:System.ServiceModel.Channels.IChannelListener> klientské kanály a pro kanály služeb. Vrstva kanálu používá pro vytváření kanálů vzor výroby. WCF poskytuje základní třídy pomocné soubory pro tento proces.  
  
- Třída <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavový počítač, který byl dříve popsán v kroku 2.

- Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> pracuje ve <xref:System.ServiceModel.Channels.ChannelBase>spojení s , což je <xref:System.ServiceModel.Channels.IChannel>základní třída, která implementuje .  
  
- Třída <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.IChannelFactory> a `CreateChannel` konsoliduje `OnCreateChannel` přetížení do jedné abstraktní metody.  
  
- Třída <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Stará se o základní státní řízení.  
  
 V této ukázce je implementace továrny obsažena v UdpChannelFactory.cs a implementace naslouchací proces je obsažena v UdpChannelListener.cs. Implementace <xref:System.ServiceModel.Channels.IChannel> jsou v UdpOutputChannel.cs a UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Továrna kanálu UDP  
 Pochází `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> poskytnout přístup k verzi zprávy kodéru zprávy. Ukázka také <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přepíše, takže můžeme strhnout naši instanci <xref:System.ServiceModel.Channels.BufferManager> při přechodu stavového počítače.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 Nářadí `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor ověří argumenty a vytvoří <xref:System.Net.EndPoint> cílový objekt <xref:System.ServiceModel.EndpointAddress> na základě, který je předán palců  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanál může být uzavřen elegantně nebo ungracefully. Pokud je kanál řádně uzavřen, soket je uzavřen a `OnClose` je provedeno volání metody základní třídy. Pokud to vyvolá výjimku, `Abort` volání infrastruktury k zajištění kanálu je vyčištěna.  
  
```csharp
this.socket.Close(0);  
```  
  
 Pak `Send()` implementujeme a `BeginSend()` / `EndSend()`. To se rozdělí na dvě hlavní části. Nejprve serializujeme zprávu do bajtového pole.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Pak pošleme výsledná data na drátu.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>Naslouchací proces UdpChannelListener  
 Ukázka `UdpChannelListener` implementuje odvodí z třídy. <xref:System.ServiceModel.Channels.ChannelListenerBase> Používá jeden soket UDP pro příjem datagramů. Metoda `OnOpen` přijímá data pomocí soketu UDP v asynchronní smyčce. Data jsou pak převedeny na zprávy pomocí rozhraní pro kódování zpráv.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Vzhledem k tomu, že stejný kanál datagram `UdpChannelListener` představuje zprávy, které přicházejí z několika zdrojů, je naslouchací proces singleton. Je maximálně jeden aktivní <xref:System.ServiceModel.Channels.IChannel> přidružené k tomuto naslouchací proces v době. Vzorek generuje jiný pouze v případě, že `AcceptChannel` kanál, který je vrácen metodou je následně vyřazen. Po přijetí zprávy je zařazendo fronty do tohoto kanálu singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 Třída `UdpInputChannel` implementuje `IInputChannel`. Skládá se z fronty příchozích zpráv, která `UdpChannelListener`je naplněna soketem společnosti . Tyto zprávy jsou dequeued `IInputChannel.Receive` metodou.  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Nyní, když jsou vytvořeny továrny a kanály, musíme vystavit je ServiceModel runtime prostřednictvím vazby. Vazba je kolekce elementů vazby, která představuje zásobník komunikace přidružené k adrese služby. Každý prvek v zásobníku je reprezentován [ \<vazby>](../../configure-apps/file-schema/wcf/bindings.md) prvek.  
  
 Ve vzorku je `UdpTransportBindingElement`prvek vazby , <xref:System.ServiceModel.Channels.TransportBindingElement>který je odvozen od . Přepíše následující metody k vybudování továrny spojené s naší vazby.  
  
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
  
 Obsahuje také členy pro `BindingElement` klonování a vrácení našeho schématu (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Přidání podpory metadat pro prvek vazby přenosu  
 Abychom integrovali náš transport do systému metadat, musíme podporovat jak import, tak export politiky. To nám umožňuje generovat klienty naší vazby prostřednictvím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Přidání podpory WSDL  
 Prvek vazby přenosu ve vazbě je zodpovědný za export a import adresování informací v metadatech. Při použití soap vazby, prvek vazby přenosu by měl také exportovat správný identifikátor URI přenosu v metadatech.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Chcete-li exportovat adresování informace `UdpTransportBindingElement` implementuje `IWsdlExportExtension` rozhraní. Metoda `ExportEndpoint` přidá správné informace o adresování wsdl port.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Implementace `UdpTransportBindingElement` `ExportEndpoint` metody také exportuje identifikátor URI přenosu, pokud koncový bod používá vazbu SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Chcete-li rozšířit systém importu WSDL pro zpracování importu adres, musíme přidat následující konfiguraci do konfiguračního souboru pro Svcutil.exe, jak je znázorněno v souboru Svcutil.exe.config.  
  
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
  
 Při spuštění svcutil.exe, existují dvě možnosti pro získání Svcutil.exe načíst rozšíření importu WSDL:  
  
1. Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.  
  
2. Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
 Typ `UdpBindingElementImporter` implementuje `IWsdlImportExtension` rozhraní. Metoda `ImportEndpoint` importuje adresu z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Přidání podpory zásad  
 Vlastní element vazby můžete exportovat kontrolní výrazy zásad ve vazbě WSDL pro koncový bod služby vyjádřit možnosti tohoto prvku vazby.  
  
#### <a name="policy-export"></a>Export zásad  
 Typ `UdpTransportBindingElement` implementuje `IPolicyExportExtension` přidat podporu pro zásady exportu. V důsledku `System.ServiceModel.MetadataExporter` toho `UdpTransportBindingElement` zahrnuje v generování zásad pro všechny vazby, která ji zahrnuje.  
  
 V `IPolicyExportExtension.ExportPolicy`aplikaci přidáme kontrolní výraz pro UDP a další kontrolní výraz, pokud jsme v režimu vícesměrového vysílání. Důvodem je, že režim vícesměrového vysílání ovlivňuje způsob vytvoření zásobníku komunikace, a proto musí být koordinován mezi oběma stranami.  
  
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
  
 Vzhledem k tomu, že vlastní `IPolicyExportExtension` prvky `UdpTransportBindingElement` vazby přenosu jsou zodpovědné za zpracování adresování, implementace na musí také zpracovat export příslušných výrazů zásad WS-Addressing k označení verze ws adresování se používá.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zásad  
 Chcete-li rozšířit systém importu zásad, musíme přidat následující konfiguraci do konfiguračního souboru pro Svcutil.exe, jak je znázorněno v souboru Svcutil.exe.config.  
  
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
  
 Pak implementujeme `IPolicyImporterExtension` z`UdpBindingElementImporter`naší registrované třídy ( ). V `ImportPolicy()`oblasti se podíváme na kontrolní výrazy v našem oboru názvů a zpracujeme ty, které generují přenos, a zkontrolujeme, zda se jedná o vícesměrové vysílání. Musíme také odebrat tvrzení, které zpracováváme ze seznamu tvrzení vazby. Opět platí, že při spuštění Svcutil.exe existují dvě možnosti integrace:  
  
1. Bod Svcutil.exe do našeho konfiguračního souboru pomocí /SvcutilConfig:\<soubor>.  
  
2. Přidejte oddíl konfigurace do svcutil.exe.config ve stejném adresáři jako Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Přidání standardní vazby  
 Náš vázací prvek lze použít následujícími dvěma způsoby:  
  
- Prostřednictvím vlastní vazby: Vlastní vazba umožňuje uživateli vytvořit vlastní vazbu na základě libovolné sady prvků vazby.  
  
- Pomocí systémově poskytované vazby, která zahrnuje náš element vazby. WCF poskytuje řadu těchto systémem definované vazby, například `BasicHttpBinding`, `NetTcpBinding`a `WsHttpBinding`. Každá z těchto vazeb je spojena s dobře definovaným profilem.  
  
 Ukázka implementuje `SampleProfileUdpBinding`profil vazby <xref:System.ServiceModel.Channels.Binding>v , který je odvozen z . Obsahuje `SampleProfileUdpBinding` v něm až čtyři `UdpTransportBindingElement`elementy vazby: , `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Přidání vlastního standardního importu vazeb  
 Svcutil.exe a `WsdlImporter` typ ve výchozím nastavení rozpozná a importuje systémem definované vazby. V opačném případě vazba `CustomBinding` získá importován jako instance. Chcete-li povolit Svcutil.exe `SampleProfileUdpBinding` `UdpBindingElementImporter` a `WsdlImporter` importovat také působí jako vlastní standardní vázací dovozce.  
  
 Vlastní standardní importér `ImportEndpoint` vazby `IWsdlImportExtension` implementuje `CustomBinding` metodu na rozhraní prozkoumat instanci importované z metadat a zjistit, zda mohla být generována konkrétní standardní vazby.  
  
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
  
 Obecně platí, že implementace vlastní standardní vazby import zahrnuje kontrolu vlastností importované elementy vazby k ověření, že pouze vlastnosti, které mohly být nastaveny standardní vazby byly změněny a všechny ostatní vlastnosti jsou jejich výchozí hodnoty. Základní strategií pro implementaci standardního importu vazby je vytvoření instance standardní vazby, šíření vlastností z elementů vazby na standardní instanci vazby, kterou podporuje standardní vazba, a porovnání vazby prvky ze standardní vazby s importovanými prvky vazby.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Chcete-li vystavit náš přenos prostřednictvím konfigurace, musíme implementovat dvě části konfigurace. První je `BindingElementExtensionElement` pro `UdpTransportBindingElement`. To je `CustomBinding` tak, že implementace můžete odkazovat na náš element vazby. Druhý je `Configuration` pro `SampleProfileUdpBinding`naše .  
  
### <a name="binding-element-extension-element"></a>Element rozšíření prvku vazby  
 Sekce `UdpTransportElement` `BindingElementExtensionElement` je, která `UdpTransportBindingElement` zpřístupňuje konfiguračnísystém. Pomocí několika základních přepsání definujeme název konfiguračního oddílu, typ našeho prvku vazby a způsob vytvoření prvku vazby. Naši příponou pak můžeme zaregistrovat v konfiguračním souboru, jak je znázorněno v následujícím kódu.  
  
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
  
 Rozšíření lze odkazovat z vlastní vazby použít UDP jako přenos.  
  
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
  
### <a name="binding-section"></a>Oddíl vazby  
 Sekce `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` je, která `SampleProfileUdpBinding` zpřístupňuje konfiguračnísystém. Převážná část implementace je delegována `SampleProfileUdpBindingConfigurationElement`na `StandardBindingElement`, který je odvozen z . Má `SampleProfileUdpBindingConfigurationElement` vlastnosti, které odpovídají `SampleProfileUdpBinding`vlastnosti na , `ConfigurationElement` a funkce mapovat z vazby. Nakonec přepsat metodu `OnApplyConfiguration` v `SampleProfileUdpBinding`našem , jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Chcete-li zaregistrovat tuto obslužnou rutinu v konfiguračním systému, přidáme do příslušného konfiguračního souboru následující část.  
  
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
  
 Potom lze odkazovat z části konfigurace serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Testovací služba UDP a klient  
 Testovací kód pro použití tohoto ukázkového přenosu je k dispozici v adresářích UdpTestService a UdpTestClient. Kód služby se skládá ze dvou testů – jeden test nastaví vazby a koncové body z kódu a druhý to provede prostřednictvím konfigurace. Oba testy používají dva koncové body. Jeden koncový bod `SampleUdpProfileBinding` používá s [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `true`. Druhý koncový bod používá vlastní `UdpTransportBindingElement`vazbu s . To je ekvivalentní `SampleUdpProfileBinding` použití s [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) nastavena na `false`. Oba testy vytvoří službu, přidají koncový bod pro každou vazbu, otevřou službu a před ukončením služby počkáte na klávesu ENTER.  
  
 Při spuštění aplikace test služby byste měli vidět následující výstup.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Potom můžete spustit testovací klientskou aplikaci proti publikovaným koncovým bodům. Testovací aplikace klienta vytvoří klienta pro každý koncový bod a odešle pět zpráv do každého koncového bodu. Následující výstup je na straně klienta.  
  
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
  
 Chcete-li spustit klientskou aplikaci proti koncovým bodům publikovaným pomocí konfigurace, stiskněte klávesu ENTER ve službě a spusťte testovacího klienta znovu. Měli byste vidět následující výstup na službu.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Spuštění klienta znovu dává stejné jako předchozí výsledky.  
  
 Chcete-li znovu vygenerovat klientský kód a konfiguraci pomocí programu Svcutil.exe, spusťte aplikaci služby a spusťte následující soubor Svcutil.exe z kořenového adresáře ukázky.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Všimněte si, že Svcutil.exe negeneruje `SampleProfileUdpBinding`konfiguraci rozšíření vazby pro , takže je nutné přidat ručně.  
  
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
  
1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Odkazovat na předchozí části "Testovací služba UDP a klienta".  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
