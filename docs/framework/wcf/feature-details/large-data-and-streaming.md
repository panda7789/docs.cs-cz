---
title: Objemná data a vysílání datových proudů
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 91e53f66fb0f2f94a315c318eb0b203d78427bae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184683"
---
# <a name="large-data-and-streaming"></a>Objemná data a vysílání datových proudů

Windows Communication Foundation (WCF) je komunikační infrastruktura založená na jazyce XML. Vzhledem k tomu, že data XML jsou běžně kódována ve standardním textovém formátu definovaném ve [specifikaci XML 1.0](https://www.w3.org/TR/REC-xml/), vývojáři a architekti připojených systémů se obvykle obávají drátové stopy (nebo velikosti) zpráv odeslaných v síti a textové kódování XML představuje zvláštní výzvy pro efektivní přenos binárních dat.  
  
## <a name="basic-considerations"></a>Základní aspekty  
 Chcete-li poskytnout základní informace o následující informace pro WCF, tato část zdůrazňuje některé obecné obavy a důležité informace pro kódování, binární data a streamování, které se obecně vztahují na infrastruktury připojených systémů.  
  
### <a name="encoding-data-text-vs-binary"></a>Kódování dat: Text vs. binární  
 Mezi běžně vyjádřené obavy vývojářů patří dojem, že XML má ve srovnání s binárními formáty značnou režii vzhledem k opakující se povaze počátečních a koncových značek, že kódování číselných hodnot je považováno za výrazně větší protože jsou vyjádřeny v textových hodnotách a že binární data nemohou být efektivně vyjádřena, protože musí být speciálně zakódována pro vložení do textového formátu.  
  
 Zatímco mnohé z těchto a podobných obav jsou platné, skutečný rozdíl mezi xml-text kódované zprávy v prostředí webových služeb XML a binární kódované zprávy ve staršívzdálené procedury volání (RPC) prostředí je často mnohem méně významný než počáteční úvaha by mohla naznačovat.  
  
 Zatímco xml-text kódované zprávy jsou transparentní a "lidské čitelné", binární zprávy jsou často poměrně obskurní ve srovnání a obtížné dekódovat bez nástrojů. Tento rozdíl v čitelnosti vede jeden přehlédnout, že binární zprávy také často nesou vložková metadata v datové části, která přidává režii stejně jako u textových zpráv XML. To platí zejména pro binární formáty, které mají za cíl poskytnout volné párování a dynamické vyvolání schopnosti.  
  
 Binární formáty však běžně nesou takové popisné informace metadat v "záhlaví", které také deklaruje rozložení dat pro následující datové záznamy. Datová část pak následuje po této společné deklaraci bloku metadat s minimální další režii. Naproti tomu XML uzavře každou datovou položku do prvku nebo atributu tak, aby ohraničující metadata byla průběžně zahrnuta pro každý serializovaný objekt datové části. V důsledku toho je velikost jednoho serializovaného objektu datové části podobná při porovnávání textu s binárními reprezentacemi, protože některá popisná metadata musí být vyjádřena pro obě, ale binární formát těží z popisu sdílených metadat s každým dalším popisem metadat s každým dalším objekt datové části, který je přenesen z důvodu nižší celkové režie.  
  
 Přesto pro některé datové typy, jako jsou čísla, může být nevýhoda použití pevné velikosti, binární číselné reprezentace, jako je například 128bitový desetinný typ namísto prostého textu, jako reprezentace prostého textu může být o několik bajtů menší. Textová data mohou mít také výhody velikosti z obvykle flexibilnějších voleb kódování textu XML, zatímco některé binární formáty mohou být ve výchozím nastavení nastaveny na 16bitový nebo dokonce 32bitový unicode, což se nevztahuje na binární formát XML .NET.  
  
 V důsledku toho rozhodování mezi textem nebo binární není tak snadné jako za předpokladu, že binární zprávy jsou vždy menší než xml textové zprávy.  
  
 Jasnou výhodou textových zpráv XML je, že jsou založeny na standardech a nabízejí nejširší výběr možností interoperability a podpory platformy. Další informace naleznete v části Kódování dále v tomto tématu.  
  
### <a name="binary-content"></a>Binární obsah  
 Jednou z oblastí, kde binární kódování jsou lepší než text-založené kódování, pokud jde o výsledné velikosti zprávy jsou velké binární datové položky, jako jsou obrázky, videa, zvukové klipy, nebo jakoukoli jinou formu neprůhledných, binární data, která musí být vyměněny mezi službami a jejich Spotřebitelé. Chcete-li tyto typy dat přizpůsobit textu XML, je běžným přístupem jejich kódování pomocí kódování Base64.  
  
 V řetězci kódu Base64 představuje každý znak 6 bitů původních 8bitových dat, což má za následek poměr režii kódování 4:3 pro Base64, nepočítaje další formátovací znaky (návratový/řádkový kanál) obvykle přidané podle konvence. Zatímco význam rozdílů mezi xml a binární kódování obvykle závisí na scénáři, zvýšení velikosti více než 33 % při přenosu datové části 500 MB je obvykle nepřijatelné.  
  
 Chcete-li se vyhnout tomuto kódování režie, mechanismus optimalizace přenosu zpráv (MTOM) standard umožňuje externalizaci velkých datových prvků, které jsou obsaženy ve zprávě a jejich přenášení se zprávou jako binární data bez zvláštního kódování. U mtom a mtom se zprávy vyměňují podobným způsobem jako e-mailové zprávy protokolu SMTP (SMTP) s přílohami nebo vloženým obsahem (obrázky a další vložený obsah); Zprávy MTOM jsou zabaleny jako vícedílné/související sekvence MIME, přičemž kořenová část je skutečná zpráva SOAP.  
  
 Zpráva MTOM SOAP je upravena z nekódované verze tak, aby značky speciálních prvků, které odkazují na příslušné části MIME, nahradily původní prvky ve zprávě, které obsahovaly binární data. V důsledku toho zpráva SOAP odkazuje na binární obsah odkazem na části MIME odeslané s ním, ale jinak pouze nese textová data XML. Vzhledem k tomu, že tento model je úzce sladěn s dobře zavedeným modelem SMTP, existuje široká podpora nástrojů pro kódování a dekódování zpráv MTOM na mnoha platformách, což z něj činí velmi interoperabilní volbu.  
  
 Přesto, stejně jako u Base64, MTOM také přichází s některé nezbytné režie pro formát MIME, takže výhody použití MTOM jsou vidět pouze v případě, že velikost binární datový prvek přesahuje asi 1 KB. Z důvodu režie zprávy kódované MTOM může být větší než zprávy, které používají base64 kódování pro binární data, pokud binární datové části zůstane pod tuto prahovou hodnotu. Další informace naleznete v části Kódování dále v tomto tématu.  
  
### <a name="large-data-content"></a>Velký obsah dat  
 Drát-stopa stranou, výše uvedené 500-MB užitečné zatížení také představuje velkou místní výzvu pro službu a klienta. Ve výchozím nastavení wcf zpracovává zprávy v *režimu ve vyrovnávací paměti*. To znamená, že celý obsah zprávy je přítomen v paměti před odesláním nebo po přijetí. I když je to dobrá strategie pro většinu scénářů a nezbytné pro zasílání zpráv funkce, jako jsou digitální podpisy a spolehlivé doručení, velké zprávy by mohly vyčerpat prostředky systému.  
  
 Strategie pro řešení velkých datových částí je streamování. Zatímco zprávy, zejména ty vyjádřené v XML, jsou běžně považovány za relativně kompaktní datové balíčky, zpráva může mít velikost více gigabajtů a podobat nepřetržitý datový proud více než datový balíček. Když jsou data přenášena v režimu streamování namísto režimu ve vyrovnávací paměti, odesílatel zpřístupní obsah textu zprávy příjemci ve formě datového proudu a infrastruktura zpráv průběžně předává data od odesílatele k příjemci, jakmile se stane K dispozici.  
  
 Nejběžnější scénář, ve kterém dochází k tak velkým přenosům datového obsahu, jsou přenosy binárních datových objektů, které:  
  
- Nelze snadno rozdělit do sekvence zpráv.  
  
- Musí být doručena včas.  
  
- Nejsou k dispozici v plném rozsahu při zahájení převodu.  
  
 Pro data, která nemá tato omezení, je obvykle lepší odeslat sekvence zpráv v rámci relace než jedna velká zpráva. Další informace naleznete v části "Streamování dat" dále v tomto tématu.  
  
 Při odesílání velkého množství dat budete `maxAllowedContentLength` muset nastavit nastavení služby IIS (další informace `maxReceivedMessageSize` viz [Konfigurace limitů požadavků služby IIS)](https://docs.microsoft.com/iis/configuration/system.webServer/security/requestFiltering/requestLimits/)a nastavení <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>vazby (například [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) nebo ). Vlastnost `maxAllowedContentLength` výchozí 28,6 MB a `maxReceivedMessageSize` vlastnost výchozí 64 KB.  
  
## <a name="encodings"></a>Kódování  
 *Kódování* definuje sadu pravidel o tom, jak prezentovat zprávy na lince. *Kodér* implementuje takové kódování a je zodpovědný, na straně odesílatele, <xref:System.ServiceModel.Channels.Message> pro soustružení v paměti do bajtového proudu nebo bajtové vyrovnávací paměti, které mohou být odeslány v síti. Na straně příjemce kodér změní posloupnost bajtů na zprávu v paměti.  
  
 WCF obsahuje tři kodéry a umožňuje psát a připojit vlastní kodéry, pokud je to nutné.  
  
 Každá standardní vazby obsahuje předkonfigurovaný kodér, přičemž vazby s předponou Net* používají <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> binární kodér (zahrnutím třídy), zatímco třídy <xref:System.ServiceModel.BasicHttpBinding> a <xref:System.ServiceModel.WSHttpBinding> používají kodér textových zpráv (pomocí <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třídy) ve výchozím nastavení.  
  
|Prvek vazby kodéru|Popis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Kodér textových zpráv je výchozí kodér pro všechny vazby založené na protokolu HTTP a vhodnou volbou pro všechny vlastní vazby, kde interoperabilita je nejvyšší obavy. Tento kodér čte a zapisuje standardní soap 1.1/SOAP 1.2 textové zprávy bez zvláštního zpracování pro binární data. Pokud <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> je vlastnost zprávy nastavena na <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>, obálka soap obálky je vynechána z výstupu a pouze obsah textu zprávy je serializován.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Kodér zpráv MTOM je textový kodér, který implementuje speciální zpracování binárních dat a ve výchozím nastavení se nepoužívá v žádné ze standardních vazeb, protože se jedná výhradně o nástroj pro optimalizaci případ od případu. Pokud zpráva obsahuje binární data, která překračuje prahovou hodnotu, kde kódování MTOM poskytuje výhodu, data jsou externalizována do části MIME následující obálky zprávy. Další informace o povolení mtom dále v této části naleznete v části Povolení mtom.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Binární kodér zpráv je výchozí kodér pro vazby Net* a vhodnou volbou vždy, když jsou obě komunikující strany založeny na WCF. Kodér binárních zpráv používá binární formát XML .NET, binární reprezentaci specifickou pro microsoftpro informační sady XML (Infosets), která obvykle poskytuje menší nároky než ekvivalentní reprezentace XML 1.0 a kóduje binární data jako bajt Proudu.|  
  
 Kódování textových zpráv je obvykle nejlepší volbou pro všechny komunikační cesty, která vyžaduje interoperabilitu, zatímco binární kódování zpráv je nejlepší volbou pro všechny ostatní komunikační cesty. Binární kódování zpráv obvykle poskytuje menší velikosti zpráv ve srovnání s textem pro jednu zprávu a postupně ještě menší velikosti zpráv po dobu trvání relace komunikace. Na rozdíl od kódování textu binární kódování nemusí používat speciální zpracování pro binární data, jako je například použití Base64, ale představuje bajty jako bajty.  
  
 Pokud vaše řešení nevyžaduje interoperabilitu, ale stále chcete použít <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> přenos HTTP, můžete <xref:System.ServiceModel.Channels.HttpTransportBindingElement> vytvořit do vlastní vazby, která používá třídu pro přenos. Pokud počet klientů ve vaší službě vyžadují interoperabilitu, je doporučeno vystavit paralelní koncové body, které má každý z nich příslušné možnosti přenosu a kódování pro příslušné klienty povolena.  
  
### <a name="enabling-mtom"></a>Povolení mtom  
 Pokud je požadavek na interoperabilitu a musí být odeslána velká binární data, je <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSHttpBinding> kódování zpráv MTOM `MessageEncoding` alternativní <xref:System.ServiceModel.WSMessageEncoding.Mtom> strategií kódování, <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kterou <xref:System.ServiceModel.Channels.CustomBinding>můžete povolit na standardu nebo vazbách nastavením příslušné vlastnosti do nebo vytvořením do . Následující ukázkový kód extrahovaný z ukázky [kódování MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) ukazuje, jak povolit mtom v konfiguraci.  
  
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
  
 Jak již bylo zmíněno dříve, rozhodnutí o použití kódování MTOM závisí na objemu dat, který odesíláte. Také protože MTOM je povolena na úrovni vazby, povolení MTOM ovlivňuje všechny operace na daný koncový bod.  
  
 Vzhledem k tomu, že kodér MTOM vždy vysílá zprávu MIME/více částí kódovky kódované mtomem bez ohledu na to, zda jsou binární data exterizována, měli byste obecně povolit mtom pro koncové body, které si vyměňují zprávy s více než 1 kb binárních dat. Také smlouvy o poskytování služeb určené pro použití s koncovými body s podporou MTOM by měly být pokud možno omezeny na určení těchto operací přenosu dat. Související funkce ovládacího prvku by měla být umístěna v samostatné smlouvě. Toto pravidlo "pouze pro MTOM" se vztahuje pouze na zprávy odeslané prostřednictvím koncového bodu s podporou MTOM; Kodér MTOM může také dekódovat a analyzovat příchozí zprávy bez MTOM.  
  
 Použití kodéru MTOM odpovídá všem ostatním funkcím WCF. Všimněte si, že nemusí být možné dodržovat toto pravidlo ve všech případech, například při podpoře relace je požadováno.  
  
### <a name="programming-model"></a>Programovací model  
 Bez ohledu na to, které ze tří vestavěných kodéry, které používáte ve vaší aplikaci, programovací prostředí je totožné s ohledem na přenos binárních dat. Rozdíl je v tom, jak WCF zpracovává data na základě jejich datových typů.  
  
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
  
 Při použití MTOM je předchozí kontrakt dat serializován podle následujících pravidel:  
  
- Pokud `binaryBuffer` není `null` a jednotlivě obsahuje dostatek dat k ospravedlnění režie externalizace MTOM (hlavičky MIME a tak dále) ve srovnání s kódováním Base64, data jsou externalizována a přenášena se zprávou jako binární část MIME. Pokud prahová hodnota není překročena, data jsou kódována jako Base64.  
  
- Řetězec (a všechny ostatní typy, které nejsou binární) je vždy reprezentován jako řetězec uvnitř textu zprávy, bez ohledu na velikost.  
  
 Vliv na kódování MTOM je stejný, zda používáte explicitdata smlouvy, jak je znázorněno v předchozím příkladu, použijte seznam parametrů v operaci, mají vnořené datové smlouvy nebo přenos objektu smlouvy dat uvnitř kolekce. Bajtová pole jsou vždy kandidáty pro optimalizaci a jsou optimalizovány, pokud jsou splněny prahové hodnoty optimalizace.  
  
> [!NOTE]
> Neměli byste <xref:System.IO.Stream?displayProperty=nameWithType> používat odvozené typy uvnitř kontraktů dat. Data datového proudu by měla být sdělována pomocí modelu streamování, který je vysvětlen v následující části "Streamovaná data".  
  
## <a name="streaming-data"></a>Streamování dat  
 Pokud máte velké množství dat k přenosu, režim přenosu datových proudů v WCF je proveditelnou alternativou k výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti v plném rozsahu.  
  
 Jak již bylo zmíněno dříve, povolit streamování pouze pro velké zprávy (s textem nebo binární obsah), pokud data nelze segmentovat, pokud zpráva musí být doručena včas, nebo pokud data ještě není plně k dispozici při zahájení přenosu.  
  
### <a name="restrictions"></a>Omezení  
 Nelze použít významný počet funkcí WCF při streamování je povolena:  
  
- Digitální podpisy pro tělo zprávy nelze provést, protože vyžadují výpočet algoritmu hash přes celý obsah zprávy. Pomocí datového proudu není obsah plně k dispozici, pokud jsou vytvořena a odeslána záhlaví zprávy, a proto nelze vypočítat digitální podpis.  
  
- Šifrování závisí na digitálních podpisech a ověřte, zda byla data správně rekonstruována.  
  
- Spolehlivé relace musí ukládat zprávy do vyrovnávací paměti pro opětovné doručení v klientovi, pokud dojde ke ztrátě zprávy při přenosu a musí obsahovat zprávy ve službě před jejich předáním do implementace služby, aby se zachovalo pořadí zpráv v případě, že jsou přijaty zprávy mimo pořadí.  
  
 Z důvodu těchto funkčních omezení můžete pro streamování používat pouze možnosti zabezpečení na úrovni přenosu a nelze zapnout spolehlivé relace. Streamování je k dispozici pouze s následujícími vazbami definovanými systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 Vzhledem k tomu, že základní přenosy <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> mají vlastní spolehlivé doručení a podporu relace založené na připojení, na rozdíl od protokolu HTTP, tyto dvě vazby jsou ovlivněny pouze minimálně těmito omezeními, v praxi.  
  
 Streamování není k dispozici s přenosem služby Řízení front zpráv (MSMQ), a proto jej nelze použít s třídou <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nebo. Přenos služby Řízení front zpráv podporuje pouze přenosy dat ve vyrovnávací paměti s omezenou velikostí zprávy, zatímco všechny ostatní přenosy nemají žádné praktické omezení velikosti zprávy pro drtivou většinu scénářů.  
  
 Streamování také není k dispozici při použití přenosu kanálu <xref:System.ServiceModel.NetPeerTcpBinding>Peer, takže není k dispozici s .  
  
#### <a name="streaming-and-sessions"></a>Streamování a relace  
 Při streamování volání pomocí vazby založené na relaci může dojít k neočekávanému chování. Všechna volání streamování jsou prováděny prostřednictvím jednoho kanálu (kanál datagram), který nepodporuje relace i v případě, že se používá vazba je nakonfigurován pro použití relací. Pokud více klientů provádět volání streamování stejného objektu služby přes vazbu založenou na relaci a režim souběžnosti objektu služby je nastavena na jednu a jeho instance kontextový režim je nastavena na PerSession, všechna volání musí projít kanálem datagram a tak pouze jeden volání zpracováno současně. Jeden nebo více klientů pak může časový mzda. Tento problém můžete vyřešit nastavením režimu kontextu instance objektu služby na PerCall nebo Souběžnost na Více.  
  
> [!NOTE]
> MaxConcurrentSessions nemá žádný vliv v tomto případě, protože je k dispozici pouze jedna "relace".  
  
### <a name="enabling-streaming"></a>Povolení streamování  
 Streamování můžete povolit následujícími způsoby:  
  
- Odesílat a přijímat požadavky v režimu streamování a přijímat<xref:System.ServiceModel.TransferMode.StreamedRequest>a vracet odpovědi v režimu ve vyrovnávací paměti ( ).  
  
- Odesílat a přijímat požadavky v režimu ve vyrovnávací paměti a<xref:System.ServiceModel.TransferMode.StreamedResponse>přijímat a vracet odpovědi v režimu streamování ( ).  
  
- Odesílejte a přijímejte požadavky a odpovědi v režimu streamování v obou směrech. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Streamování můžete zakázat nastavením <xref:System.ServiceModel.TransferMode.Buffered>režimu přenosu na , což je výchozí nastavení u všech vazeb. Následující kód ukazuje, jak nastavit režim přenosu v konfiguraci.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streamed"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Při vytváření instancí vazby v kódu, `TransferMode` je nutné nastavit příslušnou vlastnost vazby (nebo prvek vazby přenosu, pokud komponujete vlastní vazbu) na jednu z výše uvedených hodnot.  
  
 Můžete zapnout streamování pro požadavky a odpovědi nebo pro oba směry nezávisle na obou stranách komunikujících stran bez ovlivnění funkčnosti. Měli byste však vždy předpokládat, že velikost přenesených dat je tak významná, že povolení streamování je odůvodněno na obou koncových bodech komunikačního propojení. Pro komunikaci napříč platformami, kde jeden z koncových bodů není implementována s WCF, schopnost používat streamování závisí na možnosti streamování platformy. Další vzácnou výjimkou může být scénář řízený spotřebou paměti, kde klient nebo služba musí minimalizovat svou pracovní sadu a může si dovolit pouze malé velikosti vyrovnávací paměti.  
  
### <a name="enabling-asynchronous-streaming"></a>Povolení asynchronního streamování  
 Chcete-li povolit asynchronní <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> streamování, přidejte chování koncového bodu do hostitele služby a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost na `true`. Přidali jsme také schopnost skutečného asynchronního streamování na straně odeslání. To zlepšuje škálovatelnost služby ve scénářích, kde je streamování zpráv do více klientů, z nichž některé jsou pomalé čtení možná z důvodu přetížení sítě nebo nejsou čtení vůbec. V těchto scénářích nyní neblokujeme jednotlivá vlákna ve službě na klienta. Tím je zajištěno, že služba je schopna zpracovat mnohem více klientů, čímž se zlepší škálovatelnost služby.  
  
### <a name="programming-model-for-streamed-transfers"></a>Programovací model pro streamované přenosy  
 Programovací model pro streamování je jednoduchý. Pro příjem dat datových proudů zadejte <xref:System.IO.Stream> smlouvu operace, která má jeden vstupní parametr zadali. Pro vrácení dat datových <xref:System.IO.Stream> proudů vrátíte odkaz.  
  
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
  
 Operace `Echo` v předchozím příkladu přijímá a vrací datový proud a proto <xref:System.ServiceModel.TransferMode.Streamed>by měl být použit na vazbu s . Pro operaci `RequestInfo` <xref:System.ServiceModel.TransferMode.StreamedResponse> , je nejvhodnější, protože <xref:System.IO.Stream>vrátí pouze . Jednosměrná operace je nejvhodnější <xref:System.ServiceModel.TransferMode.StreamedRequest>pro .  
  
 Všimněte si, že přidání `Echo` `ProvideInfo` druhého parametru do následující nebo operace způsobí, že model služby vrátit zpět do strategie ve vyrovnávací paměti a použít run-time serializace reprezentace datového proudu. Pouze operace s jedním parametrem vstupního datového proudu jsou kompatibilní s end-to-end streamování požadavků.  
  
 Toto pravidlo platí podobně pro zprávy smlouvy. Jak je znázorněno v následující zprávě smlouvy, můžete mít pouze jeden člen těla ve smlouvě zprávy, která je datový proud. Pokud chcete komunikovat další informace s datovým proudem, tyto informace musí být nesena v záhlaví zprávy. Text zprávy je vyhrazenvýhradně pro obsah datového proudu.  
  
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
  
 Streamované přenosy končí a zpráva se zavře, když datový proud dosáhne konce souboru (EOF). Při odesílání zprávy (vrácení hodnoty nebo vyvolání operace), můžete <xref:System.IO.FileStream> předat a WCF infrastruktury následně načte všechna data z tohoto datového proudu, dokud datový proud byl zcela přečten a dosáhl EOF. Chcete-li přenést streamovaná data pro zdroj, že žádná taková předem vytvořená <xref:System.IO.Stream> odvozená třída neexistuje, vytvořte takovou třídu, překryjte tuto třídu nad zdrojem datového proudu a použijte ji jako argument nebo vrácenou hodnotu.  
  
 Při příjmu zprávy WCF vytvoří datový proud přes base64 kódované obsahu textu zprávy (nebo příslušné části MIME, pokud používáte MTOM) a datový proud dosáhne EOF po čtení obsahu.  
  
 Streamování na úrovni přenosu funguje také s jakýmkoli jiným typem smlouvy zprávy (seznamy parametrů, argumenty kontraktů dat a kontrakt explicitní zprávy), ale protože serializace a deserializace těchto zadaných zpráv vyžaduje ukládání do vyrovnávací paměti serializátorem , použití těchto smluvních variant není vhodné.  
  
### <a name="special-security-considerations-for-large-data"></a>Zvláštní důležité informace o zabezpečení pro velká data  
 Všechny vazby umožňují omezit velikost příchozích zpráv, aby se zabránilo útokům odmítnutí služby. Například <xref:System.ServiceModel.BasicHttpBinding>zpřístupňuje [Vlastnost System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize,](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) která ohraničuje velikost příchozí zprávy a proto také ohraničuje maximální množství paměti, ke které se při zpracování zprávy přistupuje. Tato jednotka je nastavena v bajtů s výchozí hodnotou 65 536 bajtů.  
  
 Ohrožení zabezpečení, které je specifické pro scénář přenosu velkých dat vyvolává odmítnutí služby tím, že způsobí, že data do vyrovnávací paměti, když příjemce očekává, že bude datový proud. Například WCF vždy vyrovnávací paměti soap záhlaví zprávy, a tak útočník může vytvořit velké škodlivé zprávy, která se skládá výhradně z záhlaví vynutit data do vyrovnávací paměti. Pokud je povoleno `MaxReceivedMessageSize` streamování, může být nastavena na extrémně velkou hodnotu, protože příjemce nikdy neočekává, že celá zpráva bude uložena do vyrovnávací paměti najednou. Pokud WCF je vynuceno do vyrovnávací paměti zprávy, dojde k přetečení paměti.  
  
 Proto omezení maximální velikost příchozí zprávy není v tomto případě dost. Vlastnost `MaxBufferSize` je nutné omezit paměť, která WCF vyrovnávací paměti. Je důležité nastavit na bezpečnou hodnotu (nebo ji zachovat na výchozí hodnotu) při streamování. Předpokládejme například, že vaše služba musí přijímat soubory o velikosti až 4 GB a ukládat je na místní disk. Předpokládejme také, že vaše paměť je omezena takovým způsobem, že můžete pouze vyrovnávací paměti 64 KB dat najednou. Pak byste nastavili `MaxReceivedMessageSize` na `MaxBufferSize` 4 GB a 64 KB. Také v implementaci služby je nutné zajistit, že číst pouze z příchozího datového proudu v 64 kB bloky a nečíst další blok před předchozí byl zapsán na disk a zahozeny z paměti.  
  
 Je také důležité si uvědomit, že tato kvóta omezuje pouze ukládání do vyrovnávací paměti provádí WCF a nemůže chránit před ukládání do vyrovnávací paměti, které provádíte ve vlastní službě nebo implementace klienta. Další informace o dalších aspektech zabezpečení naleznete [v tématu Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
> Rozhodnutí použít přenosy ve vyrovnávací paměti nebo datového proudu je místní rozhodnutí koncového bodu. U přenosů HTTP se režim přenosu nešíří přes připojení nebo na proxy servery a další zprostředkovatele. Nastavení režimu přenosu se neprojeví v popisu rozhraní služby. Po generování wcf klienta ke službě, je nutné upravit konfigurační soubor pro služby určené pro použití s datových proudových přenosů nastavit režim. Pro přenosy tcp a pojmenované kanály je režim přenosu rozšířen jako kontrolní výraz zásady.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
