---
title: "Generování trasování v uživatelském kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2162377fbe8f8329c12dfd88a55d893d26f5b2bf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="emitting-user-code-traces"></a>Generování trasování v uživatelském kódu
Kromě povolení trasování v konfiguraci ke shromažďování dat instrumentace generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], můžete také generování trasování v uživatelském kódu prostřednictvím kódu programu. Tímto způsobem můžete vytvořit proaktivně instrumentace data, která můžete zobrazit později pro účely diagnostiky. Toto téma popisuje, jak můžete to provést.  
  
 Kromě toho [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka zahrnuje všechny kód ukázáno v následujících částech.  
  
## <a name="creating-a-trace-source"></a>Vytváření zdroje trasování  
 Následující kód slouží k vytvoření zdroj trasování uživatele.  
  
```  
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Vytvoření aktivity  
 Aktivity jsou logické jednotky zpracování. Můžete vytvořit jednu aktivitu pro každou hlavní výpočetní jednotky, ve kterém chcete trasování do seskupeny dohromady. Můžete například vytvořit jednu aktivitu pro každý požadavek pro službu. Uděláte to tak, proveďte následující kroky.  
  
1.  ID aktivity a uložte v oboru.  
  
2.  Vytvoření nového ID aktivity.  
  
3.  Přenos z aktivity v oboru do nového, nastavte novou aktivitu v oboru a emitování spuštění trasování pro danou aktivitu.  
  
 Následující kód ukazuje, jak to provést.  
  
```  
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Generování trasování v rámci aktivity uživatelů  
 Následující kód vysílá trasování v rámci aktivity uživatelů.  
  
```  
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Zastavení aktivity  
 K zastavení aktivity, přeneste zpět do původní aktivity, zastavte id aktuální aktivity a obnovit původní id aktivity v oboru.  
  
 Následující kód ukazuje, jak to provést.  
  
```  
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Šíření ID aktivity služby  
 Pokud nastavíte `propagateActivity` atribut `true` pro `System.ServiceModel` zdroj trasování v konfiguraci klient a služba souborů, služba zpracování dojde k žádosti přidat do stejné aktivity, jako je definována v klientovi. Pokud službu definuje vlastní aktivity a přenosy, služba trasování se nezobrazí v aktivitě klienta rozšířen. Místo toho se v aktivitě korelační pomocí přenosu trasování na aktivitu, jejíž ID je rozšířena klientem.  
  
> [!NOTE]
>  Pokud `propagateActivity` je atribut nastaven na `true` na klienta a služby, vedlejším aktivity v rámci operace služby je nastavený [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
 Následující kód vám pomůže zkontrolovat, zda byl nastaven aktivitu v oboru podle [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
```  
// Check if an activity was set in scope by WCF, if it was   
// propagated from the client. If not, ( ambient activity is   
// equal to Guid.Empty), create a new one.  
if(Trace.CorrelationManager.ActivityId == Guid.Empty)  
{  
    Guid newGuid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = newGuid;  
}  
// Emit your Start trace.  
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");  
  
// Emit the processing traces for that request.  
serviceTs.TraceInformation("Service receives Add "   
                            + n1 + ", " + n2);  
// double result = n1 + n2;  
serviceTs.TraceInformation("Service sends Add result" + result);  
  
// Emit the Stop trace and exit the method scope.  
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");  
// return result;  
```  
  
## <a name="tracing-exceptions-thrown-in-code"></a>Trasování výjimky vydané v kódu  
 Pokud je vyvolána výjimka v kódu, můžete také trasování výjimky na úrovni upozornění nebo si pomocí následujícího kódu.  
  
```  
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Zobrazení trasování uživatele v nástroji Prohlížeč trasování pro služby  
 Tato část obsahuje snímky obrazovky trasování generované systémem [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázkové, při zobrazení pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 V následujícím diagramu je vybraná aktivita "žádostí Přidat" předtím vytvořili na levém panelu. Zobrazí se aktivitách tři další matematické operace (dělit, Subtract, násobkem) které tvoří program klienta aplikace. Kód uživatele nemá definovánu jednu novou aktivitu, pro každou operaci izolovat potenciální chyby výskytů na jiné požadavky.  
  
 K předvedení použití přenosů [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázce kalkulačky aktivity, který zapouzdřuje čtyři operace žádosti, které se také vytvoří. Pro každý požadavek, je přenos a zpět z aktivity kalkulačky pro aktivitu žádosti (trasování je zvýrazněn v horním pravém panelu na obrázku).  
  
 Když vyberete aktivitu na levém panelu, trasování začleněn sám v této aktivity se zobrazí v horním pravém panelu. Pokud `propagateActivity` je `true` na každý koncový bod v cestě požadavku trasování v aktivitu žádosti jsou ze všech procesů, které jsou součástí požadavku. V tomto příkladu se zobrazí trasování z klienta a služby ve sloupci 4. v panelu.  
  
 Tato aktivita se zobrazí následující pořadí zpracování:  
  
1.  Klient odešle zprávu do přidat.  
  
2.  Služba přijímá přidat zprávu požadavku.  
  
3.  Služba odešle odpověď přidat.  
  
4.  Klient obdrží odpověď přidat.  
  
 Všechny tyto trasování byly vygenerované na úrovni informace. Kliknutím na trasování v pravém panelu zobrazuje podrobnosti o této trasování v pravém panelu.  
  
 V následujícím diagramu vidíte také přenos trasování od a do aktivity kalkulačky, jakož i dvě dvojice spuštění a zastavení trasování za aktivitu žádosti o, jeden pro klienta a jeden pro službu (jeden pro každý zdroj trasování).  
  
 ![Prohlížeč trasování: Generování č. 45; & uživatelského kódu trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Seznam aktivit podle času vytvoření (levém panelu) a jejich vnořené aktivity (pravém panelu)  
  
 Pokud kódu služby vyvolá výjimku, která způsobuje, že klient má být vyvolána také (například když klient neobdržela odpověď na žádost), jak služba a klient upozornění nebo chybové zprávy objevit ve stejné aktivitě pro přímé korelace. V následujícím diagramu službu vyvolá výjimku, která stavy "služba odmítá zpracovat tento požadavek v uživatelském kódu." Klient také vyvolá výjimku, která stavy "server nemohl zpracovat požadavek z důvodu vnitřní chyby."  
  
 ![Použití prohlížeče trasování pro vydávání č. 45; & uživatelského kódu trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Chyby napříč koncovými body pro daný požadavek se zobrazují ve stejné aktivitě, pokud byla rozšířena id aktivity žádosti  
  
 Dvojitým kliknutím násobkem aktivita na levém panelu se zobrazí následující graf s trasování pro násobení aktivity související se situací jednotlivých procesů. Vidíme, že upozornění nejdřív došlo k chybě na službu (vyvolána výjimka), která následuje upozornění a chyby v klientovi protože nebylo možné zpracovat žádost. Proto jsme implikují příčinnou chyba vztah mezi koncovými body a odvodí hlavní příčinu chyby.  
  
 ![Použití prohlížeče trasování pro vydávání č. 45; & uživatelského kódu trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Zobrazení grafu chybě korelace  
  
 Pokud chcete získat předchozí trasování, nastaví `ActivityTracing` pro trasování zdrojů uživatele a `propagateActivity=true` pro `System.ServiceModel` zdroj trasování. Jsme nenastavili `ActivityTracing` pro `System.ServiceModel` zdroj trasování povolit uživatelský kód pro rozšíření aktivity kódu uživatele. (Pokud ServiceModel trasování aktivit je zapnutý, ID aktivity definované v klientovi není rozšířen úplně do kódu uživatele služby; Přenosy, ale korelovat aktivity kód klienta a služby uživatele do mezilehlých [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aktivity.)  
  
 Definování aktivity a šíření ID aktivity a umožňuje nám k provedení korelace přímé chyba napříč koncovými body. Tímto způsobem jsme rychleji najít hlavní příčinu chyby.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md)
