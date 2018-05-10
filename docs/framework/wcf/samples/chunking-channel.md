---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 1acb635be23b9a838abee714156d818abee6bcd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="chunking-channel"></a>Kanál s dělením dat do bloků
Při odesílání velké zprávy pomocí služby Windows Communication Foundation (WCF), je často žádoucí omezit množství paměti k přechodnému ukládání těchto zpráv. Jedním z možných řešení je k vysílání datového proudu tělo zprávy (za předpokladu, že hromadné dat je v textu). Ale vyžadují některé protokoly ukládání do vyrovnávací paměti celé zprávy. Spolehlivé zasílání zpráv a zabezpečení jsou dva příklady takových. Další možnou příčinou je zdola nahoru velké zprávy do menších zpráv názvem bloky dat, najednou odeslat jeden blok tyto bloků a rekonstruovat velké zprávy na straně příjmu. Vlastní aplikace udělat toto rozdělování a zrušte rozdělování nebo použít vlastní kanál to udělat. Bloku dat kanál příklad ukazuje, jak vlastního protokolu nebo vrstveného kanál slouží k rozdělování a zrušte rozdělování libovolně velké zpráv.  
  
 Rozdělování by měl vždycky být použity pouze po celé zprávy před jejich odesláním byla vytvořená. Bloku dat kanál, který by měl vrstvený vždy pod zabezpečený kanál a spolehlivé relace kanál.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Rozdělování kanál předpoklady a omezení  
  
### <a name="message-structure"></a>Struktura zprávy  
 Bloku dat kanál předpokládá následující strukturu zpráva pro zpráv, které mají být blokové:  
  
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
  
 Při použití ServiceModel, kontrakt operace, které mají 1 vstupní parametr v souladu se tento tvar zprávy pro jejich vstupní zprávu. Podobně kontrakt operace, které mají 1 výstupní parametr, nebo může vracet hodnotu v souladu se tento tvar zprávy pro jejich výstup zprávu. Následují příklady těchto operací:  
  
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
 Kanál bloku dat vyžaduje zpráv, které mají být doručeny právě jednou, v doručení zprávy (bloky). To znamená, že základní zásobník kanál musí být relacemi. Relace se dá zajistit přenos (například přenos TCP) nebo protokol relacemi kanál (například ReliableSession kanál).  
  
### <a name="asynchronous-send-and-receive"></a>Asynchronní odesílání a přijímání  
 Asynchronní odesílání a příjmu metody nejsou implementované v této verzi bloku dat ukázkový kanál.  
  
## <a name="chunking-protocol"></a>Bloku dat protokolu  
 Bloku dat kanál definuje protokol, který označuje začátek a konec řadu bloky dat, a také pořadové číslo od každého bloku. Následující tři příklad zprávy ukazují spuštění a bloku a end zprávy s komentáři, které popisují každou klíčové aspekty.  
  
### <a name="start-message"></a>Spusťte zprávu  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
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
  
### <a name="chunk-message"></a>Bloku zpráv  
  
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
  
### <a name="end-message"></a>Zpráva konce  
  
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
  
