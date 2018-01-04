---
title: "Důležité informace o zabezpečení pro data"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bb7a40bc38a3fdf3f7be2b31e30e768e26be2d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-data"></a>Důležité informace o zabezpečení pro data
Při plánování práce s daty v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je nutné zvážit mnoho kategorií hrozeb. Následující tabulka uvádí nejdůležitější třídy hrozeb, které se vztahují ke zpracování dat. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje nástroje ke zmírnění tyto hrozby.  
  
 Odmítnutí služby  
 Při přijetí nedůvěryhodných dat, může způsobit data straně příjmu pro přístup k nesoustředil příliš velký objem různé prostředky, například paměť, vláken, dostupná připojení nebo cyklů procesoru tím, že na zdlouhavé výpočty. Odmítnutí služby útoku proti serveru může způsobit havárií, a nebude možné zpracovat zprávy od klientů, které legitimní.  
  
 Spuštění škodlivého kódu  
 Příchozí data nedůvěryhodné způsobí, že ke spuštění kód, který nechtěli na straně příjmu.  
  
 Zpřístupnění informací  
 Vzdálenému útočníkovi vynutí přijímající strany reagovat na jeho požadavky v tak, aby poskytnout další informace, než má v úmyslu.  
  
## <a name="user-provided-code-and-code-access-security"></a>Zadaný uživatelem kódu a zabezpečení přístupu kódu  
 Počet míst v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury spustit kód, který je zadané uživatelem. Například <xref:System.Runtime.Serialization.DataContractSerializer> serializace modul může volat zadaný uživatelem vlastnost `set` přístupové objekty a `get` přistupující objekty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanál infrastruktura může také volání do zadaný uživatelem odvozené třídy <xref:System.ServiceModel.Channels.Message> třídy.  
  
 Je zodpovědností kódu Autor zajistit, že neexistují žádné chyby zabezpečení. Například pokud vytvoříte kontraktů dat typ s vlastností člena data typu integer a v `set` přistupujícího objektu implementace přidělit pole na základě hodnoty vlastnosti, pokud škodlivý vystavit možnosti útoku odmítnutí služby zpráva obsahuje velmi velké hodnoty pro tento člen data. Obecně platí vyhněte rozdělení podle příchozích dat nebo dlouhé zpracování v kódu zadaný uživatelem (Pokud zvlášť zdlouhavé zpracování může být způsobeno malé množství příchozích dat). Při provádění analýzu zabezpečení zadaný uživatelem kódu, ujistěte se, že jste také vzít v úvahu všechny případy selhání (to znamená, že všechny kód větve kde jsou výjimky vyvolány).  
  
 Ultimate příklad kódu zadaný uživatelem je kód uvnitř vaší implementace služby pro každou operaci. Zabezpečení vaší implementace služby je vaší povinností. Je snadné vytvořit nechtěně nezabezpečené operace implementací, které může vést k ohrožení zabezpečení denial of service. Například operace, která přebírá řetězec a vrátí do seznamu zákazníků z databáze, jejichž název začíná tento řetězec. Pokud pracujete s velké databáze a řetězec předávány je právě jedním písmenem, kódu pokusu o vytvoření zprávy větší než všechny dostupné paměti, způsobuje selhání celé služby. ( <xref:System.OutOfMemoryException> Není použitelná pro obnovení v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] a vždy výsledkem ukončení aplikace.)  
  
 Ujistěte se, že žádný škodlivý kód je připojen do různých body rozšiřitelnosti. To je obzvláště důležité, při spuštění v částečné důvěryhodnosti, plánování práce s typy z částečně důvěryhodného sestavení nebo vytváření použitelné součásti částečně důvěryhodný kód. Další informace najdete v tématu "Částečné důvěryhodnosti hrozby" v další části.  
  
 Poznámka: při spuštění v částečné důvěryhodnosti, infrastruktura serializace kontraktu dat podporuje pouze omezenou podmnožinou dat kontrakt programovacího modelu – například private členy nebo typy pomocí <xref:System.SerializableAttribute> atribut nejsou podporovány. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Částečnou důvěryhodností](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Zamezení neúmyslnému přístup k informacím  
 Při navrhování Serializovatelné typy s důrazem na bezpečnost, zpřístupnění informací je možné problémy.  
  
 Mějte na paměti následující body:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Programovací model umožňuje úniku privátní a interní data mimo typ nebo sestavení během serializace. Kromě toho mohou být zpřístupněny obrazce typu během exportu schématu. Ujistěte se, že pochopení vašeho typu serializaci projekce. Pokud nechcete, aby nic vystavený, zakázat jeho serializace (například použitím není <xref:System.Runtime.Serialization.DataMemberAttribute> atribut v případě kontraktu dat).  
  
-   Upozorňujeme, že stejný typ může mít několik serializaci projekce, v závislosti na serializátoru, který je používán. Stejný typ vystavuje jednu sadu dat při použití s <xref:System.Runtime.Serialization.DataContractSerializer> a jinou sadu dat při použití s <xref:System.Xml.Serialization.XmlSerializer>. Omylem pomocí nesprávného serializátor může vést ke zpřístupnění informací.  
  
-   Pomocí <xref:System.Xml.Serialization.XmlSerializer> v postupu starší verze vzdáleného volání (RPC) / kódovaného režimu může neúmyslně vystavit obrazec grafu objektu na straně odesílání na straně příjmu.  
  
## <a name="preventing-denial-of-service-attacks"></a>Prevence útoků odmítnutí služby  
  
### <a name="quotas"></a>Kvóty  
 Způsobuje přijímající straně přidělit významné množství paměti je možný útok denial of service. Při této části soustřeďuje na otázky spotřeba paměti vyplývající z velkých zpráv, může dojít, jiným útokům. Zprávy mohou například používat nesoustředil příliš velký objem doba zpracování.  
  
 Útoky DOS jsou obvykle omezeny pomocí kvóty. Při překročení kvóty <xref:System.ServiceModel.QuotaExceededException> normálně je vyvolána výjimka. Bez kvótu, škodlivé zprávy může způsobit všechny dostupné paměti nelze přistupovat, což vede k <xref:System.OutOfMemoryException> výjimky nebo všechny dostupné balíčky nelze přistupovat, což je <xref:System.StackOverflowException>.  
  
 Byla překročena kvóta scénář je obnovitelné; Jestliže ve spuštěné službě, je právě zpracovávána zprávy zahozena a službu neustále běží a zpracuje zprávy o další. Scénáře přetečení zásobníku a z důvodu nedostatku paměti, ale nejsou obnovitelné kdekoliv [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; služba ukončuje v případě nalezení takové výjimky.  
  
 Kvóty pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nezahrnují všechny předběžné přidělení. Například pokud <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kvóta (nachází se na různé třídy) je nastavena na 128 KB, neznamená, že je 128 KB automaticky přidělena pro každou zprávu. Skutečná velikost přidělené závisí na skutečná velikost příchozí zprávy.  
  
 Mnoho kvóty jsou k dispozici v přenosové vrstvě. Jedná se o kvóty podle konkrétní přenosu kanálu používá (HTTP, TCP a tak dále). Když toto téma popisuje některé z těchto kvót, těchto kvót jsou podrobně popsány v [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>Zatřiďovací tabulky ohrožení zabezpečení  
 Obsahuje chybu, pokud kontrakty dat obsahují zatřiďovacích tabulkách nebo kolekce. K problému dochází velký počet hodnot vložit do zatřiďovací tabulky, kde velký počet tyto hodnoty generovat stejnou hodnotu hash. To slouží jako útoku DOS.  Toto ohrožení zabezpečení lze zmírnit nastavíte kvótu MaxRecievedMessageSize vazby. Musí dát pozor při nastavení tato kvóta prevence takové útoky. Tato kvóta převádí horní limit velikosti zprávy WCF. Kromě toho Vyhněte se používání zatřiďovacích tabulkách nebo kolekcí v kontraktech vaše data.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Omezení využití paměti bez streamování  
 Model zabezpečení kolem velké zprávy závisí na tom streamování používán. V případě základní, datového proudu zprávy se uloží do vyrovnávací paměti do paměti. V takovém případě použijte <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kvóty v <xref:System.ServiceModel.Channels.TransportBindingElement> nebo na vazby poskytované systémem pro ochranu proti velké zprávy omezením maximální velikosti zprávy pro přístup. Všimněte si, že služba může zpracování více zpráv ve stejnou dobu, v takovém případě jsou všechny v paměti. Použijte funkci omezení pro zmírnění této hrozby.  
  
 Všimněte si také, že `MaxReceivedMessageSize` neumístí horní mez na jednotlivé zprávy využití paměti, ale její omezení v rámci konstantní faktor. Například pokud `MaxReceivedMessageSize` je 1 MB a je přijatá zpráva 1 MB a pak je potřeba obsahovat deserializovaný objekt grafu, což vede k celkové paměti spotřeba také více než 1 MB deserializovat, další paměť. Z tohoto důvodu Vyhněte se vytváření Serializovatelné typy, které by mohly způsobit významné paměťové nároky bez množství příchozích dat. Například kontrakt dat "MyContract" 50 volitelnými daty člen pole a další 100 privátní pole může být vytvořena s konstrukce XML "\<MyContract / >". Tato konfigurace XML má za následek paměti přistupuje 150 polí. Upozorňujeme, že jsou ve výchozím nastavení volitelné datových členů. Tento problém nastane, když je takového typu součástí pole.  
  
 `MaxReceivedMessageSize`samostatně není dostatečně k útokům denial of service. Deserializátor může vynutit k deserializaci hluboko vnořený objekt graf (objekt, který obsahuje jiný objekt, který obsahuje ještě jiný a tak dále), například pomocí příchozí zprávy. Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> volat metody vnořené způsobem k deserializaci takové grafy. Hluboká vnoření volání metod může mít za následek k neodstranitelné <xref:System.StackOverflowException>. Tuto hrozbu zmírnit nastavení <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> kvóty pro omezení úroveň vnoření XML, jak je popsáno v části "Použití XML bezpečně" později v tomto tématu.  
  
 Nastavení dodatečných kvótách `MaxReceivedMessageSize` je zvlášť důležité při použití binárního kódování XML. Použití binárního kódování odpovídá poněkud komprese: malou skupinu bajtů příchozí zpráva může představovat velké množství dat. Proto i zprávu hodí do `MaxReceivedMessageSize` limit může trvat až mnohem víc paměti ve plně rozšířené formuláře. Zmírnit hrozby takové specifické XML, všechny kvóty čtečky XML musí být nastavena správně, jak je popsáno v části "Použití XML bezpečně" dál v tomto tématu.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Omezení využití paměti při streamování  
 Při streamování, můžete použít malá `MaxReceivedMessageSize` nastavení k ochraně před útoky DOS. Složitější scénáře jsou však možné pomocí vysílání datového proudu. Například službu nahrávání souborů přijímá soubory větší než všechny dostupné paměti. V takovém případě nastavte `MaxReceivedMessageSize` velmi velké hodnoty, očekává, že je téměř žádná data do vyrovnávací paměti v paměti a zpráva datové proudy přímo na disku. Pokud škodlivý zprávu nějakým způsobem vynutit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyrovnávací paměť dat místo datových proudů v tomto případě `MaxReceivedMessageSize` už chrání před zpráva přístup k veškeré dostupné paměti.  
  
 Pro zmírnění této hrozby, nastavení konkrétní kvót existovat v různých [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] součásti zpracování dat, které omezit ukládání do vyrovnávací paměti. Nejdůležitější z nich je `MaxBufferSize` vlastnost na různých elementů přenosové vazby a standardní vazby. Při streamování, musí být tato kvóta nastavená vezme v úvahu maximální množství paměti, kterou chcete přidělit jednotlivých zpráv. Stejně jako u `MaxReceivedMessageSize`, nastavení není umístí absolutní maximální využití paměti, ale pouze její omezení v rámci konstantní faktor. Také jako s `MaxReceivedMessageSize`, mějte na paměti na možnost více zpráv zpracovávaný současně.  
  
### <a name="maxbuffersize-details"></a>Podrobnosti o MaxBufferSize  
 `MaxBufferSize` Vlastnost omezuje žádné hromadné ukládání do vyrovnávací paměti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepodporuje. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy vyrovnávacích pamětí hlavičky SOAP a chyb protokolu SOAP a také všechny části MIME najít tak, aby nebyl v pořadí fyzická čtení zprávy zpráva přenosu optimalizace mechanismus (MTOM). Toto nastavení omezuje množství ukládání do vyrovnávací paměti ve všech těchto případech.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dosahuje tak, že předávání `MaxBufferSize` hodnotu pro různé součásti, které může ukládat do vyrovnávací paměti. Například některé <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> přetížení <xref:System.ServiceModel.Channels.Message> proveďte třídy `maxSizeOfHeaders` parametr. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]předá `MaxBufferSize` hodnotu tohoto parametru a omezit tak velikost hlavičky SOAP ukládání do vyrovnávací paměti. Je důležité při použití nastavte tento parametr <xref:System.ServiceModel.Channels.Message> přímo třídu. Obecně platí, že při použití komponenty v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , která má parametry kvót, je důležité pochopit bezpečnostních důsledcích tyto parametry a tyto hodnoty správně nastaveny.  
  
 Kodér zpráv MTOM má také `MaxBufferSize` nastavení. Při použití standardní vazby, to je automaticky nastaven na úrovni přenosu `MaxBufferSize` hodnotu. Ale při použití prvku vazby MTOM zpráva encoder můžete vytvořit vlastní vazby, je důležité nastavit `MaxBufferSize` vlastnost na hodnotu bezpečné při streamování se používá.  
  
## <a name="xml-based-streaming-attacks"></a>Streamování útoky založenými na XML  
 `MaxBufferSize`samostatně není dostatečně zajistit, aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nelze vynutit do ukládání do vyrovnávací paměti při streamování se očekává. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čtečky XML vždy vyrovnávací paměti celý počáteční značky elementu XML při spouštění číst nového elementu. To se provádí tak, aby správně zpracovat obory názvů a atributy. Pokud `MaxReceivedMessageSize` je nakonfigurovaný jako velký (například povolit velký soubor přímo na disk streamování scénář), škodlivé zprávy může zkonstruovat kde text celé zprávy je velký počáteční značky elementu XML. Pokus o čtení ho vede <xref:System.OutOfMemoryException>. Toto je jedna z mnoha možné na základě XML denial-of-service útoků, které lze všechny zmírnit pomocí kvóty čtečky XML, které jsou popsané v části "Použití XML bezpečně" dál v tomto tématu. Při streamování, je velmi důležité nastavit všechny tyto kvóty.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Kombinování streamování a ukládání do vyrovnávací paměti modely programování  
 Řada možných útoků jsou vyvolány kombinování streamování a streamování programovací modely v rámci stejné služby. Předpokládejme, že je kontrakt služby s dvěma operacemi: jeden trvá <xref:System.IO.Stream> a jiné přijímá pole vlastní typu. Předpokládejme také který `MaxReceivedMessageSize` je nastaven na velké hodnoty, aby první operaci ke zpracování velkých datových proudů. Bohužel to znamená, velké můžete nyní odesílání zpráv i druhá operace a data vyrovnávací paměti deserializátor v paměti jako pole předtím, než se nazývá operaci. Toto je možný útok denial of service: `MaxBufferSize` kvóty neomezuje velikost těla zprávy, což je deserializátor pracuje s.  
  
 Z tohoto důvodu vyhněte míchání operací na základě datového proudu a bez datového proudu ve stejné smlouvy. Pokud musíte kombinovat absolutně dva programovací modely, pomocí následujících opatření:  
  
-   Vypnout <xref:System.Runtime.Serialization.IExtensibleDataObject> funkce nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> k `true`. Tím se zajistí, že jsou pouze členové, které jsou součástí kontraktu deserializovat.  
  
-   Nastavte <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost <xref:System.Runtime.Serialization.DataContractSerializer> na hodnotu bezpečné. Tato kvóta je také k dispozici na <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut nebo prostřednictvím konfigurace. Tato kvóta omezí počet objektů, které jsou v jedné díl deserializace deserializovat. Za normálních okolností je v jedné díl deserializovat každou operaci parametr nebo zprávy část textu v kontrakt zprávy. Při deserializaci pole, každé položky pole se počítá jako samostatný objekt.  
  
-   Nastavte všechny kvóty čtečky XML bezpečné hodnoty. Věnujte pozornost <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, a <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> a vyhnout se řetězce v operacích streamování.  
  
-   Projděte si seznam známé typy, pamatujte, že kterékoli z nich může být vytvořena instance kdykoli (viz část "Brání nezamýšleným typy z načítá" dál v tomto tématu).  
  
-   Nepoužívejte všechny typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které ukládat velké množství dat do vyrovnávací paměti. Nepřidávejte tyto typy do seznamu ze známých typů.  
  
-   Nepoužívejte <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> pole, <xref:System.Byte> maticových nebo které implementují typy <xref:System.Runtime.Serialization.ISerializable> ve smlouvě.  
  
-   Nepoužívejte <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> pole, <xref:System.Byte> maticových nebo které implementují typy <xref:System.Runtime.Serialization.ISerializable> v seznamu známých typů.  
  
 Předchozí opatření použít, když používá operaci streamování <xref:System.Runtime.Serialization.DataContractSerializer>. Nikdy kombinovat streamování a -streamování programování modely na stejnou službu, pokud používáte <xref:System.Xml.Serialization.XmlSerializer>, protože nemá ochranu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> kvóty.  
  
### <a name="slow-stream-attacks"></a>Útoky pomalé datového proudu  
 Třída útoků odmítnutí služby streamování nezahrnuje využití paměti. Místo toho útoku zahrnuje pomalé odesílatel nebo příjemce data. Při čekání na data, která mají být odesílané nebo přijímané, vyčerpání prostředků, jako je například vláken a dostupné připojení. Tato situace může nastat v důsledku napadením se zlými úmysly nebo z legitimní odesílatel/příjemce na pomalé síťové připojení.  
  
 Zmírnit tyto útoky, správně nastavené časové limity přenosu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Přenosu kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Za druhé, nikdy nepoužívejte synchronní `Read` nebo `Write` operace při práci s datovými proudy v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-xml-safely"></a>Bezpečně pomocí XML  
  
> [!NOTE]
>  I když tato část se týká XML, informace platí také pro dokumenty JavaScript Object Notation (JSON). Kvóty fungují podobně, pomocí [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>Zabezpečení čtečky XML  
 Informační sadu XML je základem veškeré zpracování zpráv v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Pokud existují přijímá data XML z nedůvěryhodného zdroje, počet možnosti útok s cílem služby, musí být omezeny. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje speciální a zabezpečené čtečky XML. Tyto čtečky automaticky vytvoří při použití jednu standardní kódování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (text, binary nebo MTOM).  
  
 Některé z funkcí zabezpečení na těchto čtečky jsou vždy aktivní. Například čtečky nikdy zpracovat definice typu dokumentu (DTD), které jsou potenciální zdroj útoky DOS a by se nikdy zobrazit v legitimní protokolu SOAP zprávy. Další funkce zabezpečení zahrnují kvóty čtečky, které musí být nakonfigurován, které jsou popsané v následující části.  
  
 Při práci přímo s čtečky XML (například při zápisu vlastní kodér nebo při práci přímo s <xref:System.ServiceModel.Channels.Message> – třída), vždy používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení čtečky, když je možné pracovat s daty nedůvěryhodné. Vytvoření zabezpečeného čtečky volání jeden statický objektu pro vytváření přetížení metody <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, nebo <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> na <xref:System.Xml.XmlDictionaryReader> třídy. Při vytváření čtečka čipových karet, předejte hodnoty zabezpečené kvóty. Nevolejte `Create` přetížení metody. Tyto Nevytvářejte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čtečky. Místo toho se vytvoří čtečka čipových karet, který není chráněný pomocí funkce zabezpečení, které jsou popsané v této části.  
  
### <a name="reader-quotas"></a>Čtečka kvóty  
 Zabezpečené čtečky XML mít pět konfigurovat kvóty. To se obvykle konfiguruje pomocí `ReaderQuotas` vlastnost na kódování prvky vazeb nebo standardní vazby, nebo můžete použít <xref:System.Xml.XmlDictionaryReaderQuotas> objekt předaný při vytváření čtečka čipových karet.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Tato kvóta omezuje počet bajtů, které se čtou v jediném `Read` operace při čtení element spustit značku a její atributy. (V případech,-streamování, není počítáno samotný název elementu proti kvótu.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> je důležité z následujících důvodů:  
  
-   Název elementu a jeho atributy jsou vždy do vyrovnávací paměti v paměti při jejich přečtení. Proto je důležité nastavit tuto kvótu správně při streamování režimu, aby se zabránilo nadměrnému ukládání do vyrovnávací paměti při streamování se očekává. Najdete v článku `MaxDepth` části kvóta informace o skutečné množství ukládání do vyrovnávací paměti, který probíhá.  
  
-   Má příliš mnoho atributů XML může použít až nesoustředil příliš velký doba zpracování, protože názvy atributů musí být vráceny jedinečnosti. `MaxBytesPerRead`omezuje tuto hrozbu.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Tato kvóta omezuje maximální hloubky vnoření elementů XML. Například v dokumentu "\<A >\<B >\<C / >\</B >\</A >" se hloubky vnoření tří. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>je důležité z následujících důvodů:  
  
-   `MaxDepth`komunikuje s `MaxBytesPerRead`: Čtečka vždy uchovává data v paměti pro aktuální prvek a veškeré jeho předchůdců, je spotřeba maximální paměť čtečky úměrný tato dvě nastavení.  
  
-   Při deserializaci hluboko vnořený objekt grafu, pro přístup k celý zásobník a throw k neodstranitelné je nucen deserializátor <xref:System.StackOverflowException>. Přímá korelace mezi vnoření XML a objekt vnoření obě existuje <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer>. Použití `MaxDepth` pro zmírnění této hrozby.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Tato kvóta omezuje velikost čtenáře *tabulky názvů*. Pracovat s tabulkou názvů obsahuje některé řetězce (například obory názvů a předpony), které jsou došlo při zpracování dokument XML. Tyto řetězce jsou uložená do vyrovnávací paměti v paměti, nastavte tuto kvótu, aby se zabránilo nadměrnému ukládání do vyrovnávací paměti při streamování se očekává.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Tato kvóta omezuje velikost maximální řetězec, který vrací čtecí modul XML. Tato kvóta neomezuje využití paměti v samotné čtecí modul XML, ale v komponentě používající čtečky. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> používá čtečku zabezpečen <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ji deserializovat není větší než tato kvóta řetězce. Při použití <xref:System.Xml.XmlDictionaryReader> třídy přímo, ne všechny metody ohledem tato kvóta, ale jenom metody, které jsou vytvořené speciálně číst řetězce, například <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> metoda. <xref:System.Xml.XmlReader.Value%2A> Vlastnost čtečky nemá vliv tato kvóta a proto by nemělo použít, pokud ochrany poskytuje tuto kvótu je nutné.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Tato kvóta omezuje maximální velikost pole primitivních elementů, které vrací čtecí modul XML, včetně pole bajtů. Tato kvóta neomezuje využití paměti v samotné čtecí modul XML, ale v jakémkoli součásti používající čtečky. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> používá čtečku zabezpečen <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, ji deserializovat není větší než tato kvóta pole bajtů. Je důležité nastavit tuto kvótu při pokusu o kombinovat streamování a ve vyrovnávací paměti programovací modely v jedné smlouvy. Mějte na paměti, že při použití <xref:System.Xml.XmlDictionaryReader> přímo, třídu pouze metody, které jsou vytvořené speciálně číst pole libovolné velikosti určité primitivní typy, jako například <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, respektují tuto kvótu.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>Specifické hrozby pro binární kódování  
 Binární kódování XML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje zahrnuje *slovníku řetězce* funkce. Řetězec velký může kódované pomocí pouze několik bajtů. To umožňuje výrazné zvýšení výkonu, ale zavádí nové hrozby odmítnutí služby, které musí být omezeny.  
  
 Existují dva druhy slovník: *statické* a *dynamické*. Statické slovník je předdefinovaný seznam dlouhých řetězců, které může být reprezentován pomocí krátký kód v binární kódování. Tento seznam řetězců vyřešen, když čtečka je vytvořena a nelze jej změnit. Žádná z řetězce ve slovníku statické, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá ve výchozím nastavení jsou dostatečně velký pro představovat závažné ohrožení denial-of-service, přestože může být přesto použít v slovníkový útok rozšíření. V pokročilých scénářích, kde zadáte vlastní statické slovník buďte opatrní při představení řetězců velké slovníku.  
  
 Funkce dynamické slovník umožňuje zprávy a pokuste se definovat vlastní řetězce a přidružte je ke krátké kódy. Tato mapování řetězec kódu jsou uloženy v paměti během celé komunikace relace tak, aby následné zprávy není nutné znovu odeslal řetězce a může využívat kódy, které jsou již definováni. Tyto řetězce mohou být o libovolné délce a proto představovat hrozbu závažnější než ty, které ve slovníku statické.  
  
 První ohrožení, které musí být omezeny je možnost výskytu nekonzistentních je dynamický slovník (tabulky mapování řetězec kódu), příliš velká. Rozbalit tohoto slovníku během několika zpráv a proto `MaxReceivedMessageSize` kvóty nabízí žádná ochrana, protože se vztahuje pouze na každou zprávu samostatně. Proto samostatné <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> vlastnost existuje na <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , která omezuje velikost slovníku.  
  
 Na rozdíl od většiny jiných kvóty tato kvóta platí i v případě zápis zprávy. Pokud dojde k překročení při čtení zprávy, `QuotaExceededException` je vyvolána jako obvykle. Pokud je překročena při zápisu zprávu, všechny řetězce, které způsobí překročení kvóty se zapisují jako-je, bez použití funkce dynamické slovník.  
  
### <a name="dictionary-expansion-threats"></a>Slovník rozšíření hrozeb  
 Třídu významné útoků specifické pro binární vyplývá z rozšíření slovníku. Krátké zprávy v binární podobě může zapněte do velké zprávy ve plně rozšířené textové formě Pokud využívají funkci slovník řetězec. Faktor rozšíření pro dynamický slovník řetězce je omezena <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> kvótu, protože žádný dynamický slovník řetězec přesahuje maximální velikost celý slovníku.  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, A `MaxArrayLength` vlastnosti pouze omezení využití paměti. Jsou obvykle není vyžadována zmírnit všechny hrozby využití datového proudu, protože využití paměti je již omezena `MaxReceivedMessageSize`. Ale `MaxReceivedMessageSize` počty předběžné rozšíření bajtů. Když binárního kódování se používá, využití paměti může potenciálně jdou nad rámec `MaxReceivedMessageSize`omezené jenom faktorem <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Z tohoto důvodu je důležité vždy nastavit všechny čtečky kvóty (zejména <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) při použití binárního kódování.  
  
 Při použití binárního kódování společně s <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` rozhraní můžete došlo ke zneužití připojit slovníkový útok rozšíření. Toto rozhraní v podstatě poskytuje neomezené úložiště pro libovolná data, která není součástí kontraktu. Pokud nelze nastavit kvóty nízké tak, aby `MaxSessionSize` násobí hodnotou `MaxReceivedMessageSize` neobsahuje představovat problém, zakažte `IExtensibleDataObject` funkce při použití binárního kódování. Nastavte `IgnoreExtensionDataObject` vlastnost `true` na `ServiceBehaviorAttribute` atribut. Alternativně neimplementují `IExtensibleDataObject` rozhraní. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Kontraktů dat s dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Souhrn kvóty  
 Následující tabulka shrnuje informace o kvóty.  
  
|Podmínka|Chcete-li nastavit důležité kvóty|  
|---------------|-----------------------------|  
|Žádné streamování nebo streamování malých zpráv, text nebo kódování MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead`, a`MaxDepth`|  
|Žádné streamování nebo streamování malých zpráv, binární kódování|`MaxReceivedMessageSize`, `MaxSessionSize`a všechny`ReaderQuotas`|  
|Streamování velké zprávy, text nebo kódování MTOM|`MaxBufferSize`a všechny`ReaderQuotas`|  
|Streamování velké zprávy, binární kódování|`MaxBufferSize`, `MaxSessionSize`a všechny`ReaderQuotas`|  
  
-   Vypršení časových limitů transportní vrstvy musí být vždycky nastavená a nikdy nepoužívejte synchronní čtení/zápisu při streamování se používá, bez ohledu na to, jestli jsou streamování velké nebo malé zprávy.  
  
-   Pokud máte pochybnosti o kvótu, nastavte ji na hodnotu bezpečné místo ponechat otevřené.  
  
## <a name="preventing-malicious-code-execution"></a>Brání spuštění škodlivého kódu  
 Následující obecné třídy hrozeb můžete spustit kód a mít nežádoucí účinky:  
  
-   Načte deserializátor typu škodlivý, unsafe nebo citlivým z hlediska zabezpečení.  
  
-   Příchozí zpráva způsobí, že deserializátor vytvořit instanci typu normálně bezpečné v například tak, že má nezamýšleným důsledky.  
  
 Následující části popisují tyto třídy další hrozby.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Zabezpečení informace na <xref:System.Xml.Serialization.XmlSerializer>, naleznete v příslušné dokumentaci.) Model zabezpečení pro <xref:System.Xml.Serialization.XmlSerializer> je podobné jako <xref:System.Runtime.Serialization.DataContractSerializer>a liší se většinou v podrobnostech. Například <xref:System.Xml.Serialization.XmlIncludeAttribute> atribut se používá pro zahrnutí typ místo <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut. Ale některé hrozby jedinečný <xref:System.Xml.Serialization.XmlSerializer> jsou popsány dále v tomto tématu.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>Brání načítá nezamýšleným typy  
 Načítání nezamýšleným typy může mít významné důsledky, jestli typ je škodlivý nebo právě má vedlejší účinky citlivé na zabezpečení. Typ může obsahovat chyba zneužití zabezpečení, provádět akce citlivé na zabezpečení v jeho konstruktoru nebo konstruktoru třídy, mít nároků velké paměti, který usnadňuje útoky DOS, nebo může vyvolat neobnovitelná výjimky. Typy může mít konstruktory třídy, které spustit hned, jak je načíst typ, a před vytvořením všechny instance. Z těchto důvodů je důležité pro řízení sadu typů, které deserializátor může načíst.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Deserializuje volně párované způsobem. Nikdy přečte common language runtime (CLR) typu a sestavení názvy z příchozí data. Toto je podobná chování <xref:System.Xml.Serialization.XmlSerializer>, ale se liší od chování <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Volné párování představuje určitou úroveň zabezpečení, protože vzdálenému útočníkovi nesmí uvádět libovolný typ se načíst právě pojmenováním typu ve zprávě.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Je vždycky povolená načíst typ, který je aktuálně očekáván podle kontrakt. Například, pokud kontraktu dat obsahuje data člena typu `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> může načíst `Customer` zadat, když ho deserializuje tento člen data.  
  
 Kromě toho <xref:System.Runtime.Serialization.DataContractSerializer> podporuje polymorfismus. Člen dat může být deklarována jako <xref:System.Object>, ale může obsahovat příchozích dat `Customer` instance. To je možné, pouze pokud `Customer` typ byl proveden "známé" deserializátor prostřednictvím jednoho z těchto mechanismů:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute>Atribut použitý k typu.  
  
-   `KnownTypeAttribute`atribut určení metodu, která vrátí seznam typů.  
  
-   `ServiceKnownTypeAttribute`atribut.  
  
-   `KnownTypes` Konfigurační oddíl.  
  
-   Seznam známých typů explicitně předaný <xref:System.Runtime.Serialization.DataContractSerializer> během vytváření, pokud se používá serializátor přímo.  
  
 Každý z těchto mechanismů zvyšuje pravděpodobnost zavedením další typy, které deserializátor může načíst. Řídit každou z těchto mechanismů zajistit, že žádné škodlivého nebo nežádoucího typy jsou přidány do seznamu známé typy.  
  
 Jakmile známý typ je v oboru, mohou být načteny kdykoli a nelze vytvořit instance typu, i když kontrakt zakazuje ve skutečnosti jeho použití. Předpokládejme například, typ, který "MyDangerousType" je přidán do seznamu známých typů pomocí jedné z výše uvedených mechanismů. To znamená, že:  
  
-   `MyDangerousType`instaluje se a jeho spuštěním konstruktoru třídy.  
  
-   I když deserializaci kontraktu dat s členem řetězec dat, škodlivé zprávy může způsobit stále instanci `MyDangerousType` k vytvoření. Kód na `MyDangerousType`, například nastavením vlastností, může spustit. Po dokončení, pokusí se deserializátor přiřadit tato instance řetězec – datový člen a selhat s výjimkou.  
  
 Při zápisu metodu, která vrátí seznam hodnot známé typy nebo při předávání přímo na seznamu <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, zkontrolujte, zda kód, který připraví seznamu je bezpečné a funguje pouze na důvěryhodné data.  
  
 Při zadání známé typy v konfiguraci, ujistěte se, že konfigurační soubor je bezpečné. Silné názvy používat v konfiguraci (zadáním veřejný klíč podepsané sestavení, které se nachází typ), ale nezadávejte žádné verzi typu, k načtení. Typ zavaděč automaticky vybere nejnovější verzi, pokud je to možné. Pokud zadáte v konfiguraci na konkrétní verzi, riskujete, následující: Typ může mít chyba zabezpečení, která může být stanovena v budoucí verzi, ale verze stále načte, protože je explicitně zadaná v konfiguraci.  
  
 Příliš mnoho známé typy má jiné důsledkem: <xref:System.Runtime.Serialization.DataContractSerializer> vytvoří mezipaměť o serializaci nebo deserializaci kódu v doméně aplikace, se záznam pro každý typ musí serializaci a deserializaci. Tato mezipaměť je nikdy vymazat tak dlouho, dokud doménu aplikace běží. Útočník, který si je vědoma, že aplikace používá mnoho známé typy proto může způsobit deserializace všechny tyto typy způsobuje mezipaměti využívat nepřiměřeně velké množství paměti.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>Typy brání používán nezamýšleným stavu  
 Typ může mít interní konzistence omezení, která musí být vynucená. Musí dát pozor na-li se vyhnout narušení těchto omezení během deserializace.  
  
 Následující příklad typu představuje stav přetlakové komory na kosmické a vynucuje omezení, že vnitřní a vnější dveře nelze otevřít ve stejnou dobu.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Útočník může odeslat zprávu škodlivý tímto způsobem, získávání kolem omezení a získávání objektu v neplatném stavu, který může mít nezamýšleným a nepředvídatelným důsledky.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Tato situace se vyhnout tím, že je vědět následující body:  
  
-   Když <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje Většina tříd, konstruktory se nespustí. Nespoléhejte proto na jakékoli správy stavu v konstruktoru.  
  
-   Zpětná volání použijte k zajištění, že objekt je v platném stavu. Zpětné volání označené jako <xref:System.Runtime.Serialization.OnDeserializedAttribute> atribut je obzvláště užitečná, protože se spustí po dokončení a možnost zkontrolujte a opravte celkový stav deserializace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Verze-zpětná volání serializace tolerantní](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Design typy kontraktů dat moct spolehnout na žádné konkrétní pořadí, ve kterých se vlastnosti musí být voláno setter.  
  
-   Vezměte v potaz pomocí starší verze typů, které jsou označené jako <xref:System.SerializableAttribute> atribut. Řada z nich byly navrženy pro práci s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálenou komunikaci pro použití s pouze důvěryhodné data. Existující typy, které jsou označené jako tento atribut nemusí byly navrženy s stavu zabezpečení v paměti.  
  
-   Nespoléhejte na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost `DataMemberAttribute` atribut zaručit přítomnosti dat jde stavu zabezpečení. Data mohou být vždy `null`, `zero`, nebo `invalid`.  
  
-   Nikdy důvěryhodnosti grafu objektu deserializovat z nedůvěryhodného zdroje bez nejprve její ověřování. Každý jednotlivý objekt může být v konzistentním stavu, ale grafu objektů jako celek nesmí být. Kromě toho i v případě režimu zachování grafu objektu je zakázané, deserializovat graf může mít několik odkazů na stejný objekt nebo mít cyklické odkazy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>Pomocí NetDataContractSerializer bezpečně  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> Serializace modul, který používá úzkou párování na typy. Toto je podobná <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. To znamená, určí, který typ instance načtením [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] název sestavení a typu z příchozí data. I když je součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], není nijak zadaný zapojení tento modul serializace; musí být napsané vlastní kód. `NetDataContractSerializer` Zajišťuje především pro usnadnění migrace z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Vzdálená komunikace na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v příslušné části v [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Protože samotnou zprávu může znamenat lze načíst libovolného typu, <xref:System.Runtime.Serialization.NetDataContractSerializer> mechanismus je ze své podstaty nezabezpečené a musí být použit pouze s důvěryhodné data. Je možné zabezpečit napsáním vazač zabezpečené, typ omezení typu, který umožňuje pouze bezpečné typy načíst (pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> vlastnost).  
  
 I v případě, že se používá pro důvěryhodné data, příchozích dat může nedostatečně zadejte typ načíst, zvlášť pokud <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> je nastavena na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Každý, kdo má přístup do adresáře aplikace nebo do globální mezipaměti sestavení můžete nahradit typu škodlivý místo ten, který se má načíst. Vždy zajistěte zabezpečení adresáře vaší aplikace a z globální mezipaměti sestavení správně nastavení oprávnění.  
  
 Obecně platí, že pokud povolíte částečně důvěryhodného kódu přístup k vaší `NetDataContractSerializer` instance nebo jinak kontrolujete selektor náhradní (<xref:System.Runtime.Serialization.ISurrogateSelector>) nebo vazače serializace (<xref:System.Runtime.Serialization.SerializationBinder>), kód může vykonávat značnou část řízení přes proces serializaci nebo deserializaci. Například je může vložit náhodné typy, způsobit zpřístupnění informací, manipulovat s výsledný objekt grafu nebo serializovaná data nebo přetečení výsledné serializovaném datovém proudu.  
  
 Jiné potíže se zabezpečením s `NetDataContractSerializer` je odepření služby, není hrozbu provádění škodlivý kód. Při použití `NetDataContractSerializer`, vždy nastavte <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kvóta na hodnotu bezpečné. Je snadné vytvořit malé škodlivý zprávu, že přiděluje pole objektů, jejíž aktuální velikost je omezena pouze tuto kvótu.  
  
### <a name="xmlserializer-specific-threats"></a>XmlSerializer specifické hrozby  
 <xref:System.Xml.Serialization.XmlSerializer> Model zabezpečení je podobné jako <xref:System.Runtime.Serialization.DataContractSerializer>. Několik hrozeb, ale jsou jedinečná pro <xref:System.Xml.Serialization.XmlSerializer>.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Generuje *sestavení serializace* za běhu, která obsahovat kód, který je ve skutečnosti serializuje a deserializuje; jsou tyto sestavení vytvořené v adresáři dočasné soubory. Pokud některé proces nebo uživatelský má přístupová práva k tomuto adresáři, může se kód serializaci nebo deserializaci přepsat libovolný kód. <xref:System.Xml.Serialization.XmlSerializer> Pak spustí tento kód používá kontext zabezpečení místo kód serializaci nebo deserializaci. Zkontrolujte, zda že jsou oprávnění nastavena správně na adresáře s dočasnými soubory k tomu zabránili.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Má také režim, ve kterém používá sestavení předem vygenerovaná serializace místo aby generovala je za běhu. Tento režim se aktivuje vždy, když <xref:System.Xml.Serialization.XmlSerializer> můžete najít vhodnou serializaci sestavení. <xref:System.Xml.Serialization.XmlSerializer> Kontroly, jestli byl sestavení serializace podepsány stejným klíčem, který se použil k podepsání sestavení, které obsahuje typy serializována. To nabízí ochranu z škodlivý sestavení se maskovaný jako sestavení serializace. Ale pokud je sestavení obsahující Serializovatelné typy není podepsaná, <xref:System.Xml.Serialization.XmlSerializer> nelze provést tuto kontrolu a používá žádné sestavení se správným názvem. To umožňuje spuštění škodlivého kódu. Vždy podepsat sestavení, které obsahují Serializovatelné typy nebo úzce řízení přístupu k adresáři vaší aplikace a globální mezipaměti sestavení aby zavlečení škodlivého sestavení.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Může podléhat odepření služby. <xref:System.Xml.Serialization.XmlSerializer> Nemá `MaxItemsInObjectGraph` kvóty (jako je k dispozici na <xref:System.Runtime.Serialization.DataContractSerializer>). Proto deserializuje libovolné množství objektů omezena pouze velikost zprávy.  
  
### <a name="partial-trust-threats"></a>Částečná důvěryhodnost hrozeb  
 Mějte na paměti následující otázky týkající se hrozeb související s kód s částečnou důvěryhodností. Tyto hrozby zahrnují škodlivý částečně důvěryhodného kódu, a také škodlivý částečně důvěryhodného kódu v kombinaci s další scénáře útoků (například částečně důvěryhodného kódu, který vytvoří si konkrétní řetězec a pak ho deserializaci).  
  
-   Při použití žádné součásti serializace, nikdy assert všechna oprávnění, než taková využití i v případě scénáře celý serializace je v rámci oboru vašeho vyhodnocení a nejsou zabývají nedůvěryhodné data ani objekty. Takové využití může vést k ohrožení zabezpečení.  
  
-   V případech, kdy částečně důvěryhodného kódu obsahuje kontrolu nad tímto procesem serializace, buď prostřednictvím body rozšiřitelnosti (náhrady), typy serializována, nebo jinými prostředky může způsobit částečně důvěryhodného kódu serializátor výstup velké množství data do serializovaném datovém proudu, což může způsobit odepření služby (DoS) k příjemce tento datový proud. Pokud jsou serializaci dat určené pro cíl, který je citlivý na DoS hrozby, serializovat částečně důvěryhodné typy nebo jinak umožní částečně důvěryhodného kódu řízení serializace.  
  
-   Pokud povolíte částečně důvěryhodného kódu, přístup k vaší <xref:System.Runtime.Serialization.DataContractSerializer> instance nebo jinak kontrolujete [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), uplatnit značnou část kontrolu nad tímto procesem serializaci nebo deserializaci. Například je může vložit náhodné typy, způsobit zpřístupnění informací, manipulovat s výsledný objekt grafu nebo serializovaná data nebo přetečení výsledné serializovaném datovém proudu. Ekvivalentní <xref:System.Runtime.Serialization.NetDataContractSerializer> threat je popsaný v části "Použití NetDataContractSerializer bezpečně".  
  
-   Pokud <xref:System.Runtime.Serialization.DataContractAttribute> je použit atribut typu (nebo typ označen jako `[Serializable]` , ale není `ISerializable`), deserializátor můžete vytvořit instanci takového typu, i když jsou všechny konstruktory neveřejný nebo chráněný moduly požadavky.  
  
-   Pokud data, která mají být deserializovat je důvěryhodný a jste si jisti, že všechny známé typy jsou typy, které důvěřujete nikdy důvěřovat výsledek deserializace. Všimněte si, že známé typy nejsou načíst z konfiguračního souboru aplikace (však jsou načteny z konfiguračního souboru počítače) při spuštění v částečné důvěryhodnosti.  
  
-   Pokud předáte `DataContractSerializer` přidána instance s náhradní částečně důvěryhodného kódu, kód můžete změnit nastavení změn na tomto náhradní.  
  
-   Pro objekt deserializovaný Pokud čtecí modul XML (nebo data v nich) pochází z částečně důvěryhodného kódu považovat za výsledný objekt deserializovaný nedůvěryhodné data.  
  
-   Fakt, na který <xref:System.Runtime.Serialization.ExtensionDataObject> typ má žádné veřejné členy neznamená, že je zabezpečení dat v něm. Například pokud deserializovat ze zdroje dat privilegované do objektu, ve které některá data nachází, pak pracovní, tento objekt částečně důvěryhodného kódu částečně důvěryhodného kódu můžete číst data v `ExtensionDataObject` pomocí serializace objektu. Zvažte nastavení <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> k `true` při deserializaci ze zdroje dat privilegované do objektu, který je novější předaný částečně důvěryhodného kódu.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporu serializace privátní, chráněné, interní a veřejné členy v režimu plné důvěryhodnosti. V částečné důvěryhodnosti, jde však serializovat pouze veřejné členy. A `SecurityException` je vyvolána, pokud se aplikace pokusí serializovat neveřejný člen.  
  
     Umožnit vnitřního nebo chráněné vnitřní členy k serializaci v částečné důvěryhodnosti, použijte `System.Runtime.CompilerServices.InternalsVisibleTo` atributu sestavení. Tento atribut umožňuje sestavení deklarovat, že její interní členové jsou viditelné pro některé jiné sestavení. V takovém případě sestavení, které chce mít jeho vnitřní členy serializovat prohlašuje, že jsou viditelné pro System.Runtime.Serialization.dll její vnitřní členy.  
  
     Výhodou tohoto přístupu je, nevyžaduje cestu generování kódu zvýšenými oprávněními.  
  
     Ve stejnou dobu existují dvě hlavní nevýhody.  
  
     První nevýhodou je, že přihlášení vlastnost `InternalsVisibleTo` atribut je celou sestavení. To znamená nelze zadat, pouze určité třídy můžou mít její vnitřní členy serializovat. Samozřejmě, stále můžete není určená k serializaci konkrétní vnitřní člen, stačí přidat není `DataMember` atribut tohoto člena. Podobně vývojář můžete také aby členem interní místo soukromé nebo chráněné s mírné viditelnost otázky.  
  
     Druhý nevýhodou je, že stále nejsou podporovány soukromé nebo chráněné členy.  
  
     Pro ilustraci použití `InternalsVisibleTo` atribut v částečné důvěryhodnosti, zvažte následující program:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     V příkladu nahoře `PermissionsHelper.InternetZone` odpovídá `PermissionSet` částečného vztahu důvěryhodnosti. Nyní, bez `InternalsVisibleToAttribute`, aplikace se nezdaří, vyvolání `SecurityException` indikující, že neveřejným členy nelze serializovat v částečné důvěryhodnosti.  
  
     Ale pokud jsme ke zdrojovému souboru přidejte následující řádek, program se úspěšně spustí.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Další aspekty správy stavu  
 Několik obavy týkající se správy stavu objektu jsou důležité zmínit:  
  
-   Pokud používáte programovací model na základě datového proudu s streamování přenosu, dojde k jako příchodu zpracování zprávy. Odesílatel zprávy může přerušit operaci odeslání uprostřed datového proudu, nechat kódu v nepředvídatelném stavu, pokud byl očekávaný další obsah. Obecně platí, nespoléhejte na datový proud je úplný a neprovádět veškerou práci v operaci na základě datového proudu, která se nedá vrátit zpět v případě, že datový proud byl přerušen. To platí také pro situace, kdy zprávu může být poškozený po streamování textu (například se pravděpodobně chybí koncová značka pro obálku protokolu SOAP nebo může mít druhý tělo zprávy).  
  
-   Pomocí `IExtensibleDataObject` funkce může způsobit, že se vygenerované citlivá data. Pokud jsou přijetí dat z nedůvěryhodného zdroje do kontrakty dat s `IExtensibleObjectData` a později znovu ji vydat na zabezpečený kanál, kde jsou podepsané zprávy, můžete se potenciálně zaručování nic vědět o data. Kromě toho je pravděpodobně neplatný, pokud byste vzít v úvahu známé a neznámé částí dat celkového stavu, ve kterém jsou odesílání. Předešli této situaci nastavením buď selektivně vlastnosti rozšíření dat na `null` nebo selektivně zakázáním `IExtensibleObjectData` funkce.  
  
## <a name="schema-import"></a>Import schématu  
 Za normálních okolností proces import schématu pro generování typy dochází pouze v době návrhu, například při použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na webovou službu, kterou generovat třídu klienta. V pokročilejších scénářích, ale může zpracovat schématu za běhu. Upozorňujeme, že díky tomu můžou zpřístupnit můžete na rizika denial of service. Některé schématu může trvat dlouhou dobu, která bude importována. Nikdy nepoužívejte <xref:System.Xml.Serialization.XmlSerializer> komponenty import schématu v takových scénářů, pokud schémata pravděpodobně pochází z nedůvěryhodného zdroje.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Specifické hrozby integrace ASP.NET AJAX  
 Když uživatel implementuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> nebo <xref:System.ServiceModel.Description.WebHttpBehavior>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpřístupní koncový bod, který může přijmout zprávy XML a JSON. Je však jen jednu sadu čtečky kvóty, používat službu čtecí modul XML a JSON čtečky. Některá nastavení kvóty může být vhodné pro jeden čtečky ale příliš velký pro druhý.  
  
 Při implementaci `WebScriptEnablingBehavior`, uživatel má možnost vystavení proxy server JavaScript na koncový bod. Je třeba zvážit následující problémy se zabezpečením:  
  
-   Informace týkající se služby (názvy operace, názvy parametrů a tak dále) můžete získat tak, že prověří proxy server JavaScript.  
  
-   Při použití JavaScript koncový bod, informace citlivé a privátní může uchovávají v klientovi mezipaměti webového prohlížeče.  
  
## <a name="a-note-on-components"></a>Poznámka: na komponenty  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]je systém flexibilní a přizpůsobit. Většina obsah tohoto tématu soustředit na nejběžnější [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] scénáře použití. Je však možné kombinovat součásti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje mnoha různými způsoby. Je důležité porozumět zabezpečení důsledky použití jednotlivých součástí. Zejména:  
  
-   Pokud musíte použít čtečky XML, použijte čtečky <xref:System.Xml.XmlDictionaryReader> třída poskytuje rozdíl od jiných čtenářů. Bezpečné čtečky jsou vytvořené pomocí <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, nebo <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> metody. Nepoužívejte <xref:System.Xml.XmlReader.Create%2A> metoda. Vždy konfigurujte čtečky s bezpečné kvóty. Serializace motory ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou zabezpečené jenom při použití s zabezpečené čtečky XML z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Při použití <xref:System.Runtime.Serialization.DataContractSerializer> k deserializaci potenciálně nedůvěryhodných dat, vždy nastavená <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> vlastnost.  
  
-   Při vytváření zprávy, nastavte `maxSizeOfHeaders` parametr Pokud `MaxReceivedMessageSize` nenabízí dostatek ochrany.  
  
-   Při vytváření kodér, vždy nakonfigurovat relevantní kvóty, jako třeba `MaxSessionSize` a `MaxBufferSize`.  
  
-   Pokud používáte filtr XPath zprávy, nastavte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> a omezit tak velikost uzlů XML navštíví filtru. Nepoužívejte XPath výrazy, které může trvat dlouhou dobu výpočetní aniž byste museli navštívit velký počet uzlů.  
  
-   Obecně platí při použití jakékoli součásti, která přijímá kvótu, pochopit její vliv na zabezpečení a nastavte ji na hodnotu bezpečné.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
