---
title: Strukturální přehled přenosu dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: f34bf82ec44140827c5d8da59911afe10ab7a853
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576470"
---
# <a name="data-transfer-architectural-overview"></a>Strukturální přehled přenosu dat
Windows Communication Foundation (WCF) si můžete představit jako infrastrukturu zasílání zpráv. Může přijímat zprávy, zpracovávat je a odesílat je do uživatelského kódu, aby bylo možné provádět další akce, nebo může sestavovat zprávy z dat poskytovaných uživatelským kódem a dodat je do cíle. Toto téma, které je určené pro pokročilé vývojáře, popisuje architekturu pro zpracování zpráv a obsažených dat. Jednodušší a uživatelsky orientované zobrazení způsobu, jak odesílat a přijímat data, najdete v tématu [určení přenos dat v kontraktech služeb](specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
> Toto téma popisuje podrobnosti implementace WCF, které nejsou viditelné prozkoumáním objektového modelu WCF. Dvě slova upozornění jsou v souvislosti s dokumentovanými podrobnostmi implementace v daném pořadí. Nejprve jsou popisy zjednodušeny. Skutečná implementace může být složitější z důvodu optimalizace nebo z jiných důvodů. Za druhé, neměli byste spoléhat na konkrétní podrobnosti implementace, a to ani na ty, které se nedají změnit, aniž by bylo nutné si všimnout verze na verzi nebo dokonce i v servisní verzi.  
  
## <a name="basic-architecture"></a>Základní architektura  
 V jádru funkcí pro zpracování zpráv WCF je <xref:System.ServiceModel.Channels.Message> třída, která je podrobněji popsána v tématu [použití třídy zpráv](using-the-message-class.md). Komponenty služby WCF spouštěné za běhu lze rozdělit do dvou hlavních částí: zásobníku kanálů a rozhraní, s třídou, která je <xref:System.ServiceModel.Channels.Message> spojovacím bodem.  
  
 Zásobník kanálů zodpovídá za převod mezi platnou <xref:System.ServiceModel.Channels.Message> instancí a několik akcí, které odpovídají odesílání nebo přijímání dat zpráv. Zásobník kanálu na straně odesílání přebírá platnou <xref:System.ServiceModel.Channels.Message> instanci a po nějakém zpracování provádí určitou akci, která logicky odpovídá odeslání zprávy. Akce může odesílat pakety TCP nebo HTTP, zasílat zprávy do služby Řízení front zpráv, zapsat zprávu do databáze, uložit ji do sdílené složky nebo jakoukoli jinou akci, v závislosti na implementaci. Nejběžnější akcí je odeslání zprávy přes síťový protokol. Na straně příjmu dojde k opačné situaci – je zjištěna akce (což může být doručeno paketů TCP nebo HTTP nebo jakákoli jiná akce) a po zpracování kanál kanálu převede tuto akci na platnou <xref:System.ServiceModel.Channels.Message> instanci.  
  
 Můžete použít WCF pomocí <xref:System.ServiceModel.Channels.Message> třídy a zásobníku kanálů přímo. Nicméně to je obtížné a časově náročné. Kromě toho <xref:System.ServiceModel.Channels.Message> objekt neposkytuje podporu metadat, takže nemůžete generovat klienty WCF se silnými typy, pokud použijete WCF tímto způsobem.  
  
 Proto WCF zahrnuje rozhraní služby, které poskytuje snadno použitelný programovací model, který můžete použít k vytvoření a přijetí `Message` objektů. Služba mapuje služby na .NET Framework typy prostřednictvím pojmu kontrakty služby a odesílá zprávy do uživatelských operací, které jsou jednoduše .NET Framework metod označených <xref:System.ServiceModel.OperationContractAttribute> atributem (Další informace najdete v tématu [Navrhování kontraktů služby](../designing-service-contracts.md)). Tyto metody mohou mít parametry a návratové hodnoty. Na straně služby převede rozhraní služby příchozí <xref:System.ServiceModel.Channels.Message> instance na parametry a převede návratové hodnoty na odchozí <xref:System.ServiceModel.Channels.Message> instance. Na straně klienta se jedná o opak. Zvažte například `FindAirfare` následující operaci.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Předpokládejme `FindAirfare` , že je volána na klientovi. Rozhraní služby na klientovi převede `FromCity` `ToCity` parametry a do odchozí <xref:System.ServiceModel.Channels.Message> instance a předá je do zásobníku kanálů k odeslání.  
  
 Když je na straně služby <xref:System.ServiceModel.Channels.Message> instance doručena ze zásobníku kanálů, rozhraní Service Framework extrahuje příslušná data ze zprávy, aby naplnila `FromCity` `ToCity` parametry a a pak zavolá metodu na straně služby `FindAirfare` . Když metoda vrátí, rozhraní služby vezme vrácenou celočíselnou hodnotu a `IsDirectFlight` výstupní parametr a vytvoří <xref:System.ServiceModel.Channels.Message> instanci objektu, která obsahuje tyto informace. Pak předá `Message` instanci do zásobníku kanálů, který se pošle zpátky klientovi.  
  
 Na straně klienta se <xref:System.ServiceModel.Channels.Message> objeví instance, která obsahuje zprávu odpovědi ze zásobníku kanálu. Rozhraní služby extrahuje vrácenou hodnotu a `IsDirectFlight` hodnotu a vrátí je volajícímu klienta.  
  
## <a name="message-class"></a>Message – třída  
 <xref:System.ServiceModel.Channels.Message>Třída je určena jako abstraktní reprezentace zprávy, ale její návrh je silně svázán se zprávou SOAP. <xref:System.ServiceModel.Channels.Message>Obsahuje tři hlavní části informací: tělo zprávy, záhlaví zpráv a vlastnosti zprávy.  
  
## <a name="message-body"></a>Tělo zprávy  
 Tělo zprávy by představovalo skutečnou datovou část zprávy. Tělo zprávy je vždy reprezentované jako informační sada XML. To neznamená, že všechny zprávy vytvořené nebo přijaté v WCF musí být ve formátu XML. Chcete-li se rozhodnout, jak interpretovat tělo zprávy, je až do zásobníku kanálů. Může ji vygenerovat jako XML, převést ji na jiný formát nebo dokonce ji vynechat zcela. Samozřejmě s využitím většiny vazeb WCF poskytuje text zprávy v části tělo obálky protokolu SOAP jako obsah XML.  
  
 Je důležité si uvědomit, že `Message` Třída nutně neobsahuje vyrovnávací paměť s daty XML reprezentujícími tělo. Logicky `Message` obsahuje XML informační sadu, ale tato informační sada může být dynamicky vytvořena a nikdy nemusí fyzicky existovat v paměti.  
  
### <a name="putting-data-into-the-message-body"></a>Vložení dat do textu zprávy  
 Neexistuje žádný jednotný mechanismus pro vložení dat do těla zprávy. <xref:System.ServiceModel.Channels.Message>Třída má abstraktní metodu, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> která přijímá <xref:System.Xml.XmlDictionaryWriter> . Každá podtřídou <xref:System.ServiceModel.Channels.Message> třídy zodpovídá za přepsání této metody a zapsání vlastního obsahu. Text zprávy logicky obsahuje XML informační sadu, která `OnWriteBodyContent` vytváří. Zvažte například následující `Message` podtřídu.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 `AirfareRequestMessage`Instance fyzicky obsahuje jenom dva řetězce ("FromCity" a "ToCity"). Logicky však zpráva obsahuje následující XML sadu:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Tímto způsobem byste samozřejmě obvykle nevytvořili zprávy, protože k vytvoření zprávy, jako je předchozí z parametrů kontraktu operace, můžete použít rozhraní Service Framework. Kromě toho <xref:System.ServiceModel.Channels.Message> Třída obsahuje statické `CreateMessage` metody, které lze použít k vytvoření zpráv se společnými typy obsahu: prázdná zpráva, zpráva, která obsahuje objekt serializovaný do XML s <xref:System.Runtime.Serialization.DataContractSerializer> , zprávu, která obsahuje chybu SOAP, zprávu, která obsahuje XML reprezentovanou <xref:System.Xml.XmlReader> a tak dále.  
  
### <a name="getting-data-from-a-message-body"></a>Získání dat z těla zprávy  
 Data uložená v těle zprávy můžete extrahovat dvěma hlavními způsoby:  
  
- Celý text zprávy můžete získat jednorázovým voláním <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> metody a předáním do zapisovače XML. Do tohoto zapisovače se zapíše úplný text zprávy. Získání celého textu zprávy je také nazýváno *zápis zprávy*. Zápis se provádí hlavně zásobníkem kanálů při posílání zpráv – některá část zásobníku kanálu obvykle získá přístup k celému textu zprávy, zakóduje ho a pošle.  
  
- Dalším způsobem, jak získat informace z těla zprávy, je zavolat <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> a získat čtecí modul XML. Tělo zprávy lze následně přičíst podle potřeby, a to voláním metod v čtecím zařízení. Získání těla zprávy je také označováno jako *čtení zprávy*. Čtení zprávy je primárně používáno rozhraním Service Framework při přijímání zpráv. Například když <xref:System.Runtime.Serialization.DataContractSerializer> je používán, rozhraní služby získá čtecí modul XML nad tělo a přesměruje ho do modulu deserializace, který pak začne číst prvek zprávy podle prvku a vytvoří odpovídající graf objektu.  
  
 Tělo zprávy lze načíst pouze jednou. Díky tomu je možné pracovat s datovými proudy, které jsou jen pro čtení. Můžete například napsat <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> přepsání, které přečte z <xref:System.IO.FileStream> a, a vrátí výsledky jako XML informační sadu. Na začátek souboru nikdy nebudete muset "Rewind".  
  
 `WriteBodyContents`Metody a `GetReaderAtBodyContents` jednoduše kontrolují, že tělo zprávy nebylo nikdy dříve načteno, a potom zavolá `OnWriteBodyContents` nebo `OnGetReaderAtBodyContents` , v uvedeném pořadí.  
  
## <a name="message-usage-in-wcf"></a>Použití zprávy ve službě WCF  
 Většinu zpráv je možné klasifikovat buď jako *odchozí* (ty, které vytvořila služba pro odeslání zásobníkem kanálů), nebo *příchozí* (ty, které dorazí ze zásobníku kanálů a jsou interpretovány rozhraním Service Framework). Zásobník kanálů navíc může fungovat buď v režimu vyrovnávací paměti, nebo v režimu streamování. Rozhraní služby může také zveřejnit model programování s datovými proudy nebo nedatovým proudem. To vede k případům uvedeným v následující tabulce společně s zjednodušenými podrobnostmi o jejich implementaci.  
  
|Typ zprávy|Data těla zprávy ve zprávě|Zápis (OnWriteBodyContents) – implementace|Čtení (OnGetReaderAtBodyContents) – implementace|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Odchozí, vytvořené z nestreamované programovacího modelu|Data potřebná k zápisu zprávy (například objekt a <xref:System.Runtime.Serialization.DataContractSerializer> instance potřebné k jejímu serializaci) *|Vlastní logika pro zápis zprávy na základě uložených dat (například volání `WriteObject` v `DataContractSerializer` případě, že se používá serializátor) *|Volání `OnWriteBodyContents` , uložení výsledků do vyrovnávací paměti, vrácení čtecího modulu XML přes vyrovnávací paměť|  
|Odchozí, vytvořené z programového modelu streamování|`Stream`S daty, která mají být zapsána *|Vypište data z uloženého datového proudu pomocí <xref:System.Xml.IStreamProvider> mechanismu *|Volání `OnWriteBodyContents` , uložení výsledků do vyrovnávací paměti, vrácení čtecího modulu XML přes vyrovnávací paměť|  
|Příchozí ze zásobníku kanálu streamování|`Stream`Objekt, který představuje data, která přicházejí přes síť, <xref:System.Xml.XmlReader> přes něj|Vypište obsah z uloženého `XmlReader` pomocí`WriteNode`|Vrátí uložený`XmlReader`|  
|Příchozí z nestreamování zásobníku kanálů|Vyrovnávací paměť, která obsahuje data základního obsahu. `XmlReader`|Zapisuje obsah z uloženého `XmlReader` pomocí`WriteNode`|Vrátí uložený jazyk.|  
  
 \*Tyto položky nejsou implementovány přímo v `Message` podtříd, ale v podtříd <xref:System.ServiceModel.Channels.BodyWriter> třídy. Další informace o najdete v <xref:System.ServiceModel.Channels.BodyWriter> tématu [použití třídy Message](using-the-message-class.md).  
  
## <a name="message-headers"></a>Záhlaví zpráv  
 Zpráva může obsahovat záhlaví. Záhlaví se logicky skládá ze sady XML, která je přidružena k názvu, oboru názvů a několika dalším vlastnostem. Záhlaví zpráv jsou k dispozici pomocí `Headers` vlastnosti v <xref:System.ServiceModel.Channels.Message> . Každé záhlaví je reprezentované <xref:System.ServiceModel.Channels.MessageHeader> třídou. Při použití zásobníku kanálů nakonfigurovaných pro práci se zprávami SOAP jsou obvykle záhlaví zpráv mapována na záhlaví zpráv protokolu SOAP.  
  
 Vložení informací do záhlaví zprávy a extrakce informací z nich je podobné jako při použití textu zprávy. Proces je trochu zjednodušený, protože streamování se nepodporuje. Je možné získat přístup k obsahu stejné hlavičky více než jednou a k hlavičkám lze přistupovat v libovolném pořadí, což vynutí ukládání hlaviček do vyrovnávací paměti. K dispozici není žádný mechanismus pro obecné účely, který by měl získat čtecí modul XML přes hlavičku, ale `MessageHeader` podtřídou je vnitřní třída pro WCF, která představuje čitelnou hlavičku s takovou schopností. Tento typ `MessageHeader` je vytvořen zásobníkem kanálu, pokud se zobrazí zpráva s vlastními záhlavími aplikace. To umožňuje, aby služba Service Framework používala k interpretaci těchto hlaviček modul deserializace, jako je <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 Další informace najdete v tématu [použití třídy zpráv](using-the-message-class.md).  
  
## <a name="message-properties"></a>Vlastnosti zprávy  
 Zpráva může obsahovat vlastnosti. *Vlastnost* je libovolný objekt .NET Framework, který je spojen s názvem řetězce. Vlastnosti jsou k dispozici prostřednictvím `Properties` vlastnosti v `Message` .  
  
 Na rozdíl od textu zprávy a záhlaví zpráv (které jsou obvykle mapovány na tělo protokolu SOAP a hlavičky protokolu SOAP) jsou vlastnosti zprávy obvykle odesílány ani přijímány spolu se zprávami. Vlastnosti zprávy existují hlavně jako komunikační mechanismus pro předávání dat o zprávě mezi různými kanály v zásobníku kanálů a mezi zásobníkem kanálu a modelem služby.  
  
 Například transportní kanál HTTP zahrnutý jako součást WCF je schopný vytvářet různé kódy stavu HTTP, například "404 (Nenalezeno)" a "500 (interní chyba serveru)", "při posílání odpovědí klientům. Před odesláním zprávy s odpovědí zkontroluje, zda obsahuje vlastnost s `Properties` `Message` názvem "HttpResponse", která obsahuje objekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty> . Pokud taková vlastnost najde, bude se pohlížet na <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> vlastnost a použije se tento stavový kód. Pokud se nenajde, použije se výchozí kód "200 (OK)".  
  
 Další informace najdete v tématu [použití třídy zpráv](using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Zpráva jako celek  
 Zatím jsme probrali metody pro přístup k různým částem zprávy, která je v izolaci. Nicméně <xref:System.ServiceModel.Channels.Message> Třída také poskytuje metody pro práci s celou zprávou jako celek. Například `WriteMessage` Metoda zapisuje celou zprávu do zapisovače XML.  
  
 Aby to bylo možné, musí být mapování definováno mezi celou `Message` instancí a informačním kódem XML. Toto mapování faktně existuje: WCF používá k definování tohoto mapování Standard SOAP. V případě `Message` , že je instance zapsána jako informační sada XML, výsledná sada je platná obálka protokolu SOAP, která obsahuje zprávu. Proto `WriteMessage` by normálně prováděl následující kroky:  
  
1. Zápis počáteční značky elementu obálky SOAP.  
  
2. Zapište značku otevření elementu záhlaví SOAP, vypište všechny hlavičky a zavřete element Header.  
  
3. Zapište počáteční značku elementu těla zprávy SOAP.  
  
4. `WriteBodyContents`K vypsání těla můžete zavolat nebo ekvivalentní metodu.  
  
5. Zavřete tělo a prvky obálky.  
  
 Předchozí kroky jsou úzce vázané na standard SOAP. To je složitou skutečností, že existuje více verzí protokolu SOAP, například není možné vypsat správně Obálkový prvek SOAP bez znalosti používané verze protokolu SOAP. V některých případech může být také vhodné toto komplexní mapování specifické pro protokol SOAP vypnout úplně.  
  
 Pro tyto účely je k `Version` dispozici vlastnost na `Message` . Dá se nastavit na verzi protokolu SOAP, která se má použít při zápisu zprávy, nebo může být nastavená na, `None` aby se zabránilo jakémukoli mapování specifickému pro protokol SOAP. Pokud `Version` je vlastnost nastavena na hodnotu `None` , metody, které pracují s celou zprávou, fungují, jako kdyby zpráva obsahovala pouze tělo, například, `WriteMessage` `WriteBodyContents` místo provedení více kroků uvedených výše. Očekává se, že u příchozích zpráv se `Version` automaticky zjistí a nastaví správně.  
  
## <a name="the-channel-stack"></a>Zásobník kanálů  
  
### <a name="channels"></a>Kanály  
 Jak je uvedeno dříve, zásobník kanálů zodpovídá za převod odchozích <xref:System.ServiceModel.Channels.Message> instancí na určitou akci (například odeslání paketů přes síť) nebo převod některé akce (například příjem síťových paketů) do příchozích `Message` instancí.  
  
 Zásobník kanálů se skládá z jednoho nebo více kanálů seřazených v sekvenci. Odchozí `Message` instance se předává prvnímu kanálu v zásobníku (označuje se také jako *vrchní kanál*), který ho předá dalšímu kanálu v zásobníku a tak dále. Zpráva se ukončí v posledním kanálu, který se označuje jako *Transportní kanál*. Příchozí zprávy pocházejí z transportního kanálu a jsou předány z kanálu, aby kanál procházely ve frontě. Od nejvyššího kanálu je zpráva obvykle předána do rozhraní služby. I když se jedná o obvyklý vzor pro zprávy aplikací, některé kanály můžou fungovat trochu jinak, můžou například odesílat vlastní zprávy infrastruktury bez nutnosti předávat zprávu z kanálu výše.  
  
 Kanály můžou pracovat na zprávě různými způsoby, jak procházejí prostřednictvím zásobníku. Nejběžnější operace je přidání záhlaví do odchozí zprávy a čtení hlaviček příchozí zprávy. Kanál například může vypočítat digitální podpis zprávy a přidat ho jako záhlaví. Kanál může také zkontrolovat tuto hlavičku digitálního podpisu u příchozích zpráv a zablokovat zprávy, které nemají platný podpis, aby bylo možné v zásobníku kanálu. Kanály také často nastavují nebo kontrolují vlastnosti zpráv. Tělo zprávy se obvykle nemění, i když je to povoleno, například kanál zabezpečení WCF může šifrovat tělo zprávy.  
  
### <a name="transport-channels-and-message-encoders"></a>Transportní kanály a kodéry zpráv  
 Nejspodnější kanál v zásobníku zodpovídá za to, že ve skutečnosti transformuje odchozí výstup <xref:System.ServiceModel.Channels.Message> , jak ho změnily jiné kanály, do nějakého postupu. Na straně příjmu se jedná o kanál, který převede určitou akci na `Message` jiný proces.  
  
 Jak bylo uvedeno dříve, akce mohou být proměnlivé: odesílání nebo příjem síťových paketů prostřednictvím různých protokolů, čtení nebo zápis zprávy v databázi nebo zařazování do fronty nebo deřazení zpráv ve frontě služby Řízení front zpráv, aby bylo možné poskytnout několik příkladů. Všechny tyto akce mají jednu věc společné: vyžadují transformaci mezi instancí služby WCF `Message` a skutečnou skupinou bajtů, které lze odeslat, přijmout, číst, zapsat, zařadit do fronty nebo zrušit jejich zařazení do fronty. Proces převodu na `Message` skupinu bajtů se nazývá *kódování*a zpětný proces vytváření `Message` ze skupiny bajtů se nazývá *dekódování*.  
  
 Většina přenosových kanálů využívá komponenty s názvem *kodéry zpráv* k tomu, aby fungovalo kódování a dekódování. Kodér zprávy je podtřídou <xref:System.ServiceModel.Channels.MessageEncoder> třídy. `MessageEncoder`zahrnuje různá `ReadMessage` `WriteMessage` přetížení a přetížení metod pro převod mezi `Message` a skupinami bajtů.  
  
 Na straně odesílání předává kanál přenosu vyrovnávací paměti `Message` objekt, který přijal z kanálu nad ním `WriteMessage` . Vrátí pole bajtů, které pak použije k provedení akce (například balení těchto bajtů jako platných paketů TCP a jejich odeslání do správného cíle). Kanál pro přenos streamování nejprve vytvoří `Stream` (například přes odchozí připojení TCP) a pak předá `Stream` a `Message` musí odeslat příslušnému `WriteMessage` přetížení, které zapíše zprávu.  
  
 Přenosový kanál na straně příjmu extrahuje Příchozí bajty (například z příchozích paketů TCP) do pole a volání `ReadMessage` , aby získal `Message` objekt, který může předat dál zásobník kanálu. Kanál pro přenos streamování vytvoří `Stream` objekt (například síťový datový proud přes příchozí připojení TCP) a předá ho, aby se `ReadMessage` `Message` objekt vrátil.  
  
 Oddělení přenosů mezi transportními kanály a kodérem zpráv není povinné. je možné zapisovat transportní kanál, který nepoužívá kodér zpráv. Výhodou tohoto oddělení je však snadné složení. Pokud transportní kanál používá jenom základní <xref:System.ServiceModel.Channels.MessageEncoder> , může spolupracovat s jakýmkoli WCF nebo kodérem zpráv od jiných výrobců. Podobně je možné, že se stejný kodér obvykle používá v jakémkoli transportním kanálu.  
  
### <a name="message-encoder-operation"></a>Operace kodéru zpráv  
 Chcete-li popsat typickou operaci kodéru, je vhodné vzít v úvahu následující čtyři případy.  
  
|Operace|Komentář|  
|---------------|-------------|  
|Kódování, ukládání do vyrovnávací paměti|V režimu vyrovnávací paměti kodér normálně vytvoří vyrovnávací paměť s proměnlivou velikostí a následně vytvoří zapisovač XML. Pak zavolá <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> kódovaný text, který zapisuje hlavičky a pak tělo pomocí <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> , jak je vysvětleno v předchozí části `Message` v tomto tématu. Obsah vyrovnávací paměti (reprezentovaný jako pole bajtů) se pak vrátí transportnímu kanálu, který se má použít.|  
|Kódování, streamování|V režimu streamování je operace podobná výše, ale jednodušší. Není nutné ukládat do vyrovnávací paměti. Zapisovač XML je obvykle vytvořen přes datový proud a <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> je volán na, `Message` aby jej bylo možné zapsat do tohoto zapisovače.|  
|Dekódování, ukládání do vyrovnávací paměti|Při dekódování v režimu vyrovnávací paměti `Message` je obvykle vytvořeno speciální podtřída obsahující data uložená ve vyrovnávací paměti. Hlavičky zprávy jsou čteny a čtecí modul XML umístěný na textu zprávy je vytvořen. Toto je čtenář, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
|Dekódování, streamování|Při dekódování v režimu streamování je obvykle vytvořeno speciální podtřída zprávy. Datový proud je pro čtení všech hlaviček dostatečně pokročilý a je umístěn v těle zprávy. V datovém proudu se pak vytvoří čtecí modul XML. Toto je čtenář, který bude vrácen s <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
  
 Kodéry můžou provádět i další funkce. Kodéry můžou například fondovat čtečky a zapisovače XML. Vytvoření nového čtecího modulu XML nebo zapisovače je náročné při každém vyžadování. Proto kodéry obvykle udržují fond čtenářů a fond konfigurovatelných objektů, které mají konfigurovatelné velikosti. V popisech dříve popsané operace kodéru pokaždé, když se použije fráze "vytvořit modul XML/zapisovač", obvykle to znamená "vzít si z fondu" nebo ho vytvořit, pokud není k dispozici. " Kodér (a `Message` podtřídy, které vytvoří při dekódování) obsahují logiku pro vrácení čtenářů a zapisovačů do fondů, jakmile už nejsou potřeba (například když `Message` je uzavřený).  
  
 WCF nabízí tři kodéry zpráv, i když je možné vytvořit další vlastní typy. Zadané typy jsou text, binary a mechanizmus pro optimalizaci přenosu zpráv (MTOM). Tyto informace jsou podrobně popsané v tématu [Volba kodéru zpráv](choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Rozhraní IStreamProvider  
 Při psaní odchozí zprávy, která obsahuje obsah datového proudu do zapisovače XML, používá aplikace <xref:System.ServiceModel.Channels.Message> sekvenci volání, která je podobná následující v <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementaci:  
  
- Zapsat veškeré potřebné informace před datovým proudem (například otevření značky XML).  
  
- Napište datový proud.  
  
- Zapište všechny informace za proudem (například uzavírací značku XML).  
  
 To funguje dobře s kódováními podobnými textovému kódování XML. Některá kódování však neumísťují informace o XML sadě (například značky pro počáteční a koncové prvky XML) spolu s daty obsaženými v prvcích. Například v kódování MTOM je zpráva rozdělena na více částí. Jedna část obsahuje XML informační sadu, která může obsahovat odkazy na jiné součásti pro skutečný obsah elementu. Informační sada XML je normálně v porovnání s obsahem streamu velmi malá, takže má smysl ukládat do vyrovnávací paměti informační sadu, zapsat ji a pak obsah streamovat. To znamená, že v době, kdy je zapsána značka uzavíracího elementu, datový proud ještě neměl být zapsán.  
  
 Pro účely tohoto účelu se <xref:System.Xml.IStreamProvider> používá rozhraní. Rozhraní má <xref:System.Xml.IStreamProvider.GetStream> metodu, která vrací datový proud, který se má zapsat. Správný způsob, jak v nástroji vytvořit text zprávy datového proudu, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> je následující:  
  
1. Zapsat veškeré potřebné informace před datovým proudem (například otevření značky XML).  
  
2. Zavolejte `WriteValue` přetížení na, <xref:System.Xml.XmlDictionaryWriter> který přebírá <xref:System.Xml.IStreamProvider> , s `IStreamProvider` implementací, která vrací datový proud, který chcete zapsat.  
  
3. Zapište všechny informace za proudem (například uzavírací značku XML).  
  
 U tohoto přístupu zapisovač XML má možnost zvolit, kdy se má volat <xref:System.Xml.IStreamProvider.GetStream> a zapsat data z datového proudu. Například textový a binární zapisovač XML ho hned zavolá a vypíše streamovaná data v-mezi počátečními a koncovými značkami. Modul pro zápis MTOM se může rozhodnout zavolat <xref:System.Xml.IStreamProvider.GetStream> později, až bude připravený zapsat příslušnou část zprávy.  
  
## <a name="representing-data-in-the-service-framework"></a>Reprezentace dat v rozhraní služby  
 Jak je uvedeno v části "základní architektura" v tomto tématu, je součástí služby WCF, která je mimo jiné za převod mezi uživatelsky přívětivým programovacím modelem pro data zpráv a skutečné `Message` instance. Výměna zpráv je standardně reprezentovaná v rámci služby jako metoda .NET Framework označená <xref:System.ServiceModel.OperationContractAttribute> atributem. Metoda může v některých parametrech převzít a může vracet návratovou hodnotu nebo výstupní parametry (nebo obojí). Na straně služby vstupní parametry reprezentují příchozí zprávy a výstupní a výstupní parametry reprezentují odchozí zprávu. Na straně klienta se obrátí na hodnotu true. Programovací model pro popis zpráv pomocí parametrů a návratové hodnoty je podrobně popsán v tématu [určení přenos dat v kontraktech služeb](specifying-data-transfer-in-service-contracts.md). Tato část však poskytuje stručný přehled.  
  
## <a name="programming-models"></a>Programovací modely  
 Rozhraní služby WCF podporuje pět různých programovacích modelů pro popisované zprávy:  
  
### <a name="1-the-empty-message"></a>1. prázdná zpráva  
 Toto je nejjednodušší případ. Chcete-li popsat prázdnou příchozí zprávu, nepoužívejte žádné vstupní parametry.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Chcete-li popsat prázdnou odchozí zprávu, použijte návratovou hodnotu void a nepoužívejte žádné výstupní parametry:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Všimněte si, že se liší od kontraktu jednosměrné operace:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 V tomto `SetDesiredTemperature` příkladu je popsán obousměrný vzor výměny zpráv. Operace vrátila zprávu, ale je prázdná. Je možné vrátit chybu z operace. V příkladu "set žárovky" je vzor výměny zpráv jednosměrný, takže není k dispozici žádná odchozí zpráva k popisu. Služba nemůže v tomto případě sdělit žádné stavy zpátky klientovi.  
  
### <a name="2-using-the-message-class-directly"></a>2. použití třídy zprávy přímo  
 Je možné použít <xref:System.ServiceModel.Channels.Message> třídu (nebo některou z jejích podtříd) přímo v kontraktu operace. V tomto případě rozhraní služby pouze předává rozhraní `Message` z operace do zásobníku kanálu a naopak, bez dalšího zpracování.  
  
 Existují dva hlavní případy použití při použití `Message` přímo. Tuto možnost můžete použít pro pokročilé scénáře, pokud žádný z ostatních programovacích modelů neposkytuje dostatečnou flexibilitu pro popis zprávy. Například můžete chtít použít soubory na disku k popsání zprávy s vlastnostmi souboru, které se stanou záhlavími zpráv a obsah souboru se stane textem zprávy. Pak můžete vytvořit něco podobného jako následující.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Druhá společná použití pro `Message` v kontraktu operace je v případě, že se služba netýká konkrétního obsahu zprávy a funguje ve zprávě jako černý rámeček. Například můžete mít službu, která předává zprávy více příjemcům. Kontrakt lze zapsat následujícím způsobem.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Řádek Action = "*" (akce = "*") efektivně vypíná odesílání zpráv a zajišťuje, aby všechny zprávy odesílané do `IForwardingService` kontraktu provedly jejich způsob `ForwardMessage` fungování. (Normálně by dispečer prověřil hlavičku "Action" zprávy, aby určil, pro kterou operaci je určena. Action = " \* " znamená "všechny možné hodnoty hlavičky Action".) Kombinace akce = " \* " a použití zprávy jako parametru je označována jako "Universal Contract", protože je schopna získat všechny možné zprávy. Aby bylo možné odeslat všechny možné zprávy, jako návratovou hodnotu použijte zprávu a nastavte `ReplyAction` na " \* ". Tím zabráníte, aby rozhraní Service Framework přidalo vlastní hlavičku akce, což vám umožní řídit tuto hlavičku pomocí `Message` objektu, který vrátíte.  
  
### <a name="3-message-contracts"></a>3. kontrakty zpráv  
 WCF poskytuje deklarativní programovací model pro popis zpráv nazývaných *kontrakty zpráv*. Tento model je podrobně popsaný v tématu [Použití kontraktů zpráv](using-message-contracts.md). V podstatě je celá zpráva reprezentována jedním .NET Framework typem, který používá atributy jako <xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute> k popisu, které části třídy kontraktu zprávy by měly být namapovány na tuto část zprávy.  
  
 Kontrakty zpráv poskytují velkou kontrolu nad výslednou `Message` instancí (i když zjevně nezpůsobí, že by `Message` přímo používala třídu). Například tělo zprávy se často skládají z více informací, z nichž každý představuje vlastní XML element. Tyto prvky mohou buď být provedeny přímo v těle (režim*úplné* ), nebo mohou být *zabaleny* do zahrnutého elementu XML. Pomocí programovacího modelu kontraktu zpráv můžete vytvořit rozhodnutí o úplném přebalení a řídit název obálky a oboru názvů.  
  
 Následující příklad kódu kontraktu zprávy tyto funkce znázorňuje.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Položky označené k serializaci (s <xref:System.ServiceModel.MessageBodyMemberAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> atributem, nebo jinými souvisejícími atributy) musí být serializovatelný, aby se mohly zúčastnit kontraktu zprávy. Další informace naleznete v části "serializace" dále v tomto tématu.  
  
### <a name="4-parameters"></a>4. parametry  
 Vývojář, který chce popsat operaci, která funguje na více částech dat, často nepotřebuje stupeň řízení, který poskytují kontrakty zpráv. Když například vytváříte nové služby, jeden obvykle nechce učinit rozhodnutí po rozbalení a rozhodnout o názvu elementu obálky. Tato rozhodnutí často vyžadují důkladnou znalost webových služeb a protokolu SOAP.  
  
 Rozhraní služby WCF může automaticky vybrat nejlepší a nejvíce interoperabilní reprezentace protokolu SOAP pro odesílání nebo přijímání více souvisejících informací, a to bez vynucení těchto možností na uživateli. To se dá udělat tak, že jednoduše popisují tyto části informací jako parametry nebo návratové hodnoty kontraktu operace. Zvažte například následující kontrakt operace.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Rozhraní služby se automaticky rozhodne vložit všechny tři části informací ( `customerID` , `item` a `quantity` ) do těla zprávy a zabalit je do prvku obálky s názvem `SubmitOrderRequest` .  
  
 Popis informací, které se mají odeslat nebo přijmout jako jednoduchý seznam parametrů kontraktu operace, je doporučený postup, pokud neexistují zvláštní důvody pro přechod na složitější kontrakty zpráv nebo `Message` programovací modely založené na bázi.  
  
### <a name="5-stream"></a>5. Stream  
 Použití `Stream` nebo jedna z jejích podtříd v kontraktu operace nebo jako část těla zprávy v kontraktu zprávy lze považovat za samostatný programovací model z těch, které jsou popsány výše. `Stream`Tímto způsobem je jediným způsobem, jak zaručit, aby se váš kontrakt používal v datovém proudu, což je krátký zápis vlastní podtřídy kompatibilní s datovým proudem `Message` . Další informace najdete v tématu [velké objemy dat a streamování](large-data-and-streaming.md).  
  
 Když `Stream` nebo jedna z jejích podtříd je použita tímto způsobem, serializátor není vyvolán. U odchozích zpráv se vytvoří speciální `Message` Podtřída streamování a datový proud se zapíše tak, jak je popsáno v části v <xref:System.Xml.IStreamProvider> rozhraní. V případě příchozích zpráv rozhraní Service Framework vytvoří `Stream` podtřídu přes příchozí zprávu a poskytne ji této operaci.  
  
## <a name="programming-model-restrictions"></a>Omezení programovacího modelu  
 Výše popsané programovací modely nelze libovolně kombinovat. Pokud například operace přijme typ kontraktu zprávy, musí být kontraktem zprávy pouze vstupní parametr. Kromě toho musí operace pak buď vracet prázdnou zprávu (návratový typ void), nebo jiný kontrakt zprávy. Tato omezení programovacího modelu jsou popsána v tématech pro každý konkrétní programovací model: [Použití kontraktů zpráv](using-message-contracts.md), [použití třídy zpráv](using-the-message-class.md)a [velkých dat a streamování](large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formátovací moduly zpráv  
 Výše popsané programovací modely jsou podporovány zapojením součástí, které se nazývají *Formátovací moduly zpráv* , do architektury služby. Formátovací moduly zpráv jsou typy, které implementují <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní nebo, nebo obojí, pro použití v klientech a službách Service WCF v uvedeném pořadí.  
  
 Formátovací moduly zpráv jsou obvykle zapojeny pomocí chování. Například <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> moduly plug-in zprávy kontraktu dat. To se provádí na straně služby nastavením <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> správného formátovacího modulu v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metodě nebo na straně klienta nastavením <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> správného formátovacího modulu v <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> metodě.  
  
 V následujících tabulkách jsou uvedeny metody, které mohou být implementovány pomocí formátovacího modulu zprávy.  
  
|Rozhraní|Metoda|Akce|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede parametry příchozího `Message` provozu na operaci.|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Vytvoří odchozí `Message` a výstupní parametry operace návratové hodnoty.|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Vytvoří odchozí `Message` parametry operace from.|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Převede příchozí `Message` na návratovou hodnotu nebo výstupní parametry.|  
  
## <a name="serialization"></a>Serializace  
 Vždy, když použijete kontrakty nebo parametry zprávy pro popis obsahu zprávy, je nutné použít serializaci k převedení mezi .NET Framework typy a reprezentace XML v informačním souboru. Serializace se používá na jiných místech v technologii WCF, například <xref:System.ServiceModel.Channels.Message> má obecnou <xref:System.ServiceModel.Channels.Message.GetBody%2A> metodu, kterou lze použít ke čtení celého těla zprávy do objektu.  
  
 WCF podporuje dvě technologie serializace "mimo rámeček" pro serializaci a deserializaci parametrů a částí zprávy: <xref:System.Runtime.Serialization.DataContractSerializer> a `XmlSerializer` . Kromě toho můžete napsat vlastní serializátory. Nicméně jiné části služby WCF (například obecná `GetBody` Metoda nebo serializace chyby protokolu SOAP) mohou být omezeny pouze na použití <xref:System.Runtime.Serialization.XmlObjectSerializer> podtříd ( <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> , ale ne na <xref:System.Xml.Serialization.XmlSerializer> ), nebo mohou být pevně zakódovány, aby používaly pouze <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 `XmlSerializer`Je modul serializace používaný v ASP.NET webové služby. `DataContractSerializer`Je nový Serializační modul, který rozumí novému programovacímu modelu kontraktu dat. `DataContractSerializer`je výchozí volbou a volba, která se má použít, `XmlSerializer` může být provedena na základě jednotlivých operací pomocí <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atributu.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>a <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> představují chování, které zodpovídá za připojení v formátovacích modulech zpráv pro `DataContractSerializer` a v `XmlSerializer` uvedeném pořadí. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>Chování může ve skutečnosti fungovat s jakýmkoli serializátorem, který je odvozen z <xref:System.Runtime.Serialization.XmlObjectSerializer> , včetně <xref:System.Runtime.Serialization.NetDataContractSerializer> (podrobně popsané v tématu použití samostatné serializace). Chování volá jedno z `CreateSerializer` přetížení virtuální metody pro získání serializátoru. Chcete-li připojit jiný serializátor, vytvořte novou <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podtřídu a přepište obě `CreateSerializer` přetížení.  
  
## <a name="see-also"></a>Viz také

- [Určování přenosu dat v kontraktech služby](specifying-data-transfer-in-service-contracts.md)
