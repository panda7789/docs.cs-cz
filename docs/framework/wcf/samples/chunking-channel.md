---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 6de513db82c49821c8f6758509f1bd356035b9c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951009"
---
# <a name="chunking-channel"></a>Kanál s dělením dat do bloků
Při posílání velkých zpráv pomocí Windows Communication Foundation (WCF) je často žádoucí omezit množství paměti využité k ukládání těchto zpráv do vyrovnávací paměti. Jedním z možných řešení je vysílat datový proud zprávy (za předpokladu, že část dat je v těle). Některé protokoly ale vyžadují ukládání celé zprávy do vyrovnávací paměti. Spolehlivé zasílání zpráv a zabezpečení jsou dva příklady. Dalším možným řešením je rozdělit velkou zprávu na menší zprávy s názvem bloky dat, odeslat tyto bloky v jednom okamžiku a znovu vytvořit velkou zprávu na straně příjmu. Samotná aplikace by mohla provádět tyto bloky dat a neblokování nebo by k tomu mohla použít vlastní kanál. Ukázka kanálu pro dělení na bloky dat ukazuje, jak lze použít vlastní protokol nebo vrstvený kanál k provádění bloků dat a rozblokování libovolně velkých zpráv.  
  
 Blokování by mělo být vždy použito až po sestavení celé zprávy, která má být odeslána. Kanál bloků dat by měl být vždy vrstven pod kanálem zabezpečení a spolehlivým kanálem relace.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Předpoklady a omezení kanálu pro vytváření bloků dat  
  
### <a name="message-structure"></a>Struktura zprávy  
 Kanál pro zpracování zpráv předpokládá, že pro zprávy, které mají být v bloku dat, má následující strukturu zpráv:  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 Při použití třídy ServiceModel musí operace kontraktu s 1 vstupním parametrem odpovídat tomuto obrazci zprávy pro svou vstupní zprávu. Podobně operace kontraktu, které mají 1 výstupní parametr nebo návratovou hodnotu, jsou v rozporu s tímto tvarem zprávy pro výstupní zprávu. Následují příklady takových operací:  
  
```  
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
 Kanál pro dělení na bloky dat vyžaduje, aby se zprávy přesně předávaly v seřazeném doručování zpráv (bloků dat). To znamená, že musí být příslušný zásobník kanálů relace. Relace můžou být poskytovány přenosem (například přenos TCP) nebo kanálem protokolu relace (například ReliableSession Channel).  
  
### <a name="asynchronous-send-and-receive"></a>Asynchronní odesílání a příjem  
 Asynchronní metody Send a Receive nejsou v této verzi ukázky kanálu bloků dat implementovány.  
  
## <a name="chunking-protocol"></a>Protokol bloků dat  
 Kanál pro dělení na bloky dat definuje protokol, který indikuje začátek a konec série bloků dat a také pořadové číslo každého bloku. V následujících třech příkladech se zprávy ukazují na úvodní, blokové a koncové zprávy s komentáři, které popisují klíčové aspekty každého z nich.  
  
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
  
### <a name="end-message"></a>Koncová zpráva  
  
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
  
## <a name="chunking-channel-architecture"></a>Architektura kanálu bloků dat  
 Kanál pro dělení na bloky dat `IDuplexSessionChannel` je na nejvyšší úrovni, který následuje za typickou architekturou kanálů. Existuje, který může `ChunkingChannelFactory` vytvořit a `ChunkingChannelListener`. `ChunkingBindingElement` `ChunkingChannelFactory` Vytvoří instance,když`ChunkingChannel` se na ni žádá. `ChunkingChannelListener` Vytvoří`ChunkingChannel` instance při přijetí nového vnitřního kanálu. K posílání a přijímání zpráv zodpovídá sámsebe.`ChunkingChannel`  
  
 Na další úrovni `ChunkingChannel` spoléhá na několik komponent k implementaci protokolu bloků dat. Na straně odeslání kanál používá vlastní <xref:System.Xml.XmlDictionaryWriter> volanou `ChunkingWriter` zprávu, která provádí skutečné zpracování dat. `ChunkingWriter`používá vnitřní kanál přímo k odesílání bloků dat. Pomocí vlastního `XmlDictionaryWriter` obsahu můžeme poslat bloky dat, když se zapisuje velký text původní zprávy. To znamená, že neuložíme do vyrovnávací paměti celou původní zprávu.  
  
 ![Diagram znázorňující architekturu odesílání kanálu bloků dat.](./media/chunking-channel/chunking-channel-send.gif)  
  
 Na straně příjmu se `ChunkingChannel` stáhnou zprávy z vnitřního kanálu a zadají se do vlastního <xref:System.Xml.XmlDictionaryReader> volaného `ChunkingReader`, který znovu vytvoří původní zprávu z příchozích bloků dat. `ChunkingChannel`zabalí `Message`dovlastní implementace s názvem `ChunkingMessage` a vrátí tuto zprávu do vrstvy výše. `ChunkingReader` Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje nám deserializovat původní text zprávy, který je čten vrstvou výše, místo abyste museli ukládat celý původní text zprávy do vyrovnávací paměti. `ChunkingReader`má frontu, ve které vyrovnávací paměti ukládají příchozí bloky až do maximálního konfigurovatelného počtu bloků v bufferu. Když je dosaženo tohoto maximálního limitu, čtečka čeká na vyřazení zpráv z fronty výše uvedenou vrstvou (to znamená pouhým čtením z původního těla zprávy) nebo až do dosažení maximálního časového limitu příjmu.  
  
 ![Diagram znázorňující architekturu příjmu kanálu bloků dat.](./media/chunking-channel/chunking-channel-receive.gif)  
  
## <a name="chunking-programming-model"></a>Model programování bloků dat  
 Vývojáři služeb mohou určit, které zprávy mají být v bloku, použitím `ChunkingBehavior` atributu na operace v rámci kontraktu. Atribut zpřístupňuje `AppliesTo` vlastnost, která vývojářům umožňuje určit, zda se má použít pro vstupní zprávu, výstupní zprávu nebo obojí. Následující příklad ukazuje použití `ChunkingBehavior` atributu:  
  
```  
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
  
 Z tohoto programovacího modelu `ChunkingBindingElement` zkompiluje seznam identifikátorů URI akcí, které identifikují zprávy, které mají být zablokované. Akce každé odchozí zprávy je porovnána s tímto seznamem, aby bylo možné určit, zda má být zpráva v bloku nebo odeslána přímo.  
  
