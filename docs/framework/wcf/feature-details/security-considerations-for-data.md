---
title: Důležité informace o zabezpečení pro data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 8cb7ee2ea2418602d944c3c08cec2b9279dca3b9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601059"
---
# <a name="security-considerations-for-data"></a>Důležité informace o zabezpečení pro data

Při práci s daty v Windows Communication Foundation (WCF) musíte vzít v úvahu několik kategorií hrozeb. V následující tabulce jsou uvedeny nejdůležitější třídy hrozeb, které se vztahují ke zpracování dat. WCF nabízí nástroje, které tyto hrozby zmírnit.

Při odepření nedůvěryhodných dat může tato data způsobit, že přijímající strana získá přístup k neúměrnému množství různých prostředků, jako jsou paměť, vlákna, dostupná připojení nebo cykly procesoru, a to díky zdlouhavým výpočtům. Útok DOS na server může způsobit jeho chybu a nebude moct zpracovávat zprávy z jiných, legitimních klientů.

Škodlivá nedůvěryhodná data při spuštění kódu způsobí, že přijímající strana spustí kód, který nezamýšlel.

Zpřístupnění informací vzdálenému útočníkovi přinutí přijímající straně reagovat na své žádosti tak, aby bylo možné zveřejnit více informací, než je v úmyslu.

## <a name="user-provided-code-and-code-access-security"></a>Uživatelem poskytnutý kód a zabezpečení přístupu kódu

Počet míst v infrastruktuře Windows Communication Foundation (WCF), které poskytuje uživatel. Například <xref:System.Runtime.Serialization.DataContractSerializer> modul serializace může volat `set` přistupující objekty vlastnosti a `get` přistupující objekty. Infrastruktura kanálu WCF může také volat do uživatelem odvozených tříd <xref:System.ServiceModel.Channels.Message> třídy.

Je zodpovědný za autora kódu, aby se zajistilo, že neexistují žádné chyby zabezpečení. Například pokud vytvoříte typ kontraktu dat s vlastností datového člena typu celé číslo a v `set` implementaci přistupující objekt přidělíte pole na základě hodnoty vlastnosti, vystavíte možnost útoku DOS, pokud škodlivá zpráva obsahuje extrémně velkou hodnotu pro tento datový člen. Obecně se vyhněte jakémukoli přidělení na základě příchozích dat nebo zdlouhavého zpracování v uživatelsky poskytnutém kódu (zejména v případě, že může být zdlouhavé zpracování způsobeno malým množstvím příchozích dat). Při provádění analýzy zabezpečení uživatelsky zadaného kódu nezapomeňte také vzít v úvahu všechny případy selhání (tj. všechny větve kódu, kde jsou výjimky vyvolány).

Konečný příklad uživatelsky zadaného kódu je kód uvnitř implementace služby pro každou operaci. Zabezpečení vaší implementace služby je vaše zodpovědnost. Nechtěně Vytvářejte nezabezpečené implementace operací, které mohou vést k ohrožení zabezpečení při odepření služby. Například operace, která přebírá řetězec a vrátí seznam zákazníků z databáze, jejíž název začíná řetězcem. Pokud pracujete s velkou databází a předávaný řetězec je pouze jedno písmeno, váš kód se může pokusit vytvořit zprávu větší než veškerá dostupná paměť, což způsobí selhání celé služby. ( <xref:System.OutOfMemoryException> Nelze obnovit .NET Framework a vždy má za následek ukončení aplikace.)

Měli byste zajistit, aby žádný škodlivý kód nebyl připojen do různých bodů rozšiřitelnosti. To je obzvláště důležité při spuštění v částečném vztahu důvěryhodnosti, v souvislosti s typy z částečně důvěryhodných sestavení nebo při vytváření komponent použitelných částečně důvěryhodným kódem. Další informace najdete v části "hrozby s částečným vztahem důvěryhodnosti" v pozdější části.

