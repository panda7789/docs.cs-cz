---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7b436e2ce708a122a7eae3b07ad01515fb2dce96
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463969"
---
# <a name="chunking-channel"></a>Kanál s dělením dat do bloků

Při odesílání velkých zpráv pomocí Windows Communication Foundation (WCF), je často žádoucí omezit množství paměti používané k ukládání těchto zpráv do vyrovnávací paměti. Jedním z možných řešení je streamovat text zprávy (za předpokladu, že většina dat je v těle). Některé protokoly však vyžadují ukládání do vyrovnávací paměti celé zprávy. Spolehlivé zasílání zpráv a zabezpečení jsou dva takové příklady. Dalším možným řešením je rozdělit velké zprávy do menších zpráv s názvem bloky, odeslat tyto bloky jeden blok najednou a rekonstruovat velké zprávy na straně příjmu. Samotná aplikace může provést tento bloků a de-chunking nebo může použít vlastní kanál k tomu. Ukázka kanálu bloků ukazuje, jak vlastní protokol nebo vrstvený kanál lze použít k provádění bloků a odstranění bloků libovolně velkých zpráv.

Bloků by měla být vždy použita pouze po vytvoření celé zprávy, která má být odeslána. Kanál bloků by měl být vždy vrstvený pod kanálem zabezpečení a spolehlivým kanálem relace.

> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Předpoklady a omezení bloků kanálu

### <a name="message-structure"></a>Struktura zpráv

Kanál bloků předpokládá následující strukturu zpráv pro zprávy, které mají být bloků dat:

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

Při použití ServiceModel, operace smlouvy, které mají 1 vstupní parametr v souladu s tímto obrazcem zprávy pro jejich vstupní zprávy. Podobně smlouvy operace, které mají 1 výstupní parametr nebo vrácená hodnota v souladu s tímto obrazcem zprávy pro jejich výstupní zprávy. Následují příklady těchto operací:

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    Stream EchoStream(Stream stream);

    [OperationContract]
    Stream DownloadStream();

    [OperationContract(IsOneWay = true)]
    void UploadStream(Stream stream);
}
```

### <a name="sessions"></a>Relace

Kanál bloků vyžaduje, aby zprávy byly doručeny přesně jednou, v objednaném doručování zpráv (bloků). To znamená, že základní zásobník kanálu musí být relace. Relace mohou být poskytovány přenosem (například přenost CP) nebo kanálem protokolu relace (například kanál ReliableSession).

### <a name="asynchronous-send-and-receive"></a>Asynchronní odesílání a přijímání

Asynchronní metody odesílání a přijímání nejsou implementovány v této verzi ukázky kanálu bloků.

## <a name="chunking-protocol"></a>Protokol bloků

Kanál bloků definuje protokol, který označuje začátek a konec řady bloků dat a pořadové číslo každého bloku. Následující tři ukázkové zprávy ukazují počáteční, blok a konec zprávy s komentáři, které popisují klíčové aspekty každého.

### <a name="start-message"></a>Spustit zprávu

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>
<!--
Original message is assigned a unique id that is transmitted
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.
-->
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">
53f183ee-04aa-44a0-b8d3-e45224563109
</MessageId>
<!--
ChunkingStart header signals the start of a chunked message.
-->
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />
<!--
Original message action is transmitted in OriginalAction.
This is required to re-create the original message on the other side.
-->
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">
http://tempuri.org/ITestService/EchoStream
    </OriginalAction>
   <!--
    All original message headers are included here.
   -->
  </s:Header>
  <s:Body>
<!--
Chunking assumes this structure of Body content:
<element>
  <childelement>large data to be chunked<childelement>
</element>
The start message contains just <element> and <childelement> without
the data to be chunked.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

### <a name="chunk-message"></a>Zpráva bloku

```xml
<s:Envelope
  xmlns:a="http://www.w3.org/2005/08/addressing"
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
   <!--
    All chunking protocol messages have this action.
   -->
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
The sequence number of the chunk.
This number restarts at 1 with each new sequence of chunks.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      1096
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The chunked data is wrapped in a chunk element.
The encoding of this data (and the entire message)
depends on the encoder used. The chunking channel does not mandate an encoding.
-->
    <chunk xmlns="http://samples.microsoft.com/chunking">
