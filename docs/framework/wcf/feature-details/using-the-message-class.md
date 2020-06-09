---
title: Používání třídy Message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: 142578ef76a70fed27dc0137378b59e228cd25c9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585646"
---
# <a name="using-the-message-class"></a>Používání třídy Message
<xref:System.ServiceModel.Channels.Message>Třída je zásadní pro Windows Communication Foundation (WCF). Veškerá komunikace mezi klienty a službami nakonec vede k <xref:System.ServiceModel.Channels.Message> posílání a přijímání instancí.  
  
 Nebudete obvykle pracovat s <xref:System.ServiceModel.Channels.Message> třídou přímo. Místo toho se k popisu příchozích a odchozích zpráv používají konstrukce modelu služby WCF, například kontrakty dat, kontrakty zpráv a kontrakty operací. V některých pokročilých scénářích však můžete programovat přímo pomocí <xref:System.ServiceModel.Channels.Message> třídy. Například může být vhodné použít <xref:System.ServiceModel.Channels.Message> třídu:  
  
- Pokud potřebujete alternativní způsob vytváření obsahu odchozí zprávy (například vytvoření zprávy přímo ze souboru na disku) místo serializace .NET Framework objektů.  
  
- Pokud potřebujete alternativní způsob použití příchozího obsahu zprávy (například pokud chcete použít transformaci XSLT na nezpracovaný obsah XML) místo deserializace do objektů .NET Framework.  
  
- Pokud potřebujete, aby se zprávy všeobecně vyrovnaly bez ohledu na obsah zpráv (například při směrování nebo předávání zpráv při sestavování směrovače, Vyrovnávání zatížení nebo systému pro publikování a odběr).  
  
 Před použitím <xref:System.ServiceModel.Channels.Message> třídy se seznamte s architekturou přenosu dat WCF v [přenos dat přehled architektury](data-transfer-architectural-overview.md).  
  
 <xref:System.ServiceModel.Channels.Message>Pro data je kontejner pro obecné účely, ale jeho návrh úzce sleduje návrh zprávy v protokolu SOAP. Stejně jako v protokolu SOAP, zpráva obsahuje i tělo zprávy a záhlaví. Tělo zprávy obsahuje skutečná data datové části, zatímco hlavičky obsahují další pojmenované datové kontejnery. Pravidla pro čtení a zápis těla a záhlaví jsou odlišná, například hlavičky jsou v paměti vždy uloženy do vyrovnávací paměti a mohou být v libovolném pořadí k dispozici v libovolném pořadí, zatímco tělo může být načteno pouze jednou a může být použito jako datový proud. V normálním případě při použití protokolu SOAP je tělo zprávy namapováno na tělo protokolu SOAP a hlavičky zprávy jsou namapovány na hlavičky protokolu SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Použití třídy zpráv v operacích  
 Třídu můžete použít <xref:System.ServiceModel.Channels.Message> jako vstupní parametr operace, návratovou hodnotu operace nebo obojí. Pokud <xref:System.ServiceModel.Channels.Message> se použije kdekoli v operaci, platí následující omezení:  
  
- Operace nemůže mít žádné `out` parametry ani `ref` .  
  
- Nemůžete mít více než jeden `input` parametr. Pokud je parametr přítomen, musí být buď zpráva nebo typ kontraktu zprávy.  
  
- Návratový typ musí být buď `void` , `Message` nebo typ kontraktu zprávy.  
  
 Následující příklad kódu obsahuje platný kontrakt operace.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Vytváření základních zpráv  
 <xref:System.ServiceModel.Channels.Message>Třída poskytuje statické `CreateMessage` metody továrny, které lze použít k vytvoření základních zpráv.  
  
 Všechna `CreateMessage` přetížení přebírají parametr verze typu <xref:System.ServiceModel.Channels.MessageVersion> , který označuje verze SOAP a WS-Addressing, které mají být použity pro zprávu. Pokud chcete použít stejné verze protokolů jako příchozí zprávy, můžete použít <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> vlastnost u <xref:System.ServiceModel.OperationContext> instance získané z <xref:System.ServiceModel.OperationContext.Current%2A> Vlastnosti. Většina `CreateMessage` přetížení má také řetězcový parametr, který označuje akci SOAP, která se má použít pro zprávu. Verze se dá nastavit tak, aby `None` se zakázalo generování obálky protokolu SOAP. zpráva se skládá jenom z těla.  
  
