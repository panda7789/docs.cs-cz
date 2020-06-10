---
title: Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: e1cd1443e96e7195127cb95e7ef1b2c4d6d9c176
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587752"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů

Toto téma popisuje formát dat trasování, jejich zobrazení a přístupy k řešení potíží s aplikací pomocí prohlížeče trasování služby.

## <a name="using-the-service-trace-viewer-tool"></a>Použití nástroje pro prohlížeč trasování služby

Nástroj pro prohlížeč trasování služby Windows Communication Foundation (WCF) pomáhá sladit trasování diagnostiky vytvořené naslouchacími procesy WCF za účelem nalezení hlavní příčiny chyby. Tento nástroj poskytuje způsob, jak snadno zobrazit, seskupit a filtrovat trasování, abyste mohli diagnostikovat, opravovat a ověřovat problémy se službami WCF. Další informace o použití tohoto nástroje naleznete v tématu [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md).

Toto téma obsahuje snímky obrazovky vygenerované v ukázce [trasování a protokolování zpráv](../../samples/tracing-and-message-logging.md) při zobrazení pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md). V tomto tématu se dozvíte, jak pochopit obsah trasování, aktivity a jejich korelaci a jak analyzovat velký počet trasování při řešení potíží.

## <a name="viewing-trace-content"></a>Zobrazení obsahu trasování

Událost trasování obsahuje následující nejvýznamnější informace:

- Název aktivity při nastavení

- Doba emise.

- Úroveň trasování.

- Název zdroje trasování

- Název procesu.

- ID vlákna.

- Jedinečný identifikátor trasování, což je adresa URL, která odkazuje na cíl v Microsoft Docs, ze kterého můžete získat další informace týkající se tohoto trasování.

 Všechny tyto možnosti lze zobrazit v pravém horním panelu v prohlížeči trasování služby nebo v sekci **základní informace** ve formátovaném zobrazení spodního panelu při výběru trasování.

> [!NOTE]
> Pokud je klient a služba ve stejném počítači, budou k dispozici trasování pro obě aplikace. Je možné je filtrovat pomocí sloupce **název procesu** .

Kromě toho formátované zobrazení také poskytuje popis pro trasování a další podrobné informace, pokud jsou k dispozici. Druhá může zahrnovat typ a zprávu výjimky, zásobníky volání, akce zprávy, pole/k a další informace o výjimce.

V zobrazení XML jsou užitečné značky XML následující:

- `<SubType>`(úroveň trasování).

- `<TimeCreated>`.

- `<Source>`(název zdroje trasování).

- `<Correlation>`(ID aktivity nastaveno při generování trasování).

- `<Execution>`(ID procesu a vlákna).

- `<Computer>`.

- `<ExtendedData>`, včetně `<Action>` `<MessageID>` a `<ActivityId>` nastaveného v záhlaví zprávy při odesílání zprávy.

Pokud prohlížíte trasování "odeslání zprávy přes kanál", může se zobrazit následující obsah.

```xml
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">
      <EventID>262163</EventID>
      <Type>3</Type>
      <SubType Name="Information">0</SubType>
      <Level>8</Level>
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />
      <Source Name="System.ServiceModel" />
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />
       <Channel />
       <Computer>TEST1</Computer>
   </System>
   <ApplicationData>
       <TraceData>
          <DataItem>
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>
                 <Description>Sent a message over a channel.</Description>
                 <AppDomain>client.exe</AppDomain>
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">

                  <MessageProperties>
                     <AllowOutputBatching>False</AllowOutputBatching>
                  </MessageProperties>
                  <MessageHeaders>
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>
                    </ReplyTo>
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>
                  </MessageHeaders>
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>
                </ExtendedData>
            </TraceRecord>
          </DataItem>
       </TraceData>
   </ApplicationData>
</E2ETraceEvent>
```

## <a name="servicemodel-e2e-tracing"></a>Sledování E2E ServiceModel

Pokud `System.ServiceModel` je zdroj trasování nastaven s `switchValue` jiným než off a `ActivityTracing` , WCF vytvoří aktivity a přenosy pro zpracování služby WCF.

