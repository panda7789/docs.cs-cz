---
title: Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: dd5fe08054b3a10c1663a7dd7dab5f9de5327cbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329047"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů
Toto téma popisuje formátu trace dat, jak zobrazit a přístupů, které použití prohlížeče trasování služeb k řešení problémů s aplikací.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Pomocí nástroje prohlížeče trasování služeb  
 Nástroj prohlížeče trasování služeb Windows Communication Foundation (WCF) umožňuje korelovat diagnostická trasování vytvářených naslouchacích procesů WCF najít hlavní příčinu chyby. Nástroj poskytuje způsob, jak snadno zobrazit, skupiny a filtrovat trasování, takže můžete diagnostikovat, opravit a ověřit problémy se službami WCF. Další informace o použití tohoto nástroje najdete v tématu [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Toto téma obsahuje snímky obrazovky generovány spuštěním trasování [trasování a protokolování zpráv](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázkový při prohlížení pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Toto téma ukazuje, jak můžete porozumět obsah trasování, aktivit a jejich korelaci a jak analyzovat velké množství trasování při řešení potíží s.  
  
## <a name="viewing-trace-content"></a>Obsah zobrazení trasování  
 Události trasování obsahuje následující nejdůležitější informace:  
  
-   Název aktivity při nastavení.  
  
-   Emise čas.  
  
-   Úroveň trasování.  
  
-   Název zdroje trasování.  
  
-   Název procesu.  
  
-   Id vlákna.  
  
-   Trasování jedinečný identifikátor, který je adresa URL, která směřuje k cíli v Microsoft Docs, ze kterého můžete získat další informace o trasování.  
  
 Všechny tyto uvidíte v horním pravém panelu v prohlížeče trasování služeb nebo **základní informace** část v zobrazení formátovaného pravém panelu při výběru trasování.  
  
> [!NOTE]
>  Pokud klienta a služby jsou ve stejném počítači, bude k dispozici trasování pro obě aplikace. Ty lze filtrovat pomocí **název procesu** sloupce.  
  
 Kromě toho formátovaný zobrazení poskytuje také popis pro trasovacího a další podrobné informace, pokud je k dispozici. Druhá možnost může zahrnovat výjimka typu a zpráva, zásobníky volání akce zprávy, z/do pole a další informace o výjimce.  
  
 V XML-zobrazení značky xml užitečné, patří:  
  
-   `<SubType>` (úroveň trasování).  
  
-   `<TimeCreated>`.  
  
-   `<Source>` (název zdroje trasování).  
  
-   `<Correlation>` (id aktivity nastaven při generování trasování).  
  
-   `<Execution>` (id procesu a vlákně).  
  
-   `<Computer>`.  
  
-   `<ExtendedData>`, včetně `<Action>`, `<MessageID>` a `<ActivityId>` nastavit v záhlaví zprávy při odesílání zprávy.  
  
 Pokud zobrazíte "Odeslané zprávy přes kanál" trasování, může se zobrazit následující obsah.  
  
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
  
## <a name="servicemodel-e2e-tracing"></a>Trasování ServiceModel E2E  
 Při `System.ServiceModel` zdroj trasování nastavená `switchValue` jiné než vypnuté, a `ActivityTracing`, WCF vytvoří aktivity a přenosy WCF zpracování.  
  
 Aktivita je logické jednotky zpracování, které skupiny všechna trasování související pro tento procesor. Například můžete definovat jednu aktivitu pro každý požadavek. Přenosy vytvořit příčinnou vztah mezi aktivity v rámci koncových bodů. Šíření ID aktivity umožňuje týkají aktivity napříč koncovými body. To můžete udělat tak, že nastavíte `propagateActivity` = `true` v konfiguraci na každý koncový bod. Aktivity, přenosy a šíření umožňují provádět korelace chyby. Tímto způsobem můžete najít hlavní příčinu chyby rychleji.  
  
 Na straně klienta se vytvoří jedna aktivita WCF pro každé volání modelu objektu (například otevřít třídu ChannelFactory, přidat, rozdělit a atd.) Každé volání operace, jsou zpracovávána v aktivity jako "Action procesu".  
  
 Na následujícím snímku obrazovky, extrahovat z [trasování a protokolování zpráv](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka na levém panelu zobrazí seznam aktivit, které jsou vytvořeny během procesu klienta, seřazené podle času vytvoření. Následuje chronologický seznam aktivit:  
  
-   Vytvořený objekt pro vytváření kanálů (třídu ClientBase).  
  
-   Otevřít objekt pro vytváření kanálů.  
  
-   Přidat akci zpracování.  
  
-   Nastavte zabezpečenou relaci (Tento došlo k na první požadavek) a infrastruktura zpracovaných tři zabezpečení zprávy s odezvami: RVNÍ RSTR, SCT (proces zpráva 1, 2, 3).  
  
-   Zpracování Subtract, násobit a požádá o dělení.  
  
-   Zavření objekt pro vytváření kanálů, a tím zabezpečené relaci a zpracuje odpověď na zprávu zabezpečení Storno.  
  
 Protože vazba wsHttpBinding vidíme zprávy Infrastruktura zabezpečení.  
  
> [!NOTE]
>  Ve službě WCF, ukážeme odpovědích zpočátku zpracovávána v samostatných aktivity (zpracovat zprávu) předtím, než jsme korelovat je odpovídající aktivity procesu akce, která obsahuje zprávy s požadavkem, k tomu přenos. To se stane pro zprávy o infrastrukturu a asynchronní požadavků a je vzhledem k tomu, že jsme musí zkontrolovat zprávy, přečíst hlavičku activityId a identifikovat existující aktivitu akce. proces s tímto identifikátorem ke korelaci do něj. Synchronní žádosti jsme pro odpovědi, blokují a vědět, tedy procesu akci, která má vztah k odpovědi.  
  
Uvedený čas vytvoření (levý panel) a jejich vnořené aktivity a trasování (pravý horní panel) činnosti klienta WCF na následujícím obrázku:

 ![Snímek obrazovky zobrazující klienta WCF seřazené podle času vytvoření aktivity.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)  
  
 Když vybereme aktivitu na levém panelu, můžeme vidět v pravém horním rohu panelu vnořené aktivity a trasování. Proto je toto snížené hierarchické zobrazení seznamu aktivit na levé straně na základě vybrané nadřazené aktivity. Vzhledem k tomu, že je vybraný proces akce přidat první žádost, tato aktivita obsahuje aktivitu nastavit až zabezpečenou relaci (přenos pro přenos zpátky ze) a trasování pro vlastní zpracování přidat akci.  
  
 Když dvakrát kliknete na Přidat aktivitu na levém panelu Akce proces, můžeme vidět grafická reprezentace klienta WCF aktivity související s přidat. První aktivitu na levé straně je kořenová aktivita (0000), což je výchozí aktivita. Přenosy WCF mimo okolí aktivity. Pokud není definována, mimo 0000 přenosy WCF. Druhá aktivita zpracovat přidání akce, tady, přenáší z 0. Potom jsme naleznete v tématu Instalace zabezpečenou relaci.  

 Následující obrázek ukazuje zobrazení grafu klienta WCF aktivity, konkrétně okolí aktivity (zde 0), zpracování akce a nastavte zabezpečenou relaci:   

 ![Rozhraní Graph v prohlížeči trasování okolí aktivity a procesu akce.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)   
  
 V pravém horním rohu panelu vidět všechna trasování týkající se činnosti proces přidání akce. Konkrétně jsme poslali žádost ("odeslaná zpráva přes kanál") a přijaté odpovědi ("přijatá zpráva přes kanál") do stejné aktivity. To je ukázáno v následujícím grafu. Pro přehlednost je sbalený nastavte zabezpečenou relaci aktivity v grafu.  
  
 Následující obrázek ukazuje seznam trasování aktivity procesu akce. Odeslat žádost o jsme přijetí odpovědi do stejné aktivity.
 
 ![Snímek obrazovky trasování prohlížeč zobrazující seznam trasování pro aktivitu procesu akce.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)  
  
 Tady, se nám načíst trasování klienta pouze pro přehlednost, ale trasování služeb (byla přijata zpráva požadavku a odpovědi zpráva odeslaná) zobrazí stejné aktivity v případě, že jsou také načteny v nástroji a `propagateActivity` byl nastaven na `true.` to je ukázáno dále obrázku.  
  
 Ve službě model aktivity mapuje koncepty WCF následujícím způsobem:  
  
1. Můžeme vytvářet a otevřete ServiceHost (to může vytvořit několik aktivit souvisejících s hostiteli, například v případě zabezpečení).  
  
2. Vytvoříme naslouchat na aktivitu pro každý naslouchací proces ve hostitele ServiceHost (s přenosy do a z Open ServiceHost).  
  
3. Pokud naslouchací proces zjistí žádost komunikace iniciované klientem, přenáší ho na aktivitu "Přijímat bajtů", ve kterém jsou zpracovány všechny bajtů odeslaných z klienta. V rámci této aktivity můžeme vidět žádné chyby připojení, ke kterým došlo během interakce služba klienta.  
  
4. Pro každou sadu bajtů, které se přijal, která odpovídá na zprávu zpracujeme těchto bajtů v aktivitě "Zpracovat zprávu", kde můžeme vytvořit objekt zprávy WCF. V této aktivitě vidíme chyby související s chybný obálky nebo chybnou zprávu.  
  
5. Jakmile je vytvořen zprávy, jsme přenést do aktivity procesu akce. Pokud `propagateActivity` je nastavena na `true` na klienta a služby, tato aktivita má stejné id jako definovaný v klientovi a je popsáno výše. V této fázi začneme těžit z přímou spojitost s míněním napříč koncovými body, protože všechna trasování, protože ho ve službě WCF, které se vztahují na žádost v této aktivity, včetně zpracování zpráv odpovědí.  
  
6. Pro akci mimo proces se nám vytvořit aktivitu "Spouštění uživatelského kódu" izolovat trasování v uživatelském kódu z těch, které jsou emitovány ve službě WCF, protože ho. V předchozím příkladu je vygenerován trasování "Service odešle odpověď přidat" aktivity "Spouštění uživatelského kódu" není v aktivitě rozšíří klientem, pokud je k dispozici.  
  
 Na obrázku, který následuje první aktivitu na levé straně je kořenová aktivita (0000), což je výchozí aktivita. Následující tři aktivit jsou k otevření hostitele ServiceHost. Aktivita ve sloupci 5 je naslouchací proces a zbývajících aktivit (6 až 8) popisují WCF zpracování zprávy, bajty zpracování aktivace kódu uživatele.  

 Zobrazení grafu aktivit služby WCF na následujícím obrázku:   

 ![Snímek obrazovky trasování prohlížeč zobrazující seznam aktivit služby WCF](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)  

 Na následujícím snímku obrazovky činnosti klienta a služby se zobrazí a zvýrazní zpracovat akci Přidání aktivity napříč procesy (oranžová). Šipky se týkají požadavků a odpovědí zpráv odesílaných i přijímaných klienta a služby. Trasování procesu akce jsou odděleny napříč procesy v grafu, ale zobrazí jako součást do stejné aktivity v pravém horním panelu. V tomto panelu vidět trasování klienta pro odeslané zprávy, za nímž následuje trasování služby pro přijatá a zpracovaná zprávy.  
  
 Následující obrázky ukazují zobrazení grafu obě aktivity klienta a služby WCF  
 
 ![Graf z prohlížeče trasování, který zobrazuje obě aktivity klienta a služby WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)   
  
 V následujícím scénáři chyba jsou související chyby a upozornění trasování na klienta a služby. V uživatelském kódu ve službě (úplně vpravo zelené aktivity, která obsahuje upozornění trasování pro výjimku "službu nelze zpracovat tento požadavek v uživatelském kódu.") je nejprve vyvolána výjimka. Při odesílání odpovědi klientovi trasování upozornění je znovu vygenerován pro označení chybová zpráva (levý růžový aktivita). Klient pak zavře klienta WCF (žlutá aktivita na straně levém), který zruší připojení ke službě. Služba vyvolá chybu (nejdelší růžový aktivity na pravé straně).  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Chyba korelací napříč klienta a služby  
  
 Ukázka používá ke generování těchto trasování je řada synchronní žádosti pomocí vazba wsHttpBinding. Existují odchylky od tohoto grafu pro scénáře bez zabezpečení nebo s asynchronní požadavků, kde aktivitu akce. proces zahrnuje begin a end operací, které představují asynchronní volání a zobrazuje přenosy do zpětného volání aktivity. Další informace o dalších scénářů, najdete v části [začátku do konce trasování scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Řešení problémů pomocí prohlížeče trasování služeb  
 Při načítání trasovací soubory v nástroji Prohlížeč trasování služeb, můžete vybrat žádnou aktivitu žluté nebo červené na levém panelu zjistit příčinu problému ve vaší aplikaci. 000 aktivit obvykle má neošetřené výjimky, které se až uživatel.  
  
  Následující obrázek ukazuje, jak vybrat aktivitu žluté nebo červené zjistit příčinu problému.   
 ![Snímek obrazovky s červenou nebo žlutou aktivit pro vyhledání příčinu problému.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)  

 V pravém horním rohu panelu můžete zkontrolovat trasování aktivity, které jste vybrali na levé straně. Potom můžete zkontrolovat žluté nebo červené trasování v panelu a zobrazit, jak se korelují. V předchozím grafu vidíme trasování upozornění pro klienta a služby do procesu akce aktivity.  
  
 Pokud toto trasování není poskytnout hlavní příčinu chyby, můžete využít graf dvojitým kliknutím na vybranou aktivitou na levém panelu (zde akce proces). Zobrazí graf s souvisejících aktivit. Můžete rozbalit souvisejících aktivit (kliknutím symboly "+") k vyhledání prvního emitovaný trasování v red nebo žlutá v souvisejících aktivit. Zachovejte rozbalení aktivity, ke kterým došlo před žluté nebo červené trasování zájmu následující převody souvisejících činností nebo zprávy toků napříč koncovými body, dokud sledování hlavní příčinu problému.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Rozbalení aktivity pro sledování hlavní příčinu problému  
  
 Pokud ServiceModel `ActivityTracing` je vypnuté, ale ServiceModel trasování je zapnutý, můžete zobrazit, protože ho v aktivitě 0000 trasování ServiceModel. Ale to vyžaduje další úsilí o korelaci těchto trasování.  
  
 Pokud je povoleno protokolování zpráv, můžete na kartě zpráva zobrazíte zpráv, které má vliv chyby. Dvojitým kliknutím zprávy v red nebo žlutou barvou, zobrazí se zobrazení grafu aktivit souvisejících. Tyto aktivity jsou ty, které nejvíce úzce souvisí s žádost, ve kterém došlo k chybě.  
  
 ![Snímek obrazovky z prohlížeče trasování povoleno protokolování zpráv.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)  

Proces řešení potíží, můžete také vybrat žluté nebo červené zprávy trasování a dvojím kliknutím ho sledujte hlavní příčinu.  
  
## <a name="see-also"></a>Viz také:

- [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
