---
title: Strukturální přehled přenosu dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: 22d2ce71d850fc799304cadf7e8d7d8af2670d5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856588"
---
# <a name="data-transfer-architectural-overview"></a>Strukturální přehled přenosu dat
Windows Communication Foundation (WCF) můžete představit jako infrastruktura zasílání zpráv. Může přijímat zprávy, zpracovat je a jejich vypravování do uživatelského kódu pro další akce, nebo můžete vytvořit zprávy z dat zadané v uživatelském kódu a doručujte je na cíli. Toto téma, které je určené pro pokročilé vývojáře, popisuje architekturu zpracování zpráv a omezením data. Jednodušší, orientovaných zobrazení toho, jak odesílat a přijímat data, najdete v části [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Toto téma popisuje podrobnosti implementace WCF, které nejsou viditelné prozkoumáním objektový model WCF. Dvě slova upozornění jsou v pořadí s ohledem na podrobnosti implementace dokument. Popisy jsou nejprve zjednodušené; Skutečná implementace může být složitější z důvodu optimalizace nebo z jiných důvodů. Za druhé, můžete se nikdy spoléhají na podrobnosti konkrétní implementace, dokonce i uvedeno, protože ty můžou změnit bez předchozího upozornění z verze na verzi nebo dokonce i v servisní verze.  
  
## <a name="basic-architecture"></a>Základní architektura  
 V jádru možnosti zpracování zpráv WCF je <xref:System.ServiceModel.Channels.Message> třída, která je popsána v části [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Běhové komponenty technologie WCF je možné rozdělit do dvou hlavních částí: zásobník kanálu a architektura služby s <xref:System.ServiceModel.Channels.Message> třídy se spojovací bod.  
  
 Kanál zásobníku je zodpovědný za převod mezi platné <xref:System.ServiceModel.Channels.Message> instance a některá z akcí, která odpovídá odesílání nebo přijímání dat zprávy. Na straně odesílání trvá kanál zásobníku platný <xref:System.ServiceModel.Channels.Message> instance a po nějaké zpracování provede určitou akci, která odpovídá logicky k odeslání zprávy. Akce může odesílat TCP nebo HTTP paketů služby Řízení front zpráv služby Řízení front zpráv, zápis zprávy do databáze, ukládání do sdílené složky nebo jakoukoli jinou akci, v závislosti na implementaci. Nejběžnější akce odesílá zprávy přes síťový protokol. Na straně příjmu se stane opak – akce je zjištěna (který může být pakety TCP nebo HTTP přijaté nebo jakoukoli jinou akci), a po zpracování kanálu zásobníku převádí tuto akci platný <xref:System.ServiceModel.Channels.Message> instance.  
  
 Můžou využít WCF pomocí <xref:System.ServiceModel.Channels.Message> třídy a kanál zásobníku přímo. To uděláte tak ale obtížné a časově náročné. Kromě toho <xref:System.ServiceModel.Channels.Message> objekt nepodporuje metadata, takže se silnými typy klientů WCF nelze generovat, pokud používáte WCF tímto způsobem.  
  
 Proto WCF obsahuje rozhraní služby, které poskytuje snadným ovládáním programovací model, který vám pomůže vytvořit a přijímat `Message` objekty. Architektura služby map služeb [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů prostřednictvím pojem kontrakty služeb a odesílá zprávy do operace uživatelů, které jsou jednoduše [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody označené <xref:System.ServiceModel.OperationContractAttribute> atribut (Další podrobnosti najdete v tématu [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)). Tyto metody mohou mít parametry a vracet hodnoty. Na straně služeb, převede příchozí architektura služby <xref:System.ServiceModel.Channels.Message> instancí do parametrů a převede návratové hodnoty do odesílaných <xref:System.ServiceModel.Channels.Message> instancí. Na straně klienta se provádí opak. Představme si třeba, `FindAirfare` operace níže.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Předpokládejme, že `FindAirfare` volá se na klientovi. Architektura služby na straně klienta převede `FromCity` a `ToCity` parametry do odchozí <xref:System.ServiceModel.Channels.Message> instance a předá ji do zásobníku kanálu k odeslání.  
  
 Na straně služeb když <xref:System.ServiceModel.Channels.Message> instance e-mailu ze zásobníku kanál, architektura služby extrahuje relevantní data ze zprávy k naplnění `FromCity` a `ToCity` parametry a potom volání straně služby `FindAirfare` Metoda. Po návratu metody rozhraní služby trvá vrácené celočíselné hodnotě a `IsDirectFlight` výstupní parametr a vytvoří <xref:System.ServiceModel.Channels.Message> instance objektu, který obsahuje tyto informace. Pak předá `Message` instanci kanálu zásobníku odeslána zpět klientovi.  
  
 Na straně klienta <xref:System.ServiceModel.Channels.Message> instance, která obsahuje zprávy s odpovědí vyplývá ze zásobníku kanálu. Architektura služby extrahuje návratovou hodnotu a `IsDirectFlight` hodnotu a vrátí do volajícího klienta.  
  
## <a name="message-class"></a>Message – třída  
 <xref:System.ServiceModel.Channels.Message> Třída je zamýšlená jako abstraktní reprezentaci zprávy, ale jeho návrhu se silnou vazbu na zprávu protokolu SOAP. A <xref:System.ServiceModel.Channels.Message> obsahuje tři hlavní údaje: text zprávy, záhlaví zpráv a vlastnosti zprávy.  
  
## <a name="message-body"></a>Text zprávy  
 Text zprávy je určený k reprezentaci skutečná data datové části zprávy. Text zprávy je vždy reprezentována jako informační sadu XML. To neznamená, že všechny zprávy vytvořené ani přijmout ve službě WCF musí být ve formátu XML. Záleží zásobníku kanálu se rozhodnout, jak interpretovat obsah zprávy. Může generovat ve formátu XML, převeďte jej na jiném formátu nebo ještě ji vynechte úplně. S největším počtem dodávek vazby WCF, samozřejmě, text zprávy je vyjádřena jako obsah XML v části tělo obálky protokolu SOAP.  
  
 Je důležité si uvědomit, `Message` třídy nezbytně nemusí obsahovat vyrovnávací paměti s daty XML představující tělo. Logicky `Message` obsahuje informační sadu XML, ale tento informační sadu dynamicky vytvořený a můžou existovat nikdy fyzicky v paměti.  
  
### <a name="putting-data-into-the-message-body"></a>Ukládání dat do datové části zprávy  
 Neexistuje žádný jednotný mechanismus k vložení dat do textu zprávy. <xref:System.ServiceModel.Channels.Message> Třída je abstraktní metody, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, který přebírá <xref:System.Xml.XmlDictionaryWriter>. Každá podtřída <xref:System.ServiceModel.Channels.Message> třídy je zodpovědná za potlačení této metody a zápis vlastní obsah. Tělo zprávy obsahuje logicky informační sadu XML, který `OnWriteBodyContent` vytvoří. Představte si třeba následující `Message` podtřídy.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fyzicky `AirfareRequestMessage` instance obsahuje pouze dva řetězce ("fromCity" a "toCity"). Však logicky zpráva obsahuje následující informační sadu XML:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Samozřejmě nejsou obvykle vytvoříte zprávy tímto způsobem, protože architektura služby můžete použít k vytvoření zprávy jako na předchozím z operace kontraktu parametry. Kromě toho <xref:System.ServiceModel.Channels.Message> třída má statické `CreateMessage` metody, které můžete použít k vytvoření zpráv pomocí běžných typů obsahu: prázdný zprávy, zprávu, která obsahuje objekt serializován do formátu XML s <xref:System.Runtime.Serialization.DataContractSerializer>, zprávu, která obsahuje SOAP selhání, zprávu, která obsahuje kód XML reprezentována <xref:System.Xml.XmlReader>, a tak dále.  
  
### <a name="getting-data-from-a-message-body"></a>Získání dat z textu zprávy  
 Můžete extrahovat data uložená v textu zprávy dva hlavní způsoby:  
  
- Obsah celé zprávy najednou můžete získat voláním <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> metoda a předáním zapisovače XML. Zprávu o dokončení text je zapsán do tohoto zapisovače. Získávání těla celá zpráva v jednom okamžiku se také nazývá *zápisu zprávy*. Zápis probíhá primárně v zásobníku kanál při odesílání zprávy – některé části zásobníku kanálu se obvykle získáte přístup k celé zprávy, kódovat a jeho odeslání.  
  
- Dalším způsobem, jak získat informace o mimo tělo zprávy je volání <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> a získat čtecí funkce XML. Tělo zprávy lze poté přistupovat sekvenčně, podle potřeby pomocí volání metody čtecího zařízení. Získávání zprávu textu část jednotlivé se také nazývá *čtení zprávy*. Čtení zprávy se používá především v rámci služby rozhraní při přijímání zprávy. Například, když <xref:System.Runtime.Serialization.DataContractSerializer> se používá, bude architektura služby získat čtecí funkce XML v těle a předejte jej do deserializace modul, který pak začne zprávu prvek po prvku pro čtení a vytváření odpovídající objekt grafu.  
  
 Text zprávy je možné načíst pouze jednou. Díky tomu je možné pracovat s posouváním pouze datové proudy. Můžete například napsat <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> přepsání, která čte z <xref:System.IO.FileStream> a vrátí výsledky jako informační sadu XML. Musíte nikdy "zpět" na začátku souboru.  
  
 `WriteBodyContents` a `GetReaderAtBodyContents` metody jednoduše zkontrolujte, že nikdy nebyly načtené před text zprávy a poté zavolejte `OnWriteBodyContents` nebo `OnGetReaderAtBodyContents`v uvedeném pořadí.  
  
## <a name="message-usage-in-wcf"></a>Použití zpráv ve WCF  
 Většina zprávy mohou být klasifikovány jako buď *odchozí* (ty, které jsou vytvořeny pomocí rozhraní služby do zásobníku channel) nebo *příchozí* (těch, které přicházejí z kanálu zásobníku a jsou interpretuje rozhraním služby). Kromě toho zásobníku kanál můžou fungovat v režimu ve vyrovnávací paměti nebo datových proudů. Architektura služby mohou také vystavovat proudu nebo nonstreamed programovací model. To vede k případy uvedené v následující tabulce, spolu s zjednodušené podrobnostmi o jejich implementaci.  
  
|Typ zprávy|Data těla zprávy|Popište implementaci (OnWriteBodyContents)|Implementace čtení (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Odchozí, vytvořené z nonstreamed programovací model|Data potřebná k zápisu zprávy (například objekt a <xref:System.Runtime.Serialization.DataContractSerializer> potřeba ho serializovat instance) *|Vlastní logiku k zapsání zprávy podle uložených dat (například volání `WriteObject` na `DataContractSerializer` Pokud tomu tak serializátoru, který je používán) *|Volání `OnWriteBodyContents`, výsledky ve vyrovnávací paměti, vraťte se čtecí funkce XML přes vyrovnávací paměti|  
|Odchozí, vytvořené z proudu programovací model|`Stream` s daty, která má být proveden zápis *|Zápis dat z pomocí uloženého datového proudu <xref:System.Xml.IStreamProvider> mechanismus *|Volání `OnWriteBodyContents`, výsledky ve vyrovnávací paměti, vraťte se čtecí funkce XML přes vyrovnávací paměti|  
|Příchozí z datových proudů kanál zásobníku|A `Stream` objekt, který představuje data přicházející přes síť pomocí <xref:System.Xml.XmlReader> nad ním|Vypsat obsah od uložené `XmlReader` pomocí `WriteNode`|Vrátí uloženou `XmlReader`|  
|Příchozí ze zásobníku nonstreaming kanálu|Vyrovnávací paměť, která obsahuje text dat pomocí `XmlReader` nad ním|Zapíše obsah od uložené `XmlReader` pomocí `WriteNode`|Vrátí uložené lang|  
  
 \* Tyto položky nejsou implementované přímo v `Message` podtřídy, ale v podtřídy třídy <xref:System.ServiceModel.Channels.BodyWriter> třídy. Další informace o <xref:System.ServiceModel.Channels.BodyWriter>, naleznete v tématu [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Záhlaví zpráv  
 Zpráva může obsahovat záhlaví. Záhlaví logicky se skládá z XML informační sadu, která souvisí s názvem, obor názvů a několik dalších vlastností. Záhlaví zprávy jsou přístupné pomocí `Headers` vlastnost <xref:System.ServiceModel.Channels.Message>. Je reprezentován jednotlivé hlavičky <xref:System.ServiceModel.Channels.MessageHeader> třídy. Za normálních okolností záhlaví zpráv se mapují na záhlaví zpráv SOAP při použití kanálu zásobníku nakonfigurováno pro práci s zprávy protokolu SOAP.  
  
 Vložení informací do záhlaví zprávy a extrahování informací z ní je podobný používání tělo zprávy. Proces je poněkud jednodušší, protože streamování se nepodporuje. Je možné pracovat s více než jednou obsah stejné záhlaví a záhlaví je přístupná v pořadí, vynucení záhlaví vždy být ukládány do vyrovnávací paměti. Neexistuje žádný k dispozici pro získání čtecí funkce XML v záhlaví pro obecné účely mechanismus, ale neexistuje `MessageHeader` WCF, který představuje čitelné hlavička s takovou schopnost vnitřní podtřídy. Tento typ `MessageHeader` vzniká zásobníkem kanálu, pokud zpráva hlavičky vlastní aplikace je k dispozici ve. Architektura služby použít modul deserializace, jako tomu <xref:System.Runtime.Serialization.DataContractSerializer>, interpretovat tyto hlavičky.  
  
 Další informace najdete v tématu [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Vlastnosti zprávy  
 Zpráva může obsahovat vlastnosti. A *vlastnost* libovolnou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekt, který je přidružený k názvu řetězce. Vlastnosti jsou přístupné prostřednictvím `Properties` vlastnost `Message`.  
  
 Na rozdíl od text zprávy a záhlaví zpráv (což obvykle mapují na SOAP body a záhlaví SOAP, v uvedeném pořadí) jsou vlastnosti zprávy nejsou obvykle odesílané nebo přijímané spolu s zprávy. Vlastnosti zprávy existovat především jako komunikační mechanizmus k předávání dat o zprávy mezi různými kanály v zásobníku kanálu a mezi zásobníku kanálu a model služby.  
  
 Například je kanál přenosu HTTP jsou součástí WCF vyprodukovat různých stavové kódy HTTP, jako například "404 (Nenalezeno)" a "500 (vnitřní chyba serveru)," při odesílání odpovědi na klienty. Před odesláním zprávy s odpovědí, zkontroluje, zda `Properties` z `Message` obsahovat vlastnost s názvem "httpResponse", který obsahuje objekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Pokud takovou vlastnost najde, se zabývá <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> vlastnosti a použít tento kód stavu. Pokud se nenajde, výchozí "200 (OK)" kód se používá.  
  
 Další informace najdete v tématu [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Zpráva jako celek  
 Zatím jsme mají popsané metody pro přístup k různé části zprávy v izolaci. Ale <xref:System.ServiceModel.Channels.Message> třída rovněž poskytuje metody pro práci s celou zprávu jako celek. Například `WriteMessage` Metoda zapíše celé zprávy do zapisovače XML.  
  
 Chcete-li to možné, musí být definována mapování mezi celý `Message` instanci a informační sadu XML. Ve skutečnosti takové mapování existuje: WCF pomocí standardu SOAP definuje toto mapování. Když `Message` instance je zapsán jako informační sadu XML platný obálku protokolu SOAP, která obsahuje zprávy je výsledný informační sadu. Proto `WriteMessage` by normálně proveďte následující kroky:  
  
1. Zapsat element obálky protokolu SOAP počáteční značku.  
  
2. Zapsat element záhlaví SOAP počáteční značku, vypsat všechny hlavičky a zavřít prvku záhlaví.  
  
3. Zapsat element body SOAP počáteční značku.  
  
4. Volání `WriteBodyContents` nebo ekvivalentní metody k zapsání textu.  
  
5. Zavřete elementy textu a obálky.  
  
 V předchozích krocích jsou úzce vázané na standardu protokolu SOAP. Toto je složité fakt, že více verzí modulu protokolu SOAP existují, například není možné vypsat element obálky protokolu SOAP správně nainstalovat bez mého verze protokolu SOAP používá. Také v některých případech může být žádoucí vypnutí této komplexní SOAP konkrétní mapování úplně.  
  
 Pro tyto účely `Version` vlastnost je k dispozici na `Message`. Můžete nastavit na verzi protokolu SOAP k použití při zápisu zprávu nebo může být nastavena na `None` zabránit všechna SOAP konkrétní mapování. Pokud `Version` je nastavena na `None`, metody, které pracují s act celá zpráva jako v případě, že zprávy se skládal z jeho těla pouze, například `WriteMessage` by jednoduše volala `WriteBodyContents` místo více kroků uvedených výše. Očekává se, která na příchozích zprávách `Version` bude automaticky zjištěno a zařídit správné.  
  
## <a name="the-channel-stack"></a>Kanál zásobníku  
  
### <a name="channels"></a>Kanály  
 Jak je uvedeno dříve, kanál zásobníku je zodpovědný za převod odchozí <xref:System.ServiceModel.Channels.Message> instance některé akce na základě (jako je například odesílání paketů v síti) nebo převodu některé akce (např. přijetí síťových paketů) na příchozí `Message` instance.  
  
 Zásobník kanál se skládá z jednoho nebo několika kanálů, v pořadí řazení. Odchozí `Message` instance předána první kanál v zásobníku (také nazývané *nejvyššího kanál*), který předává je na další kanál v zásobníku a tak dále. Zpráva ukončení v poslední kanálu, která je volána *přenosový kanál*. Příchozí zprávy pocházejí z přenosový kanál a z kanálu channel jsou předány do zásobníku. Z nejvyšší kanálu obvykle v rámci služby předávání zpráv. Když je obvykle vzor pro zprávy aplikace, některé kanály mohou fungovat trochu jinak, například mohli zasílat zprávy své vlastní infrastruktury bez předává zprávy z kanálu výše.  
  
 Při průchodu zásobníku kanály fungovat u zprávy různými způsoby. Nejběžnější operace je přidání hlavičky odchozích zpráv a čtení záhlaví na příchozí zprávy. Kanál může například compute digitální podpis zprávy a přidejte jako záhlaví. Kanál může také zkontrolovat toto záhlaví digitální podpis na příchozí zprávy a blokování zpráv, které nemají žádný platný podpis v cestě zásobníkem kanálu provádění. Kanály také často nastavte nebo zkontrolujte vlastnosti zprávy. Text zprávy je obvykle nedojde ke změně, i když je to povoleno, například zabezpečený kanál WCF můžete šifrovat tělo zprávy.  
  
### <a name="transport-channels-and-message-encoders"></a>Přenosové kanály a zpráva kodérů  
 Nejspodnějších kanálu v zásobníku je zodpovědný za skutečně transformace odchozí <xref:System.ServiceModel.Channels.Message>, jak upravit podle jiných kanálů na určitou akci. Na straně příjmu, to je kanál, který převede některé akce do `Message` , jiné nástroje procesu.  
  
 Jak bylo uvedeno dříve, může se lišit akce: odesílání nebo přijímání síťových paketů pomocí různých protokolů, čtení nebo zápisu se zprávou v databázi, nebo služby Řízení front nebo vyřazování z fronty zpráv do fronty služby Řízení front zpráv, k poskytování ale několik příkladů. Všechny tyto akce mají jedno společné: vyžadují transformaci mezi WCF`Message` instancí a skupinu skutečný počet bajtů, které mohou být odesílány, přijetí, číst, zapsat, zařazených do fronty nebo vyřazených z fronty. Proces převodu `Message` do skupiny podle bajtů se nazývá *kódování*a reverzní procesem vytvoření `Message` ze skupiny bajtů se nazývá *dekódování*.  
  
 Většina přenosové kanály pomocí komponenty volá *zprávy kodérů* k provedení kódování a dekódování práce. Kodér zprávy je podtřídou třídy <xref:System.ServiceModel.Channels.MessageEncoder> třídy. `MessageEncoder` obsahuje různé `ReadMessage` a `WriteMessage` přetížení metody pro převod mezi `Message` a skupiny bajtů.  
  
 Na straně odesílání vyrovnávací paměti přenosový kanál předá `Message` objekt, který přijal z kanálu nad ním na `WriteMessage`. Získá zpět pole bajtů, které poté používá k provedení akcí (například balení těchto bajtů jako platný pakety protokolu TCP a jejich odesílání do správné cíl). Streamování kanál přenosu nejdříve vytvoří `Stream` (například přes odchozí připojení TCP) a poté předá i `Stream` a `Message` musí odeslat na příslušné `WriteMessage` přetížení, která zapíše zpráva .  
  
 Na straně příjmu extrahuje vyrovnávací paměti přenosový kanál Příchozí bajty (např. z příchozí pakety protokolu TCP) do pole a volání `ReadMessage` zobrazíte `Message` objektu, můžete předat další zásobníkem kanálu. Streamování přenosový kanál vytvoří `Stream` objektu (například sítě datového proudu přes příchozí připojení protokolu TCP) a, který se předává `ReadMessage` chcete vrátit zpět `Message` objektu.  
  
 Není to povinné; oddělení mezi přenosové kanály a kodér zprávy je možné psát přenosový kanál, který nepoužívá kodéru zprávy. Ale výhodou toto oddělení je snadné složení. Za předpokladu, přenosový kanál používá pouze základní <xref:System.ServiceModel.Channels.MessageEncoder>, můžete pracovat s WCF nebo kodéru zpráv třetích stran. Stejného kodéru, je obvykle možné v jakémkoli jiném kanálu přenosu.  
  
### <a name="message-encoder-operation"></a>Operace kodéru zpráv  
 K popisu typické operaci kodéru, je vhodné vzít v úvahu následující čtyři případy.  
  
|Operace|Komentář|  
|---------------|-------------|  
|Kódování a uložená do vyrovnávací paměti|V režimu vyrovnávací paměti kodér obvykle vytvoří proměnné velikosti vyrovnávací paměti a pak vytvoří zapisovače XML nad ním. Poté zavolá <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> ve zprávě zakódována, který zapíše hlavičky a potom na textu pomocí <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, jak je popsáno v předchozí části o `Message` v tomto tématu. Pro přenosový kanál k použití se potom vrátí obsah vyrovnávací paměti (reprezentovány jako pole bajtů).|  
|Kódování a streamování|Operace je v režimu proudu, podobně jako výše, ale jednodušší. Není nutné vyrovnávací paměti. Zapisovače XML se obvykle vytváří přes datový proud a <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> je volán na `Message` vypsat do tohoto zapisovače.|  
|Dekódování, ukládány do vyrovnávací paměti|Při dekódování v režimu vyrovnávací paměti, speciální `Message` podtřídy, který obsahuje data ve vyrovnávací paměti je obvykle vytvořen. Jsou přečteny hlavičky zprávy a je vytvořen čtecí modul XML, který je umístěn v textu zprávy. Toto je čtecí modul, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Dekódování, streamování|Při dekódování v proudu režimu, se obvykle vytvoří zvláštní zpráva podtřídy. Datový proud je pokročilý tak akorát na tyto hlavičky přečíst a umístěte ho na obsah zprávy. Čtecí funkce XML se pak vytvoří v datovém proudu. Toto je čtecí modul, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodérů můžete provádět také další funkce. Například u kodérů může vytvořit fond z XML čtečky a zapisovače. Je nákladné pokaždé, když je zapotřebí vytvořit nový čtecí modul XML nebo zapisovač. Proto kodérů obvykle udržovat fondu čtenářů a zapisovačů konfigurovat velikost fondu. V popisech kodér operace je popsáno výše vždy, když frázi "Vytvoření čtečky a zapisovače XML" se používá, je obvykle znamená, že "proveďte jednu z fondu, nebo vytvořit novou, pokud není k dispozici." Kodér (a `Message` podtřídy vytvoří při dekódování výplně) obsahují logiku k vrácení čtečky a zapisovače do fondů, jakmile už nejsou potřeba (například když `Message` je uzavřený).  
  
 WCF poskytuje tři kodérů zprávu, i když je možné vytvořit další vlastní typy. Zadané typy jsou Text, binární soubor a zpráv přenosu optimalizace mechanismus (MTOM). Tyto možnosti jsou popsány podrobně v [výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Rozhraní IStreamProvider  
 Při zápisu odchozí zprávy, která obsahuje tělo streamovaná do zapisovače XML <xref:System.ServiceModel.Channels.Message> využívá posloupnost volání podobně jako v následujícím jeho <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementace:  
  
- Zapisovat všechny potřebné informace před stream (například otevírání – značka XML).  
  
- Zápis datového proudu.  
  
- Zapisovat všechny informace o streamu (například uzavírací značky XML).  
  
 Tento postup funguje dobře s kódování, které jsou podobné textové kódování XML. Ale některé kódování Neumísťujte informační sadu XML informace (například značky pro počáteční a koncovou elementů XML) společně s data obsažená v rámci prvků. Kódování MTOM, například zprávy je rozdělit na více částí. Jednou ze součástí obsahuje informační sadu XML, které mohou obsahovat odkazy na ostatní části pro obsah skutečným prvkem. Informační sada XML je obvykle malé ve srovnání s datovým proudem obsah, proto je vhodné uložit do vyrovnávací paměti informační sadu, tak zapisovat a pak zapsat obsah datovým proudem způsobem. To znamená, že čas zavření značky elementu je zapsán, datového proudu by neměla být napsán takto ještě.  
  
 Pro tento účel <xref:System.Xml.IStreamProvider> rozhraní se používá. Rozhraní <xref:System.Xml.IStreamProvider.GetStream> metodu, která vrací datový proud, který má být proveden zápis. Správný způsob k zapsání textu zapsal zprávu v <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> vypadá takto:  
  
1. Zapisovat všechny potřebné informace před stream (například otevírání – značka XML).  
  
2. Volání `WriteValue` přetížit na <xref:System.Xml.XmlDictionaryWriter> , která má <xref:System.Xml.IStreamProvider>, pomocí `IStreamProvider` implementace, která vrací datový proud, který má být proveden zápis.  
  
3. Zapisovat všechny informace o streamu (například uzavírací značky XML).  
  
 S tímto přístupem zapisovací modul XML se zobrazí možnost výběru při volání <xref:System.Xml.IStreamProvider.GetStream> a vypsat streamovaná data. Textové a binární zapisovače XML se například volání okamžitě a vypsat streamovaná obsah mezi úvodní a koncovou značkou. Zapisovací funkce MTOM rozhodnout volání <xref:System.Xml.IStreamProvider.GetStream> později, až bude připravená k zápisu odpovídající část zprávy.  
  
## <a name="representing-data-in-the-service-framework"></a>Reprezentující Data v rámci služby  
 Jak je uvedeno v části "Základní architekturu" tohoto tématu, architektura služby je součástí WCF, který mimo jiné, je zodpovědný za převod mezi uživatelsky přívětivé programovací model pro data zprávy, ve skutečnosti `Message` instancí. Za normálních okolností je reprezentován výměně zpráv v rámci služby jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metoda označena <xref:System.ServiceModel.OperationContractAttribute> atribut. Metoda využít některé parametry a může vrátit návratovou hodnotu nebo parametry (nebo obojí). Na straně služby vstupních parametrů představují příchozí zpráva a návratová hodnota a výstupní parametry představují odchozí zprávu. Na straně klienta naopak je true. Programovací model pro popis zpráv s použitím parametrů a návratové hodnoty je podrobně popsán v [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Tato část se však poskytli stručný přehled.  
  
## <a name="programming-models"></a>Programovací modely  
 Architektura služby WCF podporuje pět různých programovacích modelů popisem zprávy:  
  
### <a name="1-the-empty-message"></a>1. Prázdná zpráva  
 Toto je nejjednodušší případ. K popisu prázdný příchozí zprávy, se nepoužívá žádné vstupní parametry.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 K popisu prázdný odchozí zprávy, použijte návratovou hodnotu typu void a nepoužívají žádné výstupní parametry:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Všimněte si, že se liší od Jednosměrná operace kontraktu:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 V `SetDesiredTemperature` například vzoru výměny zpráv obousměrný je popsáno. Operace vrátí zprávy, ale je prázdný. Je možné vrátit chybu z operace. V příkladu "Nastavit žárovky" je jednosměrný vzoru výměny zpráv, takže neexistuje žádná odchozí zprávy k popisu. Služba nemůže komunikovat v tomto případě libovolný stav zpět do klienta.  
  
### <a name="2-using-the-message-class-directly"></a>2. Používání třídy Message přímo  
 Je možné použít <xref:System.ServiceModel.Channels.Message> třídy (nebo některá z jejích podtříd) přímo v kontrakt operace. V takovém případě stačí předá architektura služby `Message` z operace na kanálu zásobníku a naopak, se žádné další zpracování.  
  
 Existují dva hlavní případy použití `Message` přímo. Můžete to pro pokročilé scénáře, pokud žádná z jiných programovacích modelů poskytuje dostatek flexibilitu k popisu zprávy. Například můžete chtít použít soubory na disku k podrobnému popisu zprávy, se stávají záhlaví zpráv a stát tělo zprávy obsah souboru vlastnosti souboru. Potom můžete vytvořit něco podobného následujícímu.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Druhý běžné účely `Message` v kontrakt operace při služby nezáleží na konkrétní zprávy obsah a funguje jako na černé políčko ve zprávě. Například může mít službu, která předává zprávy více ostatním příjemcům. Kontrakt může být napsán takto.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Akce = "*" řádku efektivně vypne odesílání zpráv a zajistí, že všechny zprávy odeslané do `IForwardingService` kontraktu dostanou k `ForwardMessage` operace. (Za normálních okolností dispečer prozkoumá "Action" záhlaví zprávy k určení operace, která je určená pro zpracování na polovinu. Akce = "\*" znamená "všechny možné hodnoty záhlaví akce".) Kombinací akcí = "\*" a pomocí zprávy jako parametr je označováno jako "univerzální kontrakt", protože je schopný přijímat všechny možné zprávy. Aby bylo možné odeslat všechny zprávy je to možné, použijte zprávy jako návratovou hodnotu a nastavte `ReplyAction` na "\*". Architektura služby zabráníte přidání své vlastní záhlaví akce, umožňuje řídit tato záhlaví pomocí `Message` objektu se vrátit.  
  
### <a name="3-message-contracts"></a>3. Kontrakty zpráv  
 WCF poskytuje deklarativní programovací model pro popis zprávy označované jako *kontrakty zprávy*. Tento model je podrobně popsán v [použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). V podstatě celá zpráva představuje jeden [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ, který používá atributů, například <xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute> k popisu, které části třídy kontraktu zprávy by měl mapovat na kterou část zprávy.  
  
 Kontrakty zpráv poskytují velké množství kontrolu nad výsledný `Message` instance (i když samozřejmě mnohem ovládací prvek jako pomocí `Message` přímo třídu). Například zpráv se často skládají z více kusů informace, každý reprezentována vlastní – element XML. Tyto prvky může dojít buď přímo v textu (*úplné* režimu), nebo může být *zabalené* v včetně elementu jazyka XML. Pomocí kontraktu zprávy programovací model umožňuje rozhodnutí úplné srovnání zabalená a název oboru názvů a název obálky ovládacího prvku.  
  
 Následující příklad kódu kontraktu zprávy ukazuje tyto funkce.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Položky označené k serializaci (s <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, nebo jiné vztahující se atributy) musí být serializovatelný k účasti v kontraktu zprávy. Další informace najdete v části "Serializace" dále v tomto tématu.  
  
### <a name="4-parameters"></a>4. Parametry  
 Jako vývojář, který chce popisují operace, která funguje na více částí dat často, není nutné stupeň ovládací prvek, který poskytuje kontraktů zpráv. Například při vytváření nové služby, jeden nechce obvykle rozhodnutí úplné srovnání zabalená a rozhodnout o název prvku obálky. Rozhodování o těchto často vyžaduje hlubokých znalostí webových služeb a SOAP.  
  
 Architektura služby WCF můžete automaticky vybrat nejlepší a interaktivní reprezentace SOAP pro odesílání nebo přijímání více souvisejících řadu informací, bez vynucení tyto možnosti na uživatele. Tím se dosahuje tak, že jednoduše popisující tyto údaje jako parametry nebo návratové hodnoty pro kontrakt operace. Představte si třeba následující operace kontraktu.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Architektura služby rozhodne automaticky umístit všechny tři údaje (`customerID`, `item`, a `quantity`) do textu zprávy a zalamování řádků je v prvku obálky s názvem `SubmitOrderRequest`.  
  
 Informace, které mají být odeslány nebo přijaty jako jednoduchý seznam parametrů operace kontraktu je doporučený postup, pokud speciální důvody pro přesun do kontraktu zprávy složitější popisující nebo `Message`– na základě programovacích modelů.  
  
### <a name="5-stream"></a>5. Stream  
 Pomocí `Stream` nebo jeden z jejích podtříd kontrakt operace nebo jako část textu jedinou zprávy v kontraktu zprávy lze považovat za samostatný programovací model z těch, které jsou popsané výše. Pomocí `Stream` tímto způsobem je jediný způsob, jak zajistit, že bude možné použít streamovaná způsobem nemá psaní vlastních datových proudů kompatibilní s vaší smlouvy `Message` podtřídy. Další informace najdete v tématu [velkých objemů dat a datových proudů](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Když `Stream` nebo jeden z jejích podtříd tímto způsobem je použít, není vyvolána serializátor. Pro odchozí zprávy, speciální streamování `Message` vytvořit podtřídu a datový proud je zapsaný odhlašování, jak je popsáno v části na <xref:System.Xml.IStreamProvider> rozhraní. Pro příchozí zprávy, vytvoří architektura služby `Stream` podtřídy přes příchozí zprávy a poskytuje operace.  
  
## <a name="programming-model-restrictions"></a>Omezení Model programování  
 Programovací modely výše popsané libovolně nelze kombinovat. Například pokud operace přijímá typ kontraktu zprávy, kontrakt zprávy musí být jeho pouze vstupní parametr. Kromě toho musí operaci pak vrátit prázdnou zprávu (typ vrácené hodnoty void) nebo jiné zprávy kontraktu. Tato programovací model omezení jsou popsaná v tématech pro každou konkrétní programovací model: [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), a [velkých objemů dat a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formátování zpráv  
 Programovací modely výše popsané podporují zapojení součásti volá *zprávy formátovací moduly* v rámci služby. Formátování zpráv jsou typy, které implementují <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> nebo <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní, nebo obojí pro použití v klienty a služby WCF, v uvedeném pořadí.  
  
 Formátování zpráv jsou obvykle zapojené do elektrické zásuvky podle chování. Například <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> zpřístupní ve formátovacím modulu dat kontrakt zprávy. To se provádí na straně služby tak, že nastavíte <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> do správné formátování v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metodu, nebo na straně klienta tím, že nastavíte <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> do správné formátování v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> metoda.  
  
 V následující tabulce jsou uvedeny metody, které může implementovat formátovací modul zpráv.  
  
|Rozhraní|Metoda|Akce|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede příchozí `Message` na parametry operace|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Vytvoří odchozí `Message` z operace vrátit hodnotu/výstupní parametry|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Vytvoří odchozí `Message` z parametry operace|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede příchozí `Message` na návratovou hodnotu/výstupní parametry|  
  
## <a name="serialization"></a>Serializace  
 Při každém použití kontraktů zpráv nebo parametry k popisu obsah zprávy, je nutné použít serializace pro převod mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a reprezentaci XML informační sadu. Serializace se používá na dalších místech WCF, například <xref:System.ServiceModel.Channels.Message> má obecný <xref:System.ServiceModel.Channels.Message.GetBody%2A> metodu, která vám umožní načíst celý text zprávy deserializovat do objektu.  
  
 WCF podporuje dvě technologie serializace "mimo pole" pro serializaci a deserializaci parametry a částí zprávy: <xref:System.Runtime.Serialization.DataContractSerializer> a `XmlSerializer`. Kromě toho můžete napsat vlastní serializátory. Však dalších součástí WCF (jako je obecný `GetBody` metody nebo SOAP k chybě serializace) může být omezena na používání jenom <xref:System.Runtime.Serialization.XmlObjectSerializer> podtřídy (<xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer>, ale ne <xref:System.Xml.Serialization.XmlSerializer>), nebo dokonce může být pevně určený jenom <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Serializační stroj se používá v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby. `DataContractSerializer` Je nový Serializační stroj, který rozpozná nový model programování kontraktu dat. `DataContractSerializer` je výchozí volbou a možnost použití `XmlSerializer` provádět na základě každou operaci pomocí <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atribut.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> zodpovídají chování operace pro formátování zpráv pro zapojení `DataContractSerializer` a `XmlSerializer`v uvedeném pořadí. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Chování ve skutečnosti můžete pracovat s jakékoli serializátoru, který je odvozen z <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.NetDataContractSerializer> (podrobně popsány v pomocí samostatného serializace). Chování volá jedno ze `CreateSerializer` přetížení virtuální metody pro získání serializátoru. Chcete-li zařadit jiný serializátor, vytvořte nový <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podtřídy a přepsání `CreateSerializer` přetížení.  
  
## <a name="see-also"></a>Viz také:

- [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