## <a name="creating-messages-from-objects"></a>Vytváření zpráv z objektů  
 Základní `CreateMessage` přetížení, které přijímá pouze verzi a akci, vytvoří zprávu s prázdným textem. Jiné přetížení přebírá další <xref:System.Object> parametr. tím se vytvoří zpráva, jejíž tělo je serializovaná reprezentace daného objektu. <xref:System.Runtime.Serialization.DataContractSerializer>Pro serializaci použijte výchozí nastavení. Pokud chcete použít jiný serializátor nebo chcete nakonfigurovat jiné nastavení `DataContractSerializer` , použijte `CreateMessage` přetížení, které také převezme `XmlObjectSerializer` parametr.  
  
 Například chcete-li vrátit objekt ve zprávě, můžete použít následující kód.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Vytváření zpráv z čtecích zařízení XML  
 Existují `CreateMessage` přetížení, která přijímají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> pro tělo místo objektu. V tomto případě tělo zprávy obsahuje kód XML, který je výsledkem čtení z předaného čtecího modulu XML. Například následující kód vrátí zprávu s obsahem textu načteného ze souboru XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Kromě toho existují `CreateMessage` přetížení, která přijímají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> který představuje celou zprávu, a ne jenom tělo. Tato přetížení také přebírají celočíselný `maxSizeOfHeaders` parametr. Hlavičky jsou vždy uloženy do vyrovnávací paměti ihned po vytvoření zprávy a tento parametr omezuje velikost vyrovnávací paměti, která je provedena. Je důležité nastavit tento parametr na bezpečnou hodnotu, pokud XML pochází z nedůvěryhodného zdroje, aby se zmírnila možnost útoku DOS (Denial of Service). Verze zprávy SOAP a WS-Addressing, kterou čtečka XML představuje, musí odpovídat verzím uvedeným pomocí parametru Version.  
  
## <a name="creating-messages-with-bodywriter"></a>Vytváření zpráv pomocí BodyWriter  
 Jedno `CreateMessage` Přetížení přebírá `BodyWriter` instanci, která popisuje tělo zprávy. `BodyWriter`Je abstraktní třída, která může být odvozena pro přizpůsobení způsobu vytvoření těla zprávy. Můžete vytvořit vlastní `BodyWriter` odvozenou třídu pro popis těla zprávy vlastním způsobem. Musíte přepsat `BodyWriter.OnWriteBodyContents` metodu, která přijímá. <xref:System.Xml.XmlDictionaryWriter> Tato metoda zodpovídá za vypsání těla.  
  
 Zapisovače textu lze ukládat do vyrovnávací paměti nebo bez vyrovnávací paměti (streamované). Zapisovače těla obsahu ve vyrovnávací paměti může kdykoliv vypsat svůj obsah, zatímco streamované objekty můžou obsah jenom jednou zapsat. `IsBuffered`Vlastnost označuje, zda je zapisovač textu zprávy ukládán do vyrovnávací paměti. Můžete jej nastavit pro zapisovač těla voláním chráněného `BodyWriter` konstruktoru, který přebírá `isBuffered` logický parametr. Autoři textu podporují vytvoření zapisovače těla zprávy z neuloženého zapisovače těla. Můžete přepsat `OnCreateBufferedCopy` metodu pro přizpůsobení tohoto procesu. Ve výchozím nastavení je použita vyrovnávací paměť, která obsahuje kód XML vrácený funkcí `OnWriteBodyContents` . `OnCreateBufferedCopy`přebírá `maxBufferSize` celočíselný parametr; Pokud přepíšete tuto metodu, nemusíte vytvářet vyrovnávací paměti větší, než je tato maximální velikost.  
  
 `BodyWriter`Třída poskytuje `WriteBodyContents` `CreateBufferedCopy` metody a, které jsou v podstatě tenké obálky kolem `OnWriteBodyContents` a `OnCreateBufferedCopy` metody, v uvedeném pořadí. Tyto metody provádějí kontrolu stavu, aby se zajistilo, že zapisovači těla bez vyrovnávací paměti není k dispozici více než jednou. Tyto metody jsou volány přímo pouze při vytváření vlastních `Message` odvozených tříd založených na `BodyWriters` .  
  