kfSr2QcBlkHTvQ==
    </chunk>
  </s:Body>
</s:Envelope>
```

### <a name="end-message"></a>Ukončit zprávu

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
ChunkingEnd header signals the end of a chunk sequence.
-->
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"
                 xmlns="http://samples.microsoft.com/chunking" />
<!--
ChunkingEnd messages have a sequence number.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      79
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The ChunkingEnd message has the same <element><childelement> structure
as the ChunkingStart message.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

## <a name="chunking-channel-architecture"></a>Architektura kanálu bloků

Kanál bloků je, `IDuplexSessionChannel` že na vysoké úrovni následuje typickou architekturu kanálu. Tam `ChunkingBindingElement` je, že `ChunkingChannelFactory` může `ChunkingChannelListener`stavět a . Vytvoří `ChunkingChannelFactory` instance, `ChunkingChannel` kdy je požádán. Vytvoří `ChunkingChannelListener` instance, `ChunkingChannel` kdy je přijat nový vnitřní kanál. Sám `ChunkingChannel` je zodpovědný za odesílání a přijímání zpráv.

Na další úroveň `ChunkingChannel` dolů, spoléhá na několik součástí k implementaci bloku protokolu. Na straně odeslání kanál používá <xref:System.Xml.XmlDictionaryWriter> vlastní `ChunkingWriter` volané, který provádí skutečné bloků. `ChunkingWriter`používá vnitřní kanál přímo k odesílání bloků dat. Použití vlastní `XmlDictionaryWriter` nám umožňuje vyslat bloky jako velké tělo původní zprávy je psáno. To znamená, že nebudeme do vyrovnávací paměti celou původní zprávu.

![Diagram, který ukazuje architekturu odesílání kanálu bloků.](./media/chunking-channel/chunking-channel-send.gif)

Na straně příjmu `ChunkingChannel` vytáhne zprávy z vnitřního kanálu <xref:System.Xml.XmlDictionaryReader> a `ChunkingReader`předá je vlastní volal , který rekonstituuje původní zprávy z příchozí bloky. `ChunkingChannel`zabalí `ChunkingReader` to ve `Message` vlastní `ChunkingMessage` implementaci s názvem a vrátí tuto zprávu do výše uvedené vrstvy. Tato kombinace `ChunkingReader` `ChunkingMessage` a umožňuje nám de-chunk původní text zprávy, jak je čteno vrstvou výše namísto nutnosti vyrovnávací paměti celé původní text zprávy. `ChunkingReader`má frontu, kde vyrovnávací paměti příchozí bloky až do maximálního konfigurovatelného počtu bloků vyrovnávací paměti. Po dosažení tohoto maximálního limitu čtenář čeká na zprávy, které mají být vyprázdněny z fronty vrstvou výše (to znamená, že pouze čtení z původního textu zprávy) nebo dokud není dosaženo maximálního časového limitu příjmu.

![Diagram, který ukazuje blokovací kanál přijímat architekturu.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Blokovací programovací model

Vývojáři služeb můžete určit, které zprávy `ChunkingBehavior` mají být bloků dat pomocí atributu operace v rámci smlouvy. Atribut zpřístupňuje `AppliesTo` vlastnost, která umožňuje vývojáři určit, zda bloing platí pro vstupní zprávu, výstupní zprávu nebo obojí. Následující příklad ukazuje použití `ChunkingBehavior` atributu:

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.Both)]
    Stream EchoStream(Stream stream);

    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]
    Stream DownloadStream();

    [OperationContract(IsOneWay=true)]
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]
    void UploadStream(Stream stream);

}
```

