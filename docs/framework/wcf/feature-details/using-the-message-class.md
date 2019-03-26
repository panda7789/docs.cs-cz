---
title: Používání třídy Message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: d9b1c1242fe2686a66e41b777f904a71898159ea
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409598"
---
# <a name="using-the-message-class"></a>Používání třídy Message
<xref:System.ServiceModel.Channels.Message> Třída je základní na Windows Communication Foundation (WCF). Veškerá komunikace mezi klienty a služby, přílišnou <xref:System.ServiceModel.Channels.Message> instancí se odeslané a přijaté.  
  
 By obvykle interakci s <xref:System.ServiceModel.Channels.Message> třídy přímo. Místo toho WCF service model konstruktorů, jako jsou kontrakty dat, kontrakty zpráv a operace smlouvy, se používají k popisu příchozí a odchozí zprávy. Nicméně některé pokročilé scénáře, které můžete naprogramovat pomocí <xref:System.ServiceModel.Channels.Message> třídy přímo. Například můžete chtít použít <xref:System.ServiceModel.Channels.Message> třídy:  
  
-   Pokud potřebujete alternativní způsob vytváření obsah odchozí zprávy (například vytváření zprávy přímo ze souboru na disku) namísto serializace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty.  
  
-   Pokud potřebujete alternativní způsob použití obsahu příchozí zprávy (třeba když chcete použití transformace XSLT nezpracovaný obsah XML) namísto deserializaci do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty.  
  
-   Pokud potřebujete řešit zprávy obecným způsobem bez ohledu na obsah zprávy (třeba když směrovat nebo předávat zprávy při sestavování směrovač, nástroje pro vyrovnávání zatížení nebo publikování-odběru systému).  
  
 Před použitím <xref:System.ServiceModel.Channels.Message> třídy, seznamte se s architekturou přenos WCF data v [strukturální Přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 A <xref:System.ServiceModel.Channels.Message> je kontejner pro obecné účely pro data, ale jeho návrhu přesně dodržuje návrhu zprávy v protokolu SOAP. Stejně jako v protokolu SOAP, zpráva obsahuje text zprávy a záhlaví. Tělo zprávy obsahuje skutečné datová část dat, zatímco hlavičky obsahovat další pojmenované datové kontejnery. Pravidla pro čtení a zápis záhlaví a text se liší, například záhlaví, vždy jsou ukládány do vyrovnávací paměti v paměti a lze získat přístup v žádné pořadí libovolný počet pokusů, zatímco subjekt může načíst jenom jednou a může Streamovat. Za normálních okolností při použití protokolu SOAP, text zprávy je namapovaná na těle SOAP a záhlaví zpráv jsou mapovány na záhlaví SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Používání třídy Message v operacích  
 Můžete použít <xref:System.ServiceModel.Channels.Message> třídy jako vstupní parametr operace, návratový typ operace, nebo obojí. Pokud <xref:System.ServiceModel.Channels.Message> je použít kdekoli v operaci, platí následující omezení:  
  
-   Operace nesmí obsahovat žádné `out` nebo `ref` parametry.  
  
-   Nemůže existovat více než jeden `input` parametru. Pokud je přítomen parametr, musí být typ kontraktu zprávy nebo zprávy.  
  
-   Návratový typ musí být buď `void`, `Message`, nebo typ kontraktu zprávy.  
  
 Následující příklad obsahuje kontrakt platná operace.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Vytváření základních zprávy  
 <xref:System.ServiceModel.Channels.Message> Třída poskytuje statické `CreateMessage` metody pro vytváření objektů, které můžete použít k vytvoření základní zpráv.  
  
 Všechny `CreateMessage` přetížení může verze parametr typu <xref:System.ServiceModel.Channels.MessageVersion> , která indikuje, verze protokolu SOAP a WS-Addressing pro zprávy. Pokud chcete použít stejné verze protokolu jako příchozí zprávy, můžete použít <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> vlastnost <xref:System.ServiceModel.OperationContext> instance získaných <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost. Většina `CreateMessage` přetížení také mít parametr řetězec, který označuje akce SOAP pro zprávy. Může být verze nastavená `None` zakázat generování obálky protokolu SOAP; zpráva se skládá pouze text.  
  
## <a name="creating-messages-from-objects"></a>Vytváření zprávy z objektů  
 Nejzákladnější `CreateMessage` přetížení, které přijímá pouze verze a akcí, která vytvoří zprávu s prázdným textem zprávy. Další přetížení má další <xref:System.Object> parametr; tím se vytvoří zprávu, jejichž text je serializovaná reprezentace daného objektu. Použití <xref:System.Runtime.Serialization.DataContractSerializer> s výchozím nastavením pro serializaci. Pokud chcete použít jiný serializátor, nebo chcete, aby `DataContractSerializer` nakonfigurován odlišně, použijte `CreateMessage` přetížení, které přijímá také `XmlObjectSerializer` parametr.  
  
 Například k vrácení objektu ve zprávě, můžete použít následující kód.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Vytváření zprávy z čtečky XML  
 Existují `CreateMessage` přetížení trvají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> těla místo objektu. V takovém případě tělo zprávy obsahuje kód XML, který je výsledkem čtení z předané čtecí funkce XML. Například následující kód vrátí zprávu s tělem obsah čtení ze souboru XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Kromě toho existují `CreateMessage` přetížení trvají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlDictionaryReader> , která představuje celé zprávy a ne jenom text. Tato přetížení také trvat celé `maxSizeOfHeaders` parametru. Hlavičky jsou vždy ukládány do vyrovnávací paměti do paměti co nejdříve, vytvoření zprávy, a tento parametr omezuje objem ukládání do vyrovnávací paměti, které u něho. Je důležité v případě XML pochází z nedůvěryhodného zdroje pro omezení možností útoku DoS nastavte tento parametr na hodnotu bezpečné. Verze protokolu SOAP a WS-Adressing zprávy, kterou představuje čtecí funkce XML musí odpovídat verze uvedené, pomocí parametru verze.  
  
## <a name="creating-messages-with-bodywriter"></a>Vytváření zprávy s BodyWriter  
 Jeden `CreateMessage` přetížení přijímá `BodyWriter` instance pro popis textu zprávy. A `BodyWriter` je abstraktní třída, která mohou být odvozeny přizpůsobení způsobu vytváření zpráv. Můžete vytvořit svoje vlastní `BodyWriter` odvozené třídy k popisu zpráv vlastním způsobem. Je nutné přepsat `BodyWriter.OnWriteBodyContents` metodu, která přebírá <xref:System.Xml.XmlDictionaryWriter>; tato metoda je zodpovědná za zápis textu.  
  
 Zapisovače textu může být ukládány do vyrovnávací paměti nebo bez vyrovnávací paměti (prostřednictvím datového proudu). Zapisovače textu ve vyrovnávací paměti můžete vypsat jejich obsah libovolný počet pokusů, zatímco streamovaná ty můžete vypsat jejich obsah pouze jednou. `IsBuffered` Vlastnost určuje, zda je zapisovač textu do vyrovnávací paměti nebo ne. Tento parametr můžete nastavit pro váš modul pro zápis voláním chráněné `BodyWriter` konstruktor, který přebírá `isBuffered` parametr logické hodnoty. Zapisovače textu podporují vytváření zapisovače textu ve vyrovnávací paměti z zapisovač bez vyrovnávací paměti textu. Je možné přepsat `OnCreateBufferedCopy` metodu za účelem přizpůsobení tento proces. Ve výchozím nastavení, vyrovnávacích pamětí, která obsahuje kód XML vrácený `OnWriteBodyContents` se používá. `OnCreateBufferedCopy` přijímá `maxBufferSize` parametru celé číslo; Pokud tuto metodu přepíšete, není možné vytvořit vyrovnávací paměti větší než maximální velikost.  
  
 `BodyWriter` Třída poskytuje `WriteBodyContents` a `CreateBufferedCopy` metody, které jsou v podstatě dynamicky obálky `OnWriteBodyContents` a `OnCreateBufferedCopy` metody, v uvedeném pořadí. Tyto metody provádět kontroly stavu kvůli zapisovače textu bez vyrovnávací paměti není více než jednou. Tyto metody jsou volány pouze při vytváření vlastní `Message` odvozené třídy na základě `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Vytváří se chybové zprávy  
 Můžete použít některé `CreateMessage` selhání přetížení k vytvoření protokolu SOAP zprávy. Nejvíce basic tyto přebírá <xref:System.ServiceModel.Channels.MessageFault> objekt popisující chybu. Další přetížení jsou k dispozici ke zvýšení pohodlí. První přetížení tyto přebírá `FaultCode` a řetězec důvod a vytvoří `MessageFault` pomocí `MessageFault.CreateFault` pomocí těchto informací. Další přetížení přebírá objekt podrobností a také předá ho do `CreateFault` společně s kód chyby a důvod. Například následující operace vrátí chybu.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Extrahování dat těla zprávy  
 `Message` Třídy podporuje více způsobů extrahování informací z jeho textu. Ty je možné rozdělit do těchto kategorií:  
  
-   Získávání těla celá zpráva zapsat najednou do zapisovače XML. To se označuje jako *zápisu zprávy*.  
  
-   Získání čtecí funkce XML v textu zprávy. To vám umožní pro pozdější přístup zprávu textu část jednotlivé podle potřeby. To se označuje jako *čtení zprávy*.  
  
-   Celá zpráva, včetně jeho obsah, je možné zkopírovat do vyrovnávacích pamětí o <xref:System.ServiceModel.Channels.MessageBuffer> typu. To se označuje jako *kopírování zprávu*.  
  
 Můžete přístup k textu `Message` jenom jednou, bez ohledu na to, jak je přístupný. Objekt zprávy má `State` vlastnost, která je zpočátku nastaven na vytvořit. Tři přístupové metody popsané v předchozím seznamu nastavit stav na Written, čtení a zkopírovaných, v uvedeném pořadí. Kromě toho `Close` metoda můžete nastavit stav na Uzavřeno, když obsah zprávy se už nevyžadují. Text zprávy je přístupná pouze ve stavu vytvořen. proto neexistuje žádný způsob, jak přejít zpět do stavu vytvořeno po změně stavu.  
  
## <a name="writing-messages"></a>Zápis zpráv  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Metoda zapíše obsah textu daný `Message` instance daného zapisovače XML. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Metoda dělá to samé, s tím rozdílem, že ho obklopuje obsah textu v elementu příslušné obálky (například <`soap:body`>). Nakonec <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> zápisy celou zprávu, včetně zabalenou SOAP obálky a hlavičky. Pokud je vypnutý SOAP (<xref:System.ServiceModel.Channels.Message.Version> je <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>), to samé udělejte všechny tři metody:, Vypsat obsah zprávy.  
  
 Například následující kód zapíše text příchozí zprávy do souboru.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dva další pomocné metody zapsat určitým SOAP počáteční element značky. Tyto metody nemají přístup k textu zprávy, a proto nemění stav zprávy. Zde jsou některé z nich:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> zapíše element počáteční body, například `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> zapíše počáteční element obálky, například `<soap:Envelope>`.  
  
 Chcete-li zapsat odpovídající konci značky elementu, zavolejte `WriteEndElement` odpovídající zapisovače XML. Tyto metody jsou zřídka volat přímo.  
  
## <a name="reading-messages"></a>Čtení zpráv  
 Primární způsob, jak načíst tělo zprávy je volání <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Můžete se vrátit <xref:System.Xml.XmlDictionaryReader> , můžete použít ke čtení textu zprávy. Všimněte si, že <xref:System.ServiceModel.Channels.Message> přechází do stavu čtení co nejdříve <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> je volána, a ne při použití vráceného čtecí funkce XML.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Metoda také umožňuje získat přístup k textu zprávy jako zadaný objekt. Interně tato metoda používá `GetReaderAtBodyContents`, a proto také změní stav zprávy, který má <xref:System.ServiceModel.Channels.MessageState.Read> stavu (naleznete v tématu <xref:System.ServiceModel.Channels.Message.State%2A> vlastnost).  
  
 Je dobrým zvykem zkontrolovat <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> vlastnosti, ve kterém je prázdný případ text zprávy a <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> vyvolá <xref:System.InvalidOperationException>. Navíc pokud přijaté zprávy (třeba odpověď), můžete také zkontrolovat <xref:System.ServiceModel.Channels.Message.IsFault%2A>, která určuje, jestli zpráva obsahuje chybu.  
  
 Nejzákladnější přetížení <xref:System.ServiceModel.Channels.Message.GetBody%2A> deserializuje tělo zprávy do instance typu (označená obecný parametr) pomocí <xref:System.Runtime.Serialization.DataContractSerializer> nakonfigurovaný s výchozím nastavením a <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> kvóty zakázány. Pokud chcete používat různé Serializační stroj, nebo můžete nakonfigurovat `DataContractSerializer` způsobem, jiné než výchozí, použijte <xref:System.ServiceModel.Channels.Message.GetBody%2A> přetížení přebírající <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Například následující kód extrahuje data ze zprávy, obsahující serializovaný seznam `Person` objektu a vytiskne na jméno uživatele.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Kopírování zprávu do vyrovnávací paměti  
 Někdy je nezbytné pro přístup k textu zprávy více než jednou, například, přeposílat stejné zprávy do více cílů jako součást systému vydavatele odběratele. V takovém případě je nutná k uložení celé zprávy (včetně textu) v paměti. Toto lze provést zavoláním <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Tato metoda přijímá parametr celé číslo, které představuje maximální vyrovnávací paměť a vytvoří vyrovnávací paměť není větší než tato velikost. Je důležité, abyste tuto možnost nastavte na hodnotu bezpečné zpráva pochází z nedůvěryhodného zdroje.  
  
 Vyrovnávací paměť se vrátí jako <xref:System.ServiceModel.Channels.MessageBuffer> instance. Můžou k datům ve vyrovnávací paměti několika způsoby. Hlavní způsob, jak se má volat <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> vytvořit `Message` instancí z vyrovnávací paměti.  
  
 Dalším způsobem, jak získat přístup k datům ve vyrovnávací paměti je pro implementaci <xref:System.Xml.XPath.IXPathNavigable> rozhraní, která <xref:System.ServiceModel.Channels.MessageBuffer> třída implementuje přímý přístup k podkladové XML. Některé <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> přetížení umožňují vytvářet <xref:System.Xml.XPath> navigátory chráněn kvótu uzlu, omezením počtu uzlů XML, které mohou být zobrazeny. To pomáhá zabránit odmítnutí útoků služby založené na delší dobu zpracování. Tato nabídka je ve výchozím nastavení zakázána. Některé `CreateNavigator` přetížení umožňují určit způsob zpracování prázdné znaky v souboru XML pomocí <xref:System.Xml.XmlSpace> výčet s výchozím nastavení se `XmlSpace.None`.  
  
 Poslední způsob, jak přistupovat k obsahu vyrovnávací paměť zpráv je vypsat svůj obsah rozbalí do datového proudu pomocí <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 Následující příklad znázorňuje proces práci s `MessageBuffer`: příchozí zprávy je předán více příjemců a potom zaznamenán do souboru. Bez ukládání do vyrovnávací paměti, to není možné, protože text zprávy lze přistupovat pouze jednou.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Třída má jiné členy za zmínku. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Metodu můžete volat k uvolnění prostředků, pokud obsah vyrovnávací paměti se už nevyžadují. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Vlastnost vrátí velikost přidělené vyrovnávací paměti. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Vlastnost vrátí typ MIME obsahu zprávy.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Přístup k textu zprávy pro ladění  
 Pro účely ladění, můžete volat <xref:System.ServiceModel.Channels.Message.ToString%2A> metodu k získání reprezentaci zprávy jako řetězec. Tento zápis obecně odpovídá způsob, jakým zprávu by vypadalo na lince nebyly zakódovány kodér textu s tím rozdílem, že by pro lepší čitelnost lidské lépe formátu XML. Jedinou výjimkou je text zprávy. Text lze číst pouze jednou, a `ToString` nezmění stav zprávy. Proto `ToString` metody nemusí být možné přístup k textu a mohou nahradit zástupný text (například "..." nebo tři tečky) namísto textu zprávy. Proto nepoužívejte `ToString` k protokolování zpráv, pokud je důležité obsah textu zprávy.  
  
## <a name="accessing-other-message-parts"></a>Přístup k další části zprávy  
 Různé vlastnosti jsou k dispozici přístup k informacím o zprávě než jeho obsah. Ale tyto nelze volat, poté, co je zpráva byla zavřena.:  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> Vlastnost představuje záhlaví zpráv. Viz oddíl "Práce s záhlaví" dále v tomto tématu.  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> Vlastnost představuje vlastnosti zprávy, které jsou pojmenované dat připojen ke zprávě, která není obecně získat, protože ho při odeslání zprávy. V části "Práce s vlastností" dále v tomto tématu.  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> Vlastnost označuje verzi protokolu SOAP a WS-Addressing spojený se zprávou, nebo `None` Pokud SOAP je zakázaná.  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A> Vrátí vlastnost `true` Pokud zpráva je zprávou chybu protokolu SOAP.  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Vrátí vlastnost `true` Pokud zpráva je prázdná.  
  
 Můžete použít <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> metody přístup konkrétní atribut na element obálky textu (například `<soap:Body>`) identifikovat podle konkrétního názvu a oboru názvů. Pokud není nalezen takový atribut, `null` je vrácena. Tuto metodu lze volat pouze tehdy, když `Message` je ve stavu Created (text zprávy ještě nepřistupovalo).  
  
## <a name="working-with-headers"></a>Práce s záhlaví  
 A `Message` může obsahovat libovolný počet pojmenovaných fragmenty XML, volá *záhlaví*. Každý fragment obvykle mapuje na záhlaví SOAP. Hlavičky jsou přístupné prostřednictvím `Headers` vlastnost typu <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> je kolekce <xref:System.ServiceModel.Channels.MessageHeaderInfo> objekty a jednotlivé hlavičky budou přístupné prostřednictvím jeho <xref:System.Collections.IEnumerable> rozhraní nebo přes její indexer. Například následující kód uvádí všechny hlavičky v `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Přidání, odebrání, jak najít záhlaví  
 Můžete přidat nové záhlaví na konci všechny existující záhlaví pomocí <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> metody. Můžete použít <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> metoda Vložit hlavičku na konkrétním indexem. Existující záhlaví posunuty pro vložená položka. Hlavičky jsou řazeny podle jejich rejstřík a první dostupná index je 0. Můžete použít různé <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> přetížení metody pro přidání hlavičky z jiného `Message` nebo `MessageHeaders` instance. Některá přetížení zkopírujte jeden jednotlivé hlavičky, zatímco ostatní zkopírujte všechny z nich. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Metoda odstraní všechny hlavičky. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Metoda odebere záhlaví na konkrétním indexem (posunutí všechny hlavičky za něj). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Metoda odstraní všechny hlavičky s určitým názvem a oborem názvů.  
  
 Načíst konkrétní záhlaví pomocí <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> metody. Tato metoda přebírá název a obor názvů záhlaví najít a vrátí jeho index. Pokud záhlaví vyskytuje více než jednou, je vyvolána výjimka. Pokud hlavička nebyla nalezena, vrátí hodnotu -1.  
  
 V modelu záhlaví SOAP, záhlaví mohou obsahovat `Actor` hodnotu, která určuje, že zamýšlený příjemce hlavičky. Nejzákladnější `FindHeader` přetížení vyhledá pouze záhlaví určená pro ultimate příjemce zprávy. Ale jiné přetížení umožňuje určit, které `Actor` hodnoty jsou zahrnuty do hledání. Další informace naleznete ve specifikaci protokolu SOAP.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> metoda je k dispozici ke zkopírování záhlaví z <xref:System.ServiceModel.Channels.MessageHeaders> kolekce do pole <xref:System.ServiceModel.Channels.MessageHeaderInfo> objekty.  
  
 Pro přístup k datům XML v záhlaví, můžete volat <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> a vraťte se čtecí funkce XML pro konkrétní hlavičky index. Pokud chcete obsah těchto hlaviček deserializují na objekt, použijte <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> nebo mezi dalšími přetíženími. Většina základních přetížení deserializaci záhlaví pomocí <xref:System.Runtime.Serialization.DataContractSerializer> nakonfigurované ve výchozím způsobem. Pokud chcete použít jiný serializátor nebo jinou konfiguraci `DataContractSerializer`, použijte jednu z přetížení, která přijímají `XmlObjectSerializer`. Existují také přetížení, která přijímá název hlavičky, obor názvů a volitelně seznam `Actor` hodnoty místo indexu; to je kombinací `FindHeader` a `GetHeader`.  
  
## <a name="working-with-properties"></a>Práce s vlastnostmi  
 A `Message` instance může obsahovat libovolný počet pojmenovaných objektů libovolných typů. Tato kolekce je přístupný prostřednictvím `Properties` vlastnost typu `MessageProperties`. Implementuje kolekci <xref:System.Collections.Generic.IDictionary%602> rozhraní a funguje jako mapování z <xref:System.String> k <xref:System.Object>. Za normálních okolností nemapovaly přímo do libovolné části zpráv na lince hodnoty vlastností, ale místo toho poskytují různé zprávy pomocné parametry zpracování do různých kanálů v zásobníku kanál WCF nebo na <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> architektura služby. Příklad najdete v tématu [strukturální Přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Dědění z tříd zpráv  
 Pokud předdefinované typy vytvořené pomocí zpráv `CreateMessage` není splňují vaše požadavky, vytvořte třídu, která je odvozena z `Message` třídy.  
  
### <a name="defining-the-message-body-contents"></a>Definování obsah zprávy  
 Existují tři primární techniky pro přístup k datům v rámci tělo zprávy: vytváření, čtení a kopírování do vyrovnávací paměti. Tyto operace nakonec vést <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, a <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody volaného, respektive, na vaší odvozené třídy z `Message`. Základní `Message` třídy zaručuje, že pouze jednu z těchto metod je volána pro každý `Message` instance a že není volána více než jednou. Základní třída také zajišťuje, že nejsou volány metody uzavřené zprávy. Není nutné ke sledování stavu zprávy ve vaší implementaci.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> je abstraktní metoda a musí být implementován. Základní způsob, jak definovat obsah těla zprávy je zapsat pomocí této metody. Například následující zpráva obsahuje 100 000 náhodných čísel od 1 do 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> a <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> metody mají výchozí implementace, které fungují pro většinu případů. Výchozí implementace volání <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, výsledky ve vyrovnávací paměti a pracovat s výsledný vyrovnávací paměti. Nicméně v některých případech to nemusí stačit. V předchozím příkladu čtení výsledků zpráva prvků 100 000 XML jsou ukládány do vyrovnávací paměti, které nemusí být žádoucí. Můžete chtít přepsat <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> vrátit vlastní <xref:System.Xml.XmlDictionaryReader> odvozenou třídu, která obsluhuje náhodných čísel. Pak můžete přepsat <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> používat čtecí modul, který <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> metoda vrací výsledek, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Podobně můžete chtít přepsat `OnCreateBufferedCopy` vrátit vlastní `MessageBuffer` odvozené třídy.  
  
 Kromě toho, že obsah zprávy, musí také přepsat vaší zprávy odvozené třídy `Version`, `Headers`, a `Properties` vlastnosti.  
  
 Všimněte si, že pokud vytvoříte kopii zprávy, kopie používá záhlaví zpráv od původního.  
  
### <a name="other-members-that-can-be-overridden"></a>Ostatní členy, které mohou být přepsána nastaveními  
 Je možné přepsat <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, a <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> jsou zapsané metody k určení, jak začít obálku protokolu SOAP, hlavičky SOAP a SOAP textu elementu značky. Obvykle odpovídají `<soap:Envelope>`, `<soap:Header>`, a `<soap:Body>`. Tyto metody by měl obvykle zapsat cokoli, co si <xref:System.ServiceModel.Channels.Message.Version> vrátí vlastnost <xref:System.ServiceModel.Channels.MessageVersion.None>.  
  
> [!NOTE]
>  Výchozí implementace `OnGetReaderAtBodyContents` volání `OnWriteStartEnvelope` a `OnWriteStartBody` před voláním `OnWriteBodyContents` a ukládání do vyrovnávací paměti výsledky. Záhlaví není zapsán.  
  
 Přepsat <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> metodu, která změní způsob, jakým je vytvořena celá zpráva z jeho různých součástí. `OnWriteMessage` Metoda je volána z <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> a z výchozího <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementace. Všimněte si, že přepsání <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> se nejedná osvědčený postup. Je lepší k přepsání odpovídající `On` metod (například <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, a <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Přepsat <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> přepsání, jak je vaše zprávy reprezentovaná během ladění. Ve výchozím nastavení je reprezentovat ho jako tři tečky ("..."). Všimněte si, že tuto metodu lze volat více než jednou při stavu zprávy se nic jiného než uzavřeno. Implementace této metody by nikdy nezpůsobí žádnou akci, kterou je nutné provést pouze jednou (např. čtení z datového proudu dopředné).  
  
 Přepsat <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> metoda umožňující přístup k atributům u elementu těla protokolu SOAP. Tuto metodu lze volat libovolný počet pokusů, ale `Message` základního typu zaručuje, že ho se jen volá, když zpráva je ve stavu vytvořen. Postup kontroly stavu v implementaci není potřeba. Výchozí implementace vždy vrátí `null`, což znamená, že neexistují žádné atributy v elementu tělo.  
  
 Pokud vaše `Message` objektu musí do zvláštního vyčištění, když obsah zprávy se už nevyžaduje, můžete přepsat <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Výchozí implementace nemá žádný účinek.  
  
 `IsEmpty` a `IsFault` lze vlastnosti přepsat. Ve výchozím nastavení, oba vracejí `false`.