## <a name="chunking-channel-architecture"></a>Architektura bloku dat kanál  
 Kanál bloku dat je `IDuplexSessionChannel` , na vysoké úrovni, odpovídá architektuře typické kanálu. Je `ChunkingBindingElement` , můžete vytvořit `ChunkingChannelFactory` a `ChunkingChannelListener`. `ChunkingChannelFactory` Vytváří instance `ChunkingChannel` když jej požaduje. `ChunkingChannelListener` Vytváří instance `ChunkingChannel` datum přijetí nového vnitřní kanálu. `ChunkingChannel` Samotné zodpovídá za odesílání a přijímání zpráv.  
  
 Na další úrovni dolů `ChunkingChannel` spoléhá na několik součástí k provádění bloku dat protokolu. Na straně odesílání kanál používá vlastní `XmlDictionaryWriter` názvem `ChunkingWriter` , nebude skutečná rozdělování. `ChunkingWriter` používá vnitřní kanál přímo k odesílání bloků. Použití vlastní `XmlDictionaryWriter` umožňuje nám poslat bloky dat jako rozsáhlý soubor na původní zprávu o probíhá zápis. To znamená, že jsme neukládaného ve vyrovnávací paměti celý původní zprávy.  
  
 ![Rozdělování kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Na straně příjmu `ChunkingChannel` vrátí zprávy z tohoto vnitřní kanálu a předá je na vlastní `XmlDictionaryReader` názvem `ChunkingReader`, který reconstitutes na původní zprávu z příchozí datové dávky. `ChunkingChannel` To zahrnuje `ChunkingReader` ve vlastní `Message` implementace volá `ChunkingMessage` a vrátí tuto zprávu do vrstvy výše. Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje zrušte bloku dat původní text zprávy, jako je číst vrstvu nad místo nutnosti ukládat do vyrovnávací paměti celý původní text zprávy. `ChunkingReader` má fronty, kde ukládány příchozí bloky až do maximální konfigurovat počet bloků dat z vyrovnávací paměti. Když je dosaženo této maximální limit, čtečka čeká zpráv, které mají být nečekaně z fronty vrstvou výše (to znamená, načtením právě z původní text zprávy) nebo dokud nebude přijímat maximální je dosaženo časového limitu.  
  
 ![Rozdělování kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Rozdělování modelu programování  
 Vývojáři služeb můžete zadat zprávy, které mají být blokové použitím `ChunkingBehavior` atribut operace v rámci smlouvy. Atribut zpřístupní `AppliesTo` vlastnost, která umožňuje vývojáři k určení, zda rozdělování platí pro zprávu vstupní, výstupní zprávu nebo obojí. Následující příklad ukazuje použití `ChunkingBehavior` atribut:  
  
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
  
 Z tohoto modelu programování `ChunkingBindingElement` sestaví seznam akce identifikátory URI, který identifikovat zpráv, které mají být blokové. Akce každé odchozí zprávy se porovná s tohoto seznamu k určení, pokud zpráva by měla být blokové nebo odeslat přímo.  
  
## <a name="implementing-the-send-operation"></a>Implementace operaci odeslání  
 Na vysoké úrovni, po operaci odeslání nejprve ověří, zda odchozí zprávy musí být blokové a pokud ne, odešle zprávu přímo pomocí vnitřního kanálu.  
  
 Pokud zpráva musí blokové, odeslání vytvoří novou `ChunkingWriter` a volání `WriteBodyContents` na odchozí zprávy předání to `ChunkingWriter`. `ChunkingWriter` Nemá rozdělování zprávy (včetně kopírování původní záhlaví zprávy na zprávu počáteční blok) a odešle bloky dat pomocí vnitřního kanálu.  
  
 Několik podrobnosti vhodné poznamenat:  
  
-   Odeslat první volání `ThrowIfDisposedOrNotOpened` zajistit `CommunicationState` je otevřen.  
  
-   Odesílání se synchronizují, aby pouze jeden zpráva byla odeslána současně pro každou relaci. Je `ManualResetEvent` s názvem `sendingDone` , se resetuje při odesílání bloku zprávy. Jakmile je koncový blok zpráva odeslána, tato událost je nastavena. Metoda odesílání čeká na tuto událost, chcete-li nastavit před pokusem o odeslání odchozí zprávy.  
  
-   Odeslat zámky `CommunicationObject.ThisLock` aby synchronizovat změny stavu při odesílání. Najdete v článku <xref:System.ServiceModel.Channels.CommunicationObject> dokumentace pro další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavy a stav počítače.  
  
-   Časový limit předaný odesílání slouží jako časový limit pro operaci celý odeslání, který zahrnuje všechny bloky dat odesílání.  
  
-   Vlastní `XmlDictionaryWriter` návrhu jste vybrali, aby se zabránilo ukládání do vyrovnávací paměti celý původní text zprávy. Pokud nám chcete-li získat `XmlDictionaryReader` na text pomocí `message.GetReaderAtBodyContents` celého obsahu by do vyrovnávací paměti. Místo toho máme vlastní `XmlDictionaryWriter` předá do `message.WriteBodyContents`. Jako zprávu pomocí volání WriteBase64 zapisovače zapisovač bloky dat do zpráv zabalí a odešle je vnitřní kanálu. Bloky WriteBase64 dlouho, dokud se neodešle u bloku.  
  
## <a name="implementing-the-receive-operation"></a>Implementace přijímat operace  
 Na vysoké úrovni, operace příjmu nejprve zkontroluje, že příchozí zpráva není `null` a že je jeho akce `ChunkingAction`. Pokud obě kritéria nesplňuje, bude vráceno beze změny z Receive. Jinak, vytvoří novou Receive `ChunkingReader` a novou `ChunkingMessage` zabalené kolem něj (voláním `GetNewChunkingMessage`). Před vrácením že noví `ChunkingMessage`, Receive používá podproces fondu podprocesů provést `ReceiveChunkLoop`, který volá `innerChannel.Receive` v smyčku a rukou vypnout bloky dat pro `ChunkingReader` dokud doručení zprávy koncového bloku nebo je dosaženo časového limitu příjmu.  
  
 Několik podrobnosti vhodné poznamenat:  
  
-   Jako odesílání, příjem první volání `ThrowIfDisposedOrNotOepned` zajistit `CommunicationState` je otevřen.  
  
-   Zobrazí se synchronizují taky, že pouze jednu zprávu lze přijímat současně z relace. To je obzvláště důležité, protože po přijetí zprávy počáteční blok je všechny následné přijaté zprávy se měl bloků dat v rámci tohoto nového pořadí bloku dokud neobdrží zprávu koncového bloku. Přijímat zprávy z tohoto kanálu vnitřní nemůže vyžádat, dokud všechny bloky dat, které patří do zprávy aktuálně probíhá zrušte blokové jsou přijaty. K tomu, přijímat používá `ManualResetEvent` s názvem `currentMessageCompleted`, který je nastaven při zprávu bloku end přijme a resetovat při přijetí nové zprávy počáteční blok.  
  
-   Na rozdíl od odeslání Receive nezabrání přechodů mezi stavy synchronizované při přijetí. Například Zavřít lze volat při přijetí a čeká, až do dokončení čekající receive původní zprávy nebo zadaný časový limit.  
  
-   Časový limit předaný příjmu se používá jako časového limitu pro celý zobrazí operaci, která zahrnuje všechny bloky dat přijetí.  
  
-   Pokud vrstva, která načítá zprávy spotřebovává tělo zprávy s rychlostí nižší než počet příchozích zpráv bloku, `ChunkingReader` uloží tyto příchozí bloky až do limitu určeného `ChunkingBindingElement.MaxBufferedChunks`. Po dosažení tohoto limitu jsou žádné další bloky vyžádány z nižší vrstvy, dokud se využívá ve vyrovnávací paměti datových dávek nebo je dosaženo časového limitu příjmu.  
  
## <a name="communicationobject-overrides"></a>Přepsání objektu CommunicationObject  
  
### <a name="onopen"></a>Při otevření  
 `OnOpen` volání `innerChannel.Open` otevřít vnitřní kanál.  
  
### <a name="onclose"></a>Při zavření  
 `OnClose` nejprve nastaví `stopReceive` k `true` signál na čekající `ReceiveChunkLoop` zastavit. Potom čeká `receiveStopped``ManualResetEvent`, který je nastaven při `ReceiveChunkLoop` zastaví. Za předpokladu, že `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` s zbývající časový limit.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` volání `innerChannel.Abort` k přerušení vnitřní kanál. Pokud dojde čekající `ReceiveChunkLoop` získá výjimku z na čekající `innerChannel.Receive` volání.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Nevyžaduje speciální chování, pokud je kanál s chybou, tak `OnFaulted` není přepsána.  
  
## <a name="implementing-channel-factory"></a>Implementace kanálu  
 `ChunkingChannelFactory` Zodpovídá za vytvoření instancí `ChunkingDuplexSessionChannel` a pro kaskádové přechodů mezi stavy pro vnitřní kanálu.  
  
 `OnCreateChannel` vnitřní kanálu používá k vytvoření `IDuplexSessionChannel` vnitřní kanálu. Ta poté vytvoří nový `ChunkingDuplexSessionChannel` předání tohoto vnitřní kanálu spolu s seznam zpráv akce, které mají být blokové a maximální počet bloků dat do vyrovnávací paměti při příjmu. Seznam zpráv akce, které mají být blokové a maximální počet bloků dat do vyrovnávací paměti jsou dva parametry předaný `ChunkingChannelFactory` v jeho konstruktoru. V části na `ChunkingBindingElement` popisuje, kde se tyto hodnoty pocházejí z.  
  
 `OnOpen`, `OnClose`, `OnAbort` a jejich ekvivalenty u asynchronního volání metody odpovídající přechod stavu na vnitřní kanálu.  
  
## <a name="implementing-channel-listener"></a>Implementace naslouchací proces kanálu  
 `ChunkingChannelListener` Představuje obálku kolem naslouchací proces vnitřní kanálu. Jeho hlavní funkce, kromě delegáta volání této naslouchací proces vnitřní kanálu je zabalit nové `ChunkingDuplexSessionChannels` kolem kanály přijímán z naslouchací proces vnitřní kanálu. To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`. Nově vytvořený `ChunkingDuplexSessionChannel` je předána vnitřní kanálu spolu s ostatní parametry popsaných výše.  
  
## <a name="implementing-binding-element-and-binding"></a>Implementaci prvku vazby a vazby  
 `ChunkingBindingElement` zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`. `ChunkingBindingElement` Kontroluje, zda T v `CanBuildChannelFactory` \<T > a `CanBuildChannelListener` \<T > je typu `IDuplexSessionChannel` (pouze kanál nepodporuje bloku dat kanál) a další prvky vazby vazba podporují tuto Typ kanálu.  
  
 `BuildChannelFactory`\<T > nejdřív zkontroluje, zda požadovaný kanál typu se dají vytvářet a pak získá seznam zpráv akce, které mají být blokové. Další informace najdete v následující části. Ta poté vytvoří nový `ChunkingChannelFactory` předání vnitřní kanálu (vrácený z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam zpráv akce a maximální počet bloků dat do vyrovnávací paměti. Maximální počet bloků pochází z vlastnost s názvem `MaxBufferedChunks` vystavené `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` má podobné implementace pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřní kanálu.  
  
 Je třeba vazbu zahrnuté v této ukázce s názvem `TcpChunkingBinding`. Tato vazba se skládá ze dvou prvků vazby: `TcpTransportBindingElement` a `ChunkingBindingElement`. Kromě vystavení `MaxBufferedChunks` vlastnost vazby také nastaví některá `TcpTransportBindingElement` vlastnosti, jako `MaxReceivedMessageSize` (ji nastaví na `ChunkingUtils.ChunkSize` + 100 KB bajtů pro hlavičky).  
  
 `TcpChunkingBinding` také implementuje `IBindingRuntimePreferences` a vrací hodnotu true z `ReceiveSynchronously` metoda, která určuje, že jsou implementované synchronní volání Receive.  
  
### <a name="determining-which-messages-to-chunk"></a>Určení, které zpráv do bloku  
 Bloku dat kanál chunks pouze zprávy, které jsou identifikovány prostřednictvím `ChunkingBehavior` atribut. `ChunkingBehavior` Třída implementuje `IOperationBehavior` a je implementováno modulem volání `AddBindingParameter` metoda. Tato metoda `ChunkingBehavior` ověří hodnotu jeho `AppliesTo` vlastnost (`InMessage`, `OutMessage` nebo obojí) k určení zprávy, které by měl být blokové. Potom získá akce jednotlivé zprávy (z kolekce zprávy na `OperationDescription`) a přidá do kolekce řetězec obsažené v instanci `ChunkingBindingParameter`. Potom přidá to `ChunkingBindingParameter` zadanému `BindingParameterCollection`.  
  
 To `BindingParameterCollection` je předán uvnitř `BindingContext` na každý element vazby vazba, pokud daný element vazby sestavení kanálu nebo naslouchací proces kanálu nástroje. `ChunkingBindingElement`Na implementaci `BuildChannelFactory<T>` a `BuildChannelListener<T>` to pro vyžádání obsahu `ChunkingBindingParameter` mimo `BindingContext’`s `BindingParameterCollection`. Kolekci akcí, které jsou obsažené v `ChunkingBindingParameter` se pak předá do `ChunkingChannelFactory` nebo `ChunkingChannelListener`, který naopak předává jej do `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Nejprve spustit Service.exe, spusťte Client.exe a podívejte se na obě okna konzoly pro výstup.  
  
 Při spuštění ukázky, očekává se následující výstup.  
  
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
  
 Server:  
  
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
  
## <a name="see-also"></a>Viz také
