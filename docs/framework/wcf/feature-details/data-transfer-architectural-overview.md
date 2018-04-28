---
title: Strukturální přehled přenosu dat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cb64b871b8e4ba3036d70f3b84e2fde1667f4529
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="data-transfer-architectural-overview"></a>Strukturální přehled přenosu dat
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] lze považovat za infrastrukturu zasílání zpráv. Může přijímat zprávy, jejich zpracování a jejich odesílání do uživatelského kódu pro další akce nebo můžete vytvořit zprávy z data zadána pomocí uživatelského kódu a jejich doručování do cílového umístění. Toto téma, které je určeno pro pokročilé vývojáře, popisuje architekturu zpracování zpráv a obsahují data. Jednodušší, orientované na úlohy zobrazení jak odesílat a přijímat data, najdete v části [zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podrobnosti implementace, které nejsou viditelné tak, že prověří [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objektový model. Dvě slova upozornění jsou v pořadí s ohledem na podrobnosti zdokumentovaných implementace. Nejprve popisy jednodušší; Skutečná implementace může být složitější z důvodu optimalizace nebo z jiných důvodů. Druhý, můžete se nikdy spoléhají na konkrétní implementace podrobnosti i popsané, protože tyto mohou změnit bez předchozího upozornění z verze na verzi nebo i v servisní verze.  
  
## <a name="basic-architecture"></a>Základní architektura  
 Základem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] možnosti zpracování zpráv je <xref:System.ServiceModel.Channels.Message> třídy, která je podrobně popsaná v [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Spuštění součásti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je možné rozdělit na dvě hlavní části: zásobník kanál a architektura služby s <xref:System.ServiceModel.Channels.Message> třídy se spojovací bod.  
  
 Zásobník kanál je zodpovědná za převod mezi platné <xref:System.ServiceModel.Channels.Message> instance a některé akce, která odpovídá odesílání nebo přijímání zprávy data. Na straně odesílání trvá zásobníku kanál platná <xref:System.ServiceModel.Channels.Message> instance a po nějaké zpracování provádí některé akce, která logicky odpovídá odeslání zprávy. Akce může být odesílání paketů TCP nebo HTTP služby Řízení front zpráv služby Řízení front zpráv, zápis zprávy do databáze, ukládání do sdílené složky nebo jiné akce, v závislosti na implementaci. Nejběžnější akce odesílá zprávy přes síťový protokol. Na straně příjmu se stane jako opak – akce je zjištěna (který může být TCP nebo HTTP paketů přicházejících nebo jiné akce) a po zpracování kanálu zásobníku převede tato akce platná <xref:System.ServiceModel.Channels.Message> instance.  
  
 Můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí <xref:System.ServiceModel.Channels.Message> třídy a kanál zásobníku přímo. To ale, takže je obtížné a časově náročné. Kromě toho <xref:System.ServiceModel.Channels.Message> objekt poskytuje žádná podpora metadat, takže nelze generovat silného typu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, pokud používáte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tímto způsobem.  
  
 Proto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje rozhraní služby, které poskytuje programovací model snadné použití, který můžete použít k vytvoření a příjmu `Message` objekty. Architektura služby mapy služeb [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů prostřednictvím představu o kontraktů služby a expeduje zprávy do operace uživatele, které jsou jednoduše [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody označené jako <xref:System.ServiceModel.OperationContractAttribute> atribut (Další podrobnosti najdete v tématu [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)). Tyto metody mohou mít parametry a vrátí hodnoty. Na straně služby převede příchozí rozhraní služby <xref:System.ServiceModel.Channels.Message> instancí do parametry a převede návratové hodnoty do odchozí <xref:System.ServiceModel.Channels.Message> instance. Na straně klienta dělá jako opak. Představte si třeba `FindAirfare` operace níže.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Předpokládejme, že `FindAirfare` je volána v klientovi. Architektura služby v klientovi převede `FromCity` a `ToCity` parametry do odchozí <xref:System.ServiceModel.Channels.Message> instance a předává je do zásobníku kanál k odeslání.  
  
 Na straně služby když <xref:System.ServiceModel.Channels.Message> instance dorazí v zásobníku kanál, architektura služby extrahuje příslušných dat ze zprávy k naplnění `FromCity` a `ToCity` parametry a potom volání na straně služby `FindAirfare` Metoda. Po návratu metody rozhraní služby provede vrácených celočíselná hodnota a `IsDirectFlight` výstupní parametr a vytvoří <xref:System.ServiceModel.Channels.Message> instance objektu, který obsahuje tyto informace. Pak předá `Message` instance se zásobníkem kanálu odesílání zpět do klienta.  
  
 Na straně klienta <xref:System.ServiceModel.Channels.Message> ze zásobníku kanál vyplývá instanci, která obsahuje zprávu odpovědi. Architektura služby extrahuje návratovou hodnotu a `IsDirectFlight` hodnotu a vrátí tyto volajícího klienta.  
  
## <a name="message-class"></a>Message – třída  
 <xref:System.ServiceModel.Channels.Message> Třída má být abstraktní reprezentace zprávy, ale jeho návrhu je důrazně vázaný na zprávu protokolu SOAP. A <xref:System.ServiceModel.Channels.Message> obsahuje tři hlavní údaje: text zprávy, hlavičky zpráv a vlastnosti zprávy.  
  
## <a name="message-body"></a>Tělo zprávy  
 Text zprávy je určený k reprezentaci skutečná data datovou část zprávy. Text zprávy je vždy reprezentován jako informační sadu XML. To neznamená, že všechny zprávy vytvořené nebo dostali [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musí být ve formátu XML. Je zásobník kanál k rozhodování o tom, jak interpretovat obsah zprávy. Může emitování jako XML, převést na jiném formátu nebo i zcela vynechejte. Samozřejmě s většinou vazby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zdroje, tělo zprávy je reprezentován jako obsah XML v části tělo obálky protokolu SOAP.  
  
 Je důležité si uvědomit, který `Message` třída nemusí obsahovat vyrovnávací paměť s daty XML představující text. Logicky `Message` obsahuje informační sadu XML, ale tento informační sadu dynamicky zkonstruovat a může existovat nikdy fyzicky v paměti.  
  
### <a name="putting-data-into-the-message-body"></a>Ukládání dat do textu zprávy  
 Neexistuje žádný uniform mechanismus dávat data do textu zprávy. <xref:System.ServiceModel.Channels.Message> Třída obsahuje metody abstraktní <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, které trvá <xref:System.Xml.XmlDictionaryWriter>. Každý podtřídou třídy <xref:System.ServiceModel.Channels.Message> třída je odpovědná za potlačení této metody a zápis na svůj vlastní obsah. Tělo zprávy obsahuje logicky informační sadu XML, `OnWriteBodyContent` vytváří. Například vezměte v úvahu následující `Message` podtřídy.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fyzicky `AirfareRequestMessage` instance obsahuje pouze dva řetězce ("fromCity" a "toCity"). Však logicky zpráva obsahuje následující informační sadu XML:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Samozřejmě nejsou obvykle vytvoříte zprávy tímto způsobem, protože rozhraní služby můžete použít k vytvoření kontraktu parametry zpráva podobná té předchozí z operace. Kromě toho <xref:System.ServiceModel.Channels.Message> třída má statické `CreateMessage` metody, které můžete použít k vytvoření zpráv s běžnými typy obsahu: prázdný zprávy, zprávu, která obsahuje objekt serializován do formátu XML s <xref:System.Runtime.Serialization.DataContractSerializer>, zprávu, která obsahuje SOAP poruch, zprávu, který obsahuje XML reprezentována <xref:System.Xml.XmlReader>a tak dále.  
  
### <a name="getting-data-from-a-message-body"></a>Získání dat z text zprávy  
 Můžete rozbalit data uložená v textu zprávy dvěma hlavními způsoby:  
  
-   Můžete získat obsah celé zprávy najednou voláním <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> metoda a předávání zapisovače XML. Tělo zprávy dokončení je zapsána na tento modul pro zápis. Získávání obsah celé zprávy v jednom okamžiku se také nazývá *zápis zprávy*. Zápis je potřeba především kanál zásobníku při odesílání zpráv – některé části zásobníku v kanálu se obvykle získat přístup k tělu celé zprávy, zakódovat je a odeslat.  
  
-   Jiný způsob, jak získat informace o text zprávy je volání <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> a získat čtecí modul XML. Tělo zprávy lze poté přistupovat postupně podle potřeby voláním metod v programu pro čtení. Získávání zprávu textu část jednotlivé se taky říká *čtení zprávy*. Čtení zprávy slouží především rozhraní služby při přijímání zprávy. Například když <xref:System.Runtime.Serialization.DataContractSerializer> je používán, bude rozhraní služby získat čtecí modul XML přes text a předejte ji do deserializace modul, který se pak spustí čtení zpráv element podle elementu a vytváření odpovídající grafu objektu.  
  
 Tělo zprávy mohou být načteny pouze jednou. To umožňuje pracovat s datovými proudy dopředné. Můžete například napsat <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> přepsání, který čte z <xref:System.IO.FileStream> a vrátí výsledky jako informační sadu XML. Musíte nikdy "rewind" na začátek souboru.  
  
 `WriteBodyContents` a `GetReaderAtBodyContents` metody jednoduše zkontrolujte, zda nikdy nebyly načtené před text zprávy a pak zavolají `OnWriteBodyContents` nebo `OnGetReaderAtBodyContents`, v uvedeném pořadí.  
  
## <a name="message-usage-in-wcf"></a>Využití zprávy ve WCF  
 Většina zprávy mohou být klasifikovány jako buď *odchozí* (ty, které jsou vytvořené pomocí rozhraní služby je odeslal zásobníku kanál) nebo *příchozí* (ty, které přicházejí z tohoto kanálu zásobníku a jsou interpretovat rozhraní služby). Kromě toho zásobníku kanál můžou fungovat v režimu ve vyrovnávací paměti nebo streamování. Architektura služby může také vystavit přenášené datovými proudy nebo nonstreamed programovací model. To vede k případy uvedené v následující tabulce, společně s zjednodušené podrobnosti o jejich implementaci.  
  
|Typ zprávy|Data text ve zprávě|Zapsat implementace (OnWriteBodyContents)|Implementace pro čtení (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Odchozí, vytvořené z nonstreamed programovací model|Data potřebná k zápisu zprávy (například objekt a <xref:System.Runtime.Serialization.DataContractSerializer> instance, které jsou potřebné k serializaci ji) *|Vlastní logika k zapsání zprávy založené na uložená data (například volání `WriteObject` na `DataContractSerializer` případě serializátoru, který je používán) *|Volání `OnWriteBodyContents`, výsledky ukládat do vyrovnávací paměti, vraťte se čtecí modul XML přes vyrovnávací paměti|  
|Odchozí, vytvořené z přenášené datovými proudy programovací model|`Stream` s daty, která má být zapsán *|Zápis dat z datového proudu uložené pomocí <xref:System.Xml.IStreamProvider> mechanismus *|Volání `OnWriteBodyContents`, výsledky ukládat do vyrovnávací paměti, vraťte se čtecí modul XML přes vyrovnávací paměti|  
|Příchozí z datových proudů kanál zásobníku|A `Stream` objekt, který představuje data procházející přes síť s <xref:System.Xml.XmlReader> nad ním|Zapsat obsah z uložené `XmlReader` pomocí `WriteNode`|Vrátí uložené `XmlReader`|  
|Příchozí z nonstreaming kanál zásobníku|Vyrovnávací paměť, která obsahuje data textu s `XmlReader` nad ním|Zapíše obsah z uložené `XmlReader` pomocí `WriteNode`|Vrátí uložené jazyk|  
  
 \* Tyto položky nejsou implementované přímo v `Message` podtřídy, ale v podtřídách z <xref:System.ServiceModel.Channels.BodyWriter> třídy. Další informace o <xref:System.ServiceModel.Channels.BodyWriter>, najdete v části [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Hlavičky zpráv  
 Zpráva může obsahovat záhlaví. Záhlaví logicky se skládá z XML informační sadu, která souvisí s název oboru názvů a několik dalších vlastností. Hlavičky zpráv ke kterým se přistupuje pomocí `Headers` vlastnost <xref:System.ServiceModel.Channels.Message>. Každá hlavička je reprezentována <xref:System.ServiceModel.Channels.MessageHeader> třídy. Za normálních okolností hlavičky zpráv jsou namapované na záhlaví zprávy SOAP při použití kanálu zásobníku, nakonfigurováno pro práci s protokolu SOAP zprávy.  
  
 Vložení informací do záhlaví zprávy a extrahování informací z ní je podobný používání tělo zprávy. Proces je poněkud jednodušší, protože streamování není podporován. Je možné k přístupu k obsahu stejné hlavičky více než jednou a hlavičky jsou přístupné z libovolného pořadí, vynucení záhlaví vždycky být ukládán do vyrovnávací paměti. Neexistuje žádný pro obecné účely mechanismus, který je k dispozici pro získání čtecí modul XML na záhlaví, ale je `MessageHeader` vnitřní podtřídy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čitelný hlavička s takové funkce, která představuje. Tento typ `MessageHeader` zásobníku kanálu se vytvoří, když zprávu s vlastní aplikaci hlavičky se dodává. To umožňuje architektura služby použít modul deserializace, jako <xref:System.Runtime.Serialization.DataContractSerializer>, interpretovat tyto hlavičky.  
  
 Další informace najdete v tématu [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Vlastnosti zprávy  
 Zpráva může obsahovat vlastnosti. A *vlastnost* libovolnou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekt, který je přidružen názvu řetězce. Vlastnosti jsou přístupné prostřednictvím `Properties` vlastnost `Message`.  
  
 Na rozdíl od tělo zprávy a hlavičky zpráv (které obvykle mapování na textu protokolu SOAP a hlavičky SOAP, v uvedeném pořadí) jsou vlastnosti zprávy, které nejsou obvykle odesílané nebo přijímané společně s zprávy. Vlastnosti zprávy existovat především jako mechanismus komunikace k předávání dat o zprávy mezi různými kanály v zásobníku kanál a mezi zásobník kanál a model služby.  
  
 Například HTTP přenosu channel, které jsou součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je schopné různé stavové kódy HTTP, jako například "404 (není nalezena)" a "500 (vnitřní chyba serveru)," při odesílání odpovědi na klienty. Před odesláním zprávy s odpovědí, zkontroluje, zda `Properties` z `Message` obsahovat vlastnost s názvem "httpResponse", který obsahuje objekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Pokud je tato vlastnost nalezena, bude vypadat na <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> vlastnost a použít tento kód stavu. Pokud nebyl nalezen, výchozí hodnota "200 (OK)" kód používá.  
  
 Další informace najdete v tématu [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Zprávu jako celek  
 Pokud budeme mít popsané metody pro přístup k různých částí zprávy v izolaci. Ale <xref:System.ServiceModel.Channels.Message> třída rovněž poskytuje metody pro práci s celé zprávy jako celek. Například `WriteMessage` Metoda zapíše celou zprávu do zapisovače XML.  
  
 Chcete-li to možné, musí být definován mapování mezi celý `Message` instance a informační sadu XML. Mapování, ve skutečnosti existuje: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá k definování toto mapování standard protokolu SOAP. Když `Message` instance zapisuje jako informační sadu XML informační výslednou sadu je platný obálku protokolu SOAP, který obsahuje zprávu. Proto `WriteMessage` by za normálních okolností proveďte následující kroky:  
  
1.  Zápis počáteční značce elementu obálky protokolu SOAP.  
  
2.  Zápis element header SOAP počáteční značce, vypsat všechny hlavičky a zavřete header element.  
  
3.  Zápis textu elementu SOAP počáteční značce.  
  
4.  Volání `WriteBodyContents` nebo metodu ekvivalentní k zapsání textu.  
  
5.  Zavřete elementy textu a obálku.  
  
 Předchozí kroky jsou podrobně svázané s standard protokolu SOAP. Toto je složitá fakt, že více verzí protokolu SOAP existují, například je možné zapsat element obálky protokolu SOAP správně bez znalosti verze protokolu SOAP používá. Také v některých případech může být žádoucí vypnutí této komplexní SOAP konkrétní mapování úplně.  
  
 Pro tyto účely `Version` vlastnost je k dispozici na `Message`. Může být nastaven na verzi protokolu SOAP k použití při zápisu zprávu nebo může být nastaven na `None` aby veškerá jeho mapování specifické protokolu SOAP. Pokud `Version` je nastavena na `None`, metody, které pracují se celá zpráva act jako, pokud zpráva se skládal z jeho text, například `WriteMessage` by jednoduše volání `WriteBodyContents` namísto provádění více kroků uvedených výše. Očekává se, které příchozí zprávy `Version` bude automaticky nalezeny a správně nastavené.  
  
## <a name="the-channel-stack"></a>Kanál zásobníku  
  
### <a name="channels"></a>Kanály  
 Jak jsme uvedli před, zásobník kanál je zodpovědná za převod odchozí <xref:System.ServiceModel.Channels.Message> instance do některé akce (například odesílání paketů přes síť) nebo převodem některé akce (např. přijetí síťových paketů) na příchozí `Message` instance.  
  
 Kanál zásobníku se skládá z jeden nebo více kanálů v pořadí řazení. Odchozí `Message` instance předána první kanál v zásobníku (také nazývané *nejhornější kanál*), který předává je na další kanál v zásobníku a tak dále. Zpráva se ukončuje v poslední kanál, který se nazývá *kanál přenosu*. Příchozí zprávy pochází z kanál přenosu a jsou předávány z kanálu na kanál nahoru v zásobníku. Z tohoto kanálu nejhornější je předán do rozhraní služby obvykle zprávy. To je obvykle vzor pro zprávy aplikace, některé kanály může fungovat trochu jinak, například se může odesílat své vlastní zprávy infrastruktury bez předávány zprávu z výše uvedených kanál.  
  
 Kanály může fungovat na zprávu různými způsoby podle projdou zásobníku. Nejběžnější operaci je přidání hlavičky odchozí zprávy a čtení hlavičky na příchozí zprávy. Kanál může například výpočetní digitální podpis zprávy a přidejte jej jako hlavičku. Kanál může také prohlédnout tuto hlavičku digitální podpis na příchozí zprávy a bloku zpráv, které neobsahuje platný podpis provádět jejich představ až zásobníku kanálu. Kanály také často nastavte nebo zkontrolujte vlastnosti zprávy. Text zprávy se obvykle nemění, i když je to povoleno, například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečený kanál můžete šifrovat obsah zprávy.  
  
### <a name="transport-channels-and-message-encoders"></a>Přenosové kanály a kodéry zpráv  
 Nejspodnějších kanál v zásobníku zodpovídá za ve skutečnosti transformace odchozí <xref:System.ServiceModel.Channels.Message>, jak upravit podle dalších kanálů na některé akce. Na straně příjmu, to je kanál, který převede do některé akce `Message` , jiné nástroje procesu.  
  
 Jak jsme uvedli dříve, může být nejrůznější akce: odesílání nebo přijímání síťových paketů pomocí různých protokolů, čtení nebo zápisu se zprávou v databázi, nebo služby Řízení front nebo vyřazení zprávu ve frontě služby Řízení front zpráv, zajistit ale několik příkladů. Všechny tyto akce mají společnou jednou z věcí: vyžadují transformace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Message` instance a skupinu skutečného bajtů, které lze odeslat, přijme, číst, zapisovat, zařazených do fronty nebo vyjmutou. Proces převodu `Message` do skupiny bajtů se nazývá *kódování*a zpětnou procesem vytvoření `Message` ze skupiny bajtů je volána *dekódování*.  
  
 Většina přenosové kanály pomocí součásti názvem *zprávy kodéry* provedete kódování a dekódování pracovní. Kodér zpráv je podtřídou třídy <xref:System.ServiceModel.Channels.MessageEncoder> třídy. `MessageEncoder` zahrnuje různé `ReadMessage` a `WriteMessage` přetížení metody pro převod mezi `Message` a skupiny bajtů.  
  
 Na straně odesílání vyrovnávací paměti přenosu kanálu předá `Message` objekt, který obdržel z kanál nad jeho `WriteMessage`. Získá zpět pole bajtů, které se pak použije k jeho akci (například balení těchto bajtů jako platný pakety TCP a je pošlete na správnou cílovou). Streamování přenosu kanál, který první vytvoří `Stream` (například přes odchozí připojení TCP) a pak předá i `Stream` a `Message` musí se poslat odpovídající `WriteMessage` přetížení, která zapíše zpráva .  
  
 Na straně příjmu vyrovnávací paměti kanál přenosu extrahuje Příchozí bajty (například z příchozí pakety TCP) do pole a volání `ReadMessage` získat `Message` objektu, že můžete předat další až zásobníku kanálu. Streamování přenosu kanál, který vytvoří `Stream` objektu (například síť datového proudu prostřednictvím příchozí připojení protokolu TCP) a předá to `ReadMessage` a vraťte se zpět `Message` objektu.  
  
 Oddělení mezi přenosové kanály a kodér zpráv není povinné; je možné zapisovat přenosu kanálu, který nepoužívá kodéru zprávy. Výhodou tohoto oddělení je však snadné sestavení. Tak dlouho, dokud přenos kanál, který používá jenom základní <xref:System.ServiceModel.Channels.MessageEncoder>, můžete spolupracovat s kterýmkoli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo kodér zpráv třetích stran. Podobně stejné kodér normálně lze v jakékoli kanál přenosu.  
  
### <a name="message-encoder-operation"></a>Operace kodéru zpráv  
 K popisu typické operaci kodér, je vhodné vzít v úvahu následující čtyři případy.  
  
|Operace|Komentář|  
|---------------|-------------|  
|Kódování, uložená do vyrovnávací paměti|Kodér v režim s vyrovnávací pamětí, obvykle vytvoří proměnlivé velikosti vyrovnávací paměti a poté vytvoří zapisovače XML nad ním. Potom zavolá <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> na zprávu zakódování, který zapisuje hlavičky a potom na textu pomocí <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, jak je popsáno v předchozí části o `Message` v tomto tématu. Pro přenos kanálu pro použití se pak vrátí obsah vyrovnávací paměti (vyjádřený jako pole bajtů).|  
|Kódování, streamování|Operace je v režimu přenášené datovými proudy, podobně jako výše, ale jednodušší. Není nutné vyrovnávací paměti. Zapisovače XML se obvykle vytvoří prostřednictvím datového proudu a <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> se volá na `Message` k zapsání do tohoto zapisovače.|  
|Dekódování, uložená do vyrovnávací paměti|Při dekódování režim s vyrovnávací pamětí, speciální `Message` podtřídami, který obsahuje data ve vyrovnávací paměti se obvykle vytvoří. Jsou přečteny hlavičky zprávy a vytvoření čtecí modul XML, který je umístěný v textu zprávy. Toto je čtecí modul, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Dekódování, streamování|Při dekódování přenášené datovými proudy režimu, se obvykle vytvoří speciální zprávy podtřídy. Datový proud je rozšířený právě dostatek číst všechny hlavičky a pozice v textu zprávy. Program pro čtení XML se pak vytvoří prostřednictvím datového proudu. Toto je čtecí modul, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodéry mohou provádět také další funkce. Například kodéry může vytvořit fond XML čtení a zápis. Je nákladné pokaždé, když je zapotřebí vytvořit nový čtecí modul XML nebo zapisovač. Proto kodéry normálně udržovat fond čtečky a fond zapisovače konfigurovat velikost. V popisech kodér operace popsané vždy, když frázi "vytvořit čtecí modul XML nebo zapisovač" se používá, obvykle znamená "provést jednu z fondu, nebo, pokud žádný není k dispozici vytvořit." Kodér (a `Message` podtřídy vytvoří při dekódování) obsahují logiku vrátit čtení a zápis do fondů, jakmile už nejsou potřeba (například když `Message` je uzavřený).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje tři kodéry zpráva, i když je možné vytvořit další vlastní typy. Zadané typy jsou Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM). Tyto možnosti jsou popsány v části [výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Rozhraní IStreamProvider  
 Při psaní odchozí zprávy, který obsahuje přenášené datovými proudy text do zapisovače XML <xref:System.ServiceModel.Channels.Message> používá pořadí volání podobný následujícímu v jeho <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementace:  
  
-   Zapsat všechny potřebné informace předcházející datového proudu (například otevírání – značka XML).  
  
-   Zápis do datového proudu.  
  
-   Zapisovat všechny informace o následujících datového proudu (například ukončovací značka XML pro dokumentaci).  
  
 To funguje dobře u kódování, které jsou podobné textové kódování XML. Ale některé kódování Neumísťujte informační XML sadu informace (například značky pro počáteční a koncovou elementů XML) společně s data obsažená v rámci prvků. Například v kódování MTOM, je zpráva rozdělit do několika částí. Část obsahuje informační sadu XML, který může obsahovat odkazy na další části skutečným prvkem obsah. Informační sadu XML je obvykle malé ve srovnání s přenášené datovými proudy obsah, má smysl vyrovnávací paměti informační sadu, ho zapsat a zapište si obsah přenášené datovými proudy způsobem. To znamená, že v době ukončovací značky elementu je zapsán, do datového proudu by neměla mít byla zapsána ještě.  
  
 Pro tento účel <xref:System.Xml.IStreamProvider> použít rozhraní. Rozhraní má <xref:System.Xml.IStreamProvider.GetStream> metodu, která vrátí datového proudu má být proveden zápis. Správný způsob zapsat text zprávy přenášené datovými proudy v <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> vypadá takto:  
  
1.  Zapsat všechny potřebné informace předcházející datového proudu (například otevírání – značka XML).  
  
2.  Volání `WriteValue` přetížení na <xref:System.Xml.XmlDictionaryWriter> , která má <xref:System.Xml.IStreamProvider>, se `IStreamProvider` implementace, která vrátí datového proudu má být proveden zápis.  
  
3.  Zapisovat všechny informace o následujících datového proudu (například ukončovací značka XML pro dokumentaci).  
  
 S tímto přístupem zapisovače XML má vybrat, kdy se má volat <xref:System.Xml.IStreamProvider.GetStream> a zapsat datové proudy. Například zapisovače XML textové a binární zavolá ho okamžitě a zapsat přenášené datovými proudy obsah mezi počáteční a koncové značky. Zapisovač MTOM rozhodnout pro volání <xref:System.Xml.IStreamProvider.GetStream> později, až bude program připraven k zápisu odpovídající část zprávy.  
  
## <a name="representing-data-in-the-service-framework"></a>Reprezentující Data v rámci služby  
 Jak je uvedeno v části "Základní architekturu" v tomto tématu, architektura služby je ta část [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mimo jiné, která je zodpovědná za převod mezi uživatelsky přívětivý programovací model pro zprávu dat a aktuální `Message` instance. Za normálních okolností představuje zprávu exchange v rámci služby jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metoda označena <xref:System.ServiceModel.OperationContractAttribute> atribut. Metoda může trvat v některé parametry a může vrátit návratovou hodnotu nebo se parametry (nebo oba). Na straně služby vstupní parametry představují příchozí zprávy a návratovou hodnotu a výstupní parametry představují odchozí zprávy. Na straně klienta platí opačně. Programovací model pro s popisem zprávy pomocí parametry a návratové hodnoty je podrobně popsaná v [zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). V této části se však zadejte stručný přehled.  
  
## <a name="programming-models"></a>Modely programování  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Architektura služby podporuje pět různých programovacích modelů popisující zprávy:  
  
### <a name="1-the-empty-message"></a>1. Prázdná zpráva  
 Toto je nejjednodušším případě. K popisu prázdný příchozí zprávy, nepoužívejte žádné vstupní parametry.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 K popisu prázdný odchozí zprávy, použijte void návratovou hodnotu a nepoužívejte žádný výstupní parametry:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Všimněte si, že se to neliší od kontraktu Jednosměrná operace:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 V `SetDesiredTemperature` například vzorce výměny zpráv obousměrný je popsáno. Zpráva je vrácená z operace, ale je prázdný. Je možné vrátit chybu z operace. V příkladu "Nastavit žárovek" je jednosměrný, vzorce výměny zpráv, takže není žádná odchozí k popisu. Služba nemůže komunikovat v tomto případě žádné stavu zpět do klienta.  
  
### <a name="2-using-the-message-class-directly"></a>2. Používání třídy Message přímo  
 Je možné použít <xref:System.ServiceModel.Channels.Message> – třída (nebo jeden z jejích podtříd) přímo operaci kontrakt. V takovém případě jednoduše předají rozhraní služby `Message` z operace se zásobníkem kanál a naopak a žádné další zpracování.  
  
 Jsou dva případy nejčastěji se využívá pro používání `Message` přímo. Můžete to pro pokročilé scénáře, pokud žádná z s programovacími modely poskytuje dostatek flexibilitu k popisu zprávy. Například můžete chtít použít soubory na disku k popisu zprávy, s vlastností souboru stal hlavičky zpráv a jeho obsah stal tělo zprávy. Potom můžete vytvořit něco podobný následujícímu.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Druhý nejběžnější použít pro `Message` ve smlouvě operaci je při služby není záleží na konkrétní zprávu obsah a funguje na zprávu jako na černé políčko. Například můžete mít služby, který přeposílá zprávy několika dalších příjemcům. Takto lze zapsat kontrakt.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Akce = "*" řádku efektivně vypne odeslání zpráv a zajistí, že všechny zprávy odeslané do `IForwardingService` kontrakt zkontrolujte jejich způsob, jak `ForwardMessage` operaci. (Za normálních okolností dispečera by Zkontrolujte záhlaví zprávy "Action" k určení operace, která je určena pro. Akce = "\*" znamená "všech možných hodnot hlavičky akce".) Kombinace akce = "\*" a pomocí zprávy jako parametr se označuje jako "universal kontrakt", protože je schopný přijímat všechny možné zprávy. Abyste mohli odeslat všechny možné zprávy, zprávu použít jako návratová hodnota a nastavte `ReplyAction` na "\*". Tím se zabrání rozhraní služby přidání vlastní hlavičky akce umožňuje řídit tento záhlaví pomocí `Message` objektu vrátíte.  
  
### <a name="3-message-contracts"></a>3. Kontrakty zpráv  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje deklarativní programovací model pro s popisem zprávy, označované jako *zprávy kontrakty*. Tento model je podrobně popsaná v [pomocí kontrakty zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). V podstatě představuje celé zprávy jedné [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ, který používá atributů, například <xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute> k popisu, které části třídou kontraktu zpráva by měla být mapována ke které části zprávy.  
  
 Kontrakty zpráv poskytují spoustu kontrolu nad výsledná `Message` instance (i když samozřejmě mnohem ovládací prvek, pomocí `Message` přímo třídu). Například těla zprávy jsou často skládá z více položek informací, každý reprezentován vlastní – element XML. Tyto prvky může dojít, buď přímo v těle (*úplné* režim), případně může být *zabalené* včetně elementu XML. Pomocí kontrakt zprávy programovací model umožňuje provést úplné porovnání zabalené rozhodnutí a řídit název obálku názvem a oborem názvů.  
  
 Kontrakt zprávy na následující příklad kódu ukazuje tyto funkce.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Položky označena k serializaci (s <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, nebo dalších atributů v relaci) musí být serializovatelný zapojit se do kontrakt zprávy. Další informace najdete v části "Serializace" dál v tomto tématu.  
  
### <a name="4-parameters"></a>4. Parametry  
 Vývojáři, který chce popisují operaci, která funguje na více částí dat často, není nutné stupeň kontroly, které poskytují kontrakty zpráv. Například při vytváření nové služby, jeden nechce obvykle provést úplné porovnání zabalené rozhodnutí a rozhodnout, název elementu obálku. Tyto rozhodování často vyžaduje hluboké znalosti webových služeb a protokolu SOAP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Architektura služby můžete automaticky vybrat nejlepší a interaktivní reprezentace SOAP pro odesílání nebo přijímání více souvisejících řadu informací, bez vynucení tyto volby na uživatele. To se provádí jednoduše popisující tyto údaje jako parametry nebo návratové hodnoty operaci kontrakt. Zvažte například následující operace kontrakt.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Architektura služby automaticky rozhoduje uvést všechny tři údaje (`customerID`, `item`, a `quantity`) do text zprávy a wrap je v elementu obálky s názvem `SubmitOrderRequest`.  
  
 Popisuje informace, které mají být odesílané nebo přijímané jako jednoduchý seznam parametrů kontrakt operaci se o doporučený postup, pokud existují zvláštní důvody pro přesun do kontrakt zprávy složitější nebo `Message`– na základě programovacích modelů.  
  
### <a name="5-stream"></a>5. Stream  
 Pomocí `Stream` nebo jeden z jeho podtřídy ve smlouvě operaci nebo jako jedinou zpráva části textu v kontrakt zprávy lze považovat za samostatný programovací model z těm, které jsou popsané výše. Pomocí `Stream` tímto způsobem je jediný způsob, jak zaručit, že smlouva bude možné použít přenášené datovými proudy způsobem souborem zápis vlastní streamování kompatibilní s `Message` podtřídy. Další informace najdete v tématu [velkého množství dat a Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Když `Stream` nebo jeden z jeho podtřídy tímto způsobem je použít, není vyvolána serializátor. Odchozí zprávy, speciální streamování `Message` podtřídami je vytvořen a je do datového proudu odhlašování, jak je popsáno v části na zapisovat <xref:System.Xml.IStreamProvider> rozhraní. Pro příchozí zprávy, vytvoří rozhraní služby `Stream` podtřídami přes příchozí zprávy a poskytuje pro operaci.  
  
## <a name="programming-model-restrictions"></a>Omezení modelu programování  
 Nahodile nelze kombinovat s programovacími modely popsané výše. Například pokud operace přijímá typ kontrakt zprávy, kontrakt zprávy musí být jeho jenom vstupní parametr. Kromě toho musí operaci pak vrátí zprávu prázdný (návratový typ void) nebo jiné zprávy kontrakt. Tato omezení programovací model jsou popsané v tématech pro každou konkrétní programovací model: [pomocí kontrakty zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), a [velkého množství dat a datových proudů ](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formátování zpráv  
 Programovací modely popsané výše jsou podporovány zapojením v součásti názvem *zprávy formátování* do rozhraní služby. Formátování zpráv jsou typy, které implementují <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> nebo <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní, nebo obojí, pro použití v klienti a služba [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, v uvedeném pořadí.  
  
 Formátování zpráv jsou obvykle zapojen podle chování. Například <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> připojuje ve formátovacím modulu dat kontrakt zprávy. To se provádí na straně služby nastavením <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> do správné formátování v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metoda, nebo na straně klienta nastavením <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> do správné formátování v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> metoda.  
  
 V následujících tabulkách jsou uvedené metody, které může implementovat formátování zprávy.  
  
|Rozhraní|Metoda|Akce|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede příchozí `Message` operaci parametry|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Vytvoří odchozí `Message` z operace návratová hodnota/out parametry|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Vytvoří odchozí `Message` z parametry operace|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede příchozí `Message` do návratovou hodnotu nebo výstupní parametry|  
  
## <a name="serialization"></a>Serializace  
 Vždy, když používáte kontrakty zpráv nebo parametry k popisu obsah zprávy, musíte použít serializace pro převod mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a reprezentaci XML informační sadu. Serializace se používá na jiných místech [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], například <xref:System.ServiceModel.Channels.Message> má obecný <xref:System.ServiceModel.Channels.Message.GetBody%2A> metodu, kterou můžete použít k načtení celého obsahu zprávy deserializovat do objektu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje dvě technologie serializace "předinstalované" pro serializaci a deserializaci parametry a částí zprávy: <xref:System.Runtime.Serialization.DataContractSerializer> a `XmlSerializer`. Kromě toho můžete napsat vlastní serializátorů. Však dalších částí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (například obecná `GetBody` metoda nebo SOAP poruch serializace) může být omezen na používání jenom <xref:System.Runtime.Serialization.XmlObjectSerializer> podtřídy (<xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer>, ale ne <xref:System.Xml.Serialization.XmlSerializer>), nebo může být i pevně zakódovaná na používání jenom <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Se používá pro Serializační stroj v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby. `DataContractSerializer` Je nové Serializační stroj, že jste srozuměni s tím nový model programování kontraktu dat. `DataContractSerializer` výchozí volba, a rozhodnout použít pro `XmlSerializer` můžete provedeny na každou operaci zvlášť pomocí <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atribut.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> odpovídají operaci chování pro zapojení formátování zpráv pro `DataContractSerializer` a `XmlSerializer`, v uvedeném pořadí. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Chování lze provozovat ve skutečnosti se žádné serializátor, která je odvozena od <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.NetDataContractSerializer> (podrobně popsané v pomocí samostatného serializace). Chování volání mezi `CreateSerializer` přetížení virtuální metody k získání serializátoru. Zařadit jiný serializátor, vytvořte novou <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podtřídami a přepsání `CreateSerializer` přetížení.  
  
## <a name="see-also"></a>Viz také  
 [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