## <a name="creating-fault-messages"></a>Vytváření zpráv o chybách  
 Můžete použít určitá `CreateMessage` přetížení k vytvoření zpráv o chybách protokolu SOAP. Nejzákladnější z nich přebírá <xref:System.ServiceModel.Channels.MessageFault> objekt, který popisuje chybu. Další přetížení jsou k dispozici pro usnadnění. První takové přetížení získá `FaultCode` řetězec důvod a a vytvoří `MessageFault` pomocí `MessageFault.CreateFault` těchto informací. Druhé přetížení přebírá objekt detail a také ho předává `CreateFault` spolu s kódem chyby a důvodem. Například následující operace vrátí chybu.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Extrakce dat těla zprávy  
 `Message`Třída podporuje více způsobů extrakce informací z těla. Tyto kategorie je možné klasifikovat v následujících kategoriích:  
  
- Získání celého textu zprávy zapsaného najednou do zapisovače XML. To se označuje jako *zápis zprávy*.  
  
- Získání čtecího modulu XML přes tělo zprávy To vám umožní později získat přístup k hlavnímu textu zprávy podle potřeby. Tento postup se označuje jako *čtení zprávy*.  
  
- Celou zprávu, včetně jejího těla, lze zkopírovat do vyrovnávací paměti typu v paměti <xref:System.ServiceModel.Channels.MessageBuffer> . Tento postup se označuje jako *kopírování zprávy*.  
  
 K obsahu můžete přistupovat `Message` jenom jednou, a to bez ohledu na to, jak k němu přistupuje. Objekt zprávy má `State` vlastnost, která je zpočátku nastavena na hodnotu vytvořeno. Tři metody přístupu popsané v předchozím seznamu nastaví stav na zapsat, číst a kopírovat, v uvedeném pořadí. Kromě toho `Close` může metoda nastavit stav na uzavřeno, pokud již není požadován obsah textu zprávy. Tělo zprávy lze použít pouze ve stavu vytvořeno a neexistuje žádný způsob, jak se vrátit do stavu Created po změně stavu.  
  
## <a name="writing-messages"></a>Zápis zpráv  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>Metoda zapisuje obsah těla dané `Message` instance do daného zapisovače XML. <xref:System.ServiceModel.Channels.Message.WriteBody%2A>Metoda se shoduje s tím rozdílem, že obklopuje obsah těla v příslušném prvku obálky (například <`soap:body`>). Nakonec <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> zapíše celou zprávu, včetně obálky s obálkami protokolu SOAP a záhlaví. Pokud je protokol SOAP vypnutý ( <xref:System.ServiceModel.Channels.Message.Version> je <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> ), všechny tři metody mají stejnou věc: zapisují obsah textu zprávy.  
  
 Například následující kód zapíše tělo příchozí zprávy do souboru.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dvě další pomocné metody zapisují určité značky počátečního elementu SOAP. Tyto metody nepřístupují k tělo zprávy, takže nemění stav zprávy. Zde jsou některé z nich:  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>zapíše element počáteční text, například `<soap:Body>` .  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>zapisuje spouštěcí obálku, například `<soap:Envelope>` .  
  
 Chcete-li zapsat odpovídající značky elementu end, zavolejte `WriteEndElement` na odpovídající ZAPISOVAČ XML. Tyto metody jsou volány pouze zřídka.  
  