Všimněte si, že při spuštění v částečném vztahu důvěryhodnosti podporuje infrastruktura serializace kontraktů dat pouze omezené podmnožiny programovacího modelu kontraktu dat, například soukromé datové členy nebo typy s použitím <xref:System.SerializableAttribute> atributu nejsou podporovány. Další informace najdete v tématu [částečná důvěryhodnost](partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Zamezení neúmyslnému zpřístupnění informací

Při navrhování serializovatelných typů s ohledem na zabezpečení je možné se vyzrazení informací.

Vezměte v úvahu následující body:

- <xref:System.Runtime.Serialization.DataContractSerializer>Programovací model umožňuje vystavení privátních a interních dat mimo typ nebo sestavení během serializace. Kromě toho může být tvar typu vystaven během exportu schématu. Nezapomeňte pochopit projekci serializace typu. Pokud nechcete, aby bylo cokoli vystaveno, zakažte jeho serializaci (například nepoužití <xref:System.Runtime.Serialization.DataMemberAttribute> atributu v případě kontraktu dat).

- Počítejte s tím, že stejný typ může mít více projekcí serializace v závislosti na používaném serializátoru. Stejný typ může vystavit jednu sadu dat při použití s <xref:System.Runtime.Serialization.DataContractSerializer> a jinou sadou dat při použití s <xref:System.Xml.Serialization.XmlSerializer> . Omylem s použitím špatného serializátoru může vést k odhalení informací.

- Použití <xref:System.Xml.Serialization.XmlSerializer> ve starším režimu vzdáleného volání procedur (RPC)/Encoded může neúmyslně zveřejnit tvar grafu objektů na straně odeslání na straně příjmu.

## <a name="preventing-denial-of-service-attacks"></a>Zabránění útokům DOS (Denial-of-Service)

### <a name="quotas"></a>Kvóty

Způsob, jakým přijímající strana přidělí značnou velikost paměti, je potenciální útok na útok DoS (Denial-of-Service). I když se tato část soustředí na problémy s spotřebou paměti vznikající z velkých zpráv, může dojít k dalším útokům. Zprávy mohou například používat neúměrné množství času zpracování.

Útoky DoS (Denial-of-Service) jsou obvykle zmírňované pomocí kvót. Při překročení kvóty <xref:System.ServiceModel.QuotaExceededException> je obvykle vyvolána výjimka. Bez této kvóty může škodlivá zpráva způsobit přístup k veškeré dostupné paměti, výsledkem je <xref:System.OutOfMemoryException> výjimka nebo všechny dostupné zásobníky, které mají za následek přístup <xref:System.StackOverflowException> .

Scénář překročení kvóty je obnovitelný; Pokud se ve spuštěné službě vyskytne, zpráva, která se právě zpracovává, se zahodí a služba pokračuje v běhu a zpracovává další zprávy. Scénáře nedostatku paměti a přetečení zásobníku ale nejsou obnovitelné kdekoli v .NET Framework; Služba se ukončí, pokud nalezne takové výjimky.

Kvóty v technologii WCF nezahrnují žádné předběžné přidělení. Pokud <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> je například kvóta (v různých třídách) nastavená na 128 KB, neznamená to, že se pro každou zprávu automaticky přidělí 128 KB. Skutečná přidělená částka závisí na skutečné velikosti příchozích zpráv.

K dispozici je mnoho kvót na transportní vrstvě. Jedná se o kvóty vynutilé konkrétním transportním kanálem, který se používá (HTTP, TCP atd.). I když toto téma popisuje některé z těchto kvót, jsou tyto kvóty podrobně popsané v části [přenosové kvóty](transport-quotas.md).

### <a name="hashtable-vulnerability"></a>Zranitelnost zatřiďovací tabulky

V případě, že kontrakty dat obsahují zatřiďovacími tabulkami nebo kolekce, existuje ohrožení zabezpečení. K tomuto problému dochází, pokud je do zatřiďovací tabulky vložen velký počet hodnot, kde velký počet těchto hodnot vygeneruje stejnou hodnotu hash. Tato možnost se dá použít jako útok DOS.  Tuto chybu zabezpečení lze zmírnit nastavením kvóty vazby třídy MaxReceivedMessageSize. Při nastavování této kvóty je nutné dbát na to, aby tyto útoky nedocházelo. Tato kvóta přináší horní limit velikosti zprávy WCF. Kromě toho se vyhněte používání zatřiďovacími tabulkami nebo kolekcí v kontraktech dat.

## <a name="limiting-memory-consumption-without-streaming"></a>Omezení spotřeby paměti bez streamování

Model zabezpečení kolem velkých zpráv závisí na tom, jestli se streamování používá. V případě běžného nestreamového případu jsou zprávy ukládány do vyrovnávací paměti. V takovém případě můžete použít <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kvótu na <xref:System.ServiceModel.Channels.TransportBindingElement> vazbách poskytovaných systémem nebo k ochraně před velkými zprávami tím, že omezíte maximální velikost zprávy pro přístup. Všimněte si, že služba může zpracovávat více zpráv současně. v takovém případě jsou všechny v paměti. K zmírnění této hrozby použijte funkci omezování.

Všimněte si také, že `MaxReceivedMessageSize` není umístěn horní mez pro paměť na základě zpráv, ale omezuje ho v rámci konstantního faktoru. Pokud je například `MaxReceivedMessageSize` přijata a pak deserializovat zpráva o velikosti 1 MB a potom deserializace, je nutné, aby objekt obsahoval další paměť, která má za následek celkovou spotřebu paměti po 1 MB. Z tohoto důvodu Vyhněte se vytváření serializovatelných typů, které by mohly mít za následek značnou spotřebu paměti bez množství příchozích dat. Například u kontraktu dat "MyContract" s 50mi volitelnými poli datových členů a dalšími 100 soukromými poli může být vytvořena instance XML konstrukce " \<MyContract/> ". Výsledkem tohoto XML je paměť, která je k dispozici pro pole 150. Všimněte si, že datové členy jsou ve výchozím nastavení volitelné. Pokud je takový typ součástí pole, je problém složený.

`MaxReceivedMessageSize`samotný není dostatek, aby nedocházelo k útokům DOS (Denial-of-Service). Například deserializátor může být vynuceně deserializovat graf hluboko vnořeného objektu (objekt, který obsahuje jiný objekt, který obsahuje ještě jiný objekt, a tak dále) příchozí zprávou. <xref:System.Runtime.Serialization.DataContractSerializer>Metody a volají jak <xref:System.Xml.Serialization.XmlSerializer> vnořeným způsobem pro deserializaci takových grafů. Hluboká vnořování volání metod může způsobit neobnovení <xref:System.StackOverflowException> . Tato hrozba se snižuje tím, že nastaví <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> kvótu pro omezení úrovně vnoření XML, jak je popsáno v části "používání XML bezpečně" dále v tématu.

Nastavení dalších kvót na `MaxReceivedMessageSize` je obzvláště důležité při použití binárního kódování XML. Použití binárního kódování je poměrně stejné jako komprese: malá skupina bajtů v příchozí zprávě může představovat velké množství dat. To znamená, že i zpráva přizpůsobující se do `MaxReceivedMessageSize` limitu může zabírat mnohem více paměti v plně rozbaleném formátu. Chcete-li zmírnit takové hrozby specifické pro XML, musí být všechny kvóty čtečky XML nastaveny správně, jak je popsáno v části "používání XML bezpečně" dále v tomto tématu.

## <a name="limiting-memory-consumption-with-streaming"></a>Omezení spotřeby paměti pomocí streamování

Při streamování můžete použít malé `MaxReceivedMessageSize` nastavení pro ochranu před útoky DoS (Denial-of-Service). U streamování je ale možné použít složitější scénáře. Například služba nahrání souborů akceptuje soubory větší než veškerá dostupná paměť. V takovém případě nastavte `MaxReceivedMessageSize` na extrémně velkou hodnotu, očekává se, že téměř žádná data nejsou ukládána do vyrovnávací paměti a proudem zprávy přímo na disk. Pokud by škodlivá zpráva mohla nějakým způsobem vynutit, aby WCF vynutilo data vyrovnávací paměti, místo jejich streamování v tomto případě už `MaxReceivedMessageSize` nechrání zprávu s přístupem k veškeré dostupné paměti.

Pro zmírnění této hrozby existují specifická nastavení kvót u různých komponent zpracování dat WCF, které omezují ukládání do vyrovnávací paměti. Nejdůležitější z nich je `MaxBufferSize` vlastnost u různých prvků vazby přenosu a standardních vazeb. Při streamování by měla být tato kvóta nastavena s ohledem na maximální velikost paměti, kterou jste ochotni přidělit na jednu zprávu. Stejně jako u platí `MaxReceivedMessageSize` , že nastavení nevloží absolutní maximum pro paměťovou spotřebu, ale omezuje ho pouze v rámci konstantního faktoru. Stejně jako u nástroje `MaxReceivedMessageSize` si pamatujte na možnost souběžného zpracování několika zpráv.

### <a name="maxbuffersize-details"></a>Podrobnosti o MaxBufferSize

`MaxBufferSize`Vlastnost omezuje všechny hromadné vyrovnávací paměti WCF. Například technologie WCF vždycky ukládá do vyrovnávací paměti hlavičku SOAP a chyby protokolu SOAP a také všechny části MIME, které se v přirozeném pořadí čtení ve zprávě mechanizmus pro optimalizaci přenosu zpráv (MTOM) nepoužívají. Toto nastavení omezuje velikost vyrovnávací paměti ve všech těchto případech.

Služba WCF to dosahuje předáním `MaxBufferSize` hodnoty do různých komponent, které se mohou ukládat do vyrovnávací paměti. Například některá <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> přetížení <xref:System.ServiceModel.Channels.Message> třídy přebírají `maxSizeOfHeaders` parametr. Technologie WCF předá `MaxBufferSize` hodnotu tomuto parametru, aby omezila velikost vyrovnávací paměti hlaviček SOAP. Je důležité nastavit tento parametr při <xref:System.ServiceModel.Channels.Message> přímém použití třídy. Obecně platí, že při použití komponenty ve službě WCF, která přijímá parametry kvóty, je důležité pochopit dopady zabezpečení těchto parametrů a správně je nastavit.

Kodér zpráv MTOM má také `MaxBufferSize` nastavení. Při použití standardních vazeb je tato hodnota nastavena automaticky na hodnotu transportní úrovně `MaxBufferSize` . Při použití prvku vazby kodéru zpráv MTOM k vytvoření vlastní vazby je však důležité nastavit `MaxBufferSize` vlastnost na bezpečnou hodnotu při použití streamování.

## <a name="xml-based-streaming-attacks"></a>Útoky streamování založené na XML

`MaxBufferSize`samotný není dostačující pro zajištění, že se WCF nedá vynutit do vyrovnávací paměti, když se očekává streamování. Například čtečky XML WCF vždy ukládají do vyrovnávací paměti celou počáteční značku XML elementu při počátečním čtení nového prvku. To se provádí tak, že se správně zpracovávají obory názvů a atributy. Pokud `MaxReceivedMessageSize` je nakonfigurován tak, aby byl velký (například pokud chcete povolit scénář přímého streamování velkých souborů), může být vytvořena škodlivá zpráva, kde je celá tělo zprávy velkým počátečním tagem elementu XML. Pokus o jeho čtení má za následek <xref:System.OutOfMemoryException> . Toto je jeden z mnoha možných útoků DOS založených na jazyce XML, které je možné zmírnit pomocí kvót čtečky XML, popsané v části "používání XML bezpečně" dále v tomto tématu. Při streamování je obzvláště důležité nastavit všechny tyto kvóty.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Kombinování streamování a programovacích modelů do vyrovnávací paměti

Mnoho možných útoků nastane z kombinování streamování a nestreamování programovacích modelů ve stejné službě. Předpokládejme, že existuje kontrakt služby se dvěma operacemi: jedna <xref:System.IO.Stream> a druhá má pole nějakého vlastního typu. Předpokládejme také, že `MaxReceivedMessageSize` je nastavena na velkou hodnotu, aby první operace mohla zpracovat velké datové proudy. To bohužel znamená, že velké zprávy se teď dají poslat druhé operaci zároveň a deserializace ukládá data v paměti jako pole před zavoláním operace. Toto je potenciální útok na útok typu DOS (Denial-of-Service): `MaxBufferSize` kvóta neomezuje velikost textu zprávy, což je to, s čím je deserializátor pracuje.

Z tohoto důvodu Vyhněte se kombinování operací založených na streamech a nestreamování v rámci stejné smlouvy. Pokud je nezbytně nutné kombinovat dva programovací modely, použijte následující opatření:

- Vypněte <xref:System.Runtime.Serialization.IExtensibleDataObject> funkci nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnosti na <xref:System.ServiceModel.ServiceBehaviorAttribute> `true` . Tím se zajistí, že se deserializovat jenom členové, kteří jsou součástí kontraktu.

- Nastavte <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost <xref:System.Runtime.Serialization.DataContractSerializer> na bezpečnou hodnotu. Tato kvóta je také k dispozici v <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu nebo prostřednictvím konfigurace. Tato kvóta omezuje počet objektů, které jsou deserializovány v jedné epizodě deserializace. Obvykle se každý parametr operace nebo část těla zprávy v kontraktu zprávy deserializovat v jedné epizodě. Při deserializaci polí se každá položka pole počítá jako samostatný objekt.

- Nastavte všechny kvóty čtečky XML na bezpečné hodnoty. Věnujte pozornost <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> , a <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> a vyhnete se řetězcům v operacích, které nestreamují.

- Projděte si seznam známých typů, přičemž mějte na paměti, že některé z nich lze kdykoli vytvořit. (Další informace naleznete v části "prevence načítání nezamýšlených typů" dále v tomto tématu).

- Nepoužívejte žádné typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které ukládá do vyrovnávací paměti velké množství dat. Nepřidávat takové typy do seznamu známých typů.

- Nepoužívejte pole, <xref:System.Xml.XmlElement> pole <xref:System.Xml.XmlNode> <xref:System.Byte> nebo typy, které jsou implementovány <xref:System.Runtime.Serialization.ISerializable> ve smlouvě.

- Nepoužívejte pole, <xref:System.Xml.XmlElement> pole <xref:System.Xml.XmlNode> <xref:System.Byte> nebo typy, které jsou implementovány <xref:System.Runtime.Serialization.ISerializable> v seznamu známých typů.

Předchozí opatření platí v případě, že nestreamovaná operace používá <xref:System.Runtime.Serialization.DataContractSerializer> . Nikdy nekombinujte streamování a nestreamující programovací modely na stejné službě, pokud používáte <xref:System.Xml.Serialization.XmlSerializer> , protože nemá ochranu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> kvóty.

### <a name="slow-stream-attacks"></a>Pomalé útoky přes Stream

Třída útoků s cílem odepření služby streamování nezahrnuje spotřebu paměti. Místo toho útok zahrnuje pomalý odesílatel nebo přijímač dat. Při čekání na odeslání nebo přijetí dat dojde k vyčerpání prostředků, jako jsou například vlákna a dostupná připojení. Tato situace může nastat buď v důsledku zneužití škodlivého útoku, nebo z legitimního odesílatele nebo příjemce na pomalé síťové připojení.

Pro zmírnění těchto útoků nastavte časový limit přenosu správně. Další informace najdete v tématu [přenosové kvóty](transport-quotas.md). V druhé době nikdy nepoužívejte `Read` synchronní `Write` operace ani operace při práci s datovými proudy ve službě WCF.

## <a name="using-xml-safely"></a>Bezpečné používání XML

> [!NOTE]
> I když je tato část o souboru XML, informace se vztahují také na dokumenty JavaScript Object Notation (JSON). Kvóty fungují podobně, a to pomocí [mapování mezi JSON a XML](mapping-between-json-and-xml.md).

### <a name="secure-xml-readers"></a>Zabezpečení čtecích zařízení XML

Informační sada XML tvoří základ všech zpracování zpráv ve službě WCF. Při přijímání dat XML z nedůvěryhodného zdroje existuje řada možností útoku DOS, které je nutné zmírnit. WCF poskytuje speciální zabezpečené čtecí zařízení XML. Tito čtenáři se vytvářejí automaticky při použití některého ze standardních kódování ve službě WCF (text, Binary nebo MTOM).

Některé funkce zabezpečení u těchto čtecích zařízení jsou vždycky aktivní. Čtenáři například nikdy nezpracovávají definice typu dokumentu (DTD), které jsou potenciálním zdrojem útoků DOS a by se nikdy neměly zobrazovat v legitimních zprávách SOAP. K dalším funkcím zabezpečení patří kvóty čtecího zařízení, které je nutné nakonfigurovat, které jsou popsány v následující části.

Při práci přímo s čtecími moduly XML (například při psaní vlastního kodéru nebo při práci přímo s <xref:System.ServiceModel.Channels.Message> třídou) vždy používejte zabezpečené čtecí zařízení WCF, pokud je pravděpodobné, že budete pracovat s nedůvěryhodnými daty. Vytvořte zabezpečené čtecí zařízení voláním jednoho ze statických metod výrobní metody <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> , <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> nebo <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> na <xref:System.Xml.XmlDictionaryReader> třídu. Při vytváření čtecího modulu předejte hodnoty zabezpečené kvóty. Nevolejte `Create` přetížení metod. Nevytvářejí čtečku WCF. Místo toho se vytvoří čtenář, který není chráněný funkcemi zabezpečení popsanými v této části.

### <a name="reader-quotas"></a>Kvóty čtecího modulu

Zabezpečené čtečky XML mají pět konfigurovatelných kvót. Ty se obvykle konfigurují pomocí `ReaderQuotas` vlastnosti u elementů vazby kódování nebo standardních vazeb nebo pomocí <xref:System.Xml.XmlDictionaryReaderQuotas> objektu předaného při vytváření čtecího modulu.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Tato kvóta omezuje počet bajtů, které jsou čteny v rámci jedné `Read` operace při čtení počáteční značky elementu a jejích atributů. (V nestreamované případech se název elementu sám nepočítá s kvótou.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>je důležité z následujících důvodů:

- Název elementu a jeho atributy jsou při čtení vždy uloženy do vyrovnávací paměti. Proto je důležité nastavit tuto kvótu správně v režimu streamování, aby se zabránilo nadměrnému ukládání do vyrovnávací paměti, když se očekává streamování. `MaxDepth`Informace o skutečném objemu ukládání do vyrovnávací paměti najdete v části kvóta.

- Příliš mnoho atributů XML může použít neúměrný čas zpracování, protože názvy atributů musí být zkontrolovány pro jedinečnost. `MaxBytesPerRead`snižuje riziko této hrozby.

#### <a name="maxdepth"></a>MaxDepth

Tato kvóta omezuje maximální hloubku vnořování prvků XML. Například dokument " \<A> \<B> \<C/> \</B> \</A> " má vnořenou hloubku tři. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>je důležité z následujících důvodů:

- `MaxDepth`spolupracuje s `MaxBytesPerRead` : čtenář vždycky uchovává data v paměti pro aktuální prvek a všechny jeho nadřazené prvky, takže maximální spotřeba paměti čtecího zařízení je úměrná produktu těchto dvou nastavení.

- Při deserializaci diagramu hluboko vnořeného objektu je pro deserializaci nucen přístup k celému zásobníku a vyvolat neobnovitelné <xref:System.StackOverflowException> . Mezi vnořenými a vnořenými objekty XML existuje přímá korelace pro <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> . `MaxDepth`Tuto hrozbu můžete zmírnit pomocí této hrozby.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Tato kvóta omezuje velikost *NameTable*čtenářů. NameTable obsahuje určité řetězce (například obory názvů a předpony), které byly zjištěny při zpracování dokumentu XML. Vzhledem k tomu, že jsou tyto řetězce uloženy do vyrovnávací paměti, nastavte tuto kvótu tak, aby nedocházelo k nadměrnému ukládání do vyrovnávací paměti, pokud je

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Tato kvóta omezuje maximální velikost řetězce, kterou čtecí modul XML vrátí. Tato kvóta neomezuje spotřebu paměti v samotném čtecím modulu XML, ale v komponentě, která používá čtecí modul. Například pokud <xref:System.Runtime.Serialization.DataContractSerializer> používá čtecí modul zabezpečený s, neprovádí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> deserializaci řetězce větší než tato kvóta. Při <xref:System.Xml.XmlDictionaryReader> přímém použití třídy ne všechny metody respektují tuto kvótu, ale pouze metody, které jsou určeny konkrétně pro čtení řetězců, jako je například <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> metoda. <xref:System.Xml.XmlReader.Value%2A>Tato kvóta nemá vliv na vlastnost čtecího modulu, a proto by neměla být použita, pokud je tato kvóta potřebná.

#### <a name="maxarraylength"></a>MaxArrayLength

Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrátí čtecí modul XML, včetně bajtových polí. Tato kvóta neomezuje spotřebu paměti v samotném čtecím modulu XML, ale v jakékoli součásti, která používá čtecí modul. Například pokud <xref:System.Runtime.Serialization.DataContractSerializer> používá čtecí modul zabezpečený s, neprovádí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> deserializaci polí bajtů větší než tato kvóta. Je důležité nastavit tuto kvótu při pokusu o smíchání streamování a programových modelů ve vyrovnávací paměti v rámci jedné smlouvy. Mějte na paměti, že při <xref:System.Xml.XmlDictionaryReader> přímém použití třídy jsou pouze metody, které jsou určeny konkrétně pro čtení polí libovolné velikosti určitých primitivních typů, například <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A> , s ohledem na tuto kvótu.

## <a name="threats-specific-to-the-binary-encoding"></a>Hrozby specifické pro binární kódování

Rozhraní WCF kódování XML podporuje funkci *řetězce slovníku* . Velký řetězec může být kódovaný pouze v několika bajtech. To umožňuje výrazné zvýšení výkonu, ale přináší nové hrozby při odepření služby, které je potřeba zmírnit.

Existují dva druhy slovníků: *statické* a *dynamické*. Statický slovník je vestavěný seznam dlouhých řetězců, které mohou být reprezentovány pomocí krátkého kódu v binárním kódování. Tento seznam řetězců je opraven při vytvoření čtecího modulu a nelze jej upravit. Žádný z řetězců ve statickém slovníku, který služba WCF ve výchozím nastavení používá, je dostatečně velký, aby mohl představovat vážnou hrozbu pro odepření služby, i když je stále možné je použít při útoku na rozšíření slovníku. V pokročilých scénářích, kde zadáváte vlastní statický slovník, buďte opatrní při zavádění velkých řetězců slovníku.

Funkce dynamického slovníku umožňuje zprávám definovat vlastní řetězce a přidružit je k krátkým kódům. Tyto mapování řetězců na kód jsou uchovávány v paměti během celé komunikační relace, takže následné zprávy nemusí znovu odesílat řetězce a mohou využívat již definované kódy. Tyto řetězce mohou mít libovolnou délku, a proto můžou představovat vážnou hrozbu, než jaké jsou ve statickém slovníku.

První hrozba, kterou je nutné zmírnit, je možnost dynamického slovníku (tabulka mapování řetězců na kód), která se přestává být příliš velká. Tento slovník se může rozšířit v průběhu několika zpráv, takže `MaxReceivedMessageSize` kvóta nenabízí ochranu, protože platí jenom pro každou zprávu zvlášť. Proto <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> existuje samostatná vlastnost v <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , která omezuje velikost slovníku.

Na rozdíl od většiny ostatních kvót platí tato kvóta i při psaní zpráv. Pokud při čtení zprávy dojde k překročení, `QuotaExceededException` je vyvolána jako obvykle. Pokud při zápisu zprávy dojde k překročení, budou všechny řetězce, které způsobují překročení kvóty, zapsány tak, jak jsou, bez použití funkce dynamického slovníku.

### <a name="dictionary-expansion-threats"></a>Hrozby rozšíření slovníku

Významná třída binárních útoků vyplývají z rozšíření slovníku. Malá zpráva v binárním formátu může v plně rozbaleném textovém formuláři přepínat na velmi velkou zprávu, pokud má rozsáhlé použití funkce řetězce slovníku. Faktor rozšíření pro řetězce dynamického slovníku je omezen <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> kvótou, protože žádný řetězec dynamického slovníku nepřekračuje maximální velikost celého slovníku.

<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>Vlastnosti, `MaxStringContentLength` a `MaxArrayLength` omezují jenom spotřebu paměti. Obvykle se nevyžadují ke zmírnění hrozeb v nestreamované míře, protože využití paměti je už omezené nástrojem `MaxReceivedMessageSize` . Počítá ale `MaxReceivedMessageSize` počet předem rozšiřujících bajtů. Když se používá binární kódování, může využití paměti potenciálně přesahovat `MaxReceivedMessageSize` , protože je omezené jenom faktorem <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> . Z tohoto důvodu je důležité <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> při použití binárního kódování vždy nastavit všechny kvóty čtenářů (obzvláště).

Při použití binárního kódování společně s rozhraním <xref:System.Runtime.Serialization.DataContractSerializer> `IExtensibleDataObject` může být rozhraní nepoužitelné k připojení útoku na rozšíření slovníku. Toto rozhraní v podstatě poskytuje neomezené úložiště pro libovolná data, která nejsou součástí smlouvy. Pokud kvóty nemůžou být nastavené na nízké úrovni, které `MaxSessionSize` vynásobené `MaxReceivedMessageSize` nepředstavuje problém, zakažte `IExtensibleDataObject` funkci při použití binárního kódování. Nastavte `IgnoreExtensionDataObject` vlastnost na `true` `ServiceBehaviorAttribute` atribut. Alternativně Neimplementujte `IExtensibleDataObject` rozhraní. Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Souhrn kvót

Následující tabulka shrnuje doprovodné materiály k kvótám.

|Podmínka|Důležité kvóty k nastavení|
|---------------|-----------------------------|
|Bez streamování nebo streamování malých zpráv, textu nebo kódování MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead` a`MaxDepth`|
|Bez streamování nebo streamování malých zpráv, binární kódování|`MaxReceivedMessageSize`, `MaxSessionSize` a všechny`ReaderQuotas`|
|Streamování velkých zpráv, textu nebo kódování MTOM|`MaxBufferSize`a vše`ReaderQuotas`|
|Streamování velkých zpráv, binární kódování|`MaxBufferSize`, `MaxSessionSize` a všechny`ReaderQuotas`|

- Časové limity na úrovni přenosu musí být vždycky nastavené a nikdy nepoužívají synchronní čtení a zápisy, když se streamování používá, bez ohledu na to, jestli jsou streamované velké nebo malé zprávy.

- Pokud je kvóta nejistá, nastavte ji na bezpečnou hodnotu, abyste ji nenechali otevřené.

## <a name="preventing-malicious-code-execution"></a>Zabránění spuštění škodlivého kódu

Následující obecné třídy hrozeb mohou spustit kód a mít nezamýšlené účinky:

- Deserializátor načte škodlivý, nebezpečný nebo citlivý typ zabezpečení.

- Příchozí zpráva způsobí, že deserializátor vytvoří instanci normálně bezpečného typu takovým způsobem, že má nezamýšlené důsledky.

Níže uvedené části popisují tyto třídy hrozeb.

## <a name="datacontractserializer"></a>DataContractSerializer

(Informace o zabezpečení najdete v <xref:System.Xml.Serialization.XmlSerializer> příslušné dokumentaci.) Model zabezpečení pro <xref:System.Xml.Serialization.XmlSerializer> je podobný tomuto <xref:System.Runtime.Serialization.DataContractSerializer> : a liší se hlavně v podrobnostech. Například <xref:System.Xml.Serialization.XmlIncludeAttribute> atribut se používá pro zahrnutí typu místo <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu. Nicméně některé hrozby, které jsou jedinečné pro, <xref:System.Xml.Serialization.XmlSerializer> jsou popsány dále v tomto tématu.

### <a name="preventing-unintended-types-from-being-loaded"></a>Brání načtení nezamýšlených typů.

Načítání nezamýšleného typu může mít významné důsledky, zda je typ škodlivý nebo má pouze vedlejší účinky závislé na zabezpečení. Typ může obsahovat zneužitou chybu zabezpečení, provádět akce závislé na zabezpečení v konstruktoru konstruktoru nebo třídy, mít velké paměťové nároky, které usnadňují útoky DoS (Denial of-Service), nebo může vyvolat neobnovitelná výjimky. Typy mohou mít konstruktory třídy, které jsou spuštěny ihned po načtení typu a před vytvořením všech instancí. Z těchto důvodů je důležité řídit sadu typů, které může deserializace načítat.

<xref:System.Runtime.Serialization.DataContractSerializer>Deserializace volně propojených způsobů. Nikdy nečte typ Common Language Runtime (CLR) a názvy sestavení z příchozích dat. To se podobá chování <xref:System.Xml.Serialization.XmlSerializer> , ale liší se od chování <xref:System.Runtime.Serialization.NetDataContractSerializer> , <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Volné propojení přináší stupeň bezpečnosti, protože vzdálený útočník nemůže určit libovolný typ, který se má načíst, a to tak, že ve zprávě pojmenuje tento typ.

<xref:System.Runtime.Serialization.DataContractSerializer>Vždy je povoleno načíst typ, který je v současné době očekáván podle kontraktu. Například Pokud kontrakt dat má datový člen typu `Customer` , <xref:System.Runtime.Serialization.DataContractSerializer> je povoleno načíst `Customer` typ Při deserializaci tohoto datového člena.

Navíc <xref:System.Runtime.Serialization.DataContractSerializer> podporuje polymorfismus. Datový člen může být deklarován jako <xref:System.Object> , ale příchozí data mohou obsahovat `Customer` instanci. To je možné pouze v případě, že byl `Customer` typ pro deserializaci vytvořen pomocí jednoho z těchto mechanismů:

- <xref:System.Runtime.Serialization.KnownTypeAttribute>atribut aplikovaný na typ.

- `KnownTypeAttribute`atribut určující metodu, která vrátí seznam typů.

- `ServiceKnownTypeAttribute`přidělen.

- `KnownTypes`Konfigurační oddíl.

- Seznam známých typů explicitně předaných <xref:System.Runtime.Serialization.DataContractSerializer> během konstrukce při přímém použití serializátoru.

Každý z těchto mechanismů zvyšuje plochu tím, že zavádí více typů, které může deserializace načíst. Chcete-li zajistit, aby se do seznamu známých typů přidaly žádné škodlivé nebo nezamýšlené typy, proveďte kontrolu každého z těchto mechanismů.

Jakmile je známý typ v oboru, lze jej načíst kdykoli a instance typu lze vytvořit, i když je ve skutečnosti kontrakt nepoužívá. Předpokládejme například, že typ "MyDangerousType" se přidá do seznamu známých typů pomocí jednoho z mechanismů uvedených výše. To znamená, že:

- `MyDangerousType`je načten a jeho konstruktor třídy je spuštěn.

- I při deserializaci kontraktu dat s řetězcovým datovým členem může škodlivá zpráva přesto způsobit `MyDangerousType` vytvoření instance. Kód v, jako je například `MyDangerousType` setter vlastností, lze spustit. Po dokončení se deserializátor pokusí přiřadit tuto instanci k řetězcovému datovému členu a selže s výjimkou.

Při psaní metody, která vrátí seznam známých typů nebo při předání seznamu přímo <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, se ujistěte, že kód, který připravuje seznam, je zabezpečen a pracuje pouze s důvěryhodnými daty.

Pokud zadáte známé typy v konfiguraci, zajistěte, aby byl konfigurační soubor zabezpečený. Vždy používejte silné názvy v konfiguraci (zadáním veřejného klíče podepsaného sestavení, kde se nachází typ), ale nezadávejte verzi typu, který se má načíst. Zavaděč typu automaticky vybere nejnovější verzi, pokud je to možné. Pokud v konfiguraci zadáte konkrétní verzi, spustíte následující riziko: typ může mít chybu zabezpečení, která může být opravena v budoucí verzi, ale ohrožená verze je stále načtena, protože je explicitně zadána v konfiguraci.

Příliš mnoho známých typů má jiné důsledky: <xref:System.Runtime.Serialization.DataContractSerializer> vytvoří mezipaměť kódu serializace/deserializace v doméně aplikace s položkou pro každý typ, musí serializovat a deserializovat. Tato mezipaměť se nikdy nevymaže, dokud je spuštěná doména aplikace. Proto útočník, který ví, že aplikace používá mnoho známých typů, může způsobit deserializaci všech těchto typů, což způsobí, že mezipaměť spotřebuje neúměrně velký objem paměti.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Zabránění typům v nezamýšleném stavu

Typ může mít omezení Interní konzistence, která musí být vynutit. Je třeba dbát na to, abyste zabránili porušení těchto omezení během deserializace.

Následující příklad typu představuje stav mikrozámku na kosmické lodi a vynutilo omezení, že vnitřní i vnější dvířka nelze současně otevřít.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Útočník může například odeslat škodlivou zprávu s ohledem na omezení a získat objekt do neplatného stavu, což může mít nepředvídatelné a nepředvídatelné následky.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Tato situace se může vyhnout tím, že se dozvíte o následujících bodech:

- Když <xref:System.Runtime.Serialization.DataContractSerializer> deserializace většinu tříd, konstruktory se nespustí. Proto nespoléhá na žádnou správu stavu provedenou v konstruktoru.

- Pomocí zpětných volání zajistěte, aby byl objekt v platném stavu. Zpětné volání označené <xref:System.Runtime.Serialization.OnDeserializedAttribute> atributem je obzvlášť užitečné, protože se spouští po deserializaci a má možnost kontrolovat a opravovat celkový stav. Další informace naleznete v tématu [zpětná volání serializace odolná proti verzi](version-tolerant-serialization-callbacks.md).

- Nenavrhujte typy kontraktů dat tak, aby spoléhaly na konkrétní pořadí, ve kterém musí být volána metoda set vlastnosti.

- Je nutné se starat o použití starších typů označených <xref:System.SerializableAttribute> atributem. Mnoho z nich bylo navrženo tak, aby spolupracovaly se .NET Framework Vzdálená komunikace pro použití s důvěryhodnými daty. Existující typy označené pomocí tohoto atributu nemusí být navržené s ohledem na bezpečnost stavu.

- Nespoléhá se na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> atributu, aby bylo zaručeno, že data jsou v souladu se zabezpečením stavu. Data by mohla být vždycky `null` , `zero` nebo `invalid` .

- Nikdy nedůvěřovat objektu Graph deserializovatelné z nedůvěryhodného zdroje dat, aniž byste ho museli nejdřív ověřit. Každý jednotlivý objekt může být v konzistentním stavu, ale graf objektu jako celku nemusí být. Kromě toho, i když je režim uchování grafu objektů zakázaný, deserializovaný graf může mít více odkazů na stejný objekt nebo obsahovat cyklické odkazy. Další informace naleznete v tématu [serializace a deserializace](serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>Bezpečné použití NetDataContractSerializer

<xref:System.Runtime.Serialization.NetDataContractSerializer>Je Serializační modul, který používá těsné spojení s typy. To je podobné jako <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . To znamená, že určuje, který typ instance se má vytvořit, čtením .NET Framework sestavení a názvu typu z příchozích dat. I když je součástí WCF, není k dispozici žádný způsob, jak se zapojit do tohoto stroje serializace; vlastní kód musí být napsán. `NetDataContractSerializer`Je primárně k dispozici pro usnadnění migrace z .NET Framework vzdálené komunikace do WCF. Další informace naleznete v příslušném oddílu [serializace a deserializace](serialization-and-deserialization.md).

Vzhledem k tomu, že samotná zpráva může indikovat, že je možné načíst jakýkoli typ, <xref:System.Runtime.Serialization.NetDataContractSerializer> je mechanismus nezabezpečený a měl by být používán pouze s důvěryhodnými daty. Je možné ji zabezpečit zápisem zabezpečeného typu, který omezuje typ, který umožňuje načíst pouze bezpečné typy (pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> Vlastnosti).

I když se používá s důvěryhodnými daty, může příchozí data nedostatečně určovat typ, který se má načíst, zejména pokud <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> je vlastnost nastavená na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> . Každý, kdo má přístup k adresáři aplikace nebo do globální mezipaměti sestavení (GAC), může nahradit škodlivý typ místo, který by měl načíst. Vždy zajistěte, aby zabezpečení adresáře aplikace a globální mezipaměti sestavení byla zajištěna správným nastavením oprávnění.

Obecně platí, že pokud povolíte částečně důvěryhodný přístup ke své `NetDataContractSerializer` instanci nebo jiným způsobem ovládat selektor náhradních ( <xref:System.Runtime.Serialization.ISurrogateSelector> ) nebo serializace ( <xref:System.Runtime.Serialization.SerializationBinder> ), kód může vycházet z Skvělé kontroly nad procesem serializace/deserializace. Například může vkládat libovolný typ, vést k vyzrazení informací, manipulaci s výsledným grafem objektů nebo serializovanými daty nebo přetečení výsledného serializovaného datového proudu.

Dalším problémem se zabezpečením `NetDataContractSerializer` je odmítnutí služby, což není hrozba při spuštění škodlivého kódu. Při použití rozhraní `NetDataContractSerializer` vždy nastavte <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kvótu na bezpečnou hodnotu. Je snadné vytvořit malou škodlivou zprávu, která přiděluje pole objektů, jejichž velikost je omezena pouze touto kvótou.

### <a name="xmlserializer-specific-threats"></a>Hrozby specifické pro XmlSerializer

<xref:System.Xml.Serialization.XmlSerializer>Model zabezpečení je podobný jako u <xref:System.Runtime.Serialization.DataContractSerializer> . Pár hrozeb je ale jedinečný pro <xref:System.Xml.Serialization.XmlSerializer> .

<xref:System.Xml.Serialization.XmlSerializer>Generuje *sestavení serializace* za běhu, která obsahují kód, který skutečně serializace a deserializace; tato sestavení jsou vytvořena v adresáři dočasných souborů. Pokud má nějaký jiný proces nebo uživatel přístupová práva k tomuto adresáři, může přepsat kód serializace/deserializace s libovolným kódem. <xref:System.Xml.Serialization.XmlSerializer>Pak tento kód spustí pomocí svého kontextu zabezpečení namísto kódu serializace/deserializace. Ujistěte se, že jsou oprávnění nastavena správně v adresáři dočasných souborů, aby k tomu nedocházelo.

<xref:System.Xml.Serialization.XmlSerializer>Má také režim, ve kterém používá předem vygenerovaná sestavení serializace namísto jejich generování za běhu. Tento režim se spustí pokaždé, když <xref:System.Xml.Serialization.XmlSerializer> může najít vhodné sestavení serializace. <xref:System.Xml.Serialization.XmlSerializer>Kontroluje, zda bylo sestavení serializace podepsáno stejným klíčem, který byl použit k podepsání sestavení obsahujícího serializované typy. To nabízí ochranu před škodlivými sestaveními, která jsou maskována jako sestavení serializace. Nicméně pokud sestavení, které obsahuje vaše Serializovatelné typy, není podepsáno, <xref:System.Xml.Serialization.XmlSerializer> nemůže provést tuto kontrolu a použít jakékoli sestavení se správným názvem. Díky tomu je možné spustit škodlivý kód. Vždy Podepište sestavení, která obsahují vaše Serializovatelné typy, nebo důkladně řízení přístupu k adresáři vaší aplikace a globální mezipaměti sestavení (GAC), aby nedocházelo k zavedení škodlivých sestavení.

<xref:System.Xml.Serialization.XmlSerializer>Může to být podléhat útokům DOS (Denial of Service). Nemá <xref:System.Xml.Serialization.XmlSerializer> `MaxItemsInObjectGraph` kvótu (jak je k dispozici v <xref:System.Runtime.Serialization.DataContractSerializer> ). Proto deserializace libovolné množství objektů, které jsou omezeny pouze velikostí zprávy.

### <a name="partial-trust-threats"></a>Hrozby s částečným vztahem důvěryhodnosti

Všimněte si následujících otázek týkajících se hrozeb souvisejících s kódem spuštěným s částečnou důvěryhodností. Tyto hrozby zahrnují škodlivý částečně důvěryhodný kód a také škodlivý částečně důvěryhodný kód v kombinaci s jinými scénáři útoku (například částečně důvěryhodný kód, který vytvoří konkrétní řetězec a poté je deserializace).

- Při použití všech komponent serializace nikdy nehodnotte žádná oprávnění před tímto použitím, a to ani v případě, že celý scénář serializace spadá do rozsahu vašeho kontrolního výrazu a nepracujete s nedůvěryhodnými daty nebo objekty. Takové použití může vést k ohrožení zabezpečení.

- V případech, kdy částečně důvěryhodný kód má kontrolu nad procesem serializace, buď prostřednictvím bodů rozšiřitelnosti (náhrady), serializovaných typů, nebo prostřednictvím jiných prostředků, částečně důvěryhodný kód může způsobit, že serializátor vytvoří výstup velkého množství dat do serializovaného datového proudu, což může způsobit odepření služby (DoS) příjemci tohoto datového proudu. Pokud provádíte serializaci dat určených pro cíl, který je citlivý na systémy DoS – hrozby, neserializovat částečně důvěryhodné typy nebo jinak umožnit částečně důvěryhodné serializaci řízení kódu.

- Pokud povolíte částečně důvěryhodnému přístupu ke své <xref:System.Runtime.Serialization.DataContractSerializer> instanci nebo jiným způsobem ovládat [náhrady u kontraktu dat](../extending/data-contract-surrogates.md), může dojít k skvělému řízení procesu serializace/deserializace. Například může vkládat libovolný typ, vést k vyzrazení informací, manipulaci s výsledným grafem objektů nebo serializovanými daty nebo přetečení výsledného serializovaného datového proudu. Podobná <xref:System.Runtime.Serialization.NetDataContractSerializer> hrozba je popsaná v části "použití zabezpečeného NetDataContractSerializeru".

- Pokud <xref:System.Runtime.Serialization.DataContractAttribute> je atribut použit na typ (nebo typ označený jako, ale není <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> ), může deserializátor vytvořit instanci takového typu, i když jsou všechny konstruktory neveřejné nebo chráněné požadavky.

- Nikdy nedůvěřuje výsledku deserializace, pokud nejsou data pro deserializaci důvěryhodná a Vy jste si jisti, že všechny známé typy jsou typy, kterým důvěřujete. Všimněte si, že známé typy nejsou načteny z konfiguračního souboru aplikace (ale jsou načteny z konfiguračního souboru počítače) při spuštění v částečném vztahu důvěryhodnosti.

- Pokud předáte <xref:System.Runtime.Serialization.DataContractSerializer> instanci s náhradním přidaným do částečně důvěryhodného kódu, kód může změnit libovolně upravitelná nastavení v této zástupnosti.

- Pro deserializovaný objekt, pokud čtecí modul XML (nebo data v něm) pochází z částečně důvěryhodného kódu, považovat výsledný deserializovaný objekt za nedůvěryhodná data.

- Skutečnost, že <xref:System.Runtime.Serialization.ExtensionDataObject> typ nemá žádné veřejné členy, neznamená, že data v rámci tohoto typu jsou zabezpečená. Například pokud provádíte deserializaci z privilegovaných zdrojů dat do objektu, ve kterém jsou uložena nějaká data, částečně důvěryhodný kód může číst data v objektu `ExtensionDataObject` pomocí serializace objektu. Zvažte nastavení <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> na `true` Při deserializaci z privilegovaného zdroje dat do objektu, který je později předán částečně důvěryhodnému kódu.

- <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporují serializaci privátních, chráněných, interních a veřejných členů v úplném vztahu důvěryhodnosti. V částečném vztahu důvěryhodnosti však lze serializovat pouze veřejné členy. <xref:System.Security.SecurityException>Výjimka je vyvolána, pokud se aplikace pokusí serializovat neveřejný člen.

    Pro umožnění serializace interních nebo chráněných interních členů v částečném vztahu důvěryhodnosti použijte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut Assembly. Tento atribut umožňuje sestavení deklarovat, že jeho interní členy jsou viditelné pro některé jiné sestavení. V tomto případě sestavení, které má serializovat své interní členy, deklaruje deklaraci, že jeho interní členy jsou viditelné pro System. Runtime. Serialization. dll.

    Výhodou tohoto přístupu je, že nevyžaduje cestu pro generování zvýšeného kódu.

    Ve stejnou dobu existují dvě hlavní nevýhody.

    První nevýhodou je, že vlastnost opt-in <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu je platná pro sestavení. To znamená, že nemůžete určit, že jeho interní členy mají serializovat pouze určitá třída. Samozřejmě si stále můžete zvolit, že nechcete serializovat konkrétní interní člen, pouhým přidáním <xref:System.Runtime.Serialization.DataMemberAttribute> atributu k tomuto členu. Podobně může vývojář také rozhodnout, že má místo soukromého nebo chráněného člena, a to s mírnými aspekty viditelnosti.

    Druhým nevýhodou je, že stále nepodporuje soukromé nebo chráněné členy.

    K ilustraci použití <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu v částečném vztahu důvěryhodnosti zvažte následující program:

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    V předchozím příkladu `PermissionsHelper.InternetZone` odpovídá poli <xref:System.Security.PermissionSet> pro částečnou důvěryhodnost. Nyní bez <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributu nebude aplikace úspěšná, bude aktivována <xref:System.Security.SecurityException> zpráva oznamující, že neveřejné členy nelze serializovat v částečném vztahu důvěryhodnosti.

    Pokud však přidáme následující řádek do zdrojového souboru, program se úspěšně spustí.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Další aspekty správy stavů

Další aspekty týkající se správy stavu objektů jsou zmínky o:

- Při použití programovacího modelu založeného na datových proudech s přenosem streamování dojde ke zpracování zprávy při doručení zprávy. Odesílatel zprávy může přerušit operaci odeslání uprostřed datového proudu, přičemž váš kód zůstane v nepředvídatelném stavu, pokud bylo očekáváno více obsahu. Obecně platí, že se nespoléhá na dokončování datového proudu a neprovádějte žádné práce v operaci založené na datových proudech, které nelze vrátit zpět pro případ, že je datový proud přerušen. To platí také pro situaci, kdy může být zpráva po tělo streamování poškozena (například může chybět koncová značka pro obálku protokolu SOAP nebo může obsahovat druhý text zprávy).

- Použití `IExtensibleDataObject` funkce může způsobit vygenerování citlivých dat. Pokud přijímáte data z nedůvěryhodného zdroje do kontraktů dat s `IExtensibleObjectData` a později je znovu vygenerujete na zabezpečeném kanálu, kde jsou zprávy podepsány, může vám doručíme za data, o kterých víte, že nic neznáte. Kromě toho je možné, že celkový stav, který odesíláte, může být neplatný, pokud se v účtu podrží známá i neznámá data. Tuto situaci Vyhněte buď selektivním nastavením vlastnosti dat rozšíření na, `null` nebo selektivním zakázáním této `IExtensibleObjectData` funkce.

## <a name="schema-import"></a>Import schématu

Proces importu schématu pro generování typů se obvykle provádí pouze v době návrhu, například při použití nástroje pro vytvoření třídy klienta [(Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ve webové službě. V pokročilejších scénářích ale můžete schéma zpracovat za běhu. Uvědomte si, že pokud to uděláte, můžete si vystavit rizika při odepření služby. Import některých schémat může trvat dlouhou dobu. Nikdy nepoužívejte <xref:System.Xml.Serialization.XmlSerializer> komponentu importu schématu v takových scénářích, pokud jsou schémata pravděpodobně přicházející z nedůvěryhodného zdroje.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>Hrozby specifické pro integraci ASP.NET AJAX

Když uživatel implementuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> nebo <xref:System.ServiceModel.Description.WebHttpBehavior> , WCF zpřístupňuje koncový bod, který může přijímat zprávy XML i JSON. Existuje však pouze jedna sada kvót čtecího modulu, kterou používá čtečka XML i čtečka JSON. Některá nastavení kvót můžou být vhodná pro jedno čtecí zařízení, ale jsou pro ně moc velká.

Při implementaci nástroje `WebScriptEnablingBehavior` má uživatel možnost vystavit proxy JavaScript na koncovém bodu. Je potřeba vzít v úvahu následující problémy se zabezpečením:

- Informace o službě (názvy operací, názvy parametrů atd.) lze získat prozkoumáním proxy JavaScript.

- Při použití koncového bodu JavaScriptu můžou být citlivé a soukromé informace zachovány v mezipaměti klientského webového prohlížeče.

## <a name="a-note-on-components"></a>Poznámka k součástem

WCF je flexibilní a přizpůsobitelný systém. Většina obsahu tohoto tématu se zaměřuje na nejběžnější scénáře použití WCF. Je však možné napsat komponenty WCF poskytují mnoho různých způsobů. Je důležité pochopit důsledky zabezpečení při používání jednotlivých komponent. Zejména jde o toto:

- Pokud je nutné použít čtečky XML, použijte čtečky, které <xref:System.Xml.XmlDictionaryReader> Třída poskytuje, na rozdíl od ostatních čtenářů. Bezpečná čtenáři se vytvářejí pomocí <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> metod, a <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> . Nepoužívejte <xref:System.Xml.XmlReader.Create%2A> metodu. Vždy nakonfigurujte čtečky s bezpečnými kvótami. Serializační moduly ve službě WCF jsou zabezpečené pouze v případě, že se používají s zabezpečenými čtenáři XML ze služby WCF.

- Při použití <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci potenciálně nedůvěryhodných dat vždy nastavte <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost.

- Při vytváření zprávy nastavte `maxSizeOfHeaders` parametr, pokud `MaxReceivedMessageSize` nenabízí dostatečnou ochranu.

- Při vytváření kodéru vždy konfigurujte příslušné kvóty, například `MaxSessionSize` a `MaxBufferSize` .

- Při použití filtru zpráv XPath nastavte, aby se <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> omezil počet uzlů XML, na které se filtr navštíví. Nepoužívejte výrazy XPath, jejichž výpočet může trvat dlouhou dobu, aniž by bylo nutné navštěvovat mnoho uzlů.

- Obecně platí, že při použití libovolné komponenty, která přijímá kvótu, je potřeba pochopit její vliv na zabezpečení a nastavit ji na bezpečnou hodnotu.

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Známé typy kontraktů dat](data-contract-known-types.md)