## <a name="implementing-the-send-operation"></a>Implementace operace Send  
 Na vysoké úrovni operace odeslání nejprve zkontroluje, zda musí být odchozí zpráva v bloku, a pokud ne, odesílá zprávu přímo pomocí vnitřního kanálu.  
  
 Pokud je zpráva musí obsahovat bloky dat, odešle se nové `ChunkingWriter` a zavolá se na `ChunkingWriter`odchozí zprávu, která to přesměruje `WriteBodyContents` . V `ChunkingWriter` takovém případě nakopíruje do bloku zprávy (včetně kopírování původních hlaviček zpráv do zprávy spustit blok) a odešle bloky dat pomocí vnitřního kanálu.  
  
 Je potřeba poznamenat si několik podrobností:  
  
- Odešlete první `ThrowIfDisposedOrNotOpened` volání, aby `CommunicationState` se zajistilo, že se otevře.  
  
- Odesílání je synchronizováno, aby bylo možné každou relaci odeslat současně pouze jednu zprávu. Při posílání `ManualResetEvent` zprávy `sendingDone` se systémem se zobrazí název, který se resetuje. Po odeslání zprávy koncového bloku se tato událost nastaví. Metoda send počká na nastavení této události, než se pokusí odeslat odchozí zprávu.  
  
- Odeslat zamkne, `CommunicationObject.ThisLock` aby se zabránilo synchronizovaným změnám stavu při odesílání. Další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavech a stavu počítače najdete v dokumentaci.<xref:System.ServiceModel.Channels.CommunicationObject>  
  
- Časový limit odeslaný do odeslání se používá jako časový limit pro celou operaci odeslání, která zahrnuje odesílání všech bloků dat.  
  
- Vlastní <xref:System.Xml.XmlDictionaryWriter> návrh byl vybrán, aby nedošlo k ukládání do vyrovnávací paměti pro celý původní text zprávy. <xref:System.Xml.XmlDictionaryReader> V případě, že jsme se dostali na tělo s `message.GetReaderAtBodyContents` použitím celého těla, bude uloženo do vyrovnávací paměti. Místo toho máme vlastní <xref:System.Xml.XmlDictionaryWriter> předaný do. `message.WriteBodyContents` Když zpráva volá WriteBase64, zapisovač zabalí do zpráv bloky a pošle je pomocí vnitřního kanálu. WriteBase64 bloky až do odeslání bloku dat.  
  
