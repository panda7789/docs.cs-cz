---
title: Objemná data a vysílání datových proudů
description: Seznamte se s důležitými informacemi o komunikaci založené na XML WCF, kodérech a streamovaná data, včetně přenosu binárních dat.
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 2eb57e2f57bebb2e765ea798b3dff27e0187e8c7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246581"
---
# <a name="large-data-and-streaming"></a>Objemná data a vysílání datových proudů

Windows Communication Foundation (WCF) je komunikační infrastruktura založená na jazyce XML. Vzhledem k tomu, že data XML jsou obvykle kódována ve standardním textovém formátu definovaném ve [specifikaci XML 1,0](https://www.w3.org/TR/REC-xml/), jsou obvykle zapojeni vývojáři a architekti propojených systémů, které se týkají zátěže (nebo velikosti) zpráv odesílaných v síti a kódování XML založeného na textu, což má za následek zvláštní výzvy pro efektivní přenos binárních dat.  
  
## <a name="basic-considerations"></a>Základní požadavky  
 Pokud chcete poskytnout informace o následujících informacích o WCF, Tato část popisuje některé obecné aspekty a důležité informace pro kódování, binární data a streamování, které se obecně vztahují na infrastrukturu připojených systémů.  
  
### <a name="encoding-data-text-vs-binary"></a>Data kódování: text oproti binárnímu souboru  
 Obvykle vyjadřují obavy vývojářů, jako je vnímání kódu XML v porovnání s binárními formáty z důvodu opakovaného charakteru počátečních značek a koncových značek, že kódování numerických hodnot je považováno za podstatně větší, protože je vyjádřeno v textových hodnotách a že binární data nelze vyjádřit efektivně, protože musí být speciálně kódována pro vkládání do textového formátu.  
  
 I když je mnoho z těchto a podobných otázek platných, skutečný rozdíl mezi zprávami kódovanými v jazyce XML v prostředí webových služeb XML a binárními zprávami ve starším prostředí vzdáleného volání procedur (RPC) jsou často mnohem méně významné, než by bylo možné navrhnout počáteční pozornost.  
  
 I když zprávy kódované v jazyce XML jsou transparentní a "čitelné", binární zprávy jsou často poměrně zakryté porovnáním a obtížné dekódovat bez nástrojů. Tento rozdíl v čitelnosti vede k přehlédnout, že binární zprávy také často obsahují vložená metadata v datové části, což zvyšuje režii stejně jako textové zprávy XML. To platí konkrétně pro binární formáty, které se zaměřují na poskytování možností volného spojení a dynamického vyvolání.  
  
 Binární formáty však obvykle přenášejí takové popisné informace o metadatech v "hlavičce", která také deklaruje rozložení dat pro následující záznamy dat. Datová část pak následuje za deklarací Common metadata Block s minimální další režií. Naproti tomu XML uzavře každou datovou položku v elementu nebo atributu tak, aby se nadřazené metadata opakovaně zahrnutá pro každý serializovaný objekt datové části. V důsledku toho je velikost jednoho serializovaného objektu datové části podobná při porovnávání textu s binárními reprezentacemi, které je třeba vyjádřit pro obě, ale v binárním formátu jsou přínosy z popisu sdílených metadat s každým dalším objektem datové části, který se přenáší z důvodu nižší celkové režie.  
  
 U některých datových typů, jako jsou třeba čísla, může být Nevýhodou použití binárního číselné reprezentace s pevnou velikostí, jako je například 128 desítkový typ místo prostého textu, protože reprezentace v podobě prostého textu může být menší než několik bajtů. Textová data také mohou mít výhody z typicky flexibilního flexibilního kódování textu XML, zatímco některé binární formáty mohou být ve výchozím nastavení 16bitové nebo na32elné Unicode, které se nevztahují na binární formát XML .NET.  
  
 V důsledku toho se rozhoduje, že mezi textem a binárním souborem není poměrně snadné, protože binární zprávy jsou vždycky menší než textové zprávy XML.  
  
 Nejasnou výhodou textových zpráv XML je, že jsou založené na standardech a nabízejí nejširší možnosti pro interoperabilitu a podporu platforem. Další informace najdete v části "kódování" dále v tomto tématu.  
  
### <a name="binary-content"></a>Binární obsah  
 Jedna oblast, kde jsou binární kódování nadřazené kódování založenému na textu, pokud jde o výslednou velikost zprávy, jsou velké binární datové položky, jako jsou obrázky, videa, zvukové klipy nebo jakákoli jiná forma neprůhledných binárních dat, která musí být vyměněna mezi službami a jejich příjemci. Aby se tyto typy dat vešly do textu XML, společný přístup je kódování pomocí kódování Base64.  
  
 V řetězci zakódovaném ve formátu base64 každý znak představuje 6 bitů původních 8 bitových dat, což 4:3 vede ke zvýšení poměru znaků pro kódování Base64 a nepočítá se navíc k vypočítávání znaků nadbytečného formátování (návrat na řádku nebo LF), které jsou běžně přidané podle konvence. I když význam rozdílů mezi XML a binárním kódováním obvykle závisí na scénáři, velikost větší než 33% při přenosu datové části 500-MB obvykle není přijatelná.  
  
 Aby se tato režie při kódování nezobrazovala, Standard MTOM (Message reoptimization) umožňuje přenesení velké datové prvky, které jsou obsaženy ve zprávě, a jejich předání jako binární data bez jakéhokoli speciálního kódování. U MTOM se zprávy vyměňují podobným způsobem jako e-mailové zprávy protokolu SMTP (Simple Mail Transfer Protocol) s přílohami nebo vloženým obsahem (obrázky a další vložený obsah). Zprávy MTOM se zabalí jako části s částmi MIME nebo související s kořenovou částí, která je skutečnou zprávou SOAP.  
  
 Zpráva SOAP protokolu MTOM je upravena ze své nekódované verze, takže speciální značky prvků, které odkazují na příslušné části MIME, přebírají místo původních prvků ve zprávě, která obsahovala binární data. V důsledku toho zpráva SOAP odkazuje na binární obsah tak, že odkazuje na části MIME, které s ním jsou odesílány, ale jinak pouze textová data XML. Vzhledem k tomu, že je tento model úzce zarovnán s dobře zavedeným modelem SMTP, existuje široká podpora nástrojů pro kódování a dekódování zpráv MTOM na mnoha platformách, což usnadňuje možnost volby.  
  
 Stejně jako u Base64 také přináší MTOM s určitou režií pro formát MIME, takže výhody použití MTOM se zobrazují jenom v případě, že velikost binárního datového elementu přesáhne 1 KB. Kvůli režii mohou být zprávy kódované pomocí MTOM větší než zprávy, které používají kódování Base64 pro binární data, pokud binární datová část zůstane pod touto prahovou hodnotou. Další informace najdete v části "kódování" dále v tomto tématu.  
  
### <a name="large-data-content"></a>Obsah velkého objemu dat  
 V případě nenáročného z provozu představuje dřív zmíněná datová část 500 MB také skvělou místní výzvu pro službu a klienta. Ve výchozím nastavení WCF zpracovává zprávy v *režimu vyrovnávací paměti*. To znamená, že celý obsah zprávy je přítomen v paměti před odesláním nebo po jeho přijetí. I když je to dobrá strategie pro většinu scénářů a je nutná pro zasílání zpráv, jako jsou digitální podpisy a spolehlivé doručování, mohou velké zprávy vyčerpat prostředky systému.  
  
 Tato strategie se zabývat velkými datovými částmi je streamování. I když se zprávy, zejména ty vyjádřené ve formátu XML, považují za poměrně kompaktní datové balíčky, může se stát, že velikost zprávy je větší a podobá se souvislému datovému streamu většímu než datový balíček. Když se data přenesou v režimu streamování místo v režimu vyrovnávací paměti, odesílatel vytvoří obsah zprávy, která je k dispozici příjemci ve formě datového proudu, a infrastruktura zpráv nepřetržitě předává data od odesílatele k příjemci, jakmile bude k dispozici.  
  
 Nejběžnější scénář, ve kterém dochází k takovým velkým datovým přenosům dat, jsou přenosy binárních datových objektů, které:  
  
- Nelze ji snadno rozdělit do sekvence zpráv.  
  
- Musí být doručen včas.  
  
- Nejsou k dispozici v celém rozsahu při zahájení přenosu.  
  
 V případě dat, která tato omezení nemají, je obvykle lepší odesílat sekvence zpráv v rámci rozsahu relace než jedna velká zpráva. Další informace najdete v části streamovaná data dále v tomto tématu.  
  
 Když posíláte velké objemy dat, budete muset nastavit `maxAllowedContentLength` nastavení IIS (Další informace najdete v tématu [Konfigurace omezení požadavků IIS](https://docs.microsoft.com/iis/configuration/system.webServer/security/requestFiltering/requestLimits/)) a `maxReceivedMessageSize` Nastavení vazby (například [System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) nebo <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A> ). `maxAllowedContentLength`Výchozí hodnota vlastnosti je 28,6 MB a `maxReceivedMessageSize` vlastnost je nastavená na 64 KB.  
  
## <a name="encodings"></a>Kódování  
 *Kódování* definuje sadu pravidel o tom, jak prezentovat zprávy na lince. *Kodér* implementuje takové kódování a zodpovídá na straně odesilatele pro zapnutí v paměti <xref:System.ServiceModel.Channels.Message> do bajtového datového proudu nebo vyrovnávací paměti bajtů, které lze odeslat přes síť. Kodér na straně přijímače zapíná sekvenci bajtů do zprávy v paměti.  
  
 WCF zahrnuje tři kodéry a v případě potřeby umožňuje psát a připojovat vlastní kodéry.  
  
 Každá standardní vazba obsahuje předem nakonfigurovaný kodér, přičemž vazby s předponou NET * používají binární kodér (zahrnutím <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> třídy), zatímco <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSHttpBinding> třídy a používají ve výchozím nastavení kodér textových zpráv (prostřednictvím <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídy).  
  
|Element vazby kodéru|Description|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Kodér textu zprávy je výchozím kodérem pro všechny vazby založené na protokolu HTTP a vhodnou volbou pro všechny vlastní vazby, kde je interoperabilita nejvyššími obavy. Tento kodér čte a zapisuje standardní textové zprávy protokolu SOAP 1.1/SOAP 1,2 bez speciálního zpracování pro binární data. Pokud <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> je vlastnost zprávy nastavena na, je obálka <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> protokolu SOAP vynechána z výstupu a je serializován pouze obsah textu zprávy.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Kodér zpráv MTOM je textový kodér, který implementuje speciální zpracování pro binární data a ve výchozím nastavení se v žádném ze standardních vazeb nepoužívá, protože se jedná o výhradně nástroj pro optimalizaci velkých a malých písmen. Pokud zpráva obsahuje binární data, která překročí prahovou hodnotu, která má za důsledek kódování MTOM, data se externě přidělí na část MIME za obálkou zprávy. Viz povolení MTOM později v této části.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Binární kodér zpráv je výchozím kodérem pro vazby NET * a vhodným výběrem, pokud jsou obě komunikující strany založené na službě WCF. Kodér binárních zpráv používá binární formát XML, který je specifický pro společnost Microsoft, binární reprezentace pro XML Information Sets (Infosets), která obvykle poskytuje menší nároky, než je ekvivalent XML 1,0 reprezentace a kódování binárních dat jako datový proud bajtů.|  
  
 Kódování textové zprávy je obvykle nejlepší volbou pro jakoukoli komunikační cestu, která vyžaduje interoperabilitu, zatímco kódování binárních zpráv je nejlepší volbou pro jakoukoli jinou komunikační cestu. Kódování binárních zpráv obvykle dává menší velikost zpráv v porovnání s textem pro jednu zprávu a postupně i menší velikosti zpráv po dobu trvání relace komunikace. Na rozdíl od kódování textu nemusí binární kódování používat speciální zpracování pro binární data, jako je například použití Base64, ale představuje bajty jako bajty.  
  
 Pokud vaše řešení nepotřebuje spolupráci, ale přesto chcete použít přenos pomocí protokolu HTTP, můžete vytvořit <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do vlastní vazby, která <xref:System.ServiceModel.Channels.HttpTransportBindingElement> pro přenos používá třídu. Pokud určitý počet klientů v rámci služby vyžaduje interoperabilitu, doporučujeme, abyste vystavili paralelní koncové body, které mají odpovídající možnosti přenosu a kódování pro příslušné klienty.  
  
### <a name="enabling-mtom"></a>Povolení MTOM  
 Je-li interoperabilita požadavek a je třeba odeslat velké binární údaje, je kódování zpráv MTOM alternativní strategií kódování, kterou lze povolit u standard <xref:System.ServiceModel.BasicHttpBinding> nebo vazeb nastavením <xref:System.ServiceModel.WSHttpBinding> příslušné `MessageEncoding` vlastnosti na <xref:System.ServiceModel.WSMessageEncoding.Mtom> nebo pomocí sestavení a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.CustomBinding> . Následující příklad kódu extrahovaný z ukázky [kódování MTOM](../samples/mtom-encoding.md) ukazuje, jak povolit MTOM v konfiguraci.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <wsHttpBinding>  
        <binding name="ExampleBinding" messageEncoding="Mtom"/>  
      </wsHttpBinding>  
    </bindings>  
     …  
</system.serviceModel>  
```  
  
 Jak bylo zmíněno dříve, rozhodnutí o použití kódování MTOM závisí na objemu dat, který odesíláte. Kromě toho, protože MTOM je povolen na úrovni vazby, povolení MTOM má vliv na všechny operace v daném koncovém bodu.  
  
 Vzhledem k tomu, že kodér MTOM vždy vygeneruje zprávu MIME/s více částmi ve formátu MTOM bez ohledu na to, zda binární data končí externě, měli byste obecně povolit pouze MTOM pro koncové body, které vyměňují zprávy s více než 1 KB binárních dat. Kontrakty služby navržené pro použití s koncovými body s podporou MTOM by měly být, pokud je to možné, omezené na určení takových operací přenosu dat. Související funkce řízení by se měly nacházet v samostatné smlouvě. Toto pravidlo pouze pro MTOM se vztahuje pouze na zprávy odeslané prostřednictvím koncového bodu s povoleným MTOM. Kodér MTOM může dekódovat a analyzovat i příchozí zprávy, které nepatří do MTOM.  
  
 Použití kodéru MTOM je v souladu se všemi ostatními funkcemi WCF. Všimněte si, že toto pravidlo nemusí být možné sledovat ve všech případech, například když je vyžadována podpora relace.  
  
### <a name="programming-model"></a>Programovací model  
 Bez ohledu na to, který ze tří vestavěných kodérů používáte ve vaší aplikaci, je programovací prostředí identické s ohledem na přenos binárních dat. Rozdíl je v tom, jak WCF zpracovává data na základě jejich datových typů.  
  
```csharp
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}
```  
  
 Při použití nástroje MTOM je předchozí kontrakt dat serializován podle následujících pravidel:  
  
- Pokud `binaryBuffer` není `null` a samostatně obsahuje dostatek dat pro zarovnání režijních nákladů na MTOM (hlavičky MIME atd.) ve srovnání s kódováním base64, data jsou externá a přenesená se zprávou jako binární část MIME. Pokud prahová hodnota není překročena, data budou kódována jako base64.  
  
- Řetězec (a všechny ostatní typy, které nejsou binární), jsou vždy reprezentovány jako řetězec uvnitř těla zprávy bez ohledu na velikost.  
  
 Účinek na kódování MTOM je stejný, ať už používáte explicitní kontrakt dat, jak je znázorněno v předchozím příkladu, použít seznam parametrů v operaci, mít vnořené kontrakty dat nebo přenést objekt kontraktu dat do kolekce. Bajtová pole jsou vždy kandidáti na optimalizaci a jsou optimalizována, pokud jsou splněny mezní hodnoty optimalizace.  
  
> [!NOTE]
> <xref:System.IO.Stream?displayProperty=nameWithType>V kontraktech dat byste neměli používat odvozené typy. Data streamu by se měla sdělit pomocí modelu streamování, který je vysvětlen v následujících částech streamování dat.  
  
## <a name="streaming-data"></a>Streamování dat  
 Pokud máte velké množství dat, která se mají přenést, je režim přenosu streamování ve službě WCF vhodná alternativa k výchozímu chování ukládání zpráv do vyrovnávací paměti a jejich zpracování v celé paměti.  
  
 Jak už bylo zmíněno dříve, povolte streamování jenom pro velké zprávy (s textovým nebo binárním obsahem), pokud se data nedají rozdělit, pokud se tato zpráva musí doručit včas, nebo pokud nejsou data při zahájení přenosu ještě plně dostupná.  
  
### <a name="restrictions"></a>Omezení  
 Pokud je povolené streamování, nemůžete použít významný počet funkcí WCF:  
  
- Digitální podpisy pro tělo zprávy nelze provést, protože vyžadují výpočet hodnoty hash přes celý obsah zprávy. U streamování není obsah po vytvoření a odeslání hlaviček zpráv plně dostupný, a proto nelze vypočítat digitální podpis.  
  
- Šifrování závisí na digitálních podpisech, aby bylo možné ověřit, zda byla data znovu správně vytvořena.  
  
- Spolehlivé relace musí ukládat zprávy na straně klienta pro opětovné doručení, pokud dojde ke ztrátě zprávy v přenosu, a před jejich předáním do implementace služby musí obsahovat zprávy, aby bylo zachováno pořadí zpráv v případě, že zprávy jsou přijímány mimo sekvenci.  
  
 Z důvodu těchto funkčních omezení můžete pro streamování použít jenom možnosti zabezpečení na úrovni přenosu a nemůžete zapnout spolehlivé relace. Streamování je dostupné jenom u následujících vazeb definovaných systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 Vzhledem k tomu, že základní přenosy <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> mají na rozdíl od http podporu spolehlivého doručování a připojení na základě připojení, jsou tyto dvě vazby v praxi jenom minimálními vlivy na tato omezení.  
  
 Pro přenos služby Řízení front zpráv (MSMQ) není služba streaming dostupná a nedá se použít s <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídou nebo. Přenos v rámci služby Řízení front zpráv podporuje pouze datové přenosy s omezenou velikostí zprávy, zatímco u všech ostatních přenosů není pro většinu scénářů k dispozici žádná praktická omezení velikosti zpráv.  
  
 Streamování není k dispozici ani při použití přenosu rovnocenného kanálu, takže není k dispozici v <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
#### <a name="streaming-and-sessions"></a>Streamování a relace  
 Může dojít k neočekávanému chování při volání streamování s vazbou založenou na relacích. Všechna volání streamování se provádějí pomocí jednoho kanálu (kanálu Datagram), který nepodporuje relace ani v případě, že použitá vazba je nakonfigurovaná tak, aby používala relace. Pokud více klientů provede volání do stejného objektu služby přes vazbu založenou na relaci a režim souběžnosti objektu služby je nastaven na hodnotu Single a kontextový režim instance je nastaven na PerSession, musí všechna volání projít kanálem datagramu a takže se zpracovává pouze jedno volání. Jeden nebo více klientů může vyprší časový limit. Tento problém můžete obejít tak, že nastavíte kontextový režim instance objektu služby na PerCall nebo souběžnost na násobek.  
  
> [!NOTE]
> MaxConcurrentSessions nemá v tomto případě žádný účinek, protože je k dispozici pouze jedna "relace".  
  
### <a name="enabling-streaming"></a>Povolení streamování  
 Streamování můžete povolit následujícími způsoby:  
  
- Odesílat a přijímat požadavky v režimu streamování a přijímat a vracet odpovědi v režimu vyrovnávací paměti ( <xref:System.ServiceModel.TransferMode.StreamedRequest> ).  
  
- Odesílat a přijímat požadavky v režimu vyrovnávací paměti a přijímat a vracet odpovědi v režimu streamování ( <xref:System.ServiceModel.TransferMode.StreamedResponse> ).  
  
- Posílání a přijímání požadavků a odpovědí v režimu streamování v obou směrech. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Streamování můžete zakázat nastavením režimu přenosu na <xref:System.ServiceModel.TransferMode.Buffered> , což je výchozí nastavení u všech vazeb. Následující kód ukazuje, jak nastavit režim přenosu v konfiguraci.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streamed"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
</system.serviceModel>  
```  
  
 Při vytváření instance vazby v kódu musíte nastavit `TransferMode` vlastnost příslušné vazby (nebo element vazby přenosu, pokud vytváříte vlastní vazbu) na jednu z dříve zmíněných hodnot.  
  
 Můžete zapnout streamování pro žádosti a odpovědi nebo pro oba směry nezávisle na kterékoli straně komunikujících stran, aniž by to ovlivnilo funkčnost. Měli byste ale vždycky předpokládat, že velikost přenesených dat je tak významná, že povolení streamování je oprávněné v obou koncových bodech komunikačního propojení. Pro komunikaci mezi platformami, kde jeden z koncových bodů není implementován pomocí služby WCF, bude možnost používat streamování záviset na funkcích streamování platformy. Další výjimečnou výjimkou může být scénář založený na spotřebě paměti, kdy klient nebo služba musí minimalizovat svou pracovní sadu a může poskytovat jenom malé velikosti vyrovnávací paměti.  
  
### <a name="enabling-asynchronous-streaming"></a>Povolení asynchronního streamování  
 Pokud chcete povolit asynchronní streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> do hostitele služby chování koncového bodu a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost na `true` . Na straně odeslání jsme také přidali možnost skutečného asynchronního streamování. To zlepšuje škálovatelnost služby ve scénářích, ve kterých je streamování zpráv do více klientů, jejichž čtení je pravděpodobně způsobeno zahlcením sítě nebo vůbec nečte. V těchto scénářích teď Neblokujte jednotlivá vlákna na službě na klienta. Tím je zajištěno, že služba bude schopna zpracovat mnoho dalších klientů, což zlepšuje škálovatelnost služby.  
  
### <a name="programming-model-for-streamed-transfers"></a>Programovací model pro streamované přenosy  
 Programovací model pro streamování je jednoduchý. Pro příjem dat odeslaných datovým proudem zadejte kontrakt operace, který má jeden <xref:System.IO.Stream> typový vstupní parametr. Pokud chcete vracet data z datového proudu, vraťte <xref:System.IO.Stream> odkaz.  
  
```csharp
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
  
 Operace `Echo` v předchozím příkladu přijme a vrátí datový proud a měl by být proto použit ve vazbě s <xref:System.ServiceModel.TransferMode.Streamed> . Pro operaci `RequestInfo` <xref:System.ServiceModel.TransferMode.StreamedResponse> je nejvhodnější, protože vrací pouze <xref:System.IO.Stream> . Jednosměrná operace je vhodná pro <xref:System.ServiceModel.TransferMode.StreamedRequest> .  
  
 Všimněte si, že přidání druhého parametru do následujících `Echo` nebo `ProvideInfo` operací způsobí, že se model služby vrátí zpět k strategii s vyrovnávací pamětí a použije reprezentace v serializaci datového proudu v době běhu. Pouze operace s jedním vstupním parametrem vstupního datového proudu jsou kompatibilní s koncovým datovým proudem požadavků.  
  
 Toto pravidlo platí podobně jako u kontraktů zpráv. Jak je znázorněno v následujícím kontraktu zprávy, můžete mít v kontraktu zprávy pouze jednoho člena těla, který je datový proud. Pokud chcete spolu s datovým proudem sdělit další informace, musí být tyto informace přenesené do záhlaví zpráv. Tělo zprávy je exkluzivně vyhrazené pro obsah datového proudu.  
  
```csharp
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}
```  
  
 Konec přenosů streamování a zpráva se zavře, když datový proud dosáhne konce souboru (EOF). Při odesílání zprávy (vrácení hodnoty nebo vyvolání operace) můžete předat <xref:System.IO.FileStream> a infrastruktura WCF následně vyžádat všechna data z tohoto datového proudu, dokud datový proud nebude kompletně načten a dosaženo koncem souboru. Chcete-li přenést streamovaná data pro zdroj, který neobsahuje žádnou takovou předem vytvořenou <xref:System.IO.Stream> odvozenou třídu, vytvořte takovou třídu, překrývají tuto třídu přes zdroj datového proudu a použijte ji jako argument nebo návratovou hodnotu.  
  
 Při příjmu zprávy vytvoří WCF datový proud prostřednictvím obsahu zprávy kódovaného ve formátu Base64 (nebo příslušné části MIME při použití MTOM) a datový proud dosáhne hodnoty EOF při čtení obsahu.  
  
 Streamování na úrovni přenosu funguje i u všech dalších typů kontraktů zpráv (seznamů parametrů, argumentů kontraktů dat a explicitního kontraktu zprávy), ale protože serializace a deserializace těchto zapisovaných zpráv vyžaduje ukládání do vyrovnávací paměti serializátorem, není vhodné tyto varianty použít.  
  
### <a name="special-security-considerations-for-large-data"></a>Zvláštní důležité požadavky na zabezpečení pro velké objemy dat  
 Všechny vazby umožňují omezit velikost příchozích zpráv, aby nedocházelo k útokům DOS (Denial-of-Service). <xref:System.ServiceModel.BasicHttpBinding>Například zpřístupňuje vlastnost [System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) , která se váže na velikost příchozí zprávy, a tak také vymezí maximální množství paměti, ke které dojde při zpracování zprávy. Tato jednotka je nastavena v bajtech s výchozí hodnotou 65 536 bajtů.  
  
 Bezpečnostní hrozba, která je specifická pro scénář rozsáhlého streamování dat, provokes odepření služby tím, že způsobí, že data budou ukládána do vyrovnávací paměti, když příjemce očekává streamování. Například technologie WCF vždycky ukládá do vyrovnávací paměti hlavičky SOAP zprávy a útočník tak může vytvořit velkou škodlivou zprávu, která se skládá výhradně z hlaviček k vynucení ukládání dat do vyrovnávací paměti. Pokud je povoleno streamování, `MaxReceivedMessageSize` může být nastaveno na velmi velkou hodnotu, protože přijímač nikdy neočekává, že celá zpráva bude ukládána do vyrovnávací paměti najednou. Pokud je do vyrovnávací paměti služby WCF vynuceně ukládat zprávy, dojde k přetečení paměti.  
  
 Proto omezení maximální velikosti příchozích zpráv není v tomto případě dostatečné. `MaxBufferSize`Vlastnost je vyžadována k omezení paměti, kterou jsou vyrovnávací paměti WCF. Je důležité nastavit tuto hodnotu jako bezpečnou (nebo zachovat výchozí hodnotu) při streamování. Předpokládejme například, že vaše služba musí přijímat soubory o velikosti až 4 GB a ukládat je na místní disk. Předpokládejme také, že vaše paměť je omezená takovým způsobem, že můžete najednou ukládat jenom 64 KB dat. Pak byste nastavili na `MaxReceivedMessageSize` 4 GB a `MaxBufferSize` až 64 KB. V rámci vaší implementace služby je také potřeba zajistit, abyste si přečetli jenom z příchozího datového proudu v blocích 64 – KB a nepřečetli další blok dat, než se předchozí zapsal na disk a zahodil z paměti.  
  
 Je také důležité pochopit, že tato kvóta omezuje pouze ukládání do vyrovnávací paměti prováděné službou WCF a nemůže chránit proti ukládání do vyrovnávací paměti, které provádíte ve vlastní službě nebo implementaci klientů. Další informace o dalších požadavcích na zabezpečení najdete v tématu [požadavky na zabezpečení pro data](security-considerations-for-data.md).  
  
> [!NOTE]
> Rozhodnutí použít buď vyrovnávací paměť, nebo přenos streamování je místní rozhodnutí koncového bodu. V případě přenosů HTTP se režim přenosu nešíří mezi připojeními nebo proxy servery a dalšími zprostředkovateli. Nastavení režimu přenosu se neprojeví v popisu rozhraní služby. Po vygenerování klienta WCF ke službě musíte upravit konfigurační soubor pro služby, které mají být použity s datovým proudem přenosů, a nastavit režim. Pro přenosy TCP a pojmenovaného kanálu je Přenosový režim šířen jako kontrolní výraz zásady.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Povolení streamování](how-to-enable-streaming.md)