Aktivita je logická jednotka zpracování, která seskupí všechna trasování související s touto jednotkou zpracování. Můžete například definovat jednu aktivitu pro každý požadavek. Přenosy vytvářejí příčinnou relaci mezi aktivitami v rámci koncových bodů. Šíření ID aktivity umožňuje propojit aktivity mezi koncovými body. To se dá udělat nastavením `propagateActivity` = `true` v konfiguraci u každého koncového bodu. Aktivity, přenosy a šíření vám umožní provádět korelaci chyb. Tímto způsobem můžete rychle najít hlavní příčinu chyby.

Na straně klienta se vytvoří jedna aktivita WCF pro každé volání objektového modelu (například otevřít třídu ChannelFactory, přidat, rozdělit a tak dále). Každé volání operace se zpracovává v aktivitě "zpracování akce".

Na následujícím snímku obrazovky extrahovaný na levém panelu ukázka [trasování a protokolování zpráv](../../samples/tracing-and-message-logging.md) zobrazí seznam aktivit vytvořených v procesu klienta, seřazené podle času vytvoření. Následuje chronologický seznam aktivit:

- Vytvořená továrna kanálu (ClientBase).

- Otevřeli jste objekt pro vytváření kanálů.

- Byla zpracována akce Přidat.

- Nastavte zabezpečenou relaci (k nimž došlo na prvním požadavku) a zpracovaly se tři zprávy odpovědi na infrastrukturu zabezpečení: RST, RSTR, SCT (procesová zpráva 1, 2, 3).

- Zpracovaly se požadavky odečíst, násobit a vydělit.

- Byla zavřena továrna kanálu a tato akce zavřela zabezpečenou relaci a zpracovala odpověď na zprávu zabezpečení zrušit.

 V důsledku wsHttpBinding se zobrazí zprávy infrastruktura zabezpečení.

> [!NOTE]
> V rámci služby WCF zobrazujeme zprávy odpovědí, které jsou zpočátku zpracovávány v samostatné aktivitě (zpracování zprávy) předtím, než je budeme korelovat s odpovídající aktivitou akce procesu, která obsahuje zprávu požadavku, prostřednictvím přenosu. K tomu dojde u zpráv infrastruktury a asynchronních požadavků a z důvodu faktu, že je nutné zprávu zkontrolovat, přečtěte si hlavičku activityId a Identifikujte aktivitu akce procesu s tímto ID, která se má přidružit ke korelaci. Pro synchronní požadavky je blokováno pro odpověď, a proto je nutné zjistit, které akce procesu odpověď souvisí.

Následující obrázek znázorňuje aktivity klienta WCF uvedené podle času vytvoření (levý panel) a jejich vnořených aktivit a trasování (horní pravý panel):

![Snímek obrazovky zobrazující aktivity klienta WCF uvedené podle času vytvoření](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)

Když na levém panelu vybereme aktivitu, uvidíme vnořené aktivity a trasování na pravém horním panelu. Proto se jedná o omezené hierarchické zobrazení seznamu aktivit na levé straně na základě vybrané nadřazené aktivity. Vzhledem k tomu, že je vybraná akce procesu přidat první požadavek, tato aktivita obsahuje nastavení aktivity zabezpečené relace (přenos do, přenos zpátky z) a trasování pro vlastní zpracování akce Přidat.

Pokud dvakrát kliknete na položku zpracovat akci přidat aktivitu na levém panelu, uvidíme grafickou reprezentaci aktivit WCF klienta souvisejících s přidáním. První aktivita na levé straně je kořenová aktivita (0000), což je výchozí aktivita. WCF přenáší mimo okolní aktivitu. Pokud není definován, WCF přenese z 0000. Zde, druhá aktivita, zpracovat akci přidat, převede z 0. Pak uvidíme nastavení zabezpečená relace.

Následující obrázek znázorňuje zobrazení grafu aktivit klienta WCF, konkrétně okolní aktivity (tady 0), akce procesu a nastavení zabezpečené relace:

![Graf v prohlížeči trasování zobrazující okolní aktivitu a akci procesu.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)