Z tohoto programovacího `ChunkingBindingElement` modelu zkompiluje seznam identifikátorů URI akce, které identifikují zprávy, které mají být odebrány. Akce každé odchozí zprávy je porovnán s tímto seznamem k určení, zda má být zpráva na bloky dat nebo odeslané přímo.

## <a name="implementing-the-send-operation"></a>Implementace operace odeslání

Na vysoké úrovni Send operace nejprve zkontroluje, zda odchozí zpráva musí být na bloky dat a pokud ne, odešle zprávu přímo pomocí vnitřníkanál.

Pokud zpráva musí být bloků, Send `ChunkingWriter` vytvoří `WriteBodyContents` nový a volá na `ChunkingWriter`odchozí zprávy předání tohoto . Potom `ChunkingWriter` se zpráva bloků (včetně kopírování záhlaví původní zprávy na počáteční zprávu bloku) a odešle bloky pomocí vnitřního kanálu.

Několik detailů stojí za zmínku:

- Odešlete `ThrowIfDisposedOrNotOpened` první `CommunicationState` volání, abyste se ujistili, že je otevřen.

- Odesílání je synchronizováno tak, aby bylo možné odeslat pouze jednu zprávu pro každou relaci. Je `ManualResetEvent` název, `sendingDone` který je resetován při odeslání zprávy bloku. Po odeslání zprávy koncového bloku je tato událost nastavena. Send Metoda čeká na tuto událost, která má být nastavena před pokusem o odeslání odchozí zprávy.

- Odeslat `CommunicationObject.ThisLock` zámky zabránit synchronizované změny stavu při odesílání. Další <xref:System.ServiceModel.Channels.CommunicationObject> informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavech a stavovém počítači naleznete v dokumentaci.

- Časový čas předaný odeslat se používá jako časový časový výtok pro celou operaci odeslání, která zahrnuje odeslání všech bloků.

- Vlastní <xref:System.Xml.XmlDictionaryWriter> návrh byl vybrán, aby se zabránilo ukládání do vyrovnávací paměti celé původní tělo zprávy. Pokud bychom měli <xref:System.Xml.XmlDictionaryReader> dostat na `message.GetReaderAtBodyContents` tělo pomocí celého těla by se pufrované. Místo toho máme <xref:System.Xml.XmlDictionaryWriter> vlastní, který `message.WriteBodyContents`je předán . Jako zpráva volá WriteBase64 na zapisovače, zapisovač balíčky do bloků do zpráv a odešle je pomocí vnitřníkanál. WriteBase64 bloky, dokud je odeslán blok.

## <a name="implementing-the-receive-operation"></a>Implementace operace příjmu

Na vysoké úrovni receive operace nejprve zkontroluje, `null` zda příchozí zpráva `ChunkingAction`není a že její akce je . Pokud nesplňuje obě kritéria, zpráva je vrácena beze změny z Receive. V opačném případě `ChunkingReader` Receive vytvoří `ChunkingMessage` nové a nové `GetNewChunkingMessage`zabalené kolem něj (voláním ). Před vrácením, `ChunkingMessage`že nové receive používá `ReceiveChunkLoop`vlákno threadpool ke spuštění , který `innerChannel.Receive` `ChunkingReader` volá ve smyčce a ruce pryč bloky až do konce bloku zprávy je přijata nebo příjem časový režim je přístupná.

Několik detailů stojí za zmínku:

- Stejně jako Odeslat, Přijímat první hovory, `ThrowIfDisposedOrNotOepned` abyste se ujistili, že `CommunicationState` je otevřeno.

