---
title: Kanál s dělením dat do bloků
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: db14ceb956202bee06ff5e6b37b21fb837c6f1d9
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066412"
---
# <a name="chunking-channel"></a>Kanál s dělením dat do bloků
Při odesílání velkých zpráv pomocí služby Windows Communication Foundation (WCF), je často žádoucí omezit množství paměti pro zprávy ve vyrovnávací paměti. Jedním z možných řešení je do datového proudu zprávy (za předpokladu, že hromadných dat je v textu). Ale některé protokoly vyžadují celé zprávy do vyrovnávací paměti. Spolehlivé zasílání zpráv a zabezpečení jsou tyto dva příklady. Další možnou příčinou je zdola nahoru objemné zprávy do menších zprávy označované jako bloky dat, odesílání jednoho bloku tyto bloky dat najednou a znovuvytvoření velkých zpráv na straně příjmu. Zrušení bloků nebo ho může používat vlastní kanál k tomu a samotná aplikace udělat tento bloků. Vytváření bloků kanál příklad ukazuje, jak vlastní protokol nebo vrstvami kanálu lze provést bloků a zrušení bloků libovolně velkých zpráv.  
  
 Dělením dat do bloků by měl vždy být použity až poté, co byl vytvořen celé zprávy k odeslání. Vytváření bloků kanálu by měl vždy vrstvy pod zabezpečení kanálu a jeho kanál stabilní relace.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Vytváření bloků kanál předpoklady a omezení  
  
### <a name="message-structure"></a>Struktura zprávy  
 Vytváření bloků kanálu se předpokládá následující strukturu zprávu pro zprávy být rozdělený do bloků dat:  
  
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
  
 Při použití modelu, kontrakt operace, které mají 1 vstupní parametr v souladu s tohoto obrazce zprávy pro jejich vstupní zprávy. Podobně kontrakt operace, které mají 1 výstupní parametr nebo návratovou hodnotu v souladu s tohoto obrazce zprávy pro jejich výstupní zprávu. Následují příklady takových operací:  
  
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
 Vytváření bloků kanálu vyžaduje zprávy v pořadí doručení zpráv (bloky) doručit přesně jednou. To znamená, že musí být základní zásobník kanál s relacemi. Relace je možné poskytnou přenosu (například přenosu protokolu TCP) nebo kanál s relacemi protokolu (například ReliableSession kanál).  
  
### <a name="asynchronous-send-and-receive"></a>Asynchronní odesílání a přijímání  
 Asynchronní odesílání a příjem metody nejsou v této verzi bloků ukázkový kanál implementovány.  
  
## <a name="chunking-protocol"></a>Vytváření bloků protokolu  
 Vytváření bloků kanál definuje protokol, který označuje začátek a konec řadu bloky dat, a také pořadové číslo od každého bloku. Následující tři příklad zprávy ukazují spuštění, bloků dat a end zprávy s komentáři, které popisují klíčové aspekty každého.  
  
### <a name="start-message"></a>Zpráva spuštění  
  
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
  
### <a name="chunk-message"></a>Blok zpráv  
  
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
  
### <a name="end-message"></a>Zpráva ukončení  
  
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
  
