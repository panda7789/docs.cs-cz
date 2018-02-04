---
title: "Objemná data a vysílání datových proudů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9551fcf4f302be899dcee8737b3bcfad15f1210
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="large-data-and-streaming"></a>Objemná data a vysílání datových proudů
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je založený na jazyce XML komunikaci infrastruktury. Protože XML data je běžně zakódován ve formátu standardního textu definované v [XML 1.0 – specifikace](http://go.microsoft.com/fwlink/?LinkId=94838), připojené systémy vývojáři a architektům jsou obvykle zajímá přenosová nároků (nebo velikost) zprávy odeslané přes síť a založený na textu kódování XML představuje speciální výzvy pro efektivní přenos binární data.  
  
## <a name="basic-considerations"></a>Základní informace  
 Poskytnout základní informace o následující informace pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], v této části jsou zdůrazněné některé obecné aspekty a aspekty kódování binárních dat, a který obecně streamování týkají připojených systémů infrastruktury.  
  
### <a name="encoding-data-text-vs-binary"></a>Kódování dat: Text vs. binární  
 Běžně vyjádřené vývojáře obavy zahrnují dojem, že XML má významné režijní náklady na ve srovnání s binární formáty vzhledem k povaze opakovaných značky počáteční a koncové značky, že kódování číselných hodnot, považuje se za výrazně větší protože jsou vyjádřeny v textové hodnoty a binární data není možné vyjádřit efektivní, protože musí být speciálně kódováním pro vložení do formátu textu.  
  
 Zatímco řada z nich a podobných týká platné, skutečný rozdíl mezi kódování textu XML zprávy v prostředí XML webové služby a binární kódování zprávy ve starší verzi vzdálené volání procedur (RPC) prostředí je často mnohem méně důležité než může naznačovat počáteční pozornost.  
  
 Při textu XML kódovaného zprávy jsou transparentní a "číselné vyjádření", binární zprávy jsou často poměrně skrytého porovnání a obtížně se dekódovat bez nástroje. Tento rozdíl v čitelnost vede jeden přehlédnout, že binární zprávy také často provádění metadata vložené v datové části, která přidá režie stejně jako v XML textové zprávy. To platí konkrétně pro formáty pro binární zaměřte se na poskytují volné párování a dynamické volání funkce.  
  
 Však binární formáty běžně přenosu těchto informací o popisná metadata v "záhlaví," což také deklaruje rozložení dat pro následující záznamy dat. Datové části pak odpovídá této společné deklarace blok metadat s minimální režií na další. Naproti tomu XML uzavře každá položka dat v elementu nebo atributu tak, aby nadřazených metadata opakovaně zahrnuté pro každý objekt serializovanou datovou část. V důsledku toho velikost jedné datové části serializovaného objektu je při porovnávání text, který se binární reprezentace jako některé popisná metadata musí být vyjádřena v obou případech ale výhody binární formát z popis sdílené metadat s každou další datová část objekt, který se přenáší z důvodu nižší celkové režijní náklady.  
  
 Přesto pro konkrétní datové typy, jako je například čísla, může být nevýhodou použití pevné velikosti, binární reprezentace číselné, jako je například 128-bit typu decimal místo prostého textu, může mít být a reprezentace jako prostý text několik bajtů menší. Textová data také může mít velikost výhody z obvykle flexibilnější textu XML kódování volby, zatímco některé binární formáty může výchozí 16bitové nebo i 32-bit Unicode, které se nevztahuje na binární formát XML .NET.  
  
 V důsledku toho rozhodování mezi textu nebo binárních není poměrně stejně snadná jako za předpokladu, že binární zprávy jsou vždy menší než XML textové zprávy.  
  
 Vymazat výhodou XML textové zprávy je, že jsou na základě standardů a nabízejí nejširší výběr možností kombinací a podporu platforem. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v části "Kódování" dál v tomto tématu.  
  