- Příjem je také synchronizován tak, aby z relace mohla být přijata pouze jedna zpráva. To je obzvláště důležité, protože po přijetí zprávy počáteční houska, všechny následné přijaté zprávy se očekává, že bloky v rámci této nové sekvence bloku dat, dokud je přijata zpráva konce bloku. Přijímat nelze vyžádat zprávy z vnitřního kanálu, dokud nejsou přijaty všechny bloky, které patří do zprávy aktuálně de-chunked. Chcete-li to provést, Receive používá `ManualResetEvent` pojmenovaný `currentMessageCompleted`, který je nastaven při přijetí zprávy bloku ukončení a obnovit při přijetí nové zprávy počáteční blok.

- Na rozdíl od odeslat, Příjem nezabrání synchronizované přechody stavu při příjmu. Například Close lze volat při příjmu a čeká na dokončení čekající příjem původní zprávy nebo zadaný časový rozsah je dosaženo.

- Časový čas předaný Receive se používá jako časový časový rozsah pro celou operaci příjmu, která zahrnuje příjem všech bloků.

- Pokud vrstva, která spotřebovává zprávu spotřebovává text zprávy rychlostí nižší než rychlost příchozích `ChunkingReader` zpráv bloku, vyrovnávací paměti těchto příchozích bloků dat až do limitu určeného . `ChunkingBindingElement.MaxBufferedChunks` Jakmile je dosaženo tohoto limitu, žádné další bloky jsou vytaženy z nižší vrstvy, dokud je spotřebována do vyrovnávací paměti bloku nebo je dosaženo časového limitu příjmu.

## <a name="communicationobject-overrides"></a>Přepsání objektu CommunicationObject

### <a name="onopen"></a>OnOpen

`OnOpen`volání `innerChannel.Open` pro otevření vnitřního kanálu.

### <a name="onclose"></a>Při uzavření

`OnClose`první `stopReceive` nastaví na `true` `ReceiveChunkLoop` signál čekající zastavit. Potom čeká na `receiveStopped` <xref:System.Threading.ManualResetEvent>, který je `ReceiveChunkLoop` nastaven při zastavení. Za `ReceiveChunkLoop` předpokladu, že zastaví `OnClose` `innerChannel.Close` v rámci zadaného časového času, volání se zbývajícím časovým časem.

### <a name="onabort"></a>Onabort

`OnAbort`volání `innerChannel.Abort` přerušit vnitřní kanál. Pokud je čekající `ReceiveChunkLoop` získá výjimku z `innerChannel.Receive` čekající volání.

### <a name="onfaulted"></a>OnFaulted

Nevyžaduje `ChunkingChannel` zvláštní chování při chybě kanálu, `OnFaulted` takže není přepsán.

## <a name="implementing-channel-factory"></a>Implementace továrny kanálů

Je `ChunkingChannelFactory` zodpovědný za vytváření `ChunkingDuplexSessionChannel` instancí a pro kaskádové přechody stavu do vnitřní hotova kanálu.

`OnCreateChannel`používá vnitřní kanál factory `IDuplexSessionChannel` k vytvoření vnitřního kanálu. Potom vytvoří nový `ChunkingDuplexSessionChannel` předávání tento vnitřní kanál spolu se seznamem akcí zprávy, které mají být bloků a maximální počet bloků do vyrovnávací paměti při příjmu. Seznam akcí zprávy, které mají být bloků dat a maximální počet bloků `ChunkingChannelFactory` do vyrovnávací paměti jsou dva parametry předané v jeho konstruktoru. Část popisuje, `ChunkingBindingElement` odkud tyto hodnoty pocházejí.

`OnOpen`, `OnClose`a `OnAbort` jejich asynchronní ekvivalenty volání odpovídající metody přechodu stavu na vnitřní kanálu factory.

## <a name="implementing-channel-listener"></a>Implementace naslouchací proces kanálu

Je `ChunkingChannelListener` obálka kolem naslouchací proces vnitřní kanál. Jeho hlavní funkcí, kromě delegáta volání, že `ChunkingDuplexSessionChannels` vnitřní kanál posluchače, je zabalit nové kolem kanály přijaté z vnitřního kanálu posluchače. To se `OnAcceptChannel` provádí `OnEndAcceptChannel`v a . Nově vytvořené `ChunkingDuplexSessionChannel` je předán vnitřní kanál spolu s dalšími parametry dříve popsanými.