## <a name="chunking-channel-architecture"></a>Vytváření bloků architektura kanálů  
 Vytváření bloků kanál `IDuplexSessionChannel` , na vysoké úrovni, následuje architektura typické kanálu. Je `ChunkingBindingElement` , které můžete vytvářet `ChunkingChannelFactory` a `ChunkingChannelListener`. `ChunkingChannelFactory` Vytváří instance `ChunkingChannel` když je vyzván k. `ChunkingChannelListener` Vytváří instance `ChunkingChannel` při přijetí nového vnitřního kanálu. `ChunkingChannel` Samotného je zodpovědná za odesílání a příjem zpráv.  
  
 Na další úrovni, `ChunkingChannel` spoléhá na několik komponent k implementaci bloků protokolu. Na straně odesílání kanál používá vlastní `XmlDictionaryWriter` volá `ChunkingWriter` , který neodpovídá skutečné bloků. `ChunkingWriter` používá vnitřního kanálu přímo k odesílání bloků. Použití vlastní `XmlDictionaryWriter` , umožníte nám odeslat bloky dat jako rozsáhlý na původní zprávu o průběhu zapisování. To znamená, že jsme neukládaného ve vyrovnávací paměti celý původní zprávy.  
  
 ![Dělením dat do bloků kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Na straně příjmu `ChunkingChannel` přetáhne zprávy z vnitřního kanálu a předá je do vlastní `XmlDictionaryReader` volá `ChunkingReader`, který reconstitutes původní zprávu z příchozí datové dávky. `ChunkingChannel` zabalí to `ChunkingReader` ve vlastním `Message` volaná implementaci `ChunkingMessage` a vrátí tuto zprávu vrstvě nad ní. Tato kombinace `ChunkingReader` a `ChunkingMessage` umožňuje zrušení bloku dat původní text zprávy, jako je čten stranou vrstvu nad namísto toho, aby do vyrovnávací paměti celý původní text zprávy. `ChunkingReader` má fronty, kde vyrovnávacích pamětí příchozí bloky dat až po maximální Konfigurovatelný počet bloků dat ve vyrovnávací paměti. Po dosažení maximální limit čtečky čeká na zprávy z fronty vybíjet ve vrstvě nad ní (to znamená podle jen pro čtení z původní text zprávy) nebo dokud se zobrazí maximální počet je dosaženo časového limitu.  
  
 ![Dělením dat do bloků kanál](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Dělením dat do bloků programovací Model  
 Vývojáři služeb můžete zadat zprávy, které mají být blokové použitím `ChunkingBehavior` atribut do operací v rámci smlouvy. Poskytuje atribut `AppliesTo` vlastnost, která umožňuje vývojářům k určení, jestli dat platí pro vstupní zprávy, výstupní zpráva nebo obojí. Následující příklad ukazuje použití `ChunkingBehavior` atribut:  
  
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
  
 V tomto programovacím modelu `ChunkingBindingElement` sestaví seznam identifikátorů URI, který identifikuje tak ty být rozdělený do bloků dat akce. Akce každé odchozí zprávy se porovná tento seznam a určují, jestli zprávy by měl být rozdělený do bloků dat nebo odesílají přímo.  
  
## <a name="implementing-the-send-operation"></a>Implementace operace odeslání  
 Na vysoké úrovni operace odeslání nejprve zkontroluje, zda odchozí zprávy musí být rozdělený do bloků dat a pokud ne, odešle zprávu přímo pomocí vnitřního kanálu.  
  
 Pokud zpráva musí být rozdělený do bloků dat, vytvoří novou odeslat `ChunkingWriter` a volání `WriteBodyContents` v odchozí zprávě předají se jí to `ChunkingWriter`. `ChunkingWriter` Neodpovídá zprávu dělením dat do bloků (včetně kopírování původní záhlaví zpráv do bloku zpráva spuštění) a odešle bloky dat pomocí vnitřního kanálu.  
  
 Za zmínku několik podrobností:  
  
-   Poslat prvním volání `ThrowIfDisposedOrNotOpened` zajistit, `CommunicationState` je otevřen.  
  
-   Odesílání se synchronizuje, aby tento pouze jedna zpráva byla odeslána současně pro každou relaci. Je `ManualResetEvent` s názvem `sendingDone` , která se resetuje při odesílání bloku zprávy. Jakmile je odeslána zpráva koncovým bloků dat, je tato událost nastavit. Tato událost nastavit před pokusem o odeslání odchozí zprávy čeká metody Send.  
  
-   Odeslat zámky `CommunicationObject.ThisLock` zabránit nesynchronizuje, změny stavu při odesílání. Najdete v článku <xref:System.ServiceModel.Channels.CommunicationObject> dokumentaci pro další informace o <xref:System.ServiceModel.Channels.CommunicationObject> stavy a stavového stroje.  
  
-   Časový limit předaný k odeslání se používá jako časový limit operace celý odeslání, který obsahuje všechny bloky dat odesílání.  
  
-   Vlastní `XmlDictionaryWriter` návrh byl zvolen ke Vyhněte se ukládání do vyrovnávací paměti celý původní text zprávy. Pokud se nám získat `XmlDictionaryReader` na text pomocí `message.GetReaderAtBodyContents` celého obsahu by být ukládány do vyrovnávací paměti. Místo toho budeme mít vlastní `XmlDictionaryWriter` , který je předán `message.WriteBodyContents`. Jako zprávu, která volá WriteBase64 zapisovače zapisovač zabalí bloků dat do zpráv a odešle je pomocí vnitřního kanálu. WriteBase64 blokuje, dokud se nepošle bloků.  
  
## <a name="implementing-the-receive-operation"></a>Implementace operace přijetí  
 Na vysoké úrovni operace obdržení nejprve zkontroluje, že příchozí zpráva není `null` a, který je akcí `ChunkingAction`. Pokud obě kritéria nesplňuje, je vrácená zpráva beze změny z parametru Receive. Jinak, vytvoří novou Receive `ChunkingReader` a nový `ChunkingMessage` zabalené kolem něj (pomocí volání `GetNewChunkingMessage`). Teprve potom se informuje, že noví `ChunkingMessage`, příjmu používá ke spouštění vláken fondu vláken `ReceiveChunkLoop`, který volá `innerChannel.Receive` ve smyčce a praktické vypnout bloků dat na `ChunkingReader` dokud přijatá zpráva ukončení bloku nebo dosažení časový limit přijetí.  
  
 Za zmínku několik podrobností:  
  
-   Jako je odesílání, příjem první volání `ThrowIfDisposedOrNotOepned` zajistit, `CommunicationState` je otevřen.  
  
-   Zobrazí se synchronizují také tak, že pouze jeden zpráva může dostat současně z relace. To je obzvláště důležité, protože po doručení zprávy do začátku bloku dat, všechny následné přijaté zprávy jsou očekávány bloků dat v rámci tohoto nového pořadí bloků dokud přijal zprávu ukončení bloku. Přijímat nelze vytahují zprávy z vnitřního kanálu, dokud se všechny bloky dat, které patří k aktuálně Probíhá zrušení rozdělený do bloků dat zprávy jsou přijímány. Chcete-li to provést, obdržet používá `ManualResetEvent` s názvem `currentMessageCompleted`, který je nastaven při zpráva ukončení bloku dat je přijetí a resetovat při doručení zprávy do nového bloku start.  
  
-   Na rozdíl od odeslání přijetí nezabraňuje synchronizované přechodů mezi stavy při příjmu. Například Zavřít lze volat při přijímání a čeká, až do dokončení čeká na příjem původní zpráva nebo zadaný časový limit.  
  
-   Časový limit předaný k příjmu se používá jako vypršení časového limitu pro celý přijímat operace, která zahrnuje příjem všechny bloky dat.  
  
-   Pokud vrstva, která zpracovává zprávy spotřebovává text zprávy s rychlostí nižší než počet příchozích zpráv bloků dat `ChunkingReader` ukládá do vyrovnávací paměti tyto příchozí bloky až do limitu určeném `ChunkingBindingElement.MaxBufferedChunks`. Po dosažení tohoto limitu, nemá nečistoty, se berou z nižší vrstvě, dokud nebude využívat ve vyrovnávací paměti datových dávek nebo je dosaženo časového limitu příjmu.  
  
## <a name="communicationobject-overrides"></a>V objektu CommunicationObject přepsání  
  
### <a name="onopen"></a>Při otevření  
 `OnOpen` volání `innerChannel.Open` vnitřního kanálu otevřít.  
  
### <a name="onclose"></a>Při zavření  
 `OnClose` nejprve nastaví `stopReceive` k `true` který signalizuje, že čeká na `ReceiveChunkLoop` zastavit. Pak čeká `receiveStopped` <xref:System.Threading.ManualResetEvent>, která je nastavena, když `ReceiveChunkLoop` zastaví. Za předpokladu, že `ReceiveChunkLoop` zastaví v rámci zadaného časového limitu, `OnClose` volání `innerChannel.Close` s zbývající časový limit.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` volání `innerChannel.Abort` přerušit vnitřního kanálu. Pokud je na čekající `ReceiveChunkLoop` získá výjimku z na čekající `innerChannel.Receive` volání.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Nevyžaduje zvláštní chování, pokud je v kanálu došlo k chybě tak `OnFaulted` nepřepíše.  
  
## <a name="implementing-channel-factory"></a>Implementace objektu pro vytváření kanálů  
 `ChunkingChannelFactory` Je zodpovědný za vytváření instancí `ChunkingDuplexSessionChannel` a pro kaskádové přechodů mezi stavy k výroba vnitřního kanálu.  
  
 `OnCreateChannel` Výroba vnitřního kanálu použije k vytvoření `IDuplexSessionChannel` vnitřního kanálu. Potom vytvoří nový `ChunkingDuplexSessionChannel` předáním tohoto vnitřního kanálu společně se seznamem zpráva akce, které mají být rozdělený do bloků dat a maximální počet bloků dat do vyrovnávací paměti při příjmu. Seznam zpráv akce, které mají být rozdělený do bloků dat a maximální počet bloků dat do vyrovnávací paměti jsou dva parametry předány `ChunkingChannelFactory` 've svém konstruktoru. V sekci `ChunkingBindingElement` popisuje, odkud pocházejí tyto hodnoty.  
  
 `OnOpen`, `OnClose`, `OnAbort` a ekvivalenty asynchronní volání odpovídající metody přechod stavu na výroba vnitřního kanálu.  
  
## <a name="implementing-channel-listener"></a>Prováděcí modul pro naslouchání kanálu  
 `ChunkingChannelListener` Představuje obálku kolem naslouchací proces vnitřního kanálu. Jeho hlavním smyslem, kromě volání delegáta pro tuto naslouchací proces vnitřního kanálu je zabalit nové `ChunkingDuplexSessionChannels` kolem kanály přijímán z vnitřního kanálu naslouchacího procesu. To se provádí v `OnAcceptChannel` a `OnEndAcceptChannel`. Nově vytvořený `ChunkingDuplexSessionChannel` je předán vnitřního kanálu společně s další parametry popsaných výše.  
  
## <a name="implementing-binding-element-and-binding"></a>Implementující Element vazby a vazby  
 `ChunkingBindingElement` zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`. `ChunkingBindingElement` Kontroluje, zda T v `CanBuildChannelFactory` \<T > a `CanBuildChannelListener` \<T > je typu `IDuplexSessionChannel` (pouze kanál nepodporuje vytváření bloků kanálu) a další prvky vazby ve vazbě podporu tohoto Typ kanálu.  
  
 `BuildChannelFactory`\<T > nejprve zkontroluje, že typ požadované kanálu může být sestaven a potom získá seznam zpráv akce, které mají být rozdělený do bloků dat. Další informace najdete v následující části. Potom vytvoří nový `ChunkingChannelFactory` předáním výroba vnitřního kanálu (vrácená `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), seznam zpráv akce a maximální počet bloků dat do vyrovnávací paměti. Maximální počet bloků, které pocházejí z vlastnost s názvem `MaxBufferedChunks` vystavené `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` má podobné implementace pro vytvoření `ChunkingChannelListener` a předají se jí vnitřního kanálu naslouchacího procesu.  
  
 Je vazbu příklad zahrnuté v této ukázce s názvem `TcpChunkingBinding`. Tato vazba se skládá ze dvou elementů vazby: `TcpTransportBindingElement` a `ChunkingBindingElement`. Kromě vystavení `MaxBufferedChunks` vlastnost vazby také nastaví některá `TcpTransportBindingElement` vlastnosti, jako `MaxReceivedMessageSize` (nastaví na `ChunkingUtils.ChunkSize` + 100 KB bajtů pro záhlaví).  
  
 `TcpChunkingBinding` také implementuje `IBindingRuntimePreferences` a vrátí hodnotu true z `ReceiveSynchronously` metoda označující, že jsou implementovány pouze synchronní volání Receive.  
  
### <a name="determining-which-messages-to-chunk"></a>Určení, které zprávy do bloků dat  
 Vytváření bloků kanál chunks pouze zprávy identifikován `ChunkingBehavior` atribut. `ChunkingBehavior` Implementuje třída `IOperationBehavior` a je implementována pomocí volání `AddBindingParameter` metody. V této metodě `ChunkingBehavior` ověří hodnotu jeho `AppliesTo` vlastnosti (`InMessage`, `OutMessage` nebo obojí) k určení, které zprávy by měl být rozdělený do bloků dat. Potom získá akce pro každou z těchto zpráv z (z kolekce zpráv na `OperationDescription`) a přidá jej do kolekce řetězců obsažených v rámci instance `ChunkingBindingParameter`. To potom přidá `ChunkingBindingParameter` zadanému `BindingParameterCollection`.  
  
 To `BindingParameterCollection` je předáno uvnitř `BindingContext` na každý prvek vazby ve vazbě při tento element vazby sestavení výrobu kanálu nebo modul pro naslouchání kanálu. `ChunkingBindingElement`Vaší implementace `BuildChannelFactory<T>` a `BuildChannelListener<T>` toto vyžádat `ChunkingBindingParameter` z celkového počtu `BindingContext’`s `BindingParameterCollection`. Kolekci akcí, které jsou obsažené `ChunkingBindingParameter` je pak předán `ChunkingChannelFactory` nebo `ChunkingChannelListener`, který pak předává jej do `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
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
  
## <a name="see-also"></a>Viz také:
