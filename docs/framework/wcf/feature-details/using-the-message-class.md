---
title: Používání třídy Message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: 0ff65d9173838a8eb8850253e62d822f06942f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-message-class"></a>Používání třídy Message
<xref:System.ServiceModel.Channels.Message> Třída je základní pro Windows Communication Foundation (WCF). Veškerá komunikace mezi klienty a služby ve výsledku <xref:System.ServiceModel.Channels.Message> instancí se odesílají a přijímají.  
  
 By obvykle interakci s <xref:System.ServiceModel.Channels.Message> přímo třídu. Místo toho konstrukce modelu služby WCF, například kontrakty dat, kontrakty zpráv a kontrakty operace, se používají k popisu příchozí a odchozí zprávy. Ale v některých pokročilé scénáře, které můžete naprogramovat pomocí <xref:System.ServiceModel.Channels.Message> přímo třídu. Například můžete chtít použít <xref:System.ServiceModel.Channels.Message> třídy:  
  
-   Když potřebujete alternativní způsob vytváření odchozí obsah zprávy (například vytvoření zprávy přímo ze souboru na disku) namísto serializaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty.  
  
-   Když potřebujete alternativní způsob použití příchozí obsah zprávy (například pokud chcete použít transformaci XSLT na nezpracovaná obsah XML) namísto deserializaci do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty.  
  
-   Pokud je potřeba řešit zprávy obecné způsobem, bez ohledu na obsah zprávy (například v případě, že směrování nebo předávat zprávy při sestavování směrovač, Vyrovnávání zatížení nebo publikování-přihlášení k odběru systému).  
  
 Před použitím <xref:System.ServiceModel.Channels.Message> třídy, seznamte se s architekturou přenos dat WCF v [architektury Přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 A <xref:System.ServiceModel.Channels.Message> je kontejner pro obecné účely pro data, ale jeho návrhu přesně dodržuje návrh zprávy v protokolu SOAP. Stejně jako v protokolu SOAP, zpráva má tělo zprávy a hlaviček. Tělo zprávy obsahuje skutečné datová část dat, zatímco hlavičky obsahovat další data s názvem kontejnery. Pravidla pro čtení a zápis textu a hlavičky se liší, například hlavičky jsou vždy do vyrovnávací paměti v paměti a můžete získat přístup v žádné pořadí libovolný počet dobu, zatímco text lze číst pouze jednou a může být streamování. Za normálních okolností při použití protokolu SOAP, tělo zprávy je namapovaná na textu protokolu SOAP a záhlaví zprávy jsou namapované na hlavičky SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Používání třídy Message v operacích  
 Můžete použít <xref:System.ServiceModel.Channels.Message> třída jako vstupní parametr operace, návratová hodnota operace, nebo obojí. Pokud <xref:System.ServiceModel.Channels.Message> slouží kdekoli v operaci, platí následující omezení:  
  
-   Operace nemůže mít žádné `out` nebo `ref` parametry.  
  
-   Nemůže být více než jeden `input` parametr. Pokud se nachází parametr, musí být zpráva nebo typ kontrakt zprávy.  
  
-   Návratový typ musí být buď `void`, `Message`, nebo zprávu typ kontraktu.  
  
 Následující příklad kódu obsahuje kontraktu platná operace.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Vytváření základních zprávy  
 <xref:System.ServiceModel.Channels.Message> Třída poskytuje statické `CreateMessage` factory metody, které můžete použít k vytvoření základní zpráv.  
  
 Všechny `CreateMessage` přetížení přebírají parametr verze typu <xref:System.ServiceModel.Channels.MessageVersion> určující verze protokolu SOAP a WS-Addressing sloužící ke zprávě. Pokud chcete použít stejné verze protokolu jako příchozí zprávy, můžete použít <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> vlastnost na <xref:System.ServiceModel.OperationContext> instance získaný <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost. Většina `CreateMessage` přetížení také mít parametr řetězec, který určuje použití pro zprávu protokolu SOAP akce. Verze může být nastaven na `None` zakázat generování obálky protokolu SOAP; tato zpráva se skládá pouze obsahu.  
  
## <a name="creating-messages-from-objects"></a>Vytváření zprávy z objektů  
 Nejzákladnější `CreateMessage` přetížení, které přijímá pouze verze a akce vytvoří zprávu s prázdným textem zprávy. Další přetížení trvá Další <xref:System.Object> parametr; tím se vytvoří zprávu, jejíž text je serializovaná reprezentace daného objektu. Použití <xref:System.Runtime.Serialization.DataContractSerializer> s výchozím nastavením pro serializaci. Pokud chcete použít jiný serializátor, nebo chcete `DataContractSerializer` nakonfigurována jinak než pomocí `CreateMessage` přetížení, které přijímá také `XmlObjectSerializer` parametr.  
  
 Například pokud chcete vrátit objekt ve zprávě, můžete použít následující kód.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Vytváření zprávy z čtečky XML  
 Existují `CreateMessage` přetížení trvají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> pro tělo namísto objektu. V takovém případě tělo zprávy obsahuje XML, který je výsledkem čtení z předaný čtecí modul XML. Například následující kód vrátí zprávu s textu, že obsah číst ze souboru XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Kromě toho existují `CreateMessage` přetížení trvají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> představující celé zprávy a nikoli pouze text. Tato přetížení také trvat celé `maxSizeOfHeaders` parametr. Hlavičky jsou vždy do vyrovnávací paměti do paměti Jakmile se vytvoří zprávu, a tento parametr omezuje množství ukládání do vyrovnávací paměti, který probíhá. Je důležité v případě XML pochází z nedůvěryhodného zdroje zmírnit možnost útoku DOS tento parametr nastavte na hodnotu bezpečné. Verze protokolu SOAP a WS-Addressing zprávy, kterou představuje čtecí modul XML musí odpovídat verze uvedené, pomocí parametru verze.  
  
## <a name="creating-messages-with-bodywriter"></a>Vytváření zprávy s BodyWriter  
 Jeden `CreateMessage` přetížení trvá `BodyWriter` instance k popisu tělo zprávy. A `BodyWriter` je abstraktní třída, která lze odvodit přizpůsobit vytváření zpráv. Můžete vytvořit vlastní `BodyWriter` odvozené třídy k popisu těla zprávy vlastním způsobem. Je nutné přepsat `BodyWriter.OnWriteBodyContents` metody, která použije <xref:System.Xml.XmlDictionaryWriter>; tato metoda je zodpovědné za zápis na text.  
  
 Můžete do vyrovnávací paměti zapisovače textu nebo bez vyrovnávací paměti (streamování). Zapisovače textu ve vyrovnávací paměti můžete zapsat jejich obsah libovolný počet dobu, během přenášené datovými proudy ty můžete zapsat jejich obsah pouze jednou. `IsBuffered` Vlastnost určuje, zda je zapisovač textu do vyrovnávací paměti nebo ne. Můžete nastavit to pro vaše zapisovač textu voláním chráněné `BodyWriter` konstruktor, který přebírá `isBuffered` logického parametru. Zapisovače textu podporují vytváření zapisovač textu ve vyrovnávací paměti z zapisovač textu bez vyrovnávací paměti. Je možné přepsat `OnCreateBufferedCopy` metodu za účelem přizpůsobení tohoto procesu. Ve výchozím nastavení, v paměti vyrovnávací paměti, který obsahuje XML vrácený `OnWriteBodyContents` se používá. `OnCreateBufferedCopy` přijímá `maxBufferSize` celé číslo parametru; Pokud tuto metodu přepíšete, nesmí vytvoříte vyrovnávací paměti větší než této maximální velikosti.  
  
 `BodyWriter` Třída poskytuje `WriteBodyContents` a `CreateBufferedCopy` metody, které jsou v podstatě dynamicky obálky kolem `OnWriteBodyContents` a `OnCreateBufferedCopy` metody, v uvedeném pořadí. Tyto metody provedení stavu kontrole zajistíte zapisovač textu bez vyrovnávací paměti není přístup k více než jednou. Tyto metody jsou pouze při vytváření vlastní volat přímo `Message` odvozených třídách na základě `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Vytváření selhání zprávy  
 Můžete použít určité `CreateMessage` poruch přetížení pro vytvoření protokolu SOAP zprávy. Nejvíce basic tyto trvá <xref:System.ServiceModel.Channels.MessageFault> objekt, který popisuje chybu. Pro usnadnění práce najdete dalšími přetíženími. První například přetížení trvá `FaultCode` a řetězec důvod a vytvoří `MessageFault` pomocí `MessageFault.CreateFault` na základě těchto informací. Další přetížení přebírá objekt podrobnosti a také předává jej do `CreateFault` společně s kódem chyby a z důvodu. Například následující operace vrátí chybu.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Extrahování dat tělo zprávy  
 `Message` Třída podporuje více způsobů extrahování informací z jeho textu. Ty můžou být klasifikované do následujících kategorií:  
  
-   Načítání textu celé zprávy najednou zapsané do zapisovače XML. Tento proces se označuje jako *zápis zprávy*.  
  
-   Získávání čtecí modul XML přes text zprávy. Díky tomu můžete zprávu textu část jednotlivé novější přístupu podle potřeby. Tento proces se označuje jako *čtení zprávy*.  
  
-   Celé zprávy, včetně jeho textu je možné zkopírovat do vyrovnávací paměť v paměti z <xref:System.ServiceModel.Channels.MessageBuffer> typu. Tento proces se označuje jako *kopírování zprávu*.  
  
 Dostanete textu `Message` pouze jednou, bez ohledu na to, jak je přístupný. Objekt zpráva má `State` vlastnosti, která je původně nastaven na vytvořit. Tři přístup metod popsaných v předchozím seznamu nastavit stav na Written, čtení a zkopírovaných, v uvedeném pořadí. Kromě toho `Close` metoda můžete nastavit stav na Uzavřeno, když obsah zprávy se už nevyžadují. Tělo zprávy jsou přístupné pouze ve stavu vytvořen a neexistuje žádný způsob, jak vrátit do stavu vytvořeno po změně stavu.  
  
## <a name="writing-messages"></a>Zápis zpráv  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Metoda zapíše obsah textu danou `Message` instance daného zapisovače XML. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Metoda dělá to stejné, s tím rozdílem, že se uzavře obsah textu v příslušné obálku elementu (například <`soap:body`>). Nakonec <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> zápisy celou zprávu, včetně zabalenou SOAP obálky a hlavičky. Pokud je vypnutý protokolu SOAP (verze je `MessageVersion.None`), stejnou věc udělat všechny tři metody: jejich Vypsat obsah textu zprávy.  
  
 Například následující kód zapíše text příchozí zprávy do souboru.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dva další pomocné metody zapsat určité značky elementu spuštění protokolu SOAP. Tyto metody k přístupu ke tělo zprávy a proto mohou změnit stav zprávy. Mezi ně patří:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> zapíše elementu počáteční body, například `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> zapíše počáteční obálky prvek, například `<soap:Envelope>`.  
  
 Zápis odpovídající koncové značky elementu, volání `WriteEndElement` na odpovídající zapisovače XML. Tyto metody jsou zřídka volat přímo.  
  
## <a name="reading-messages"></a>Čtení zpráv  
 Primární způsobem, jak číst text zprávy je volání <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Můžete se vrátit <xref:System.Xml.XmlDictionaryReader> , můžete použít ke čtení textu zprávy. Všimněte si, že <xref:System.ServiceModel.Channels.Message> přechody stavu čtení co nejrychleji <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> je volána, a není při použití vrácený čtecí modul XML.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Metoda také umožňuje přístup k tělo zprávy jako objekt typu. Interně tato metoda používá `GetReaderAtBodyContents`, a proto také přechází zpráva stav, který má <xref:System.ServiceModel.Channels.MessageState.Read> stavu (najdete v článku <xref:System.ServiceModel.Channels.Message.State%2A> vlastnost).  
  
 Je vhodné zkontrolovat <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> vlastnost, ve kterém je případ tělo zprávy prázdný a <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> vyvolá <xref:System.InvalidOperationException>. Navíc pokud je přijaté zprávy (například odpověď), můžete také zkontrolovat <xref:System.ServiceModel.Channels.Message.IsFault%2A>, což naznačuje, zda zpráva obsahuje chybu.  
  
 Nejzákladnější přetížení <xref:System.ServiceModel.Channels.Message.GetBody%2A> deserializuje tělo zprávy do instance typu (označené obecný parametr) pomocí <xref:System.Runtime.Serialization.DataContractSerializer> nakonfigurována s výchozím nastavením a s <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> kvóty zakázány. Pokud chcete používat jiný Serializační stroj, nebo můžete nakonfigurovat `DataContractSerializer` způsobem, jiné než výchozí, použijte <xref:System.ServiceModel.Channels.Message.GetBody%2A> přetížení, které přijímá <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Například následující kód extrahuje data z textu zprávy, která obsahuje serializovaný seznam `Person` objektu a vytiskne na jméno uživatele.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Kopírování zprávu do vyrovnávací paměti  
 Někdy je nezbytné pro přístup k tělo zprávy více než jednou, například, předat dál stejnou zprávu do více cílů v rámci systému vydavatele odběratele. V takovém případě je nutná k uložení celé zprávy (včetně textu) v paměti. To provedete pomocí volání <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Tato metoda přebírá parametr celé číslo, který představuje maximální velikost vyrovnávací paměti a vytvoří není větší než tato velikost vyrovnávací paměti. Je důležité nastavit na hodnotu bezpečné Pokud zpráva pochází z nedůvěryhodného zdroje.  
  
 Vyrovnávací paměť se vrátí jako <xref:System.ServiceModel.Channels.MessageBuffer> instance. Můžete přistupovat k datům ve vyrovnávací paměti několika způsoby. Primární způsob je volání <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> k vytvoření `Message` instancí z vyrovnávací paměti.  
  
 Jiný způsob, jak získat přístup k datům ve vyrovnávací paměti je implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.ServiceModel.Channels.MessageBuffer> třída implementuje pro přístup k podkladové XML přímo. Některé <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> přetížení umožňují vytvářet <xref:System.Xml.XPath> navigátory chráněn uzlu kvótu, omezení počtu uzlů XML, které lze navštívit. To pomáhá zabránit útoku DoS založené na delší dobu zpracování. Tuto nabídku ve výchozím nastavení vypnutá. Některé `CreateNavigator` přetížení umožňují určit způsob zpracování mezer v kódu XML pomocí <xref:System.Xml.XmlSpace> výčet, s právě výchozí `XmlSpace.None`.  
  
 Poslední způsob pro přístup k obsahu zprávy vyrovnávací paměť je zapsat svůj obsah rozbalí do datového proudu pomocí <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 Následující příklad znázorňuje proces práce `MessageBuffer`: příchozí zprávy předával několika příjemcům a poté protokolována do souboru. Bez ukládání do vyrovnávací paměti, to není možné, protože obsah zprávy lze přistupovat pouze jednou.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Třída má ostatní členové vhodné poznamenat. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Metodu lze volat kvůli uvolnění prostředků, pokud vyrovnávací paměti obsah se už nevyžadují. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Vlastnost vrátí velikost přidělené vyrovnávací paměti. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Vlastnost vrátí typ MIME obsahu zprávy.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Přístup k text zprávy pro ladění  
 Pro účely ladění si můžete volat <xref:System.ServiceModel.Channels.Message.ToString%2A> metodu k získání reprezentace zprávy jako řetězec. Tento zápis obecně odpovídá zprávu by vzhled přenášený Pokud byly zakódovaných pomocí kodér textu s tím rozdílem, že by lidského čitelnější lépe formátu XML. Jedinou výjimkou je text zprávy. Text může číst pouze jednou a `ToString` nezmění stav zprávy. Proto `ToString` metoda nemusí být schopni přistupovat text a může nahraďte zástupný symbol (například "..." nebo tři tečky) místo textu zprávy. Proto nepoužívejte `ToString` k protokolování zpráv, pokud je důležité obsah textu zprávy.  
  
## <a name="accessing-other-message-parts"></a>Přístup k další části zprávy  
 Různé vlastnosti jsou k dispozici pro přístup k informacím o zprávě, než jeho obsah textu. Ale tyto nelze volat po uzavření zpráva:  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> Vlastnost představuje záhlaví zprávy. Viz oddíl "Práce s hlavičky" dál v tomto tématu.  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> Vlastnost představuje vlastnosti zprávy, které jsou částí s názvem dat připojeného ke zprávě, která není obecně získat vygenerované při odeslání zprávy. Najdete v části na práci s vlastnosti"dále v tomto tématu.  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> Vlastnost označuje verzi protokolu SOAP a adresování WS spojený se zprávou, nebo `None` Pokud SOAP je zakázána.  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A> Vlastnost vrátí `true` Pokud zpráva je zprávu o chybě protokolu SOAP.  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Vlastnost vrátí `true` Pokud zpráva je prázdná.  
  
 Můžete použít <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> metody přístup konkrétní atribut v prvku body obálku (například `<soap:Body>`) identifikovaný konkrétní názvem a oborem názvů. Pokud není nalezen takový atribut, `null` je vrácen. Tuto metodu lze volat pouze tehdy, když `Message` je ve stavu vytvořen (Pokud je text zprávy nebyl ještě využívány).  
  
## <a name="working-with-headers"></a>Práce s hlavičky  
 A `Message` může obsahovat libovolný počet pojmenované fragmenty XML názvem *hlavičky*. Každý fragment obvykle mapuje hlavičku protokolu SOAP. Hlavičky jsou přístupné prostřednictvím `Headers` vlastnost typu <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> je kolekce <xref:System.ServiceModel.Channels.MessageHeaderInfo> objekty a jednotlivých záhlaví je přístupná přes jeho <xref:System.Collections.IEnumerable> rozhraní nebo pomocí jeho indexer. Například následující kód obsahuje názvy všech záhlaví v `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Přidání, odebrání, hledání hlavičky  
 Můžete přidat nové hlavičku na konci všechny existující hlavičky pomocí <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> metoda. Můžete použít <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> metoda vložte hlavičku na konkrétním indexem. Existující záhlaví posunuty vložené položky. Hlavičky jsou seřazené podle svého indexu a index prvního k dispozici je 0. Můžete použít různé <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> přetížení metody pro přidání hlavičky z jiné `Message` nebo `MessageHeaders` instance. Některé přetížení zkopírovat jeden jednotlivých záhlaví, zatímco ostatní zkopírujte všechny z nich. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Metoda odebere všechny hlavičky. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Metoda odebere hlaviček v konkrétním indexem (s posunem všechny hlavičky po jeho). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Metoda odebere všechny hlavičky s určitým názvem a oborem názvů.  
  
 Načíst konkrétní hlavičky pomocí <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> metoda. Tato metoda přebírá názvem a oborem názvů hlavičky k najít a vrátí její index. Pokud hlavička vyskytuje více než jednou, je vyvolána výjimka. Pokud hlavička nebyla nalezena, vrátí hodnotu -1.  
  
 V modelu hlavičky SOAP, může mít hlavičky `Actor` hodnotu, která určuje zamýšlený příjemce hlavičky. Nejzákladnější `FindHeader` přetížení vyhledá pouze záhlaví určený pro ultimate příjemce zprávy. Ale jiné přetížení umožňuje určit, které `Actor` hodnoty jsou zahrnuty v hledání. Další informace najdete v tématu Specifikace protokolu SOAP.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> metoda zajišťuje zkopírujte hlaviček z <xref:System.ServiceModel.Channels.MessageHeaders> kolekci na pole <xref:System.ServiceModel.Channels.MessageHeaderInfo> objekty.  
  
 Přístup k datům XML v hlavičce můžete volat <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> a vrátit čtečky XML pro konkrétní hlavičky index. Pokud chcete k deserializaci obsahu hlavičky do objektu, použijte <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> nebo jeden z dalšími přetíženími. Nejzákladnější přetížení deserializovat hlavičky pomocí <xref:System.Runtime.Serialization.DataContractSerializer> nakonfigurované ve výchozím způsobem. Pokud chcete použít jiný serializátor nebo jiné konfigurace systému `DataContractSerializer`, použijte jednu z přetížení, které provést `XmlObjectSerializer`. Existují také přetížení, které provést název hlavičky, obor názvů a volitelně seznam `Actor` hodnoty místo index; to je kombinací `FindHeader` a `GetHeader`.  
  
## <a name="working-with-properties"></a>Práce s vlastnostmi  
 A `Message` instance může obsahovat libovolný počet pojmenovaných objektů náhodné typy. Tato kolekce je přístupné přes `Properties` vlastnost typu `MessageProperties`. Implementuje kolekce <xref:System.Collections.Generic.IDictionary%602> rozhraní a funguje jako mapování z <xref:System.String> k <xref:System.Object>. Za normálních okolností se nemapují přímo na jakékoliv části zprávy v drátové síti hodnoty vlastností, ale spíš poskytují různé zprávy zpracování pomocné parametry různé kanály v zásobníku kanálu WCF nebo na <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> architektura služby. Příklad, naleznete v části [architektury Přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Která dědí z třídy Message  
 Pokud integrované zpráv typy vytvořené pomocí `CreateMessage` není vyhovovalo vašim požadavkům, vytvořte třídu, která je odvozena z `Message` třídy.  
  
### <a name="defining-the-message-body-contents"></a>Definování obsah zprávy  
 Existují tři primární techniky pro přístup k datům v rámci tělo zprávy: zápis, čtení a kopírování do vyrovnávací paměti. Tyto operace konečným výsledkem <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, a <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody volané, v uvedeném pořadí, v odvozené třídě z `Message`. Základní `Message` třída zaručuje, že pouze jeden z těchto metod je volána pro každou `Message` instance, a že není volaná víc než jednou. Základní třídy taky zajišťuje, že metody nejsou zavolána pro zprávu uzavřené. Není nutné sledovat stav zpráv v implementaci.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> je abstraktní metodu a musí být implementována. Zápis pomocí této metody je nejzákladnější způsob, jak definovat obsah textu zprávy. Například následující zpráva obsahuje 100 000 náhodných čísel od 1 až 20 číslic.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 `OnGetReaderAtBodyContents` a `OnCreateBufferedCopy` mají výchozí implementaci, která pracují pro většině případů. Výchozí implementace volání `OnWriteBodyContents`, výsledky ukládat do vyrovnávací paměti a pracovat s výsledné vyrovnávací paměti. Ale v některých případech to nemusí stačit. V předchozím příkladu čtení zpráv výsledky v 100 000 elementů XML se uloží do vyrovnávací paměti, které nemusí být žádoucí. Chcete přepsat `OnGetReaderAtBodyContents` vrátit vlastní `XmlDictionaryReader` odvozené třídy, která slouží až náhodných čísel. Potom můžete přepsat `OnWriteBodyContents` použít program pro čtení, `OnGetReaderAtBodyContents` vlastnost vrátí, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Podobně můžete chtít přepsat `OnCreateBufferedCopy` vrátit vlastní `MessageBuffer` odvozené třídy.  
  
 Kromě obsah textu zprávy, musí vaše zpráva odvozené třídy také přepsat `Version`, `Headers`, a `Properties` vlastnosti.  
  
 Všimněte si, že pokud vytvoříte kopii zprávy, kopie používá záhlaví zprávy z původní.  
  
### <a name="other-members-that-can-be-overridden"></a>Jiní členové, které je možné přepsat  
 Je možné přepsat <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, a <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> metody k určení, jak obálky protokolu SOAP, hlavičky SOAP a SOAP body element počáteční značky se zapisují. To obvykle odpovídají `<soap:Envelope>`, `<soap:Header>`, a `<soap:Body>`. Tyto metody by měl obvykle není nic se v případě zápisu `Version` vlastnost vrátí `MessageVersion.None`.  
  
> [!NOTE]
>  Výchozí implementaci `OnGetReaderAtBodyContents` volání `OnWriteStartEnvelope` a `OnWriteStartBody` před voláním `OnWriteBodyContents` a ukládání do vyrovnávací paměti výsledky. Hlavičky nejsou zapsána.  
  
 Přepsání <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> metoda změnit způsob celé zprávy je vytvořený z jeho různých místech. `OnWriteMessage` Metoda je volána z <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> a z výchozího <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementace. Všimněte si, že přepsání <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> se neshoduje osvědčenými postupy. Je lepší pro přepsání odpovídající `On` metody (například <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, a <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Přepsání <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> přepsat, jak vaše text zprávy je reprezentována během ladění. Ve výchozím nastavení se představují ho jako tři tečky ("..."). Všimněte si, že tuto metodu lze volat vícekrát Pokud zpráva stav jakoukoli jinou hodnotu než uzavřeno. Implementace této metody by nikdy způsobit žádnou akci, kterou je nutné provést pouze jednou (např. čtení z datového proudu dopředné).  
  
 Přepsání <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> metoda pro povolení přístupu k atributy elementu těla protokolu SOAP. Tuto metodu lze volat libovolný počet dobu, ale `Message` základní typ zaručuje, že je pouze volána při zprávy je ve stavu vytvořen. Není potřeba pro kontrolu stavu v implementaci. Výchozí implementace vždy vrátí `null`, což naznačuje, že neexistují žádné atributy v textu elementu.  
  
 Pokud vaše `Message` objekt nutné provést jakékoli speciální čištění, když obsah zprávy se už nevyžaduje, můžete přepsat <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Výchozí implementace neprovede žádnou akci.  
  
 `IsEmpty` a `IsFault` vlastnosti je možné přepsat. Ve výchozím nastavení, jak vrátit `false`.