## <a name="implementing-the-receive-operation"></a>Implementace operace Receive  
 V případě vysoké úrovně operace Receive nejprve zkontroluje, že příchozí zpráva `null` není a že se jedná o `ChunkingAction`akci. Pokud nesplňuje obě kritéria, zpráva se z příjmu vrátí beze změny. V opačném případě příjem vytvoří `ChunkingReader` nový a `ChunkingMessage` kolem něj obtékající (voláním `GetNewChunkingMessage`). Před vrácením tohoto `ChunkingMessage`nového příkazu obdrží použití vlákna podprocesu `ReceiveChunkLoop`ke spuštění, `innerChannel.Receive` které volá `ChunkingReader` smyčku a předá bloky dat do doby, než je obdržena zpráva koncového bloku nebo dojde k vypršení časového limitu příjmu.  
  
 Je potřeba poznamenat si několik podrobností:  
  
- Podobně jako u Send přijímají `ThrowIfDisposedOrNotOepned` první volání, `CommunicationState` aby se zajistilo, že se otevře.  
  
- Příjem je také synchronizovaný, aby bylo možné současně přijmout jenom jednu zprávu z relace. To je obzvláště důležité, protože po přijetí zprávy počátečního bloku se očekává, že všechny následné přijaté zprávy budou obsahovat bloky dat v této nové sekvenci bloků dat, dokud se nepřijme zpráva koncového bloku dat. Příjem nemůže přijímat zprávy z vnitřního kanálu, dokud nebudou přijaty všechny bloky, které patří do zprávy, která je v současné době deblokovaná. K tomu je potřeba přijmout pomocí `ManualResetEvent` pojmenovaného `currentMessageCompleted`, který se nastaví, když se přijme zpráva o ukončení bloku dat a resetování, když se přijme nová zpráva o počátečním bloku.  
  
- Na rozdíl od odeslání nebrání přijímání synchronizovaného stavu při příjmu. Například možnost Zavřít může být volána při přijímání a čeká na dokončení probíhajícího příjmu původní zprávy nebo dosažení zadané hodnoty časového limitu.  
  
- Časový limit předaný do přijetí se používá jako časový limit pro celou operaci přijetí, která zahrnuje příjem všech bloků dat.  
  
- Pokud vrstva, která využívá zprávu, spotřebovává tělo zprávy o sazbě nižší, než je počet příchozích zpráv bloku dat, `ChunkingReader` vyrovnávací paměti těchto vstupních bloků až do limitu určeného parametrem. `ChunkingBindingElement.MaxBufferedChunks` Po dosažení tohoto limitu nebudou z nižší vrstvy načítány žádné další bloky, dokud se nespotřebovává blok dat ve vyrovnávací paměti nebo dokud nedosáhnete časového limitu příjmu.  
  
## <a name="communicationobject-overrides"></a>CommunicationObject přepsání  
  
### <a name="onopen"></a>Otevřít  
 `OnOpen`volání `innerChannel.Open` pro otevření vnitřního kanálu.  
  
### <a name="onclose"></a>OnClose –  
 `OnClose`nejprve nastaví `stopReceive` , `true` aby bylo signalizaci `ReceiveChunkLoop` čekání na zastavení. Potom počká `receiveStopped` <xref:System.Threading.ManualResetEvent>na, který je nastaven při `ReceiveChunkLoop` zastavení. Za předpokladu, že se `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` se zbývajícím časovým limitem  
  
### <a name="onabort"></a>Přerušení  
 `OnAbort`volání `innerChannel.Abort` přeruší vnitřní kanál. V případě, že se `ReceiveChunkLoop` čeká na vyřízení, získá výjimku `innerChannel.Receive` z nedokončeného volání.  
  
### <a name="onfaulted"></a>Došlo k chybě  
 Při chybě kanálu není nutné speciální chování, takže `OnFaulted` není přepsán. `ChunkingChannel`  
  
## <a name="implementing-channel-factory"></a>Implementace objektu pro vytváření kanálů  
 Je zodpovědný za vytváření instancí a pro `ChunkingDuplexSessionChannel` přechody mezi stavy do továrny vnitřního kanálu. `ChunkingChannelFactory`  
  
 `OnCreateChannel`vytvoří `IDuplexSessionChannel` vnitřní kanál pomocí továrny vnitřního kanálu. Pak vytvoří nové `ChunkingDuplexSessionChannel` předání tohoto vnitřního kanálu společně se seznamem akcí zpráv, které mají být v bloku, a maximální počet bloků dat, které se po přijetí ukládají do vyrovnávací paměti. Seznam akcí zprávy, které mají být `ChunkingChannelFactory` v bloku, a maximální počet bloků na vyrovnávací paměť jsou dva parametry předané do svého konstruktoru. Část `ChunkingBindingElement` popisující, kde tyto hodnoty pocházejí.  
  
 Rozhraní `OnOpen` ,`OnClose`a jejich asynchronní ekvivalenty volají odpovídající metodu přechodu stavu na objektu pro vytváření vnitřních kanálů. `OnAbort`  
  
## <a name="implementing-channel-listener"></a>Implementace naslouchacího procesu kanálu  
 `ChunkingChannelListener` Je Obálka kolem naslouchacího procesu vnitřního kanálu. Jeho hlavní funkce, kromě volání delegátů do tohoto naslouchacího procesu interního kanálu, je `ChunkingDuplexSessionChannels` zabalit nové kolem kanálů přijatých od naslouchacího procesu vnitřního kanálu. To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`. Nově vytvořená `ChunkingDuplexSessionChannel` se předává vnitřní kanál spolu s dalšími parametry uvedenými výše.  
  
## <a name="implementing-binding-element-and-binding"></a>Implementace elementu vazby a vazby  
 `ChunkingBindingElement`zodpovídá za vytváření `ChunkingChannelFactory` a `ChunkingChannelListener`. \< `CanBuildChannelListener` `IDuplexSessionChannel` Kontroluje, zda t in `CanBuildChannelFactory`t > a \<t > je typu (jediný kanál podporovaný kanálem bloků dat) a že ostatní prvky vazby ve vazbě tuto možnost podporují. `ChunkingBindingElement` typ kanálu.  
  
 `BuildChannelFactory`\<T > nejdřív zkontroluje, jestli jde sestavit požadovaný typ kanálu, a pak získá seznam akcí zprávy, které se mají zablokovat. Další informace najdete v následující části. Potom vytvoří nový `ChunkingChannelFactory` průchod objektem pro vytváření vnitřního kanálu (vráceným ze `context.BuildInnerChannelFactory<IDuplexSessionChannel>`seznamu), seznamem akcí zpráv a maximálním počtem bloků, které mají být uloženy do vyrovnávací paměti. Maximální počet bloků dat pochází z vlastnosti s názvem `MaxBufferedChunks` vystaveno. `ChunkingBindingElement`  
  
 `BuildChannelListener<T>`má podobnou implementaci pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřního kanálu.  
  
 V této ukázce je obsažena příklad vazby s názvem `TcpChunkingBinding`. Tato vazba se skládá ze dvou prvků vazby `TcpTransportBindingElement` : `ChunkingBindingElement`a. Kromě `MaxBufferedChunks` vystavení vlastnosti vazba také nastaví některé `TcpTransportBindingElement` vlastnosti, například `MaxReceivedMessageSize` (nastaví ji na `ChunkingUtils.ChunkSize` + 100 KB bajty pro záhlaví).  
  
 `TcpChunkingBinding`také implementuje `IBindingRuntimePreferences` a vrátí hodnotu true `ReceiveSynchronously` z metody, což znamená, že jsou implementována pouze synchronní volání Receive.  
  
### <a name="determining-which-messages-to-chunk"></a>Určení zpráv pro blok dat  
 Kanál bloků dat zablokuje pouze zprávy identifikované pomocí `ChunkingBehavior` atributu. Třída implementuje `IOperationBehavior` a`AddBindingParameter` je implementována voláním metody. `ChunkingBehavior` V této metodě `ChunkingBehavior` ověřuje hodnota své `AppliesTo` vlastnosti (`InMessage` `OutMessage` nebo obou) k určení, které zprávy mají být v bloku. Pak získá akci každé z těchto zpráv (z kolekce messages on `OperationDescription`) a přidá je do kolekce řetězců obsažené v `ChunkingBindingParameter`instanci. Pak to `ChunkingBindingParameter` přidá k poskytnutému `BindingParameterCollection`.  
  
 Tato `BindingParameterCollection` třída je předána `BindingContext` do každého prvku vazby ve vazbě, pokud prvek vazby vytvoří objekt pro vytváření kanálu nebo naslouchací proces kanálu. `ChunkingBindingElement` Implementacea`BuildChannelListener<T>`vyžádá si tento `ChunkingBindingParameter` výstup z`BindingContext’`s `BindingParameterCollection`. `BuildChannelFactory<T>` Kolekce `ChunkingBindingParameter` akcí obsažených v rámci je pak předána `ChunkingChannelFactory` do nebo `ChunkingChannelListener` `ChunkingDuplexSessionChannel`, která je následně předává do.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Nejprve spusťte Service. exe a potom spusťte soubor Client. exe a Sledujte výstup oken konzoly.  
  
 Při spuštění ukázky se očekává následující výstup.  
  
 Klient:  
  
```  
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
  
 WebServer  
  
```  
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