## <a name="implementing-binding-element-and-binding"></a>Implementace prvku vazby a vazby

`ChunkingBindingElement`je zodpovědný za `ChunkingChannelFactory` `ChunkingChannelListener`vytvoření a . Zkontroluje, `ChunkingBindingElement` zda `CanBuildChannelFactory` \<T `CanBuildChannelListener` \<v T> `IDuplexSessionChannel` a T> je typu (jediný kanál podporovaný kanálu bloků) a že ostatní elementy vazby podporují tento typ kanálu.

`BuildChannelFactory`\<T> nejprve zkontroluje, zda lze sestavit požadovaný typ kanálu, a poté získá seznam akcí zpráv, které mají být na bloky dat. Další informace naleznete v následující části. Potom vytvoří nový `ChunkingChannelFactory` předávání vnitřní kanálu factory (jak se vrátil z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam akcí zprávy a maximální počet bloků do vyrovnávací paměti. Maximální počet bloků dat pochází z `MaxBufferedChunks` vlastnosti, která je vystavena `ChunkingBindingElement`.

`BuildChannelListener<T>`má podobnou implementaci `ChunkingChannelListener` pro vytvoření a předání naslouchací proces vnitřní kanál.

V této ukázce je `TcpChunkingBinding`zahrnuta příklad vazby s názvem . Tato vazba se skládá `TcpTransportBindingElement` ze `ChunkingBindingElement`dvou prvků vazby: a . `MaxBufferedChunks` Kromě vystavení vlastnosti, vazba také nastaví `TcpTransportBindingElement` některé `MaxReceivedMessageSize` vlastnosti, `ChunkingUtils.ChunkSize` jako je například (nastaví ji na + 100 kB bajtů pro záhlaví).

`TcpChunkingBinding`také implementuje `IBindingRuntimePreferences` a `ReceiveSynchronously` vrátí true z metody označující, že jsou implementovány pouze synchronní Receive volání.

### <a name="determining-which-messages-to-chunk"></a>Určení, které zprávy na blok

Blokovací kanál bloky pouze zprávy identifikované prostřednictvím atributu. `ChunkingBehavior` Třída `ChunkingBehavior` implementuje `IOperationBehavior` a je `AddBindingParameter` implementována voláním metody. V `ChunkingBehavior` této metodě zkoumá hodnotu `AppliesTo` jeho`InMessage` `OutMessage` vlastnost ( , nebo obojí) k určení, které zprávy by měly být bloků dat. Potom získá akci každé z těchto zpráv (z `OperationDescription`kolekce Messages na ) a přidá ji `ChunkingBindingParameter`do kolekce řetězců obsažené v instanci . Poté to `ChunkingBindingParameter` toto přidá `BindingParameterCollection`k poskytnutému .

To `BindingParameterCollection` je předán `BindingContext` uvnitř do každý element vazby ve vazbě při tento element vazby vytvoří factory kanálu nebo naslouchací proces kanálu. 's `ChunkingBindingElement`provádění `BuildChannelFactory<T>` a `BuildChannelListener<T>` vytáhnout `ChunkingBindingParameter` to `BindingContext’`z `BindingParameterCollection`s . Kolekce akcí obsažených v `ChunkingBindingParameter` je pak `ChunkingChannelFactory` předána nebo `ChunkingChannelListener`, která `ChunkingDuplexSessionChannel`zase předá do .

## <a name="running-the-sample"></a>Spuštění ukázky

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

5. Nejprve spusťte soubor Service.exe, potom spusťte soubor Client.exe a sledujte výstup obou oken konzoly.

Při spuštění ukázky se očekává následující výstup.

Klient:

```console
Press enter when service is available

 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

Server:

```console
Service started, press enter to exit
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```