V pravém horním panelu vidíte všechna trasování související s akcí zpracovat akce Přidat aktivitu. Konkrétně jsme poslali zprávu požadavku ("poslali zprávu přes kanál") a přijali odpověď ("přijali zprávu přes kanál") ve stejné aktivitě. To je znázorněno v následujícím grafu. Pro přehlednost je aktivita nastavit zabezpečenou relaci sbalená v grafu.

Následující obrázek ukazuje seznam trasování pro aktivitu akce procesu. Odešleme žádost a dostanete odpověď ve stejné aktivitě.

![Snímek obrazovky prohlížeče trasování zobrazující seznam trasování aktivity zpracovat akci](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)

V tomto případě načteme trasování klientů pouze pro přehlednost, ale trasování služeb (přijatá zpráva požadavku a odpověď odeslána) se zobrazí ve stejné aktivitě, pokud jsou také načteny v nástroji a `propagateActivity` byla nastavena na hodnotu na `true.` obrázku na pozdější ilustraci.

V rámci služby se model aktivit mapuje na koncepty WCF následujícím způsobem:

1. Vytvoříme a otevřete třídu ServiceHost (ta může vytvořit několik aktivit souvisejících s hostiteli, například v případě zabezpečení).

2. Vytvoříme aktivitu naslouchání v aktivitě pro každý naslouchací proces v ServiceHost (s přenosy v a z Open ServiceHost).

3. Když naslouchací proces detekuje požadavek na komunikaci iniciované klientem, přenese se na aktivitu "příjem bajtů", ve které se zpracují všechny bajty odeslané z klienta. V této aktivitě se zobrazí všechny chyby připojení, ke kterým došlo během interakce mezi klientem a službou.

4. Pro každou sadu přijatých bajtů, která odpovídá zprávě, zpracováváme tyto bajty v aktivitě "procesní zpráva", kde vytvoříme objekt zprávy WCF. V této aktivitě se zobrazí chyby související s chybnou obálkou nebo chybnou zprávou.

5. Jakmile se zpráva vytvoří, převedeme na aktivitu procesu akce. Pokud `propagateActivity` je nastavená na `true` jak na klienta, tak pro službu, má tato aktivita stejné ID jako ta, která je definovaná v klientovi, a popsaná výše. Z této fáze začneme těžit z přímé korelace mezi koncovými body, protože všechna trasování vygenerovaná v rámci služby WCF, která souvisí s požadavkem, jsou v této stejné aktivitě, včetně zpracování zpráv odpovědí.

6. V rámci procesu mimo proces vytvoříme aktivitu spustit uživatelský kód pro izolaci trasování vysílaných v uživatelském kódu z těch, které se vygenerovaly ve službě WCF. V předchozím příkladu je trasování "služba odesílá odpověď" vygenerována v aktivitě "spustit uživatelský kód", která není v aktivitě šířené klientem, pokud je k dispozici.

Na následujícím obrázku je první aktivita na levé straně kořenovou aktivitou (0000), což je výchozí aktivita. Další tři aktivity slouží k otevření třídy ServiceHost. Aktivita ve sloupci 5 je naslouchací proces a zbývající aktivity (6 až 8) popisují zpracování služby WCF ve zprávě od zpracování bajtů až po aktivaci kódu uživatele.

Následující obrázek znázorňuje zobrazení grafu aktivit služby WCF:

![Snímek obrazovky prohlížeče trasování zobrazující seznam aktivit služby WCF](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)

Následující snímek obrazovky ukazuje aktivity pro klienta i službu a zvýrazní akci procesu přidat aktivitu mezi procesy (oranžová). Šipky se týkají zpráv požadavků a odpovědí odesílaných a přijímaných klientem a službou. Trasování akce procesu je rozděleno mezi procesy v grafu, ale zobrazuje se jako součást stejné aktivity v pravém horním panelu. Na tomto panelu jsme viděli trasování klientů pro odeslané zprávy a trasování služby pro přijaté a zpracovávané zprávy.

Následující obrázky znázorňují zobrazení grafu pro aktivity klientů a služeb WCF.

