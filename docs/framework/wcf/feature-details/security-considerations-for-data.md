---
title: Důležité informace o zabezpečení pro data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
author: BrucePerlerMS
ms.openlocfilehash: bf3276353473f07f58740a5819226994123efdcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201150"
---
# <a name="security-considerations-for-data"></a>Důležité informace o zabezpečení pro data
Při práci s daty ve Windows Communication Foundation (WCF), je nutné zvážit počet kategorií ohrožení. V následující tabulce jsou uvedeny nejdůležitější hrozby tříd, které se týkají zpracování dat. WCF poskytuje nástroje ke zmírnění těchto hrozeb.  
  
 Útok DoS  
 Při přijímání nedůvěryhodná data, může způsobit dat straně příjmu pro přístup k neúměrné množství různých zdrojů, jako je například paměť, vlákna, k dispozici připojení nebo cyklů procesoru způsobením zdlouhavé výpočty. Odmítnutí služby útok proti serveru mohou způsobit, že k chybě a nebudete moct zpracovávat zprávy od klientů, které legitimní.  
  
 Spuštění škodlivého kódu  
 Příchozí nedůvěryhodná data způsobí, že na přijímající stranu pro spuštění kódu, který ho neměli v úmyslu.  
  
 Zpřístupnění informací  
 Vzdálenému útočníkovi vynutí přijímající straně reagovat na jeho požadavky způsobem, který zpřístupnit víc informací, než se chystá.  
  