## <a name="reading-messages"></a>Čtení zpráv  
 Hlavní způsob, jak číst tělo zprávy, je zavolat <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> . Vrátíte se zpátky <xref:System.Xml.XmlDictionaryReader> , který můžete použít ke čtení textu zprávy. Všimněte si, že <xref:System.ServiceModel.Channels.Message> přechody do stavu čtení hned po <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> volání, a ne při použití vráceného čtecího modulu XML.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A>Metoda také umožňuje přístup k tělo zprávy jako typový objekt. Interně používá tato metoda `GetReaderAtBodyContents` , a proto také přechází stav zprávy do <xref:System.ServiceModel.Channels.MessageState.Read> stavu (viz <xref:System.ServiceModel.Channels.Message.State%2A> vlastnost).  
  
 Je vhodné kontrolovat <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> vlastnost, v takovém případě je tělo zprávy prázdné a <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> vyvolá <xref:System.InvalidOperationException> . Pokud se jedná o přijatou zprávu (například odpověď), můžete také ověřit <xref:System.ServiceModel.Channels.Message.IsFault%2A> , zda zpráva obsahuje chybu.  
  
 Nejzákladnější přetížení <xref:System.ServiceModel.Channels.Message.GetBody%2A> deserializace tělo zprávy do instance typu (označená obecným parametrem) s použitím <xref:System.Runtime.Serialization.DataContractSerializer> konfigurace s výchozím nastavením a <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> zakázanou kvótou. Pokud chcete použít jiný Serializační modul nebo nakonfigurovat `DataContractSerializer` nevýchozí způsob, použijte <xref:System.ServiceModel.Channels.Message.GetBody%2A> přetížení, které přijímá <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
 Například následující kód extrahuje data z textu zprávy, který obsahuje serializovaný `Person` objekt, a vytiskne jméno osoby.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Kopírování zprávy do vyrovnávací paměti  
 Někdy je nutné mít přístup k tělo zprávy více než jednou, například k přeposílání stejné zprávy do více cílů v rámci systému odběratele vydavatele. V takovém případě je nutné ukládat celou zprávu (včetně těla) do vyrovnávací paměti. Můžete to provést voláním metody <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29> . Tato metoda přebírá celočíselný parametr, který představuje maximální velikost vyrovnávací paměti, a vytváří vyrovnávací paměť, která není větší než tato velikost. Pokud zpráva pochází z nedůvěryhodného zdroje, je nutné ji nastavit na bezpečnou hodnotu.  
  
 Vyrovnávací paměť se vrátí jako <xref:System.ServiceModel.Channels.MessageBuffer> instance. K datům ve vyrovnávací paměti se můžete dostat několika způsoby. Hlavním způsobem je zavolat <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> na vytvoření `Message` instancí z vyrovnávací paměti.  
  
 Dalším způsobem, jak získat přístup k datům ve vyrovnávací paměti, je implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní, které <xref:System.ServiceModel.Channels.MessageBuffer> Třída implementuje pro přímý přístup k základnímu XML. Některá <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> přetížení umožňují vytvářet <xref:System.Xml.XPath> navigátory chráněné kvótou uzlu, což omezuje počet uzlů XML, které mohou být navštíveny. To pomáhá zabránit útokům DOS (Denial of Service) na základě zdlouhavého času zpracování. Tato nabídka je ve výchozím nastavení zakázaná. Některá `CreateNavigator` přetížení umožňují určit, jak se má v XML zpracovat prázdné místo pomocí <xref:System.Xml.XmlSpace> výčtu s výchozím nastavením `XmlSpace.None` .  
  
 Konečný způsob, jak získat přístup k obsahu vyrovnávací paměti zpráv, je napsat svůj obsah do datového proudu pomocí <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> .  
  
 Následující příklad demonstruje proces práce s `MessageBuffer` : příchozí zpráva je předána více příjemcům a poté zaznamenána do souboru. Bez ukládání do vyrovnávací paměti není to možné, protože tělo zprávy je pak možné použít pouze jednou.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer`Třída obsahuje další členy, které se zaznamenaly. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A>Metodu lze volat pro uvolnění prostředků, pokud již není požadován obsah vyrovnávací paměti. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A>Vlastnost vrací velikost přidělené vyrovnávací paměti. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A>Vlastnost vrátí typ obsahu MIME zprávy.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Přístup k textu zprávy pro ladění  
 Pro účely ladění můžete zavolat <xref:System.ServiceModel.Channels.Message.ToString%2A> metodu pro získání reprezentace zprávy jako řetězce. Tato reprezentace obecně odpovídá způsobu, jakým by zpráva vypadala v případě, že byla kódována pomocí textového kodéru, s tím rozdílem, že kód XML by byl pro lidské čitelnosti lépe naformátován. Jedinou výjimkou je tělo zprávy. Tělo lze číst pouze jednou a `ToString` nezmění stav zprávy. Proto metoda nemusí `ToString` být schopna získat přístup k textu a může nahradit zástupný symbol (například "..."). nebo tři tečky) místo textu zprávy. Proto nepoužívejte `ToString` k protokolování zpráv, pokud je obsah zprávy důležitý.  
  
## <a name="accessing-other-message-parts"></a>Přístup k ostatním částem zprávy  
 K dispozici jsou různé vlastnosti pro přístup k informacím o jiné zprávě než obsah těla. Tyto zprávy však nelze volat, jakmile byla zpráva zavřena:  
  
- <xref:System.ServiceModel.Channels.Message.Headers%2A>Vlastnost představuje záhlaví zpráv. Další informace najdete v části práce se záhlavími dále v tomto tématu.  
  
- <xref:System.ServiceModel.Channels.Message.Properties%2A>Vlastnost představuje vlastnosti zprávy, které jsou částmi pojmenovaných dat připojených ke zprávě, která obecně není generována při odeslání zprávy. Další informace najdete v části práce s vlastnostmi dále v tomto tématu.  
  
- <xref:System.ServiceModel.Channels.Message.Version%2A>Vlastnost označuje verzi SOAP a WS-Addressing, která je přidružená ke zprávě, nebo `None` Pokud je protokol SOAP zakázán.  
  
- <xref:System.ServiceModel.Channels.Message.IsFault%2A>Vlastnost vrátí, `true` zda je zpráva chybová zpráva protokolu SOAP.  
  
- <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>Vlastnost vrátí, `true` zda je zpráva prázdná.  
  
 Metodu lze použít <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> pro přístup k určitému atributu u prvku obálky těla (například `<soap:Body>` ) identifikovaného určitým názvem a oborem názvů. Pokud takový atribut není nalezen, `null` je vrácen. Tuto metodu lze volat pouze v případě, že `Message` je ve stavu Created (když tělo zprávy ještě neproběhlo).  
  
## <a name="working-with-headers"></a>Práce se záhlavími  
 `Message`Může obsahovat libovolný počet jmenovaných fragmentů XML nazývaných *hlavičky*. Jednotlivé fragmenty jsou normálně mapovány na hlavičku SOAP. Záhlaví jsou k dispozici prostřednictvím `Headers` vlastnosti typu <xref:System.ServiceModel.Channels.MessageHeaders> . <xref:System.ServiceModel.Channels.MessageHeaders>je kolekce <xref:System.ServiceModel.Channels.MessageHeaderInfo> objektů a k jednotlivým hlavičkám lze přistupovat prostřednictvím jejího <xref:System.Collections.IEnumerable> rozhraní nebo prostřednictvím indexeru. Například následující kód uvádí názvy všech hlaviček v `Message` .  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Přidávání, odebírání a hledání hlaviček  
 Novou hlavičku můžete na konci všech existujících hlaviček přidat pomocí <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> metody. Můžete použít <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> metodu pro vložení záhlaví do konkrétního indexu. Existující záhlaví jsou pro vloženou položku posunuty. Záhlaví jsou uspořádána podle jejich indexu a první dostupný index je 0. Pomocí různých <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> přetížení metod můžete přidat záhlaví z jiné `Message` `MessageHeaders` instance nebo. Některá přetížení kopírují jednu jednotlivou hlavičku, zatímco ostatní si je zkopírují. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A>Metoda odebere všechny hlavičky. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A>Metoda odebere hlavičku na konkrétní index (posune všechna záhlaví za ní). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A>Metoda odebere všechny hlavičky s určitým názvem a oborem názvů.  
  
 Načte konkrétní hlavičku pomocí <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> metody. Tato metoda získá název a obor názvů záhlaví, které má být nalezeno, a vrátí jeho index. Pokud se hlavička vyskytuje více než jednou, je vyvolána výjimka. Pokud záhlaví není nalezeno, vrátí-1.  
  
 V modelu záhlaví SOAP mohou hlavičky mít `Actor` hodnotu, která určuje zamýšleného příjemce hlavičky. Nejzákladnější `FindHeader` přetížení vyhledává pouze hlavičky určené pro konečného příjemce zprávy. Další přetížení však umožňuje určit, které `Actor` hodnoty budou zahrnuty ve vyhledávání. Další informace najdete v tématu specifikace SOAP.  
  
 <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29>K dispozici je metoda kopírování hlaviček z <xref:System.ServiceModel.Channels.MessageHeaders> kolekce do pole <xref:System.ServiceModel.Channels.MessageHeaderInfo> objektů.  
  
 Pro přístup k datům XML v hlavičce můžete volat <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> a vracet čtecí modul XML pro konkrétní rejstřík hlaviček. Pokud chcete deserializovat obsah hlavičky do objektu, použijte <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> nebo jedno z dalších přetížení. Většina základních přetížení deserializace hlaviček pomocí <xref:System.Runtime.Serialization.DataContractSerializer> nakonfigurovaného výchozího způsobu. Pokud chcete použít jiný serializátor nebo jinou konfiguraci `DataContractSerializer` , použijte jedno z přetížení, které přijímá `XmlObjectSerializer` . Existují také přetížení, která přijímají název hlavičky, obor názvů a volitelně seznam `Actor` hodnot namísto indexu. Jedná se o kombinaci `FindHeader` a `GetHeader` .  
  
## <a name="working-with-properties"></a>Práce s vlastnostmi  
 `Message`Instance může obsahovat libovolný počet pojmenovaných objektů libovolných typů. Tato kolekce je k dispozici prostřednictvím `Properties` vlastnosti typu `MessageProperties` . Kolekce implementuje <xref:System.Collections.Generic.IDictionary%602> rozhraní a funguje jako mapování z <xref:System.String> na <xref:System.Object> . Hodnoty vlastností se obvykle nemapují přímo na žádnou část zprávy na lince, ale místo toho poskytují různé pomocné parametry zpracování zpráv pro různé kanály v zásobníku kanálů WCF nebo v <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> rozhraní služby. Příklad najdete v tématu [Přehled architektury přenos dat](data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Dědění z třídy Message  
 Pokud předdefinované typy zpráv vytvořené pomocí `CreateMessage` nesplňují vaše požadavky, vytvořte třídu, která je odvozena z `Message` třídy.  
  
### <a name="defining-the-message-body-contents"></a>Definice obsahu textu zprávy  
 Existují tři primární techniky pro přístup k datům v těle zprávy: zápis, čtení a zkopírování do vyrovnávací paměti. Tyto operace nakonec vedou k <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A> volání metod, a v <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> odvozené třídě `Message` . Základní `Message` třída zaručuje, že pro každou instanci je volána pouze jedna z těchto metod `Message` a že není volána více než jednou. Základní třída také zajišťuje, že metody nejsou volány na uzavřenou zprávu. Stav zprávy ve vaší implementaci není nutné sledovat.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>je abstraktní metoda a musí být implementována. Nejzákladnější způsob, jak definovat obsah těla zprávy, je napsat pomocí této metody. Například následující zpráva obsahuje 100 000 náhodných čísel od 1 do 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents>Metody a <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> mají výchozí implementace, které fungují ve většině případů. Výchozí implementace implementují <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> , ukládají výsledky do vyrovnávací paměti a pracují s výslednou vyrovnávací pamětí. V některých případech to ale nemusí být dostatečné. V předchozím příkladu čte zpráva výsledky v 100 000 prvcích XML, které se ukládají do vyrovnávací paměti, což nemusí být žádoucí. Můžete chtít přepsat <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> a vrátit vlastní <xref:System.Xml.XmlDictionaryReader> odvozenou třídu, která bude obsluhovat náhodná čísla. Pak můžete přepsat <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> pro použití čtecího modulu, který <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> Metoda vrátí, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Podobně můžete chtít přepsat `OnCreateBufferedCopy` pro vrácení vlastní `MessageBuffer` odvozené třídy.  
  
 Kromě poskytování obsahu textu zprávy musí třída odvozená vaše zpráva také přepsat `Version` `Headers` vlastnosti, a `Properties` .  
  
 Všimněte si, že pokud vytvoříte kopii zprávy, kopie použije záhlaví zprávy z původní.  
  
### <a name="other-members-that-can-be-overridden"></a>Další členové, kteří mohou být přepsáni  
 Můžete přepsat <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> metody, a a <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> určit tak, jak mají být zapsány počáteční značky na obálku protokolu SOAP, hlavičky protokolu SOAP a prvky těla protokolu SOAP. Tyto obvykle odpovídají `<soap:Envelope>` , `<soap:Header>` a `<soap:Body>` . Tyto metody by obvykle neměly zapisovat cokoli, pokud se <xref:System.ServiceModel.Channels.Message.Version> vlastnost vrátí <xref:System.ServiceModel.Channels.MessageVersion.None> .  
  
> [!NOTE]
> Výchozí implementace `OnGetReaderAtBodyContents` volání `OnWriteStartEnvelope` a `OnWriteStartBody` před voláním `OnWriteBodyContents` a ukládání výsledků do vyrovnávací paměti. Hlavičky nejsou zapsány.  
  
 Přepsat <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> metodu pro změnu způsobu, jakým je celá zpráva vytvořena z různých částí. `OnWriteMessage`Metoda je volána z <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> a z výchozí <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementace. Všimněte si, že přepsání <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> není osvědčeným postupem. Je lepší přepsat vhodné `On` metody (například,, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> a <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A> .  
  
 Přepsáním <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> přepište způsob reprezentace textu zprávy během ladění. Výchozí hodnota je reprezentovat jako tři tečky ("..."). Všimněte si, že tuto metodu lze volat několikrát, pokud je stav zprávy cokoli jiného než uzavřeno. Implementace této metody by nikdy neměla způsobit žádnou akci, kterou je nutné provést pouze jednou (například čtení z datového proudu jen pro odesílání).  
  
 Přepište <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> metodu tak, aby povolovala přístup k atributům prvku SOAP body. Tuto metodu lze volat libovolným počtem, ale `Message` základní typ zaručuje, že je volána pouze v případě, že je zpráva ve stavu Created (čas vytvoření). Není nutné kontrolovat stav implementace. Výchozí implementace vždy vrátí `null` , což znamená, že element tělo neobsahuje žádné atributy.  
  
 Pokud `Message` objekt musí provést jakékoli speciální vyčištění, když tělo zprávy již není vyžadováno, můžete přepsat <xref:System.ServiceModel.Channels.Message.OnClose%2A> . Výchozí implementace neprovádí žádnou akci.  
  
 `IsEmpty`Vlastnosti a `IsFault` lze přepsat. Ve výchozím nastavení obě vrátí `false` .