### <a name="binary-content"></a>Binární obsah  
 Jeden oblasti, kde binárního kódování hodnotu větší než založený na textu kódování z hlediska výsledná velikost zprávy jsou velké binární data položkám, jako jsou obrázky, videa, zvukových klipů nebo jakoukoli jinou formu neprůhledné, binární data, která musí být vyměňují mezi službami a jejich Příjemci knihovny. Aby se tyto typy dat do textu XML, je běžný postup zakódovat je pomocí kódování Base64.  
  
 V řetězci kódováním Base64 představuje každý znak 6bity původní data 8bitové, což vede k 4:3 kódování režii poměr pro Base64, není počítání velmi formátování znaků (znaků CR return a line feed), které jsou běžně přidány na základě konvence. Při význam rozdíly mezi XML a binární kódování obvykle závisí na scénáři, nárůst velikosti větší než 33 % při přenosu datové části 500 MB obvykle není přijatelný.  
  
 Aby se zabránilo toto kódování režie, mechanismus pro optimalizaci přenosu zpráv (MTOM) umožňuje standard externího velké datové prvky, které jsou obsaženy ve zprávě a jejich provedení se zprávou jako binární data bez jakékoli speciální kódování. S MTOM zprávy se vyměňují podobným způsobem k přenosu protokolu SMTP (Simple Mail) e-mailové zprávy s přílohy nebo vložený obsah (obrázky a další vložený obsah); Jako posloupnosti MIME multipart/related spojených s částí kořenové se skutečné zprávu protokolu SOAP zprávy MTOM.  
  
 Zprávu MTOM SOAP se liší od jeho zrušení kódovaného verze tak, aby speciální element značky, které odkazují na části odpovídající standardu MIME má nahradit původní elementů v zprávu, která obsahovala binární data. V důsledku toho zprávu SOAP odkazuje na binární obsah tak, že odkazuje na části MIME odeslané s ním, ale jinak právě představuje textová data XML. Protože tento model je úzce zarovnán s modelem zavedené SMTP, je široká podpora ke kódování a dekódování zprávy MTOM na spoustě platforem, proto je velmi interoperabilní volba nástrojů.  
  
 Stále stejně jako u Base64, MTOM také obsahuje některé potřebné režijní náklady na formát MIME tak, aby výhody používání MTOM se zobrazují pouze, když velikost binární datový prvek překračuje asi 1 KB. Z důvodu režijní náklady může být vyšší než zprávy, které používají kódování Base64 pro binární data, pokud zůstane binární datové části v rámci této prahové hodnoty kódování MTOM zprávy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v části "Kódování" dál v tomto tématu.  
  
### <a name="large-data-content"></a>Obsah velkých objemů dat  
 Přenosová nároky z produkce, datové části výše uvedených 500 MB také představuje skvělý místní výzvu v pro tuto službu a klienta. Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracovává zprávy v *režim s vyrovnávací pamětí*. To znamená, že celý obsah zprávy, které je obsažená v paměti před odesláním nebo po přijetí. Přesto, že je strategii je dobré pro většinu scénářů a potřeby zasílání zpráv funkcí, jako jsou digitální podpisy i spolehlivá doručení, může vyčerpat velké zprávy systémové prostředky.  
  
 Strategie řešení velké datové části je streamování. Při zprávy především těch, které jsou vyjádřené v XML, jsou běžně představit jako relativně compact data balíčky, zprávy mohou být několika gigabajtů velikost a vypadat průběžné datový proud více než datový balíček. Když jsou data přenášena v režimu datového místo režim s vyrovnávací pamětí, odesílatel zpřístupní obsah textu zprávy k příjemce ve formě datového proudu a infrastruktury zpráva nepřetržitě předává data od odesílatele k příjemce Jakmile je k k dispozici.  
  
 Nejběžnější scénáře, ve kterém jsou takové obsah velkého množství dat, který se přenosy přenosy binárních dat objekty, které:  
  