![Graf z prohlížeče trasování, který znázorňuje aktivity klientů a služeb WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)

V následujícím scénáři chyby se v souvislosti s trasováním chyb a upozornění na službě a klientovi vztahují. V uživatelském kódu na službě se poprvé vyvolala výjimka (nejvyšší zelená aktivita, která obsahuje trasování upozornění pro výjimku "služba nemůže tento požadavek zpracovat v uživatelském kódu."). Když je odpověď odeslána klientovi, trasování upozornění se znovu vygeneruje za účelem označení chybové zprávy (levá růžová aktivita). Klient pak ukončí svého klienta WCF (žlutou aktivitu na levé dolní straně), která přeruší připojení ke službě. Služba vyvolá chybu (nejdelší růžová aktivita napravo).

![Použití prohlížeče trasování](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Korelace chyb napříč službou a klientem

Ukázka použitá ke generování těchto trasování je série synchronních požadavků s použitím wsHttpBinding. Existují odchylky od tohoto grafu pro scénáře bez zabezpečení nebo u asynchronních požadavků, kde aktivita akce procesu zahrnuje počáteční a koncové operace, které tvoří asynchronní volání, a ukazuje přenos na aktivitu zpětného volání. Další informace o dalších scénářích najdete v tématu [kompletní scénáře sledování](end-to-end-tracing-scenarios.md).

## <a name="troubleshooting-using-the-service-trace-viewer"></a>Řešení potíží pomocí prohlížeče trasování služby

Při načítání trasovacích souborů v nástroji Prohlížeč trasování služby můžete vybrat jakoukoli červenou nebo žlutou aktivitu na levém panelu a sledovat příčinu problému ve vaší aplikaci. 000 aktivit obvykle obsahuje neošetřené výjimky, které jsou bublinou pro uživatele.

Následující obrázek ukazuje, jak vybrat červenou nebo žlutou aktivitu pro vyhledání kořenového adresáře problému.
![Snímek obrazovky červené nebo žluté aktivity pro vyhledání kořenového adresáře problému.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)

V pravém horním panelu můžete prohledat trasování pro aktivitu, kterou jste vybrali na levé straně. Pak můžete na tomto panelu prošetřit červené nebo žluté trasování a zjistit, jak se korelují. V předchozím grafu vidíte upozornění trasování pro klienta i službu ve stejné aktivitě akce procesu.

Pokud tato trasování neposkytují hlavní příčinu chyby, můžete graf využít tak, že dvakrát kliknete na vybranou aktivitu na levém panelu (zde proces procesu). Zobrazí se graf se souvisejícími aktivitami. Pak můžete rozbalit související aktivity (kliknutím na znaménko "+") a najít první vygenerované trasování červeně nebo žlutě v související aktivitě. Udržujte rozbalování aktivit, ke kterým došlo těsně před červeným nebo žlutým sledováním zájmu, po přenesení na související aktivity nebo toky zpráv napříč koncovými body, dokud nesledujete hlavní příčinu problému.

![Použití prohlížeče trasování](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Rozšiřování aktivit ke sledování hlavní příčiny problému

Pokud `ActivityTracing` je ServiceModel vypnuto, ale trasování ServiceModel je zapnuto, můžete vidět trasování ServiceModel v aktivitě 0000. To však vyžaduje více úsilí pro pochopení korelace těchto trasování.

Pokud je povoleno protokolování zpráv, můžete pomocí karty zpráva zjistit, která zpráva má vliv na chybu. Dvojitým kliknutím na zprávu na červenou nebo žlutou můžete zobrazit zobrazení grafu souvisejících aktivit. Tyto aktivity jsou ty, které úzce souvisejí s žádostí, kde došlo k chybě.

![Snímek obrazovky prohlížeče trasování se zapnutým protokolováním zpráv](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)

Pokud chcete začít řešit potíže, můžete také vybrat červené nebo žluté trasování zpráv a dvojitým kliknutím na něj sledovat hlavní příčinu.

## <a name="see-also"></a>Viz také

- [Scénáře komplexního trasování](end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Trasování](index.md)