## <a name="user-provided-code-and-code-access-security"></a>Uživatelem zadaný kód a zabezpečení přístupu kódu  
 Počet míst v infrastruktuře Windows Communication Foundation (WCF) spustit kód, který se zadal uživatel. Například <xref:System.Runtime.Serialization.DataContractSerializer> Serializační stroj může třeba volat vlastnost uživatelem zadaný `set` přístupové objekty a `get` přistupující objekty. Infrastruktura WCF kanál může také volat do uživatelem zadaného odvozené třídy <xref:System.ServiceModel.Channels.Message> třídy.  
  
 Zodpovídá za kód autora zajistit, že neexistuje žádná ohrožení zabezpečení. Například pokud vytvoříte datový typ kontraktu s vlastností datový člen celočíselného typu a v `set` přistupující objekt implementace přidělit pole na základě hodnoty vlastnosti, vystavit možnosti útoku denial-of-service-li škodlivý zpráva obsahuje velmi velké hodnoty pro tento datový člen. Obecně se vyhýbejte rozdělení na základě příchozích dat nebo dlouhé zpracování uživatelského kódu (zejména v případě malé množství příchozích dat může být způsobena dlouhé zpracování). Při provádění analýzu zabezpečení z uživatelského kódu, nezapomeňte také zvážit všechny případy selhání (to znamená všechny kód pro větvení ve kterém jsou výjimky vyvolány).  
  
 Ultimate příklad uživatelského kódu je kód uvnitř vaší implementace služby pro každou operaci. Zabezpečení vaší implementace služby je vaší povinností. Je snadné neúmyslně vytvořit nezabezpečené operace implementace, které může vést k ohrožení zabezpečení s cílem odepření služby. Například operace, která přebírá řetězec a vrátí seznam zákazníků z databáze, jejichž název začíná tento řetězec. Pokud pracujete s velkými databázemi a řetězec předávaný je právě jedno písmeno, váš kód může pokusit vytvořit zprávu větší než všechny dostupné paměti, což způsobí selhání celé služby. ( <xref:System.OutOfMemoryException> Se nedá vrátit zpátky v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] což vždy vede k ukončení aplikace.)  
  
 Měli byste zajistit, že žádný škodlivý kód zapojené do elektrické zásuvky do různých bodů rozšiřitelnosti. To je obzvláště důležité, když spouštíte v částečném vztahu důvěryhodnosti, zpracování typů z částečně důvěryhodných sestavení nebo vytváření komponent použitelné částečně důvěryhodným kódem. Další informace najdete v tématu "Částečné důvěryhodnosti hrozby" v další části.  
  
 Poznámka: při spouštění v částečném vztahu důvěryhodnosti, infrastruktura serializaci smlouvy dat podporuje pouze omezené dílčí sady dat kontraktu programovacího modelu – například privátní členy dat nebo typy pomocí <xref:System.SerializableAttribute> atributu nejsou podporovány. Další informace najdete v tématu [částečném vztahu důvěryhodnosti](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Zabránit neúmyslnému informacím  
 Při navrhování Serializovatelné typy s ohledem na bezpečnost, přístup k informacím je možné žádný problém.  
  
 Vezměte v úvahu následující body:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Programovací model umožňuje možnost vidět data privátní a interní mimo tento typ nebo sestavení během serializace. Kromě toho mohou být vystaveny tvar typu při exportu schématu. Ujistěte se, že vysvětlení vašeho typu serializaci projekce. Pokud nechcete, aby něco vystavit, zakažte jeho serializace (například použitím není <xref:System.Runtime.Serialization.DataMemberAttribute> atribut v případě kontraktu dat).  
  
-   Mějte na paměti, že stejného typu může mít více serializaci projekce, v závislosti na serializátoru, který je používán. Stejný typ vystavuje jednu sadu dat při použití s <xref:System.Runtime.Serialization.DataContractSerializer> a další sadu dat při použití s <xref:System.Xml.Serialization.XmlSerializer>. Náhodně pomocí nesprávného serializátor může způsobit zpřístupnění informací.  
  
-   Použití <xref:System.Xml.Serialization.XmlSerializer> ve starší verzi vzdálené procedury volání (RPC) / kódovaného režimu může nechtěně vystavit tvar objektu grafu na straně odesílání na straně příjmu.  
  
## <a name="preventing-denial-of-service-attacks"></a>Prevence útoků s cílem odepření služeb  
  
### <a name="quotas"></a>Kvóty  
 Příčinou přijímající straně přidělit značné množství paměti je možný útok s cílem odepření služby. Zatímco tato část se soustřeďuje na problémy spotřeba paměti vyplývající z velkých zpráv, může dojít k dalším útokům. Zprávy mohou například použít nevyrovnaný objem doba zpracování.  
  
 Útoky s cílem odepření služeb jsou obvykle zmírnit použití kvót. Když dojde k překročení kvóty, <xref:System.ServiceModel.QuotaExceededException> obvykle je vyvolána výjimka. Bez kvót, škodlivých zpráv může způsobit všechnu dostupnou paměť přístup, což vede k <xref:System.OutOfMemoryException> výjimky nebo všechny dostupné balíčky přístupná, výsledkem <xref:System.StackOverflowException>.  
  
 Scénář – překročila se kvóta je obnovitelné; Jestliže ve spuštěné službě, je aktuálně zpracovávanou zprávu zahozena a stále spuštěný a zpracovávat další zprávy. Scénáře přetečení-paměti a zásobníku, ale nejsou obnovitelné kdekoli v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; služba ukončuje Pokud nalezne takové výjimky.  
  
 Kvóty ve službě WCF nezahrnují žádné předběžné přidělení. Například pokud <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kvóty (tuto možnost najdete na různé třídy) je nastavený na 128 KB, neznamená, že 128 KB je automaticky přidělena pro každou zprávu. Skutečná velikost přidělené závisí na skutečnou velikost příchozí zprávy.  
  
 Mnoho kvóty jsou k dispozici na transportní vrstvě. Jedná se o kvóty vynucuje konkrétní přenosový kanál používá (HTTP, TCP a tak dále). Když toto téma popisuje některé z těchto kvót, tyto kvóty jsou podrobně popsány v [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>Zatřiďovací tabulka ohrožení zabezpečení  
 Obsahuje chybu, když kontraktů dat obsahují zatřiďovací tabulky nebo kolekce. Tento problém nastane, pokud velký počet hodnot jsou vloženy do zatřiďovací tabulku kde generují velký počet těchto hodnot stejnou hodnotu hash. To může sloužit jako útok DOS.  Toto ohrožení zabezpečení je možné zmírnit tím, že nastavíte kvótu třídu MaxRecievedMessageSize vazby. Při nastavování této kvóty prevence takové útoky musí věnovat pozornost. Tato kvóta vloží horní limit velikosti zprávy WCF. Kromě toho Vyhněte se použití ve vašich smlouvách data zatřiďovací tabulky nebo kolekce.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Omezení využití paměti bez datových proudů  
 Model zabezpečení kolem velkých zpráv závisí na datové proudy, jestli se používá. V případě basic, Streamovat zprávy jsou ukládány do vyrovnávací paměti do paměti. V takovém případě použijte <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kvóta na <xref:System.ServiceModel.Channels.TransportBindingElement> nebo na vazeb poskytovaných systémem pro ochranu před velkých zpráv omezením maximální velikost zprávy pro přístup k. Všimněte si, že služba může zpracovávat více zpráv ve stejnou dobu, v takovém případě jsou všechny v paměti. Pomocí omezení funkce pro zmírnění této hrozby.  
  
 Všimněte si také, `MaxReceivedMessageSize` není stanovili horní mez využití paměti za zprávy, ale umožňuje omezuje v rámci faktor konstantní. Například pokud `MaxReceivedMessageSize` je 1 MB a doručení zprávy do 1 MB a potom deserializovat, další paměť vyžádáním tak, aby obsahovala deserializovaný objekt grafu, což vede k celkové paměti a využití více než 1 MB. Z tohoto důvodu se vyhněte se vytváření Serializovatelné typy, které by mohlo způsobit významné paměťové nároky bez množství příchozích dat. Například kontraktu dat "MyContract" s 50 volitelnými daty člena pole a další 100 privátní pole může být vytvořena s XML konstrukci "\<MyContract / >". Tato konfigurace XML výsledkem paměti používané pro 150 pole. Všimněte si, že datových členů jsou volitelné ve výchozím nastavení. Tento problém nastane, pokud takový typ je součástí pole.  
  
 `MaxReceivedMessageSize` samostatně nestačí k útokům odmítnutí služby. Například deserializátor může vynutit deserializovat graf hluboce vnořený objekt (objekt, který obsahuje jiný objekt, který obsahuje jeden další a tak dále) příchozí zprávy. Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> volat metody ve vnořených způsob, jak rekonstruovat těchto grafů. Hluboká vnoření volání metody může vést k neodstranitelné <xref:System.StackOverflowException>. Tuto hrozbu zmírnit nastavení <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> kvóty pro omezení úrovní vnoření XML, jak je popsáno v části "Pomocí XML bezpečně" dále v tomto tématu.  
  
 Nastavení na hodnotu dodatečných kvótách `MaxReceivedMessageSize` je zvlášť důležité při používání binárního kódování XML. Pomocí binárního kódování odpovídá nich do jisté míry komprese: malou skupinu bajtů v příchozí zprávě můžou představovat velké množství dat. Díky tomu se i zpráva zasazené do `MaxReceivedMessageSize` limit může trvat až mnohem větší množství paměti v podobě plně rozbalený. Ke zmírnění hrozeb. tyto specifické pro XML, všechny kvóty čtečky XML musí být nastavena správně, jak je popsáno v části "Pomocí XML bezpečně" dále v tomto tématu.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Omezení využití paměti se streamováním  
 Při vysílání datových proudů, můžete použít malé `MaxReceivedMessageSize` nastavení pro ochranu před útoky s cílem odepření služeb. Složitější scénáře jsou však možné díky streamování. Služba nahrávání souborů lze například soubory větší než všechnu dostupnou paměť. V takovém případě nastavte `MaxReceivedMessageSize` velmi velké hodnoty, očekává se, že skoro žádná data do vyrovnávací paměti v paměti a zpráva datové proudy přímo na disk. Pokud škodlivý zprávu můžete vynutit nějakým způsobem WCF vyrovnávací paměti pro data místo datových proudů v tomto případě `MaxReceivedMessageSize` už chrání proti zprávě přístup k všechnu dostupnou paměť.  
  
 Pro zmírnění této hrozby, existují kvóty specifická nastavení na různých komponent pro zpracování dat WCF tento limit ukládání do vyrovnávací paměti. Nejvýznamnější z nich je `MaxBufferSize` vlastnost u různých elementů přenosové vazby a standardní vazby. Při vysílání datových proudů, tato kvóta je třeba nastavit zohledněním maximální množství paměti, kterou jste ochotni přidělovat jednotlivým zprávy. Stejně jako u `MaxReceivedMessageSize`, nastavení nevystavuje absolutní maximální využití paměti, ale jenom na omezuje v rámci faktor konstantní. Také jako s `MaxReceivedMessageSize`, mějte na paměti možnost více zpráv zpracovávaných současně.  
  
### <a name="maxbuffersize-details"></a>Třída MaxBufferSize podrobnosti  
 `MaxBufferSize` Vlastnost omezuje žádné hromadné dělá WCF vyrovnávací paměti. Například WCF vždy vyrovnávacích pamětí hlavičky SOAP a chyb SOAP, jakož i všech částí MIME najít tak, aby nebyl v pořadí fyzická čtení ve zprávě zpráv přenosu optimalizace mechanismus (MTOM). Toto nastavení omezuje objem ukládání do vyrovnávací paměti ve všech těchto případech.  
  
 WCF toho dosahuje tím, že předáte `MaxBufferSize` hodnoty pro různé součásti, které může uložit do vyrovnávací paměti. Například některé <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> přetížení <xref:System.ServiceModel.Channels.Message> třídě `maxSizeOfHeaders` parametru. Předá WCF `MaxBufferSize` hodnotu tomuto parametru a omezit tak velikost záhlaví SOAP ukládání do vyrovnávací paměti. Je důležité při použití nastavte tento parametr <xref:System.ServiceModel.Channels.Message> třídy přímo. Obecně platí při použití komponenty ve službě WCF, která přebírá parametry kvót, je důležité, abyste pochopili důsledky zabezpečení tyto parametry a tyto hodnoty správně nastaveny.  
  
 Kodér MTOM zpráv má také `MaxBufferSize` nastavení. Při použití standardní vazby, automaticky je nastavené na úrovni přenosu `MaxBufferSize` hodnotu. Ale při použití element vazby kodér zprávy MTOM k vytvoření vlastní vazby, je důležité nastavit `MaxBufferSize` vlastnost na hodnotu bezpečné při streamování se používá.  
  
## <a name="xml-based-streaming-attacks"></a>Streamování útoky založenými na XML  
 `MaxBufferSize` samostatně nestačí k zajištění, že WCF nejde vynutit do ukládání do vyrovnávací paměti při streamování se očekává. Například čtečky WCF XML vždy vyrovnávací paměti celý počáteční značce elementu XML při spouštění číst nového elementu. To se provádí tak, že jsou správně zpracovány obory názvů a atributů. Pokud `MaxReceivedMessageSize` je nakonfigurovaný jako velké (například povolit velkých souborů přímo na disk streamování scénář), lze vytvořit škodlivé zprávy kde je obsah celé zprávy velké počáteční značky elementu XML. Pokus o čtení to vede <xref:System.OutOfMemoryException>. Toto je jeden z mnoha možných založený na formátu XML denial-of-service útoků, které můžete všechny možné zmírnit použití kvót čtečky XML, popsané v části "Pomocí XML bezpečně" dále v tomto tématu. Při vysílání datových proudů, je velmi důležité nastavit všechny tyto kvóty.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Kombinace streamování a ukládání do vyrovnávací paměti programovací modely  
 Mnoho možných útoků vzniknout při kombinování datových proudů a jiných datových proudů programovací modely ve stejné službě. Předpokládejme, že se kontrakt služby s dvě operace: jeden má <xref:System.IO.Stream> a jiné přijímá pole nějakého vlastního typu. Předpokládejme také, která `MaxReceivedMessageSize` je nastaven na velké hodnoty, aby první operaci pro zpracování velkých streamů. Bohužel to znamená, že velkých zpráv je nyní možné odesílat druhou operaci a deserializátor vyrovnávací paměť dat v paměti jako pole před voláním operace. Toto je možný útok s cílem odepření služby: `MaxBufferSize` kvóty neomezuje velikost těla zprávy, což je deserializátor funguje s.  
  
 Z tohoto důvodu se vyhněte kombinování operace na základě datového proudu a bez streamování v jednom kontraktu. Pokud je naprosto nutné kombinovat dvou programovacích modelů, pomocí následujících opatření:  
  
-   Vypnout <xref:System.Runtime.Serialization.IExtensibleDataObject> funkce tak, že nastavíte <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> k `true`. Tím se zajistí, že jsou pouze členy, které jsou součástí kontraktu deserializovat.  
  
-   Nastavte <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost <xref:System.Runtime.Serialization.DataContractSerializer> bezpečné hodnotu. Tato kvóta je také k dispozici na <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut nebo prostřednictvím konfigurace. Tato kvóta omezuje počet objektů, které jsou v jedné epizodě deserializace deserializovat. Za normálních okolností je v jedné epizodě deserializovat každá operace parametr nebo zprávy část textu v kontraktu zprávy. Při deserializaci pole každé položky pole se počítá jako samostatný objekt.  
  
-   Nastaví všechny kvóty čtečky XML bezpečné hodnoty. Věnujte pozornost <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, a <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> a vyhnout se řetězce v jiných datových proudů operace.  
  
-   Projděte si seznam známých typů, dodržujte při tom, že některý z nich může být vytvořena v okamžiku (viz oddíl "Zabránit neúmyslnému typy z načítání" dále v tomto tématu).  
  
-   Nepoužívejte žádné typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které velké množství dat ve vyrovnávací paměti. Tyto typy nepřidávejte do seznamu známých typů.  
  
-   Nepoužívejte <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> pole, <xref:System.Byte> pole nebo typy, které implementují <xref:System.Runtime.Serialization.ISerializable> v kontraktu.  
  
-   Nepoužívejte <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> pole, <xref:System.Byte> pole nebo typy, které implementují <xref:System.Runtime.Serialization.ISerializable> v seznamu známých typů.  
  
 Předchozí opatření použít, když operace Streamovat používá <xref:System.Runtime.Serialization.DataContractSerializer>. Nikdy Nekombinujte streamování a jiných datových proudů programování modely ve stejné službě používáte <xref:System.Xml.Serialization.XmlSerializer>, protože nemá ochranu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> kvóty.  
  
### <a name="slow-stream-attacks"></a>Pomalé Stream útoky  
 Třídy datových proudů útoky s cílem odepření služeb nezahrnuje využití paměti. Místo toho útoku zahrnuje pomalé odesílatele a příjemce dat. Při čekání na data, která mají být odeslány nebo přijaty, jsou vyčerpání prostředků, jako jsou k dispozici připojení a vlákna. Tato situace může nastat v důsledku napadením se zlými úmysly nebo z legitimní odesílatele a příjemce na pomalé síťové připojení.  
  
 Zmírnit tyto útoky, nastavte vypršení časových limitů přenosové správně. Další informace najdete v tématu [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Za druhé, nikdy nepoužívejte synchronní `Read` nebo `Write` operace při práci s datovými proudy ve službě WCF.  
  
## <a name="using-xml-safely"></a>Bezpečně pomocí XML  
  
> [!NOTE]
>  I když tato část se týká XML, informace platí také pro dokumenty JavaScript Object Notation (JSON). Kvóty fungují podobně, pomocí [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>Zabezpečení čtečky XML  
 Informační sada XML tento balíček je základem zpracování všechny zprávy ve službě WCF. Pokud existuje přijímá data XML z nedůvěryhodného zdroje, počet možností útoku s cílem odepření služby, který musí zmírnit. WCF obsahuje speciální, zabezpečte čtečky XML. Tyto čtenáři vytvářejí automaticky, když pomocí jedné z standardních kódování ve službě WCF (text, binary nebo MTOM).  
  
 Některé funkce zabezpečení na tyto čtenáři jsou vždy aktivní. Například čtecích zařízení nikdy Nezpracovávat definice typu dokumentu (DTD), které možným zdrojem útoky s cílem odepření služeb a nikdy by měly zobrazovat v legitimní zprávy protokolu SOAP. Další funkce zabezpečení zahrnují kvóty čtečky, které musí být nakonfigurované, které jsou popsány v následující části.  
  
 Při práci přímo s čtečky XML (například při psaní vlastních vlastní kodér, nebo při práci přímo s <xref:System.ServiceModel.Channels.Message> třídy), vždy používejte čtenáři zabezpečení WCF při pokusu o práci s nedůvěryhodná data. Vytvoření zabezpečené čtenáři volání jeden statický objekt pro vytváření přetížení metody <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, nebo <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> na <xref:System.Xml.XmlDictionaryReader> třídy. Při vytváření čtečky předávání hodnot zabezpečené kvóty. Nevolejte `Create` přetížení metody. Tyto nevytvářejte čtečku WCF. Místo toho se vytvoří čtečku, které nejsou chráněny funkce zabezpečení popsané v této části.  
  
### <a name="reader-quotas"></a>Čtečka kvóty  
 Zabezpečené čtečky XML mít pět konfigurovatelné kvóty. Nastavení se obvykle konfigurují pomocí `ReaderQuotas` vlastnost kódování prvků vazby nebo standardní vazby nebo pomocí <xref:System.Xml.XmlDictionaryReaderQuotas> objekt předán při vytváření čtečky.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Tato kvóta omezuje počet bajtů, které jsou pro čtení v jediném `Read` operace při čtení elementu start značku a její atributy. (V případech,-datovým proudem, se nepočítá samotný název elementu proti kvóty.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> je důležitá z následujících důvodů:  
  
-   Název elementu a jeho atributy jsou vždy posláním ve vyrovnávací paměti při jejich čtení. Proto je důležité, abyste správně nastavena tato kvóta v režimu, aby se zabránilo nadměrnému ukládání do vyrovnávací paměti při streamování se očekává datového proudu. Zobrazit `MaxDepth` kvóty části informace o skutečný objem ukládání do vyrovnávací paměti, které u něho.  
  
-   Máte příliš mnoho atributů XML může použít nepřiměřené doba zpracování, protože názvy atributů musí být vráceny jedinečný. `MaxBytesPerRead` omezuje tuto hrozbu.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Tato kvóta omezuje maximální hloubka vnoření elementů XML. Například dokument "\<A >\<B >\<C / >\</B >\</A >" má hloubka vnoření tři. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> je důležité z následujících důvodů:  
  
-   `MaxDepth` komunikuje se službou `MaxBytesPerRead`: čtecí modul dat vždy udržuje v paměti pro aktuální element a všechny jeho předchůdce, tak maximální velikost paměti spotřeba čtečky je úměrný tato dvě nastavení.  
  
-   Při deserializaci graf objektu nejhlouběji vnořená, deserializátor musí pro přístup k celý zásobník a vyvolat neodstranitelné <xref:System.StackOverflowException>. Mezi XML vnoření a objekt vnoření pro obě existuje přímou spojitost s míněním <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer>. Použití `MaxDepth` pro zmírnění této hrozby.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Tato kvóta na omezení velikosti čtenářovu *tabulky názvů*. Tabulka obsahuje některé řetězce (například obory názvů a předpony), jež byly objeveny při zpracování dokumentu XML. Protože tyto řetězce jsou ukládány do vyrovnávací paměti v paměti, nastavte tuto kvótu, aby se zabránilo nadměrnému ukládání do vyrovnávací paměti při streamování se očekává.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Tato kvóta omezení maximální velikost řetězce, který vrací čtecí funkce XML. Tato kvóta neomezuje využití paměti v samotné čtecí funkce XML, ale v komponentě, která používá čtecí modul. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> použije čtečku zabezpečený pomocí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, to není deserializaci řetězců větší než tuto kvótu. Při použití <xref:System.Xml.XmlDictionaryReader> třídy přímo, ne všechny metody dodržování tuto kvótu, ale pouze metody, které jsou vytvořené speciálně ke čtení řetězce, jako <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> metody. <xref:System.Xml.XmlReader.Value%2A> Vlastnost čtecího zařízení není ovlivněn tuto kvótu a neměl by tedy používat při protection poskytuje tato kvóta je nezbytné.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrací čtecí funkce XML, včetně pole bajtů. Tato kvóta neomezuje využití paměti v samotné čtecí funkce XML, ale v libovolné součásti, která používá čtecí modul. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> použije čtečku zabezpečený pomocí <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, není ji deserializovat bajtová pole větší než tuto kvótu. Je důležité nastavit této kvóty při pokusu o kombinovat datových proudů a ve vyrovnávací paměti programovacích modelů v jeden kontrakt. Mějte na paměti, že při použití <xref:System.Xml.XmlDictionaryReader> třídy přímo, pouze metody, které jsou vytvořené speciálně pro čtení pole libovolné velikosti určité primitivní typy, jako například <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, nerespektují tuto kvótu.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>Hrozby konkrétní binární kódování  
 Binární kódování WCF podporuje XML obsahuje *slovníku řetězce* funkce. Velký řetězec může být kódovaný pomocí jenom pár bajtů. To umožňuje významného zvýšení výkonu, ale zavádí nové hrozby s cílem odepření služeb, které musí být zmírnit.  
  
 Existují dva druhy slovníky: *statické* a *dynamické*. Statické slovník je integrovaný seznam dlouhé řetězce, které mohou být zastoupeny pomocí krátký kód v binární kódování. Tento seznam řetězců vyřešen, když čtečka je vytvořen a nelze ji změnit. Žádný z řetězce ve statickém slovníku, který ve výchozím nastavení používá WCF není dostatečně velký, aby představovat závažné ohrožení denial-of-service, i když mohou být stále používány v slovníkový útok rozšíření. V pokročilých scénářích, kde zadáte vlastní statickém slovníku buďte opatrní při zavádění velké slovníku řetězce.  
  
 Funkce dynamické slovníky umožňuje zprávy k definování vlastní řetězce a přidružit krátké kódy. Tato mapování řetězec kódu jsou uloženy v paměti během relace celé komunikace tak, aby následné zprávy není nutné znovu odeslat řetězce a může využívat kódy, které jsou již definovány. Tyto řetězce můžou být libovolné délky a tedy představovat hrozbu závažnější než ty, které ve statickém slovníku.  
  
 První, který musí být zmírnit hrozby je možnost je dynamický slovník (tabulka mapování řetězec kódu), příliš velká. Tento slovník může rozšířit v průběhu několika zprávy a proto `MaxReceivedMessageSize` kvóty nenabízí žádnou ochranu, protože se vztahuje pouze na každou zprávu samostatně. Proto samostatné <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> na existuje vlastnost <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , která omezuje velikost slovníku.  
  
 Na rozdíl od většiny jiných kvóty tuto kvótu platí i v případě zápis zpráv. Pokud je překročena při čtení zprávy, `QuotaExceededException` je vyvolána jako obvykle. Pokud je překročena při zápisu zprávy, jako jsou zapsány všechny řetězce, které způsobí překročení kvóty – bez použití funkce dynamické slovníky.  
  
### <a name="dictionary-expansion-threats"></a>Slovník rozšíření hrozby  
 Významné třídy specifické pro binární soubor útoků vyplývá z rozšíření slovníku. Krátké zprávy v binárním formátu může proměnit velmi objemné zprávy v textové formě plně rozšířené Pokud velké míře využívá funkce slovníky řetězec. Faktor rozšíření pro dynamický slovník řetězce je omezená <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> kvóty, protože žádný dynamický slovník řetězec je větší než maximální velikost celého slovníku.  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, A `MaxArrayLength` vlastnosti pouze omezit spotřebu paměti. Jsou obvykle není nutné ke zmírnění hrozeb. jakékoli využití datovým proudem, protože využití paměti je již omezena `MaxReceivedMessageSize`. Ale `MaxReceivedMessageSize` počítá předběžné rozšíření bajtů. Pokud binární kódování se používá, využití paměti může potenciálně jít dál `MaxReceivedMessageSize`, je omezen pouze faktorem <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Z tohoto důvodu je důležité vždy nastavit všechny kvóty reader (zejména <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) při používání binárního kódování.  
  
 Při použití společně s binárního kódování <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` rozhraní může být potenciálně nebezpečného připojit slovníkový útok rozšíření. Toto rozhraní poskytuje v podstatě neomezené úložiště pro libovolná data, která není součástí kontraktu. Pokud nelze nastavit kvóty dostatečně nízko tak, aby `MaxSessionSize` vynásobené `MaxReceivedMessageSize` nemá představovat problém, zakažte `IExtensibleDataObject` funkce při používání binárního kódování. Nastavte `IgnoreExtensionDataObject` vlastnost `true` na `ServiceBehaviorAttribute` atribut. Případně, Neimplementujte `IExtensibleDataObject` rozhraní. Další informace najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Souhrn kvóty  
 Následující tabulka shrnuje pokyny kvóty.  
  
|Podmínka|Důležité kvóty pro nastavení|  
|---------------|-----------------------------|  
|Žádné datové proudy nebo datových proudů malých zpráv, text nebo kódování MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead`, a `MaxDepth`|  
|Žádné datové proudy nebo datových proudů malých zpráv, binární kódování|`MaxReceivedMessageSize`, `MaxSessionSize`a vše `ReaderQuotas`|  
|Streamování velkých zpráv, text nebo kódování MTOM|`MaxBufferSize` a vše `ReaderQuotas`|  
|Streamování velkých zpráv binární kódování|`MaxBufferSize`, `MaxSessionSize`a vše `ReaderQuotas`|  
  
-   Vypršení časových limitů transportní vrstvy musí být vždycky nastavená a nikdy nepoužívejte synchronního čtení/zápisy při streamování se používá, bez ohledu na to, zda jsou datové proudy velké nebo malé zprávy.  
  
-   Pokud máte pochybnosti o kvótu, nastavte ji na hodnotu bezpečné místo zároveň je nechává otevřené.  
  
## <a name="preventing-malicious-code-execution"></a>Zabránit spuštění škodlivého kódu  
 Následující obecné třídy hrozeb můžete spustit kód a mít nežádoucí účinky:  
  
-   Deserializátor načte typ škodlivý, nebezpečné nebo citlivé na zabezpečení.  
  
-   Příchozí zpráva způsobí, že deserializátor k vytvoření instance typu obvykle bezpečné takovým způsobem, který má nežádoucí důsledky.  
  
 Následující části popisují tyto třídy další hrozby.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Pro informace o zabezpečení <xref:System.Xml.Serialization.XmlSerializer>, najdete v příslušné dokumentaci od.) Model zabezpečení pro <xref:System.Xml.Serialization.XmlSerializer> je podobná <xref:System.Runtime.Serialization.DataContractSerializer>a liší se většinou v podrobnostech. Například <xref:System.Xml.Serialization.XmlIncludeAttribute> atribut se používá pro zahrnutí typ místo <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut. Nicméně některé hrozby jedinečné pro <xref:System.Xml.Serialization.XmlSerializer> jsou popsány dále v tomto tématu.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>Ochrana proti neúmyslnému typů nejde načíst  
 Načítání typů neúmyslnému může mít závažné důsledky, zda typ se zlými úmysly nebo právě má vedlejší účinky, citlivé na zabezpečení. Typ může obsahovat ohrožení zabezpečení zneužitelné, provádět akce citlivé na zabezpečení v jeho konstruktor nebo konstruktor třídy, mají velké paměť, která usnadňuje útoky s cílem odepření služeb, nebo může vyvolat výjimky neobnovitelná. Typy mohou mít konstruktor třídy, na kterých běží jako typ načíst a před všechny instance jsou vytvořeny. Z těchto důvodů je potřeba sada typů, které může načíst deserializátor ovládacích prvků.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Deserializuje volně způsobem. Nikdy načte common language runtime (CLR) typ a sestavení názvy z příchozích dat. To se podobá chování <xref:System.Xml.Serialization.XmlSerializer>, ale liší se od chování <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Volné párování představuje určitý stupeň zabezpečení, protože vzdálenému útočníkovi nesmí uvádět libovolného typu načíst jenom pojmenováním typu ve zprávě.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Vždy může načíst typ, který je aktuálně očekávání podle smlouvy. Například, pokud kontrakt dat má datový člen typu `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> může načíst `Customer` zadejte při deserializuje tomuto datovému členu.  
  
 Kromě toho <xref:System.Runtime.Serialization.DataContractSerializer> podporuje polymorfismus. Datový člen mohou být deklarovány jako <xref:System.Object>, ale mohou obsahovat příchozích dat `Customer` instance. To je možné pouze tehdy, pokud `Customer` typ byl proveden "známé" deserializátor prostřednictvím jednoho z těchto mechanismů:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut použité u typu.  
  
-   `KnownTypeAttribute` atribut určení metodu, která vrátí seznam typů.  
  
-   `ServiceKnownTypeAttribute` atribut.  
  
-   `KnownTypes` Konfigurační oddíl.  
  
-   Seznam známých typů explicitně předán <xref:System.Runtime.Serialization.DataContractSerializer> během konstrukce, pokud používáte serializátoru, který je přímo.  
  
 Každá z těchto mechanismů zvyšuje zavedením další typy, které můžete načíst deserializátor. Řídit každou z těchto mechanismů, ujistěte se, že žádné škodlivého nebo nežádoucího typy jsou přidány do seznamu známých typů.  
  
 Jakmile známý typ v rozsahu, je možné načíst kdykoli a nelze vytvořit instance daného typu, i v případě, že kontrakt zakazuje jejího použití. Předpokládejme například, typ, který "MyDangerousType" je přidána do seznamu známých typů pomocí jedné z výše uvedených mechanismů. To znamená, že:  
  
-   `MyDangerousType` je načten a jeho spuštěním konstruktoru třídy.  
  
-   I v případě, že deserializaci kontraktu dat s datovým členem řetězec škodlivých zpráv může způsobit stále instance `MyDangerousType` vytvořit. Kód v `MyDangerousType`, jako je například vlastnost setter může spustit. Po dokončení, pokusí se deserializátor přiřazení této instance na datový člen řetězec a neúspěšné a zobrazí se výjimka.  
  
 Při zápisu metodu, která vrátí seznam známých typů nebo při předávání přímo do seznamu <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, zajistěte, aby kód, který připraví seznamu je zabezpečená a pracuje jenom důvěryhodná data.  
  
 Při zadání známých typů v konfiguraci, ujistěte se, že je konfigurační soubor zabezpečení. Vždy používat silné názvy v konfiguraci (zadáním veřejného klíče podepsané sestavení, ve které se nachází typ), ale neurčují verzi typ, který chcete načíst. Zavaděč typ automaticky vybere nejnovější verze, pokud je to možné. Pokud chcete zadat konkrétní verzi v konfiguraci, spusťte následující rizika: Typ může mít ohrožení zabezpečení, který může být stanovena v budoucí verzi, ale verze stále načítá, protože je explicitně zadaná v konfiguraci.  
  
 Příliš mnoho známých typů má jiné důsledkem: <xref:System.Runtime.Serialization.DataContractSerializer> vytvoří mezipaměť kódu pro serializaci nebo deserializaci v doméně aplikace, s položkou pro každý typ musí serializovat a deserializovat. Tato mezipaměť se nikdy vymaže tak dlouho, dokud běží v doméně aplikace. Útočník, který si je vědoma, že aplikace používá mnoho známé typy proto může způsobit deserializace všechny tyto typy, což způsobí mezipaměti využívat nepřiměřeně velké množství paměti.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>Znemožňuje uvolnění typy v nežádoucího stavu  
 Typ může mít interní konzistence omezení, které se musí vynutit. Aby se zabránilo přerušení těchto omezení během deserializace musí věnovat pozornost.  
  
 Následující příklad typu představuje stav přetlakové komory na kosmické lodě a vynucuje omezení, že vnitřní a vnější dveře nejde otevřít ve stejnou dobu.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Útočník může odesílat škodlivé zpráva přibližně následujícího znění, navigace omezení a že načtete objekt do neplatného stavu, který může mít neočekávané a nežádoucí důsledky.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Tato situace se můžete vyhnout tím, že je seznámen následující body:  
  
-   Když <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje Většina tříd, konstruktory se nespustí. Proto není závislý na libovolný stav správy provedena v rámci konstruktoru.  
  
-   Použijte zpětná volání tak, aby byl objekt v platném stavu. Zpětné volání označené <xref:System.Runtime.Serialization.OnDeserializedAttribute> atribut je zvlášť užitečné, protože běží po deserializaci je kompletní a má možnost k prozkoumání a opravy celkového stavu. Další informace najdete v tématu [tolerantní zpětná volání serializace](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Nenavrhujte typy kontraktů dat spoléhat na všechny konkrétní pořadí, ve kterých se vlastnosti musí být volána funkce setter.  
  
-   Je třeba dbát pomocí starší verze typů označené <xref:System.SerializableAttribute> atribut. Mnohé z nich byly navrženy pro práci s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálené komunikace pro použití s jenom důvěryhodná data. Existující typy označené tento atribut nemusí byly navrženy s stavu zabezpečení v úvahu.  
  
-   Nespoléhejte na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost `DataMemberAttribute` atribut zajistit přítomnost data, co se týče stavu zabezpečení. Data mohou být vždy `null`, `zero`, nebo `invalid`.  
  
-   Nikdy důvěryhodnosti grafu objektů v daném kontextu deserializovat zdroj nedůvěryhodná data bez ověřování se nejdřív. Každého jednotlivého objektu může být v konzistentním stavu, ale graf objektu jako celek nesmí být. Kromě toho i v případě režimu zachování graf objektu je zakázané, deserializovat graf může mít více odkazů na stejný objekt nebo mít cyklické odkazy. Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>Bezpečně používat NetDataContractSerializer  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> Je Serializační stroj, který používá určitou úzkou svázanost na typy. Podobá se to <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. To znamená, určuje, jaký typ pro vytvoření instance načtením [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvů typů a sestavení z příchozí data. I když je součástí WCF, není nijak zadaný zapojení Tato serializační stroj; vlastní kód musí být napsané. `NetDataContractSerializer` Slouží především pro usnadnění migrace z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting do WCF. Další informace najdete v příslušné části v [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Protože vlastní zprávě může znamenat libovolného typu je možné načíst, <xref:System.Runtime.Serialization.NetDataContractSerializer> mechanismus je ze své podstaty nezabezpečené a by měla sloužit pouze dodávat důvěryhodná data. Je možné zabezpečit napsáním vazač zabezpečené a omezením typu typ, který umožňuje načíst pouze bezpečné typů (pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> vlastnost).  
  
 I v případě, že se používá pro důvěryhodného data, příchozí data můžou nedostatečně určovat typ, který chcete načíst, zejména v případě, <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> je nastavena na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Každý, kdo má přístup do adresáře aplikace nebo do globální mezipaměti sestavení můžete nahradit typem škodlivý místo ten, který se má načíst. Vždy zajistěte zabezpečení adresáře aplikace a globální mezipaměti sestavení správně nastavením oprávnění.  
  
 Obecně platí, že pokud je povoleno částečně důvěryhodným kódem přístup k vaší `NetDataContractSerializer` instance nebo jinak kontrolujete náhradní selektor (<xref:System.Runtime.Serialization.ISurrogateSelector>) nebo vazač serializace (<xref:System.Runtime.Serialization.SerializationBinder>), kód může vykonávat spoustu ovládací prvek průběhu procesu serializaci nebo deserializaci. Například to může vložit libovolné typy, způsobit zpřístupnění informací, manipulovat s Výsledný graf objektu nebo serializovaná data nebo přetečení výsledná serializovaného datového proudu.  
  
 Jiné potíže se zabezpečením s `NetDataContractSerializer` je útok DOS, není provádění hrozbu škodlivý kód. Při použití `NetDataContractSerializer`vždy nastavte <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kvótu pro bezpečné hodnotu. Je snadné vytvořit malé škodlivý zprávu, která přiděluje pole objektů, jejichž velikost je omezena pouze této kvóty.  
  
### <a name="xmlserializer-specific-threats"></a>XmlSerializer specifické hrozby  
 <xref:System.Xml.Serialization.XmlSerializer> Model zabezpečení je podobná <xref:System.Runtime.Serialization.DataContractSerializer>. Několik hrozby, ale jsou jedinečné pro <xref:System.Xml.Serialization.XmlSerializer>.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Generuje *sestavení serializace* za běhu, které obsahují kód, který ve skutečnosti serializuje a deserializuje; tato sestavení se vytvářejí v adresáři dočasné soubory. Pokud některé procesu nebo uživatel nemá přístupová práva do tohoto adresáře, se může přepsat serializaci/deserializaci kódu pomocí libovolného kódu. <xref:System.Xml.Serialization.XmlSerializer> Pak spustí tento kód namísto kódu pro serializaci nebo deserializaci pomocí kontext zabezpečení. Ujistěte se, že oprávnění jsou nastavené správně na adresáře dočasných souborů k tomu nedocházelo.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Má také režim, ve kterém použije místo aby generovala za běhu serializace předem generovaného sestavení. Tento režim se aktivuje vždy, když <xref:System.Xml.Serialization.XmlSerializer> najdete vhodné serializace sestavení. <xref:System.Xml.Serialization.XmlSerializer> Kontroly, zda byl podepsán sestavení serializace pomocí stejného klíče, který se použil k podepsání sestavení obsahující typy serializována. To nabízí ochranu ze škodlivých sestavení se maskovaný jako sestavení serializace. Ale pokud je sestavení obsahující Serializovatelné typy není podepsaná, <xref:System.Xml.Serialization.XmlSerializer> nemůže provést tuto kontrolu a ten se správným názvem používá žádné sestavení. To umožňuje spuštění škodlivého kódu. Vždy podepsat sestavení, které obsahují Serializovatelné typy nebo důsledně řídit přístup k adresáři vaší aplikace a mezipaměti globálního sestavení tak, aby zabránila zavlečení škodlivého sestavení.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Můžou podléhat útoku DOS. <xref:System.Xml.Serialization.XmlSerializer> Nemá `MaxItemsInObjectGraph` kvóty (tak, jak jsou k dispozici na <xref:System.Runtime.Serialization.DataContractSerializer>). Díky tomu se deserializuje libovolné množství objektů jediným omezením velikosti zprávy.  
  
### <a name="partial-trust-threats"></a>Hrozby s částečnou důvěryhodností  
 Mějte na paměti následující aspekty týkající se hrozeb týkající se kód s částečnou důvěryhodností. Tyto hrozby obsahovat škodlivé částečně důvěryhodným kódem, jakož i škodlivý částečně důvěryhodným kódem v kombinaci s další scénáře útoků (například částečně důvěryhodným kódem, který vytvoří konkrétní řetězec a potom deserializaci).  
  
-   Při použití součásti žádné serializace, nikdy uplatnit žádná oprávnění než použití, i v případě, že scénář celá serializace je v rámci oboru vaše kontrolní výraz a nezabýváte se všech nedůvěryhodná data nebo objekty. Použití může vést k ohrožení zabezpečení.  
  
-   V případech, kdy částečně důvěryhodným kódem má kontrolu nad procesu serializace, buď prostřednictvím bodů rozšiřitelnosti (náhrady), typy serializována, nebo jiným způsobem může způsobit částečně důvěryhodným kódem serializátor pro výstup velké množství data v serializovaném proudu, který může způsobit odepření služby (DoS) k příjemci tento datový proud. Pokud serializujete data určená pro cíl, který je citlivý na ně DoS, serializaci částečně důvěryhodné typy nebo jinak umožní serializace ovládacího prvku částečně důvěryhodným kódem.  
  
-   Pokud je povoleno částečně důvěryhodným kódem přístup k vaší <xref:System.Runtime.Serialization.DataContractSerializer> instance nebo jinak kontrolujete [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), uplatnit velkou kontrolu nad procesu serializace/deserializace. Například to může vložit libovolné typy, způsobit zpřístupnění informací, manipulovat s Výsledný graf objektu nebo serializovaná data nebo přetečení výsledná serializovaného datového proudu. Ekvivalentní <xref:System.Runtime.Serialization.NetDataContractSerializer> hrozeb je popsaný v části "Použití NetDataContractSerializer bezpečně".  
  
-   Pokud <xref:System.Runtime.Serialization.DataContractAttribute> atributu je použité u typu (nebo typ označen jako `[Serializable]` , ale není `ISerializable`), deserializátor může vytvořit instanci takového typu, i v případě, že všechny konstruktory jsou privátní nebo chráněné podle požadavků.  
  
-   Nikdy nepředpokládejte výsledek deserializace, pokud data k deserializaci není důvěryhodný a jste si jisti, že všechny známé typy jsou typy, které důvěřujete. Všimněte si, že známých typů nejsou načtené z konfiguračního souboru aplikace (však jsou načteny z konfiguračního souboru počítače) při spouštění v částečném vztahu důvěryhodnosti.  
  
-   Pokud předáte `DataContractSerializer` instanci s náhradní přidán do částečně důvěryhodným kódem, kód můžete změnit lze měnit nastavení na této náhradní.  
  
-   Deserializovaný objekt Pokud čtecí funkce XML (nebo data v něm) pochází z částečně důvěryhodného kódu, považovat za výsledný objekt deserializovaný nedůvěryhodná data.  
  
-   Fakt, který <xref:System.Runtime.Serialization.ExtensionDataObject> typ nemá žádné veřejné členy neznamená, že data v něm jsou zabezpečená. Například pokud jste ze zdroje dat privileged deserializovat do objektu, ve kterém některá data se nachází, pak ručně, tento objekt částečně důvěryhodným kódem, částečně důvěryhodným kódem můžete číst data v `ExtensionDataObject` o serializaci objektu. Zvažte nastavení <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> k `true` při deserializaci na objekt, který je pozdější ze zdroje dat privileged předán částečně důvěryhodným kódem.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporují serializaci privátní, chráněné, interní a veřejné členy v úplném vztahu důvěryhodnosti. Nicméně v částečném vztahu důvěryhodnosti pouze veřejné členy lze serializovat. A `SecurityException` je vyvolána, pokud se aplikace pokusí serializovat neveřejný člen.  
  
     Povolit interní nebo chráněné členy interní se musí serializovat v částečném vztahu důvěryhodnosti, použijte `System.Runtime.CompilerServices.InternalsVisibleTo` atribut sestavení. Tento atribut umožňuje sestavení, které chcete-li deklarovat, že její interní členy jsou viditelné pro některé sestavení. V takovém případě sestavení, které chce mít jeho vnitřní členy serializovat deklaruje, že její interní členy jsou viditelné pro System.Runtime.Serialization.dll.  
  
     Výhodou tohoto přístupu je, že nevyžaduje cestu k generování kódu se zvýšenými oprávněními.  
  
     Ve stejnou dobu existují dvě hlavní nevýhody.  
  
     První nevýhodou je, že vlastnost opt-in z `InternalsVisibleTo` atribut je celé sestavení. To znamená nelze zadat, že pouze určité třída může mít jeho vnitřní členy serializovat. Samozřejmě stále můžete není určená k serializaci konkrétní vnitřní člen, stačí přidat není `DataMember` atribut pro tohoto člena. Podobně vývojář můžete také zvolit, jestli členem interní místo soukromé nebo chráněné, se týká mírné viditelnost.  
  
     Druhý nevýhodou je, že stále nepodporuje soukromé nebo chráněné členy.  
  
     Pro ilustraci použití `InternalsVisibleTo` atribut v částečném vztahu důvěryhodnosti, vezměte v úvahu následující program:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     V příkladu výše `PermissionsHelper.InternetZone` odpovídá `PermissionSet` pro částečnou důvěryhodností. Nyní, bez `InternalsVisibleToAttribute`, aplikace selže, vyvolání `SecurityException` označující, že neveřejné členy nejde serializovat v částečném vztahu důvěryhodnosti.  
  
     Nicméně pokud jsme do zdrojového souboru přidejte následující řádek, program se úspěšně spustí.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Další aspekty správy stavu  
 Několik obavy týkající se správy stavu objektů jsou za zmínku:  
  
-   Pokud používáte model programování podle datového proudu streamování přenosu, zpracování zprávy dochází při doručení zprávy. Odesílatel zprávy se může přerušit operace odeslání uprostřed datový proud a ponechání kódu v nepředvídatelném stavu, pokud byla očekávána další obsah. Obecně platí, nespoléhejte na datový proud je kompletní a neprovádějte žádnou práci v rámci operace na základě datového proudu, který se nedá vrátit zpět v případě, že datový proud byl přerušen. To platí i pro situace, ve kterém zprávy mohou být poškozené za tělem streamování (například ho pravděpodobně chybí koncová značka pro obálku protokolu SOAP nebo může mít druhý text zprávy).  
  
-   Použití `IExtensibleDataObject` funkce může způsobit, že citlivá data, aby byly vypuštěny. Pokud přijímáte data z nedůvěryhodného zdroje do kontrakty dat s `IExtensibleObjectData` a později znovu generování ho na zabezpečený kanál, ve kterém jsou podepsané zprávy, můžete se potenciálně ručící za nic vědět o data. Celkový stav, který odesíláte kromě toho může být neplatný, pokud jste známými i neznámými časti dat vezměte v úvahu. Nastavením buď selektivně rozšíření dat vlastnosti této situaci zabránili `null` nebo selektivně vypnutí `IExtensibleObjectData` funkce.  
  
## <a name="schema-import"></a>Import schématu  
 Za normálních okolností proces import schématu pro generování typů dojde pouze v době návrhu, například při použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na webové služby sloužící ke generování třídy klienta. V pokročilejších scénářích, ale může zpracovat schématu v době běhu. Mějte na paměti, že to můžete zveřejnit můžete na riziko, s cílem odepření služby. Některé schéma může trvat dlouhou dobu, které se mají naimportovat. Nikdy nepoužívejte <xref:System.Xml.Serialization.XmlSerializer> komponenty import schématu v takových scénářích pokud schémata pravděpodobně pochází z nedůvěryhodného zdroje.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Hrozby specifické pro integraci technologie ASP.NET AJAX  
 Když uživatel implementuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> nebo <xref:System.ServiceModel.Description.WebHttpBehavior>, WCF zpřístupňuje koncový bod, který může přijmout zprávy XML a JSON. Je však pouze jednu sadu kvóty čtečky, používají čtecí funkce XML a čtečky JSON. Některá nastavení kvóty může být vhodné pro jeden Čtenář, ale příliš velký pro ostatní.  
  
 Při implementaci `WebScriptEnablingBehavior`, uživatel má povolenou možnost k vystavení proxy server JavaScript v koncovém bodě. Musí přestat považovat následující problémy se zabezpečením:  
  
-   Informace týkající se služby (názvy operace, názvy parametrů a tak dále) můžete získat prozkoumáním proxy server JavaScript.  
  
-   Při použití koncového bodu jazyka JavaScript, citlivé a soukromé informace může uchovávat v mezipaměti webového prohlížeče klienta.  
  
## <a name="a-note-on-components"></a>Poznámka: pro komponenty  
 WCF je systém flexibilní a přizpůsobitelné. Většina obsahu v tomto tématu se soustředí na nejběžnějších scénářů využití WCF. Je však možné kombinovat komponenty, které poskytuje WCF mnoha různými způsoby. Je důležité si uvědomit důsledky zabezpečení pomocí jednotlivých komponent. Zejména:  
  
-   Pokud je nutné použít čtečky XML, použijte čtecích zařízení <xref:System.Xml.XmlDictionaryReader> třída poskytuje na rozdíl od jinými čtenáři. Bezpečné čtenáři se vytvoří s použitím <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, nebo <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> metody. Nepoužívejte <xref:System.Xml.XmlReader.Create%2A> metody. Vždy nakonfigurujte bezpečné kvóty čtecích zařízení. Serializace moduly ve službě WCF jsou zabezpečené jenom při použití s zabezpečené čtečky XML z WCF.  
  
-   Při použití <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci potenciálně nedůvěryhodná data, vždycky nastavený <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost.  
  
-   Při vytváření zprávy, nastavte `maxSizeOfHeaders` parametr Pokud `MaxReceivedMessageSize` nenabízí dostatek ochrany.  
  
-   Při vytváření kodéru, vždy nakonfigurovat příslušné kvóty, jako jsou například `MaxSessionSize` a `MaxBufferSize`.  
  
-   Pokud používáte filtr XPath zprávy, nastavte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> a omezit tak množství filtr návštěv z uzlů XML. Nepoužívejte výrazy XPath, které může trvat dlouhou dobu compute, aniž byste museli navštívit mnoha uzly.  
  
-   Obecně platí při použití jakékoli součásti, která přijímá kvótu, pochopit jeho vliv na zabezpečení a nastavte ho na bezpečné hodnotu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