-   Nemůže být rozdělen snadno do sekvenci zpráv.  
  
-   Musí být doručována v časovém limitu.  
  
-   Nejsou k dispozici v plné výši při zahájení přenosu.  
  
 Pro data, která nemá těchto omezení je obvykle lepší odeslat pořadí zpráv v rámci oboru relace než jedna velká zpráva. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]později v tomto tématu v části "Streamování Data".  
  
 Při odesílání velkých objemů dat je potřeba nastavit `maxAllowedContentLength` nastavení služby IIS (Další informace najdete v části [konfigurace omezení počtu požadavků služby IIS](http://go.microsoft.com/fwlink/?LinkId=253165)) a `maxReceivedMessageSize` vazby nastavení (například [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) nebo <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` Výchozí hodnoty vlastností pro 28.6 M a `maxReceivedMessageSize` výchozí hodnoty vlastností na 64 KB.  
  
## <a name="encodings"></a>Kódování  
 *Kódování* definuje sadu pravidel o tom, jak zprávy k dispozici v drátové síti. *Kodér* implementuje takové kódování a na straně odesílatele za měnící <xref:System.ServiceModel.Channels.Message> zprávy v paměti do datového proudu bajtů nebo vyrovnávací paměti bajtů, které mohou být odeslány prostřednictvím sítě. Na straně příjemce zapne kodér pořadí bajtů do zprávy v paměti.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje tři kodéry a umožňuje napsat a zařadit vlastní kodéry v případě potřeby.  
  
 Každé standardní vazby zahrnuje předkonfigurovaná kodér, při němž vazby s předponou Net * používat binární kodér (zahrnutím <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> třída) při <xref:System.ServiceModel.BasicHttpBinding> a <xref:System.ServiceModel.WSHttpBinding> třídy použít kodér textu zprávy (pomocí Řešitele z <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> třída) ve výchozím nastavení.  
  
|Kodér prvku vazby|Popis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Kodér textu zprávy je kodéru pro všechny vazby založené na protokolu HTTP a příslušnou volbu pro všechny vlastní vazby, kde interoperability je nejvyšší problém. Tato kodér čte a zapisuje standardní SOAP 1.1 nebo SOAP 1.2 textové zprávy s žádné speciální zpracování pro binární data. Pokud <xref:System.ServiceModel.Channels.MessageVersion> zprávy je nastaven na `None`, je tento parametr vynechán obálku obálky protokolu SOAP z výstupu a je serializovat pouze obsah textu zprávy.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Kodér zpráv MTOM je kodér textu, který implementuje zvláštní zpracování pro binární data a není použít ve výchozím nastavení v některém z standardní vazby, protože je výhradně nástroj Optimalizace případ od případu. Pokud zpráva obsahuje binární data, která překračuje prahovou hodnotu kde kódování MTOM vypočítá výhody, se do části standardu MIME následující zpráva obálky externalized data. V tématu Povolení MTOM dál v této části.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Zprávy v binární modulu encoder je kodéru pro vazby Net * a příslušné výběr pokaždé, když oba komunikující strany jsou založené na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Kodér zprávy v binární používá rozhraní .NET binárního formátu XML, binární reprezentace specifické pro společnost Microsoft pro sady informace XML (Infosets), který obecně vypočítá menší nároky než ekvivalentní reprezentaci XML 1.0 a zakóduje binární data v bajtové podobě datový proud.|  
  
 Kódování textu zprávy je většinou nejlepší volbou pro všechny komunikace cestu, která vyžaduje vzájemná funkční spolupráce, při kódování zprávy v binární je nejlepší volbou pro jiné komunikační cesty. Kódování zprávy v binární obvykle vypočítá menší zpráva, že velikosti ve srovnání s text pro jedné zprávy a zpráva postupně i menší velikosti za celou dobu relace komunikace. Na rozdíl od kódování textu binárního kódování nemá použít zvláštní zpracování pro binární data, například pomocí Base64, ale představuje bajtů bajtů.  
  
 Pokud vaše řešení nevyžaduje vzájemná funkční spolupráce, ale nadále chcete používat přenos HTTP, můžete vytvořit <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do vlastní vazby, který používá <xref:System.ServiceModel.Channels.HttpTransportBindingElement> třídy pro přenos. Pokud počet klientů na služby vyžadují vzájemná funkční spolupráce, se doporučuje vystavit paralelní koncových bodů, že každý má odpovídající přenosu a kódování volby pro příslušné klienty povolena.  
  
### <a name="enabling-mtom"></a>Povolení MTOM  
 Při zajištění lepší interoperability je požadavek a velké binární data, musí se poslat pak kódování MTOM zprávy je alternativní kódování strategie, kterou můžete povolit na standardní <xref:System.ServiceModel.BasicHttpBinding> nebo <xref:System.ServiceModel.WSHttpBinding> vazby nastavením příslušné `MessageEncoding` Vlastnost <xref:System.ServiceModel.WSMessageEncoding.Mtom> nebo skládání <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do <xref:System.ServiceModel.Channels.CustomBinding>. Následující příklad kódu z extrahovat [kódování MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) příklad ukazuje postup povolení MTOM v konfiguraci.  
  
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
  
 Jak už bylo zmíněno dříve, rozhodnutí o použití kódování MTOM závisí na datový svazek odesílání. Také protože MTOM je povolena na úrovni vazby, povolení MTOM ovlivní všechny operace v daném koncový bod.  
  
 Vzhledem k tomu, že kodér MTOM vydá kódování MTOM MIME nebo více-částečný zprávu bez ohledu na to, jestli bude mít binární data se externalized, měli byste obecně pouze povolit MTOM pro koncové body, které vyměňovat zprávy s více než 1 KB binární data. Také kontraktů služby určený k použití u koncových bodů s povoleným MTOM by, pokud je to možné, omezen zadání takové operace přenosu dat. Funkce související ovládací prvek by měl být umístěn na samostatné kontrakt. Toto pravidlo "Jen MTOM" platí pouze pro zprávy odeslané přes koncový bod MTOM povoleno; kodér MTOM může dekódovat a analyzovat příchozí zprávy bez MTOM také.  
  
 Pomocí kodéru MTOM splňuje normu jiných [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce. Všimněte si, že nemusí být možné toto pravidlo ve všech případech, například když je potřebná podpora relace.  
  
### <a name="programming-model"></a>Programovací model  
 Bez ohledu na to, které tři předdefinované kodéry, které používáte ve vaší aplikaci se shoduje s ohledem na přenos binární data programovací prostředí. Rozdíl je v tom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracovává data v závislosti na jejich datové typy.  
  
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
  
 Pokud používáte MTOM, předchozí kontrakt dat je serializováno podle následujících pravidel:  
  
-   Pokud `binaryBuffer` není `null` a jednotlivě obsahuje dostatek dat k odůvodnění, režii externalization MTOM (MIME hlavičky atd.) v porovnání s Base64 kódování, data se externalized a provádí se zprávou jako binární části standardu MIME. Pokud není překročí prahovou hodnotu, data je kódovaný jako Base64.  
  
-   Řetězec (a všechny ostatní typy, které nejsou binární) je vždy reprezentována jako řetězec v textu zprávy, bez ohledu na velikost.  
  
 Vliv na kódování MTOM je stejný zda použijete explicitní data kontrakt, jak je uvedeno v předchozím příkladu použít seznam parametrů v operaci, mají vnořené datové kontrakty nebo přenos objekt kontraktu dat v kolekci. Bajtová pole jsou vždy kandidáty pro optimalizaci a jsou optimalizované, pokud byly splněny optimalizace prahové hodnoty.  
  
> [!NOTE]
>  Neměli byste používat <xref:System.IO.Stream?displayProperty=nameWithType> odvozené typy v kontraktech dat. Datový proud dat by mělo být oznámeno pomocí streamování modelu, popsané v následující části "Streamování Data".  
  
## <a name="streaming-data"></a>Streamování dat  
 Pokud máte velké množství dat pro přenos datových proudů režim přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vhodný alternativu, která umožňuje výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti jako celek.  
  
 Jak už bylo zmíněno dříve, umožňoval vysílání datového proudu pouze pro velké zprávy (s obsahem textu nebo binárních), pokud nemůže být segmentovány data, pokud zpráva musí doručit včas, nebo pokud data ještě není plně k dispozici při zahájení přenosu.  
  
### <a name="restrictions"></a>Omezení  
 Nemůžete použít velký počet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, pokud je povoleno vysílání datového proudu:  
  
-   Digitální podpisy pro tělo zprávy nelze provést, protože vyžadují computing hodnotu hash přes obsah celé zprávy. Při streamování obsahu není plně k dispozici při záhlaví zprávy jsou vytvořená a odeslat, a proto nelze vypočítat digitální podpis.  
  
-   Šifrování závisí na digitálních podpisů k ověření, že dat má byla znovu vytvořena správně.  
  
-   Spolehlivé relace musí buffer odeslaných zpráv na straně klienta pro opakované dodání, pokud zpráva získá ztrátě při přenosu a musí obsahovat zprávy na službu před blokováním je pro implementaci služby pro zachování pořadí zprávy v případě, že jsou přijaty zprávy. mimo pořadí.  
  
 Z důvodu těchto funkční omezení můžete použít pouze zabezpečení transportní vrstvy, které možnosti pro streamování a nelze zapnout spolehlivé relace. Vysílání datového proudu je k dispozici pouze u vazeb následující definovaná systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Protože základní přenosy z <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> vyplývajících spolehlivé doručení a založeného na připojení relace podporovat, na rozdíl od protokolu HTTP, jsou tyto dvě vazby jenom minimálně vliv těchto omezení, v praxi.  
  
 Streamování není k dispozici přenos řízení front zpráv (MSMQ) a proto jej nelze použít s <xref:System.ServiceModel.NetMsmqBinding> nebo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy. Přenos služby Řízení front zpráv podporuje pouze přenosů dat ve vyrovnávací paměti s velikostí omezené zprávy, zatímco všechny ostatní přenosy nemají žádné omezení velikosti praktické zpráva pro velká většina scénářů.  
  
 Streamování není k dispozici při použití přenos rovnocenného kanálu, takže není k dispozici <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Streaming a relace  
 Při volání streamování s vazbou na bázi relací, může dojít k neočekávanému chování. Všechna volání streamování jsou provedeny prostřednictvím jednoho kanálu (kanál datagram), který nepodporuje relace, i v případě, že je vazba používá nakonfigurovaný na použití relací. Pokud více klientů volání streamování ke stejnému objektu služby přes vazbu na bázi relací a objektu služby souběžný režim je nastaven na jediný a jeho instance kontextu režim je nastaven na PerSession, všechna volání musí procházet přes kanál datagram a proto pouze jeden volání je zpracovat najednou. Jeden nebo více klientů může pak vypršení časového limitu. Tento problém můžete vyřešit buď nastavení režimu kontextu Instance objektu služby PerCall nebo souběžnosti do několika.  
  
> [!NOTE]
>  MaxConcurrentSessions v takovém případě se neprojeví, protože není k dispozici pouze jeden "relace".  
  
### <a name="enabling-streaming"></a>Povolení streamování  
 Můžete povolit datové proudy následujícími způsoby:  
  
-   Odesílání a přijímání požadavků v režimu datového a přijmout a vrátí odpovědi v režim s vyrovnávací pamětí (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Odesílání a přijímání požadavků v režim s vyrovnávací pamětí a přijímat a vrátí odpovědi v režimu přenášené datovými proudy (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Odesílat a přijímat požadavky a odpovědi v režimu přenášené datovými proudy v obou směrech. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Můžete zakázat streamování nastavením režim přenosu na <xref:System.ServiceModel.TransferMode.Buffered>, což je výchozí nastavení pro všechny vazby. Následující kód ukazuje, jak nastavit režim přenosu v konfiguraci.  
  
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
  
 Při instanci můžete vytvořit vaše vazby v kódu, musíte nastavit příslušné `TransferMode` vlastnost vazby (nebo pokud vytváříte vlastní vazby element vazby přenosu) na jednu z výše uvedených hodnot.  
  
 Můžete zapnout streamování pro zpracování požadavků a odpovědí nebo obou směrech nezávisle na obou stranách komunikující strany bez ovlivnění funkce. By však vždy předpokládat, že velikost přenášených dat je významné tak, že povolení streamování je zarovnán do bloku na oba koncové body komunikace odkazu. Pro komunikaci napříč platformami, kde jeden z koncových bodů není implementováno s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], možnost používat streamování závisí na možnosti streamování platformy. Další výjimečných výjimku, může být spotřeba paměti řízené scénáři, kde klient nebo služby musí minimalizovat jeho pracovní sady a můžete dovolit pouze malou vyrovnávací pamětí velikosti.  
  
### <a name="enabling-asynchronous-streaming"></a>Povolení asynchronní datové proudy  
 Chcete-li povolit asynchronní streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte její <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`. Také jsme přidali možnosti true asynchronní streamování na straně odeslání. Tím se zlepšuje škálovatelnost služby ve scénářích, kde ji je streamování na více klientů, z nichž některé jsou pomalé v režimu čtení pravděpodobně z důvodu zahlcení sítě nebo nejsou vůbec čtení zpráv. V těchto scénářích jsme teď neblokují jednotlivých vláken ve službě za klienta. Tím se zajistí, že služba je schopna zpracovat mnoho více klientů a zlepšení škálovatelnosti služby.  
  
### <a name="programming-model-for-streamed-transfers"></a>Model programování pro přenosy přenášené datovými proudy  
 Programovací model pro streamování je jednoduchá. Pro přijetí přenášené datovými proudy dat, zadejte operaci kontrakt, který má jeden <xref:System.IO.Stream> zadali vstupní parametr. Pro vrácení datové proudy, vrátit <xref:System.IO.Stream> odkaz.  
  
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
  
 Operaci `Echo` v předchozím příkladu obdrží a vrátí datového proudu a proto je nutné použít na vazba s <xref:System.ServiceModel.TransferMode.Streamed>. Pro operaci `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> je nejvhodnější, protože pouze vrátí <xref:System.IO.Stream>. Jednosměrná operace je nejvhodnější pro <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Všimněte si, že přidání druhý parametr pro následující `Echo` nebo `ProvideInfo` operace způsobí, že model služby vrátit se zpátky do strategie ve vyrovnávací paměti a používat reprezentace běhu serializace datového proudu. Pouze operace s parametrem jeden vstupní datový proud jsou kompatibilní s začátku do konce požadavek streaming.  
  
 Toto pravidlo se vztahuje podobně kontrakty zpráv. Jak ukazuje následující kontrakt zprávy, může mít pouze jeden textu člen v vaší kontrakt zprávy, která je datový proud. Pokud chcete další informace, pomocí datového proudu komunikovat, musí být tyto informace provedena v záhlaví zprávy. Text zprávy je vyhrazeno pouze pro datový proud obsahu.  
  
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
  
 End přenášené datovými proudy přenosů a zpráva je zavřený, když datový proud dosáhne konce souboru (EOF). Při odesílání zprávy (návrat hodnoty nebo vyvolání operace), můžete předat <xref:System.IO.FileStream> a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury následně vrátí všechna data z tohoto datového proudu, dokud datový proud byl zcela číst a dosaženo konce souboru. Přenos přenášené datovými proudy dat pro zdroj, žádný takový předdefinovaných <xref:System.IO.Stream> odvozené třídy existuje, vytvořit taková třída, překrytí třídy přes svůj zdroj datového proudu a použít jako hodnotu argumentu nebo return.  
  
 Při přijímání zprávy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konstrukce a stream zpráv kódováním Base64 body obsah (nebo příslušné části standardu MIME, pokud používáte MTOM) a datový proud dosáhne konce souboru, když obsah byl načten.  
  
 Streamování transportní vrstvy také funguje s žádným jiným zpráva kontrakt typem (seznamy parametrů, argumenty kontraktu dat a kontrakt explicitní zprávy), ale protože serializace a deserializace například zadali zprávy vyžaduje ukládání do vyrovnávací paměti podle serializátor , není vhodné používat takové variant kontrakt.  
  
### <a name="special-security-considerations-for-large-data"></a>Speciální bezpečnostní aspekty velkých objemů dat  
 Všechny vazby umožňují omezit velikost příchozí zprávy, aby se zabránilo útoky DOS. <xref:System.ServiceModel.BasicHttpBinding>, Například zpřístupní [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) vlastnost, která bounds velikost příchozí zprávy a proto také bounds maximální množství paměti, které je přístupné Při zpracování zprávy. Tato jednotka je nastavena v bajtech s výchozí hodnotou 65 536 bajty.  
  
 Ohrožení zabezpečení, která je specifická pro scénář streamování velkých objemů dat provokes odepření služby tak, že data uložená do vyrovnávací paměti, když příjemce očekává, že odesílání. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy vyrovnávacích pamětí hlavičkách protokolu SOAP zprávy, a proto útočník může vytvořit velké škodlivý zprávu, která se skládá pouze z hlavičky vynutit data, která mají být do vyrovnávací paměti. Pokud je povoleno vysílání datového proudu, `MaxReceivedMessageSize` lze nastavit na velmi velké hodnoty, protože příjemce nikdy očekává celé zpráva, která má být ukládán do vyrovnávací paměti v paměti najednou. Pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je nucen se vyrovnávací paměť zprávy, dojde k přetečení paměti.  
  
 Proto omezení maximální velikost příchozí zprávy není dostatek v tomto případě. `MaxBufferSize` Vlastnost je potřeba omezit paměť, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyrovnávací paměti. Je důležité, abyste tuto možnost nastavíte na hodnotu bezpečné (nebo jej zachovat na výchozí hodnota) při streamování. Předpokládejme například, musí přijmout služby souborů až do 4 GB velikost a jejich uložení na místní disk. Také Předpokládejme, že vaše paměti je omezené tak, že můžete pouze buffer 64 KB dat najednou. Potom byste měli nastavit `MaxReceivedMessageSize` do 4 GB a `MaxBufferSize` na 64 KB. Také v implementaci služby musíte zajistit číst pouze z příchozího datového proudu v bloky dat 64 KB a nečtěte další blok před předchozí byl zapsaný na disk a zrušených z paměti.  
  
 Je také důležité si uvědomit, že tato kvóta pouze to, do vyrovnávací paměti provádí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a nemůže chránit proti žádné ukládání do vyrovnávací paměti, abyste provedli v implementaci vlastní služba nebo klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dodatečné informace o zabezpečení, najdete v části [důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Rozhodnutí použít ve vyrovnávací paměti nebo přenášené datovými proudy přenosy je místní rozhodnutí koncového bodu. Pro přenosy protokolu HTTP režim přenosu nešířily připojení nebo proxy servery a jiných zprostředkovatelů. Nastavení režimu přenosu se nereflektují v popisu rozhraní služby. Po generování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta ke službě, je nutné upravit konfigurační soubor pro služby určena pro použití s přenášené datovými proudy přenosy nastavení režimu. TCP a přenosy pojmenovaný kanál režim přenosu rozšířena jako výraz zásad.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
