---
title: Objemná data a vysílání datových proudů
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: f381df2acdb370c6e84d3a00079578f8fceb69f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467582"
---
# <a name="large-data-and-streaming"></a>Objemná data a vysílání datových proudů
Windows Communication Foundation (WCF) jsou infrastruktura komunikace založený na formátu XML. Protože XML data je běžně zakódován do formátu standardního textu definované v [specifikace XML 1.0](https://go.microsoft.com/fwlink/?LinkId=94838), připojené systémy vývojářům a architektům jsou obvykle, které zajímá nároky na místo při přenosu (nebo velikost) zprávy odeslané přes síť a založený na textu kódování XML představuje zvláštní výzev pro efektivní přenos binární data.  
  
## <a name="basic-considerations"></a>Základní aspekty  
 Poskytnout základní informace o následující informace pro službu WCF, tato část ukazuje některé obecné připomínky můžete vystavit a důležité informace týkající se kódování binárních dat, a streamování, které obecně platí pro připojené systémy infrastruktury.  
  
### <a name="encoding-data-text-vs-binary"></a>Kódování dat: Text vs. binární  
 Obvykle vyjádřená vývojáře starostí zahrnují dojem, že XML má významné režijní náklady v porovnání s binární typy z důvodu opakující povaze počáteční značky a koncovými značkami, že kódování číselné hodnoty je považován za výrazně větší protože jsou vyjádřeny v textových hodnot a binární data nelze efektivně vyjádřit, protože musí být speciálně kódovány pro vkládání do formátu textu.  
  
 Zatímco řada z nich a podobně se týká jsou platné, skutečné rozdíl mezi text XML kódováním zpráv v prostředí XML webové služby a kódování binární zprávy ve starší verzi vzdálené volání procedur (RPC) prostředí je často mnohem méně důležité než Počáteční faktor by mohla naznačovat.  
  
 Při XML text kódováním zprávy jsou transparentní a "lidsky čitelné" binární zprávy jsou často poměrně skrytého porovnání a obtížně dekódování bez nástroje. Tento rozdíl v čitelnost vede z nich se má přehlédnout, že binární zprávy také často provádění vložených metadat v datové části, který přidává režie stejně jako u textových zpráv XML. To platí konkrétně pro binární formáty, které mají poskytují volné párování a dynamické vyvolání funkce.  
  
 Binární formáty však běžně nesou informaci takové popisnými metadaty v "záhlaví" které také deklaruje rozložení dat následujících datových záznamů. Datová část potom následuje této společné deklarace bloku metadat s minimálními nároky na další. Naproti tomu XML obklopuje jednotlivých datových položek v elementu nebo atributu tak, aby nadřazené metadat pro každý objekt Serializovaná datová část opakovaně zahrnuty. V důsledku toho velikost objektu jedné serializované datové části je podobný jako při porovnání text, který se binární reprezentaci jako některé popisná metadata musí být vyjádřena v obou případech ale binární formát výhody popis sdílené metadat s každou další datová část objektu, který se přenáší z důvodu nižší celkové režijní náklady.  
  
 Stále, u určitých datových typů, jako je například čísla, může být nevýhodou použití pevné velikosti, binární reprezentace číselné, jako je například typ 128bitové desetinné místo prostého textu, jako prostý text reprezentace pravděpodobně několik menších bajtů. Textová data také může mít velikost výhody obvykle flexibilnější text XML kódováním volby, zatímco může ve výchozím nastavení 16 bitů nebo dokonce 32-bit Unicode, které se nevztahují na binární formát XML .NET některé binární formáty.  
  
 V důsledku toho rozhodování mezi textová nebo binární není úplně stejně jednoduše jako si za předpokladu, že binární zprávy budou vždy menší než textu XML zprávy.  
  
 Vymazat výhod textu XML zprávy je, že jsou založené na standardech a nabízejí nejširší škálu možností možností vzájemná funkční spolupráce a platformní podpory. Další informace najdete v části "Kódování" dále v tomto tématu.  
  
### <a name="binary-content"></a>Binární obsah  
 Jednu oblast, kde jsou lepší než založený na textu kódování z hlediska výsledná velikost zprávy binárního kódování jsou položky velkému objemu binárních dat jako jsou obrázky, videa, zvukové klipy nebo jakoukoli jinou formu neprůhledný, binární data, která musí být vyměňují mezi službami a jejich příjemci. Aby tyto typy dat do textu XML běžným přístupem je zakódovat je pomocí kódování Base64.  
  
 Každý znak v řetězec s kódováním Base64, představuje 6 bitů původní data 8 bitů, což vede poměr 4:3 kódování režie pro Base64, výčtu nebudou započteny velmi formátovací znaky (návrat na začátek řádku řádku), které jsou obvykle přidány na základě konvence. Přestože významné rozdíly mezi XML a binární kódování, obvykle závisí na scénáři, zvýšení velikosti více než 33 % při přenosu datovou část, která 500 MB není obvykle přijatelné.  
  
 Standard, aby toto kódování režie, mechanismus pro optimalizaci přenosu zprávu (MTOM) umožňuje zajištěním externího velké datové prvky, které jsou obsaženy ve zprávě a jejich provádění se zprávou jako binární data bez jakékoli speciální kódování. S MTOM zprávy se vyměňují podobným způsobem přenos protokolu SMTP (Simple Mail) e-mailové zprávy s přílohami nebo vložený obsah (obrázky a další obsah); Zprávy MTOM jsou dodávány jako sekvence MIME multipart/related kořenové části se skutečné zprávu protokolu SOAP.  
  
 Zpráva MTOM SOAP se liší od jeho zrušení kódovaného verzi tak, aby značky speciální elementů, které odkazují na příslušné části MIME proběhnout původní prvky ve zprávě, která obsahuje binární data. V důsledku toho zprávu protokolu SOAP odkazuje na binární obsah tak, že označíte částí MIME odeslané s ním, ale jinak právě přenáší textová data XML. Protože tento model je úzce v souladu s modelem zavedené SMTP, existuje široká podpora nástrojů pro kódování a dekódování zprávy MTOM na mnoha platformách, takže je mimořádně interoperabilní podle výběru.  
  
 Stále stejně jako Base64, MTOM také obsahuje nezbytné režijní náklady pro formát MIME tak, aby výhody používání MTOM se zobrazují pouze, pokud překročí velikost prvku binární data o velikosti 1 KB. Z důvodu režie může být větší než zprávy, které používají kódování Base64 pro binární data, pokud zůstane binární datové části v rámci této prahové hodnoty MTOM kódování zprávy. Další informace najdete v části "Kódování" dále v tomto tématu.  
  
### <a name="large-data-content"></a>Obsah velkých objemů dat  
 Při přenosu nároky jste si poznamenali, výše uvedené datové části 500 MB také představuje skvělý místní výzvu na službu a klienta. Ve výchozím nastavení, WCF zpracovávat zprávy v *ve vyrovnávací paměti režimu*. To znamená, že je k dispozici v paměti před jejím odesláním nebo po přijetí celý obsah zprávy. Který je dobrou strategii pro většinu scénářů a jsou nezbytná pro funkce zasílání zpráv, jako je digitální podpisy a spolehlivé doručování, velkých zpráv může vyčerpat systémové prostředky.  
  
 Strategie se velké datové části je streamování. Při zprávy zejména těch, které jsou vyjádřené ve formátu XML, jsou běžně považují za probíhá poměrně kompaktní data balíčky, zpráva může mít velikost několik gigabajtů a vypadat podobně jako průběžné datového proudu více než balíček dat. Při přenosu dat v datových proudů režimu místo ve vyrovnávací paměti režimu odesílatel zpřístupní obsah textu zprávy příjemci ve formě datového proudu a infrastruktury zpráva průběžně předá data od odesílatele příjemce, protože je k dispozici.  
  
 Nejběžnější scénář, ve kterém takový obsah velkých objemů dat, přenosy dojít, jsou přenosy binárních dat objektů, které:  
  
-   Nelze se rozdělit snadno do zprávy sekvence.  
  
-   Musí doručit včas.  
  
-   Nejsou k dispozici v plné výši při zahájení přenosu.  
  
 Pro data, která těchto omezení nemá je obvykle vhodnější odeslat pořadí zpráv v rámci oboru relace než velkých zpráv. Další informace najdete v části "Streamovaná Data" dále v tomto tématu.  
  
 Při odesílání velkých objemů dat je potřeba nastavit `maxAllowedContentLength` nastavení služby IIS (Další informace najdete v části [konfigurace omezení počtu požadavků služby IIS](https://go.microsoft.com/fwlink/?LinkId=253165)) a `maxReceivedMessageSize` vazby nastavení (například [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) nebo <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` Výchozí hodnoty vlastností 28.6 m a `maxReceivedMessageSize` vlastnost Výchozí hodnota je 64 KB.  
  
## <a name="encodings"></a>Kódování  
 *Kódování* definuje sadu pravidel o tom, jak zobrazení zpráv na lince. *Kodér* implementuje tyto kódování a odpovídá na straně odesílatele pro zapnutí <xref:System.ServiceModel.Channels.Message> zprávy v paměti do datového proudu bajtů nebo bajtová vyrovnávací paměť, kterou je možné odeslat přes síť. Na straně příjemce kodér změní pořadí bajtů do zprávy v paměti.  
  
 WCF obsahuje tři kodérů a umožní vám psát a zapojte vlastní kodéry v případě potřeby.  
  
 Každé standardní vazeb obsahuje předem kodér, kterým vazby s předponou Net * pomocí binárního kodéru (zahrnutím <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> třídy) zatímco <xref:System.ServiceModel.BasicHttpBinding> a <xref:System.ServiceModel.WSHttpBinding> třídy použít kodér textu zprávy (pomocí zprávy z <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídy) ve výchozím nastavení.  
  
|Element vazby kodér|Popis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Kodér textu zprávy je kodéru pro všechny vazby založené na protokolu HTTP a vhodnou volbou pro všechny vlastní vazby, kde je vzájemná funkční spolupráce nejvyšší žádný problém. Tomto kodéru čte a zapisuje standardní protokol SOAP 1.1 a SOAP 1.2 textové zprávy s žádné speciální zpracování pro binární data. Pokud <xref:System.ServiceModel.Channels.MessageVersion> zprávy je nastavena na `None`obálky obálky protokolu SOAP je vynecháno z výstupu a serializuje pouze obsah textu zprávy.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Kodér MTOM zpráv je kodér textu, který implementuje speciální zpracování binárních dat a není použita ve výchozím nastavení v některém z standardní vazby, protože je výhradně nástroj Optimalizace případ od případu. Pokud zpráva obsahuje binární data, která překročí prahovou hodnotu, pokud kódování MTOM přínosy, se do části MIME následující obálky zprávy externalized data. V tématu Povolení MTOM dál v této části.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Kodér binárních zpráv je kodéru pro Net * vazbách a vhodnou volbou pokaždé, když oba komunikujících stran jsou založené na WCF. Kodér binárních zpráv používá .NET binární formát XML, specifické pro společnost Microsoft binární reprezentaci XML informace sad (Infosets), které obvykle vrací menší nároky na místo než ekvivalentní reprezentaci XML 1.0 a zakóduje binární data v bajtové podobě datový proud.|  
  
 Kódování textu zprávy je obvykle nejlepší volbou pro jakékoli komunikační trasa, která vyžaduje spolupráci při kódování binární zprávy je nejlepší volbou pro jiné cesty komunikace. Kódování binární zprávy obvykle vrací menší zpráva, že velikosti ve srovnání s text jedné zprávy a postupně i menší velikosti za celou dobu relace komunikace. Na rozdíl od kódování textu binární kódování není nutné používat speciální zpracování pro binární data, jako je třeba použití ve formátu Base64, ale představuje bajtů na bajty.  
  
 Pokud vaše řešení nevyžaduje, aby vzájemná funkční spolupráce, ale chcete použít přenos pomocí protokolu HTTP, můžete vytvořit <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do vlastní vazby, který používá <xref:System.ServiceModel.Channels.HttpTransportBindingElement> třídy pro přenos. Pokud počet klientů pro vaši službu, které vyžadují vzájemná funkční spolupráce, se doporučuje zpřístupníte paralelní koncových bodů, která má každá odpovídající přenos a kódování volby pro příslušné klienty povolena.  
  
### <a name="enabling-mtom"></a>Povolení funkce MTOM  
 Při zajištění lepší interoperability je povinné a velkému objemu binárních dat se musí odeslat a pak kódování zprávy MTOM je alternativou kódování strategie, kterou můžete povolit na standardu <xref:System.ServiceModel.BasicHttpBinding> nebo <xref:System.ServiceModel.WSHttpBinding> vazby nastavením funkcím `MessageEncoding` Vlastnost <xref:System.ServiceModel.WSMessageEncoding.Mtom> nebo vytváření <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do <xref:System.ServiceModel.Channels.CustomBinding>. Následující příklad kódu, extrahovat z [kódování MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) Ukázka předvádí, jak povolit MTOM v konfiguraci.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <wsHttpBinding>  
        <binding name="ExampleBinding" messageEncoding="Mtom"/>  
      </wsHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Jak už bylo zmíněno dříve, rozhodnout a použít kódování MTOM závisí na objemu dat, odesílání. Také protože MTOM je povoleno na úrovni vazby, povolení MTOM ovlivňuje všechny operace na daný koncový bod.  
  
 Protože kodér MTOM vydá kódování MTOM MIME/více-částečný zprávu bez ohledu na to, zda skončilo se externalized binárních dat, měli byste obecně pouze povolit MTOM pro koncové body, které výměna zpráv s využitím více než 1 KB binární data. Také kontrakty služeb, které jsou navrženy pro použití s koncovými body s povoleným MTOM by měl, pokud je to možné, omezovat se zadáním těchto operace přenosu dat. Funkce související ovládací prvek by měl být uložený v samostatné smlouvy. Toto pravidlo "Pouze MTOM" platí pouze pro zprávy odeslané přes koncový bod povolené MTOM; kodér MTOM může dekódovat a parsovat příchozí zprávy bez MTOM také.  
  
 Pomocí kodér MTOM splňuje všechny ostatní funkce WCF. Všimněte si, že nemusí být možné toto pravidlo ve všech případech, například když je nutné podporovat relace.  
  
### <a name="programming-model"></a>Programovací model  
 Bez ohledu na to, které tři předdefinované kodérů, které používáte ve vaší aplikaci programovací prostředí je shodné s ohledem na přenos binární data. Rozdíl je v způsob, jakým WCF zpracovává data v závislosti na jejich datové typy.  
  
```  
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}   
```  
  
 Při použití MTOM předchozí kontraktu dat. je serializována podle následujících pravidel:  
  
-   Pokud `binaryBuffer` není `null` a jednotlivě obsahuje dostatek dat k vysvětlení režii externalizace MTOM (hlavičky MIME a tak dále) ve srovnání s Base64 kódování, data se externalized a provádět s touto zprávou jako binární část MIME. Pokud není překročena prahová hodnota, data kódovaná jako Base64.  
  
-   Řetězec (a všechny ostatní typy, které nejsou binární) je vždy reprezentována jako řetězec v textu zprávy, bez ohledu na velikost.  
  
 Vliv na kódování MTOM je stejné, zda je používán kontrakt explicitní data, jak je znázorněno v předchozím příkladu použít seznam parametrů v operaci, mají vnořených datových kontraktů nebo převést objekt kontraktu dat v kolekci. Bajtová pole jsou vždy kandidáty na optimalizaci a jsou optimalizované, pokud se dosažení prahové hodnoty optimalizace.  
  
> [!NOTE]
>  Neměli byste používat <xref:System.IO.Stream?displayProperty=nameWithType> odvozené typy v kontraktech dat. Stream dat by měl být oznámen pomocí streamování modelu je vysvětleno v následující části "Streamovaná Data".  
  
## <a name="streaming-data"></a>Streamování dat  
 Pokud máte velký objem přenášených dat, je režim tvorby datového proudu přenosu ve službě WCF proveditelné alternativou k výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti jako celek.  
  
 Jak už bylo zmíněno dříve, povolení streamování pouze u velkých zpráv (se textová nebo binární obsah), pokud data nelze segmentované, pokud zpráva musí doručit včas, nebo pokud data ještě nejsou plně k dispozici při zahájení přenosu.  
  
### <a name="restrictions"></a>Omezení  
 Velký počet funkcí WCF nelze použít, pokud je povoleno vysílání datového proudu:  
  
-   Digitální podpisy pro text zprávy nejde provést, protože vyžadují výpočtu hodnoty hash přes obsah celé zprávy. Díky streamování, obsah není plně k dispozici při vytvořena a posílat záhlaví zpráv, a proto nelze vypočítat digitální podpis.  
  
-   Šifrování závisí na digitálních podpisů k ověření, že data byla rekonstruována správně.  
  
-   Spolehlivé relace musí vyrovnávací paměti odeslaných zpráv na straně klienta pro opakované dodání Pokud zpráva získá ztrátě při přenosu a musí obsahovat zpráv ve službě ještě před jejich k implementaci služby pro zachování pořadí zpráv v případě, že jsou zprávy přijímány mimo pořadí.  
  
 Kvůli těmto omezením funkční můžete použít pouze zabezpečení transportní vrstvy, které možnosti pro streamování a nelze zapnout spolehlivé relace. Streamování je k dispozici pouze u následujících vazeb definovaných systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Protože základní přenosy z <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> přináší spolehlivé doručování a relace na základě připojení podporovat, na rozdíl od protokolu HTTP, tyto dvě vazby jsou pouze nejméně ovlivněný zahlcením těmto omezením, v praxi.  
  
 Streamování není k dispozici přenos řízení front zpráv (MSMQ) a proto jej nelze použít s <xref:System.ServiceModel.NetMsmqBinding> nebo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy. Přenos řízení front zpráv podporuje pouze uložené do vyrovnávací paměti datových přenosů s velikostí omezené zprávy, zatímco všechny ostatní přenosy nemají žádné omezení velikosti praktické zprávy pro většinu scénářů.  
  
 Streamování není k dispozici při pomocí přenosu protokolu Peer Channel, takže není k dispozici <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Streamování a relace  
 Můžete obdržet neočekávané chování při streamování volání s vazbou na základě relace. Všechna volání streamování se provádějí přes jeden kanál (kanálu datagramu), který nepodporuje relace, i v případě, že vazba používá je nakonfigurována pro použití relací. Pokud více klientů volání datových proudů na stejný objekt služby přes vazbu na základě relace a objekt služby souběžný režim je nastavena na jednou a jeho režimu instance kontextu je nastavena na hodnotu PerSession, všechna volání musí projít kanálu datagramu a aby volání zpracovávána v čase. Jeden nebo více klientů může potom vypršení časového limitu. Tento problém můžete obejít tak, že buď nastavíte režim kontextu instancí objektu služby PerCall nebo souběžnosti k několika.  
  
> [!NOTE]
>  MaxConcurrentSessions nemá žádný vliv v tomto případě, protože není k dispozici pouze jeden "relace".  
  
### <a name="enabling-streaming"></a>Povolení streamování  
 Můžete povolit datové proudy následujícími způsoby:  
  
-   Odesílání a příjem požadavků v režim tvorby datového proudu a přijmout a vrácení odpovědi v režimu vyrovnávací paměti (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Odesílání a příjem požadavků v režimu vyrovnávací paměti a přijímají a vrací odpovědi v režimu proudu (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Odesílat a přijímat požadavky a odpovědi v režimu proudu v obou směrech. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Vám může zcela vypnout streamování nastavením je režim přenosu na <xref:System.ServiceModel.TransferMode.Buffered>, což je výchozí nastavení na všechny vazby. Následující kód ukazuje, jak nastavit režim přenosu v konfiguraci.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streaming"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Při vytváření instance vaše vazby v kódu, musíte nastavit příslušné `TransferMode` majetku vazby (nebo element vazby přenosu, pokud vytváříte vlastní vazby) na jednu z výše uvedených hodnot.  
  
 Můžete zapnout, aniž by to ovlivnilo funkce streamování pro zpracování požadavků a odpovědí nebo pro oba směry nezávisle na obou stranách komunikujících stran. Ale byste měli vždy předpokládat, že velikost přenášených dat je důležité, že oba koncové body spoj ospravedlnit povolení streamování. Pro komunikaci napříč platformami, kde jeden z koncových bodů není implementovaná s použitím technologie WCF umožňuje používat streamování závisí na funkce streamování platformu. Další výjimečných výjimku, může být spotřebu paměti řízené scénáři, kde klienta nebo služby musíte minimalizovat jeho pracovní sada a můžete dovolit pouze malou vyrovnávací pamětí velikosti.  
  
### <a name="enabling-asynchronous-streaming"></a>Povolení asynchronního streamování  
 Pokud chcete povolit, asynchronního streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`. Přidali jsme také možnost true asynchronního streamování na straně odesílání. Tím se zlepšuje škálovatelnost služby ve scénářích, kde je datový proud zpráv do více klientů, z nichž některé jsou pomalé v režimu čtení pravděpodobně z důvodu zahlcení sítě, nebo nejsou vůbec čtení. V těchto scénářích jsme teď neblokují jednotlivá vlákna ve službě za klienta. Tím se zajistí, že služba je schopná zpracovat mnoho více klientů a zlepšuje škálovatelnost služby.  
  
### <a name="programming-model-for-streamed-transfers"></a>Programovací Model pro streamovaná přenosy  
 Programovací model pro streamování je jednoduché. Pro příjem streamovaných datech, určete kontrakt operace, která má jeden <xref:System.IO.Stream> zadaný vstupní parametr. Pro vracení datového proudu, vrátí <xref:System.IO.Stream> odkaz.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamedService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
    [OperationContract]  
    Stream RequestInfo(string query);  
    [OperationContract(OneWay=true)]  
    void ProvideInfo(Stream data);  
}  
```  
  
 Operace `Echo` v předchozím příkladu přijímá a vrací datový proud a je proto třeba použít u vazby s <xref:System.ServiceModel.TransferMode.Streamed>. Pro operaci `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> je nejvhodnější, protože se vrátí jenom <xref:System.IO.Stream>. Jednosměrná operace je nejvhodnější pro <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Všimněte si, že přidání druhého parametru následující `Echo` nebo `ProvideInfo` operací způsobí, že model služby zpátky na strategii ve vyrovnávací paměti a použití za běhu serializace reprezentace datového proudu. Operace pouze s parametrem jednoho vstupního datového proudu jsou kompatibilní s začátku do konce požadavek streaming.  
  
 Toto pravidlo se vztahuje podobně kontraktů zpráv. Jak je znázorněno v následujícím kontraktu zprávy, může mít pouze jednoho těla členské v váš kontraktu zprávy, které je datový proud. Pokud chcete sdělit Další informace pomocí datového proudu, musí být tyto informace provádí v záhlaví zpráv. Text zprávy je rezervovaných exkluzivně pro streamování obsahu.  
  
```  
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}   
```  
  
 End streamovaná přenosů a zpráva je uzavřena dosáhne datový proud na konci souboru (EOF). Při odesílání zprávy (návratová hodnota nebo vyvolání operace), můžete předat <xref:System.IO.FileStream> a infrastruktura WCF následně načte všechna data z tohoto datového proudu, dokud datový proud byl zcela čtení a bylo dosaženo konce souboru. Převést datové proudy pro zdroj, který bez těchto předdefinovaných <xref:System.IO.Stream> odvozené třídy existuje, vytvořit takové třídy, překrytí třídy přes datový proud zdroje a použít je jako argument nebo návratovou hodnotu.  
  
 Při přijímání zprávy WCF vytvoří datový proud obsahu těla zprávy s kódováním Base64 (případně odpovídající část MIME, pokud používáte MTOM) a datový proud dosáhne EOF přečtení obsahu.  
  
 Streamování transportní vrstvy také funguje s jakékoli další typ kontraktu zprávy (seznamy parametrů, argumenty kontraktu dat a kontrakt explicitní zprávy), ale vzhledem k tomu, že serializace a deserializace tohoto typu zprávy vyžaduje ukládání do vyrovnávací paměti modulem pro serializaci , není vhodné používat takové varianty kontraktu.  
  
### <a name="special-security-considerations-for-large-data"></a>Zvláštní bezpečnostní aspekty velkých objemů dat  
 Všechny vazby umožňují omezit velikost příchozí zprávy, aby se zabránilo útoky s cílem odepření služeb. <xref:System.ServiceModel.BasicHttpBinding>, Například zpřístupňuje [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) vlastnost, která za rozsahem velikost příchozí zprávy a proto také za rozsahem maximální množství paměti, která se využívají Při zpracování zprávy. Tato jednotka je sady v bajtech s výchozí hodnotou 65 536 bajtů.  
  
 Ohrožení zabezpečení, které jsou specifické pro scénář streamování velkých objemů dat vyvolá odepření služby tak, že data uložená do vyrovnávací paměti, když příjemce očekává, že odesílání. Například WCF vždy vyrovnávacích pamětí záhlaví SOAP zprávy, a proto útočník může vytvořit velké škodlivé zprávy, který je tvořen výhradně záhlaví přinutit data, která mají být ukládány do vyrovnávací paměti. Pokud je povoleno vysílání datového proudu, `MaxReceivedMessageSize` může být nastavená na velmi velké hodnoty, protože příjemce nikdy očekává celé zprávy do vyrovnávací paměti najednou. Pokud je do vyrovnávací paměti zprávy WCF, dojde k přetečení paměti.  
  
 Proto omezení maximální velikost příchozí zprávy není dostatečně v tomto případě. `MaxBufferSize` Vlastnost se vyžaduje k omezení paměti ukládaného ve vyrovnávací paměti WCF. Je důležité si nastavíte na hodnotu bezpečné (nebo je uchovávejte na výchozí hodnotu) při streamování. Předpokládejme například, že vaše služba musí přijímat soubory ve velikosti až 4 GB a jejich uložení na místním disku. Předpokládejme také, že vaše paměti je omezená tak, že jste pouze uložit do vyrovnávací paměti 64 KB dat. současně. Pak byste měli nastavit `MaxReceivedMessageSize` až 4 GB a `MaxBufferSize` 64 kB. Navíc ve vaší implementaci služby musíte zajistit, abyste si pouze z příchozího datového proudu v bloky dat 64 KB a číst další blok předtím, než se předchozí zapsané na disk a byla odstraněna z paměti.  
  
 Je také důležité pochopit, že tato kvóta omezuje pouze ukládání do vyrovnávací paměti provádí WCF a nemůže chránit proti žádné ukládání do vyrovnávací paměti, který používáte ve vaší vlastní implementaci služby ani klienta. Další informace o dodatečné informace o zabezpečení najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Rozhodnout a použít ve vyrovnávací paměti nebo streamovaná přenosy je místní rozhodnutí koncového bodu. Pro přenosy HTTP je režim přenosu nešíří přes připojení nebo proxy servery a jiných dodavatelů. Nastavení režimu převodu se neprojeví v popisu rozhraní služby. Po vygenerování klienta WCF na službu, musíte upravit konfigurační soubor služby určené pro použití s datovým proudem přenosy pro nastavení režimu. Pro protokoly TCP a přenosy pojmenovaný kanál se šíří je režim přenosu jako kontrolní výraz zásad.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
