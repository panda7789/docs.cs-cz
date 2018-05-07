---
title: Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: bfc0d2c10bfdca253f2ce410a4cd38218b3f5cfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů
Toto téma popisuje formát dat trasování, jak zobrazit a přístupy, které použití prohlížeče trasování služby problém s vaší aplikací.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Pomocí nástroje prohlížeče trasování služby  
 Nástroj prohlížeče trasování služeb Windows Communication Foundation (WCF) umožňuje korelovat diagnostické trasování vyprodukované [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] naslouchací procesy najít kořenu způsobit chyby. Nástroj nabízí způsob, jak snadno zobrazit skupiny, a trasování filtru tak, aby můžete určit příčiny, opravte a zkontrolujte problémy s [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby. Další informace o použití tohoto nástroje najdete v tématu [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Toto téma obsahuje snímky obrazovky trasování generované systémem [trasování a protokolování zpráv](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázkové, při zobrazení pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Toto téma ukazuje, jak pochopit obsah trasování, aktivity a jejich korelace a jak analyzovat velké počty trasování, při řešení potíží.  
  
## <a name="viewing-trace-content"></a>Obsah zobrazení trasování  
 Trasování událostí obsahuje následující nejdůležitější informace:  
  
-   Název aktivity Pokud nastavíte.  
  
-   Emisí čas.  
  
-   Úroveň trasování.  
  
-   Název zdroje trasování.  
  
-   Název procesu.  
  
-   Id vlákna.  
  
-   Trasování jedinečný identifikátor, který je adresu URL, která směřuje k cíli v Microsoft Docs, ze kterého můžete získat další informace o trasování.  
  
 Všechny tyto se zobrazí v horním pravém panelu do prohlížeče trasování služeb nebo **základní informace** části v pravém panelu při výběru trasování formátovaný zobrazení.  
  
> [!NOTE]
>  Pokud klienta a služby jsou na stejném počítači, trasování pro obě aplikace bude k dispozici. Ty lze filtrovat pomocí **název procesu** sloupce.  
  
 Kromě toho formátovaný zobrazení taky obsahuje popis pro trasování a další podrobné informace, pokud je k dispozici. K tomu může zahrnovat výjimka typu a zprávy, zásobníky volání zpráva akce, z/do pole a další informace o výjimce.  
  
 V zobrazení XML značky xml užitečné patří:  
  
-   \<Podtyp > (úroveň trasování).  
  
-   \<TimeCreated >.  
  
-   \<Zdroj > (název zdroje trasování).  
  
-   \<Korelace > (id aktivity nastaven při generování trasování).  
  
-   \<Provádění > (id procesu a vlákno).  
  
-   \<Počítače >.  
  
-   \<ExtendedData >, včetně \<akce >, \<MessageID > a \<aktivity > nastaveny v hlavičce zprávy při odesílání zprávy.  
  
 Pokud si projdete trasování "Odeslané zprávy přes kanál", může se zobrazit následující obsah.  
  
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
 Když `System.ServiceModel` zdroj trasování je nastaveno s `switchValue` jiné než vypnuté, a `ActivityTracing`, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vytvoří aktivity a přenosy pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zpracování.  
  
 Aktivita je logické jednotky, skupiny všech trasování související s touto jednotkou zpracování zpracování. Můžete například definovat jednu aktivitu pro každý požadavek. Přenosy vytvořit příčinnou relaci mezi aktivitami v rámci koncové body. Šíření ID aktivity umožňuje aktivity se týkají napříč koncovými body. To můžete provést nastavením `propagateActivity` = `true` v konfiguraci na každý koncový bod. Aktivity, přenosy a šíření umožňují provádět korelace chyby. Tímto způsobem můžete najít hlavní příčinu chyby rychleji.  
  
 Na klientovi jeden [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aktivity se vytvoří pro každý model volání objektu (například Open ChannelFactory, přidat, dělení a atd.) Každé volání operací se zpracovává aktivitu "Proces Action".  
  
 Na následujícím snímku obrazovky z extrahovat [trasování a protokolování zpráv](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) levém panelu ukázkové zobrazí seznam aktivity vytvořené v procesu klienta, seřazené podle času vytvoření. Následuje seznam chronologickém aktivit:  
  
-   Sestavit kanálu (třídu ClientBase).  
  
-   Otevřít kanálu.  
  
-   Zpracovat přidat akci.  
  
-   Nastavení relace Secure (Tato došlo k na první požadavek) a zpracovat tři zprávy odpovědi infrastruktury zabezpečení: RVNÍ RSTR, SCT (proces zprávy 1, 2, 3).  
  
-   Zpracování Subtract, násobit a dělení požadavky.  
  
-   Uzavřený vytváření kanálů, a tak uzavřený zabezpečené relace a zpracuje odpověď na zprávu zabezpečení Storno.  
  
 Z důvodu wsHttpBinding vidíte zprávy infrastruktury zabezpečení.  
  
> [!NOTE]
>  V [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], ukážeme odpovědí na zprávy původně zpracovávána v samostatnou aktivitě (proces zprávy) před jsme korelovat odpovídající akce proces aktivitě, která zahrnuje zprávu požadavku, prostřednictvím přenos. To se stane pro zprávy infrastruktury a asynchronní požadavky a je vzhledem k tomu, že jsme musí zkontrolujte zprávy, čtení hlavičku aktivity a identifikovat existující aktivitu procesu akce s tímto id ke korelaci do ní. Synchronní požadavkům jsme blokují pro odpověď a proto vědět proces akci, která má vztah k odpovědi.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
Činnosti klienta WCF uvedené podle času vytvoření (levém panelu) a jejich vnořených aktivit a trasování (horním pravém panelu)  
  
 Když jsme v levém panelu vyberte aktivitu, jsme můžete zobrazit vnořených aktivit a trasování v horním pravém panelu. Proto je snížené hierarchické zobrazení seznamu aktivit na levé straně na základě vybrané nadřazené aktivity. Vybraná akce procesu přidat je první požadavek, a proto tato aktivita obsahuje aktivitu nastavit až zabezpečené relace (přenos pro přenos zpět z) a trasování pro vlastní zpracování přidat akci.  
  
 Když dvakrát kliknete na akci procesu přidat aktivitu v levém panelu, jsme najdete v části grafické reprezentace klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] činnosti týkající se přidat. První aktivitu na levé straně je aktivita kořenové (0000), což je výchozí aktivity. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] přenosy mimo vedlejším aktivity. Pokud to není definován, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] přenosy mimo 0000. Druhá aktivita, proces přidat akci, zde přenáší mimo 0. Potom jsme najdete v části instalace zabezpečené relace.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Graf zobrazení činnosti klienta WCF: vedlejším aktivity (sem 0), akce procesu a nastavit si zabezpečené relace  
  
 V horním pravém panelu jsme můžete zobrazit všechny trasování týkající se činnosti procesu přidat akci. Konkrétně jsme odeslala zprávu požadavku ("odeslané zprávy přes kanál") a přijaté odpovědi ("přijaté zprávy přes kanál") do stejné aktivity. To je znázorněno v následujícím grafu. Pro přehlednost nastavení zabezpečení relace aktivity sbalena v grafu.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
Seznam trasování aktivity akce proces: jsme žádost odesílat a přijímat odpovědi do stejné aktivity.  
  
 Zde jsme načtení trasování klienta pouze pro přehlednost, ale služba trasování (přijata zpráva požadavku a odeslat zprávu odpovědi) se ve stejné aktivitě při jsou i načíst v nástroji a `propagateActivity` byla nastavena na `true.` to na novější obrázku je zobrazený.  
  
 Ve službě, aktivity modelu mapuje [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncepty následujícím způsobem:  
  
1.  Nemůžeme vytvořit a otevřete ServiceHost (to může vytvořit několik aktivit souvisejících s hostiteli, například v případě zabezpečení).  
  
2.  Vytvoříme naslouchat na aktivitu pro každý naslouchací proces v hostiteli služby (s přenosy a deaktivovat otevřete ServiceHost).  
  
3.  Zjistí-li naslouchací proces žádost komunikace iniciované klientem, přenáší k aktivitě "Přijímat bajtů", ve kterém jsou zpracovány všechny bajtů odeslaných z klienta. V této aktivity jsme se zobrazí chyby připojení, ke kterým došlo během interakce služby klienta.  
  
4.  Pro každou sadu bajtů, které je přijaly, která odpovídá na zprávu, jsme zpracovat tyto bajtů aktivity "Proces zprávu", kde se nám vytvořit [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] objekt zprávy. V této aktivitě vidíte chyby související s chybný obálky nebo chybnou zprávu.  
  
5.  Jakmile zprávy je vytvořen, jsme přeneste do procesu akce aktivity. Pokud `propagateActivity` je nastaven na `true` na klienta a služby, tato aktivita má stejné id jako definované v klientovi a popsané. Z této fázi jsme spustit, abyste mohli využívat výhod přímé korelace napříč koncovými body, protože všechny trasování vygenerované v [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] které se vztahují k žádosti jsou ve stejné aktivity, včetně zpracování zprávy odpovědi.  
  
6.  Pro akci mimo proces, vytvoříme aktivitu "Spuštění uživatelského kódu" izolovat trasování vygenerované v uživatelském kódu z těch vygenerované v [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. V předchozím příkladu jsou vydávány trasování "Service odešle odpověď přidat" aktivity "Execute uživatelský kód" není v rámci aktivity klientem, rozšíří Pokud jsou k dispozici.  
  
 Na obrázku, který následuje první aktivitu na levé straně je aktivita kořenové (0000), což je výchozí aktivity. Následující tři aktivity jsou otevřete hostiteli služby. Aktivity ve sloupci 5 je naslouchací proces a zbývajících aktivit (6 až 8) popisují WCF zpracování zprávy ze bajtů zpracování tak, aby aktivace kódu uživatele.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
Seznam aktivit služby WCF  
  
 Následující snímek obrazovky ukazuje aktivity pro klienta a služby a zvýrazňuje aktivitu přidat akci proces napříč procesy (oranžová). Dvojice šipek, které se týkají žádosti a odpovědi zpráv odesílaných i přijímaných v: klienta a služby. Trasování procesu akce jsou oddělené v rámci procesy v grafu, ale zobrazí v rámci téže aktivity v pravém panelu. V tomto panelu jsme najdete v trasování klienta pro odeslané zprávy, za nímž následuje trasování služby pro zprávy přijaté a zpracovány.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Zobrazení grafu obou aktivit klienta a služby WCF  
  
 V následujícím scénáři chyba jsou související chyby a upozornění trasování na klienta a služby. Nejprve je vyvolána výjimka v uživatelském kódu ve službě (zelený aktivity nejvíce vpravo, která obsahuje upozornění trasování pro výjimku "služba nemůže zpracovat tento požadavek v uživatelském kódu."). Při odeslání odpovědi klientovi, je upozornění trasování znovu vygenerované k označení selhání zprávy (levém růžový aktivita). Klient poté uzavře svého klienta WCF (žlutý aktivita na straně levém), který zruší připojení ke službě. Služba vrátí chybu (nejdelší růžový aktivita na pravé straně).  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Chyba korelace mezi klienta a služby  
  
 Ukázka sloužící ke generování toto trasování je řadu synchronní požadavků pomocí wsHttpBinding. Existují odchylky od tohoto grafu pro scénáře bez zabezpečení nebo s asynchronní požadavků, kde zahrnuje na začátku a konce operacích, které tvoří asynchronního volání akce proces aktivity a zobrazuje přenosů, aby se zpětné volání. Další informace o dalších scénářích najdete v tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Řešení potíží s použití prohlížeče trasování služeb  
 Při načítání trasovací soubory v nástroji Prohlížeč trasování služby, můžete vybrat všechny red nebo žlutou aktivity na levém panelu zjistit příčinu problému v aplikaci. 000 aktivita má obvykle neošetřené výjimky, které bublinový až uživatele.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Výběr red nebo žlutou aktivity k nalezení kořene problém  
  
 V horním pravém panelu můžete zkontrolovat trasování pro aktivity, které jste vybrali na levé straně. Můžete pak zkontrolujte red nebo žlutou trasování tohoto panelu a zjistit, jak jsou korelační. V předchozím grafu vidíte trasování upozornění pro klienta a služby do stejné aktivity procesu akce.  
  
 Pokud toto trasování není poskytnout hlavní příčinu chyby, můžete využít grafu poklepáním na vybranou aktivitou na levém panelu (sem procesu akce). Pak se zobrazí graf s souvisejících činností. Můžete rozbalit souvisejících činností (kliknutím na znak "+") k vyhledání prvního emitovaného trasování v red nebo žlutý související aktivity. Zachovat rozbalení aktivity, které bylo provedeno těsně před red nebo žlutou trasování zájmu, následující přenosy souvisejících činností nebo zpráva toky napříč koncovými body, dokud nebude sledovat hlavní příčinu problému.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Rozšiřování aktivit ke sledování hlavní příčinu problému  
  
 Pokud ServiceModel `ActivityTracing` je vypnuto, ale ServiceModel trasování je, uvidíte ServiceModel trasování vygenerované v 0000 aktivity. To však vyžaduje další úsilí pochopit korelaci toto trasování.  
  
 Pokud je povoleno protokolování zpráv, můžete na kartě zpráva zobrazíte zpráv, které je ovlivněno chyba. Dvojitým kliknutím na soubor zprávy v red nebo žlutý, uvidíte graf zobrazení souvisejících činností. Tyto aktivity jsou ty, které nejvíce související na žádost o, kde došlo k chybě.  
  
 ![Použití prohlížeče trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Proces řešení potíží, můžete také vybrat red nebo žlutou zprávu trasování a dvakrát klikněte na něj sledovat hlavní příčinu  
  
## <a name="see-also"></a>Viz také  
 [Scénáře komplexního trasování](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
