---
title: Generování trasování v uživatelském kódu
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: 5ecc0c2110362f715275729b5e4c4c7e1ec03496
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492661"
---
# <a name="emitting-user-code-traces"></a>Generování trasování v uživatelském kódu
Kromě povolení trasování v konfiguraci ke shromažďování dat instrumentace vygenerovaných Windows Communication Foundation (WCF), můžete také generování trasování v uživatelském kódu prostřednictvím kódu programu. Tímto způsobem můžete vytvořit proaktivně data instrumentace, který lze později prostudujte pro diagnostické účely. Toto téma popisuje, jak to udělat.  
  
 Kromě toho [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka zahrnuje veškerý kód jsme vám ukázali v následujících částech.  
  
## <a name="creating-a-trace-source"></a>Vytvoření zdroje trasování  
 Chcete-li vytvořit uživatelský zdroj trasování můžete použít následující kód.  
  
```csharp
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Vytváření aktivit  
 Aktivity jsou logické jednotky zpracování. Pro každou hlavní zpracování jednotku, ve kterém chcete traces být seskupené pohromadě, můžete vytvořit jednu aktivitu. Můžete například vytvořit jednu aktivitu pro každý požadavek do služby. Uděláte to tak, proveďte následující kroky.  
  
1.  ID aktivity uložení v oboru.  
  
2.  Vytvoření nové ID aktivity.  
  
3.  Přenos z aktivity v rozsahu do nové, nastavte novou aktivitu v oboru a generování trasování spuštění pro danou aktivitu.  
  
 Následující kód ukazuje, jak to provést.  
  
```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Generování trasování v rámci aktivity uživatelů  
 Následující kód generuje trasování v rámci aktivity uživatelů.  
  
```csharp
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Zastavení aktivity  
 K zastavení aktivity, převést zpět na původní aktivitu, zastavit aktuální id aktivity a obnovit původní id aktivity v oboru.  
  
 Následující kód ukazuje, jak to provést.  
  
```csharp
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Šíření ID aktivity ke službě  
 Pokud jste nastavili `propagateActivity` atribut `true` pro `System.ServiceModel` zdroj trasování v konfiguraci klient a služba souborů, služba zpracovává přidání požadavku dojde k do aktivity, jako je definován v klientovi. Pokud služba definuje vlastní aktivity a přenosy, trasování služby se nezobrazují v aktivitě rozšíří klienta. Místo toho se v nějaké aktivitě korelační podle přenos trasování na aktivitu, jejíž ID rozšířena klientem.  
  
> [!NOTE]
>  Pokud `propagateActivity` atribut je nastaven na `true` na klienta a služby, okolí aktivity v rámci operace služby je nastavený podle WCF.  
  
 Následující kód můžete použít ke kontrole, jestli aktivity byla nastavena v oboru službou WCF.  
  
```csharp
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
  
## <a name="tracing-exceptions-thrown-in-code"></a>Trasování výjimky vyvolané v kódu  
 Při vyvolání výjimky v kódu, můžete také sledovat výjimky na úrovni upozornění nebo si pomocí následujícího kódu.  
  
```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Zobrazení trasování uživatele v nástroji Prohlížeč trasování služby  
 Tato část obsahuje snímky obrazovky generovány spuštěním trasování [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázkový při prohlížení pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 V následujícím diagramu je vybraná aktivita "Přidat žádosti" jste předtím vytvořili na levém panelu. Je uvedený s tři další matematické operace aktivity (rozdělit, odečítání, vícenásobně), které tvoří program aplikace klienta. Uživatelský kód má definovaný jeden novou aktivitu pro každou operaci izolovat potenciální výskyty chyb v různých požadavků.  
  
 Pro demonstraci použití přenosů [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md) ukázce aktivitu kalkulačky, který zapouzdřuje čtyři operace žádosti se také vytvoří. Pro každý požadavek je přenos vpřed a zpět z aktivity kalkulačky pro aktivitu žádosti o (trasování je zvýrazněn v horním pravém panelu na obrázku).  
  
 Když vyberete aktivitu na levém panelu, trasování, které jsou součástí této aktivity se zobrazí v pravém horním rohu panelu. Pokud `propagateActivity` je `true` na každý koncový bod na cestě k žádosti o trasování aktivity žádosti jsou od všech procesů, které jsou součástí požadavku. V tomto příkladu vidíte trasování od klienta a služby ve 4 sloupci na panelu.  
  
 Tato aktivita zobrazuje následující pořadí zpracování:  
  
1.  Klient odešle zprávu přidat.  
  
2.  Služba přijímá zprávy s požadavkem přidat.  
  
3.  Služba odešle odpověď přidat.  
  
4.  Klient obdrží odpověď přidat.  
  
 Toto trasování byly generované informace na úrovni. V pravém panelu kliknete na trasování v pravém panelu zobrazuje podrobnosti o tohoto trasování.  
  
 V následujícím diagramu vidíme také přenos trasování z a do aktivity kalkulačky, jakož i dvě dvojice spuštění a zastavení trasování za aktivitu žádosti o, jeden pro klienta a jeden pro službu (jeden pro každý zdroj trasování).  
  
 ![Prohlížeč trasování: Emitting User&#45;code traces](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Seznam aktivit ve čas vytvoření (levý panel) a jejich vnořené aktivity (pravém panelu)  
  
 Kód služby vyvolá výjimku, která způsobí, že klient má vyvolat také (například, když klient neobdržela odpověď na svou žádost), do stejné aktivity pro přímou spojitost s míněním dojít i služby a klient upozornění nebo chybové zprávy. V následujícím diagramu služba vyvolá výjimku, s oznámením "služba odmítne zpracovat tento požadavek v uživatelském kódu." Klient také vyvolá výjimku, s oznámením "server nemohl zpracovat požadavek, protože došlo k vnitřní chybě."  
  
 ![Použití prohlížeče trasování a vygenerovat uživatelské&#45;kódu trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Zobrazí chyby napříč koncovými body pro daný požadavek do aktivity, pokud byla rozšířena id aktivity požadavku  
  
 Dvojitým kliknutím vícenásobně aktivita na levém panelu se zobrazí následující graf s trasování vynásobit aktivity pro každý proces zahrnuté. Můžeme vidět, že nejprve vygenerováno upozornění na službu (vyvolána výjimka), který je následován upozornění a chyby v klientském počítači protože požadavek nelze zpracovat. Proto jsme neznamená příčinnou chyba vztah mezi koncovými body a odvodit hlavní příčinu chyby.  
  
 ![Použití prohlížeče trasování a vygenerovat uživatelské&#45;kódu trasování](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Zobrazení grafu chybě korelace  
  
 Získat předchozí trasování, jsme si nastavili `ActivityTracing` pro zdroje trasování uživatele a `propagateActivity=true` pro `System.ServiceModel` zdroje trasování. Jsme nenastavil `ActivityTracing` pro `System.ServiceModel` zdroj trasování umožňuje uživatelský kód pro šíření aktivity kódu uživatele. (Při trasování činnosti ServiceModel zapnutá, ID aktivity definované v klientovi se nerozšíří zcela do kódu uživatele služby; Přenosy, však korelovat klient a služba aktivit uživatelů, které kód intermediate aktivitám WCF.)  
  
 Definování aktivity změny a šíření ID aktivity umožňuje nám to provádět korelaci s přímým přístupem chyba napříč koncovými body. Tímto způsobem můžeme rychleji najít hlavní příčinu chyby.  
  
## <a name="see-also"></a>Viz také:
- [Rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md)
