---
title: Generování trasování v uživatelském kódu
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: e8b2031165a83e24ba15a2fcf847a170f47e696a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589289"
---
# <a name="emitting-user-code-traces"></a>Generování trasování v uživatelském kódu

Kromě povolení trasování v konfiguraci pro shromažďování dat instrumentace generovaných službou Windows Communication Foundation (WCF) můžete trasovat také programově v uživatelském kódu. Tímto způsobem můžete aktivně vytvořit data instrumentace, která můžete prohledat později za účelem diagnostiky. Toto téma popisuje, jak to můžete provést.

Kromě toho rozšiřující ukázka [trasování](../../samples/extending-tracing.md) zahrnuje veškerý kód, který je znázorněn v následujících oddílech.

## <a name="creating-a-trace-source"></a>Vytvoření zdroje trasování

K vytvoření zdroje trasování uživatele můžete použít následující kód.

```csharp
TraceSource ts = new TraceSource("myUserTraceSource");
```

## <a name="creating-activities"></a>Vytváření aktivit

Aktivity jsou logickou jednotkou zpracování. Můžete vytvořit jednu aktivitu pro každou hlavní jednotku zpracování, ve které chcete, aby se trasování seskupoval dohromady. Můžete například vytvořit jednu aktivitu pro každý požadavek na službu. Uděláte to tak, že provedete následující kroky.

1. Uložte ID aktivity v oboru.

2. Vytvoří nové ID aktivity.

3. Přeneste z aktivity z oboru do nové, nastavte novou aktivitu v oboru a vygenerujte pro tuto aktivitu počáteční trasování.

Následující kód ukazuje, jak to provést.

```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;
Guid traceID = Guid.NewGuid();
ts.TraceTransfer(0, "transfer", traceID);
Trace.CorrelationManager.ActivityId = traceID; // Trace is static
ts.TraceEvent(TraceEventType.Start, 0, "Add request");
```

## <a name="emitting-traces-within-a-user-activity"></a>Generování trasování v rámci aktivity uživatele

Následující kód vygeneruje trasování v rámci aktivity uživatele.

```csharp
double value1 = 100.00D;
double value2 = 15.99D;
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);
double result = client.Add(value1, value2);
ts.TraceInformation("Client receives Add response '" + result + "'");
```

## <a name="stopping-the-activities"></a>Zastavení aktivit

Chcete-li zastavit aktivity, přeneste zpět do původní aktivity, zastavte aktuální ID aktivity a obnovte staré ID aktivity v oboru.

Následující kód ukazuje, jak to provést.

```csharp
ts.TraceTransfer(0, "transfer", oldID);
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");
Trace.CorrelationManager.ActivityId = oldID;
```

## <a name="propagating-the-activity-id-to-a-service"></a>Šíření ID aktivity do služby

Nastavíte-li `propagateActivity` atribut pro `true` `System.ServiceModel` zdroj trasování v konfiguračních souborech klienta i služby, bude zpracování služby pro žádost o přidání provedeno ve stejné aktivitě jako ta, která je definována v klientovi. Pokud služba definuje své vlastní aktivity a převody, trasování služby se nezobrazí v aktivitě, která je šířena klientem. Místo toho se zobrazí v aktivitě korelace přenosu trasování do aktivity, jejíž ID je šířeno klientem.

> [!NOTE]
> Pokud `propagateActivity` je atribut nastavený na `true` jak u klienta, tak pro službu, aktivita okolí v oboru operace služby je nastavená službou WCF.

Pomocí následujícího kódu můžete ověřit, zda byla aktivita nastavena v oboru podle služby WCF.

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

## <a name="tracing-exceptions-thrown-in-code"></a>Trasování výjimek vyvolaných v kódu

Pokud vyvoláte výjimku v kódu, můžete také trasovat výjimku na úrovni upozornění nebo pomocí následujícího kódu.

```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");
```

## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Zobrazení trasování uživatele v nástroji Prohlížeč trasování služby

Tato část obsahuje snímky obrazovky vygenerované spuštěním rozšiřování ukázek [trasování](../../samples/extending-tracing.md) při prohlížení pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md).

V následujícím diagramu se na levém panelu vybere aktivita přidat žádost, kterou jste dříve vytvořili. Je uveden se třemi dalšími aktivitami matematické operace (dělení, odčítání, násobení), které tvoří klientský program aplikace. Uživatelský kód definoval jednu novou aktivitu pro každou operaci pro izolaci potenciálních výskytů chyb v různých požadavcích.

K demonstraci použití přenosů v ukázce [rozšíření trasování](../../samples/extending-tracing.md) se také vytvoří aktivita kalkulačky, která zapouzdřuje čtyři požadavky na operace. Pro každý požadavek se z aktivity kalkulačky přenáší do aktivity žádosti (trasování se zvýrazní v pravém horním panelu na obrázku).

Když vyberete aktivitu na levém panelu, zobrazí se v pravém horním panelu trasování zahrnuté v této aktivitě. Pokud `propagateActivity` je v `true` každém koncovém bodu v cestě požadavku, trasování v aktivitě požadavku jsou ze všech procesů, které se účastní žádosti. V tomto příkladu můžete vidět trasování z klienta i služby v 4 sloupci na panelu.

Tato aktivita zobrazuje následující pořadí zpracování:

1. Klient pošle zprávu k přidání.

2. Služba obdrží zprávu žádosti o přidání.

3. Služba odešle odpověď Add.

4. Klient obdrží odpověď Add.

Všechna tato trasování byla vygenerována na úrovni informací. Kliknutím na trasování v pravém horním panelu zobrazíte podrobnosti o tomto trasování v pravém dolním panelu.

V následujícím diagramu jsme také viděli přenos trasování z a do aktivity kalkulačky a také dvě dvojice spuštění a zastavení trasování na aktivitu žádosti, jednu pro klienta a jednu pro službu (jednu pro každý zdroj trasování).

![Prohlížeč trasování: generování trasování kódu&#45;uživatelů](media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd") Seznam aktivit podle času vytvoření (levý panel) a jejich vnořených aktivit (pravý horní panel)

Vyvolá-li kód služby výjimku, která způsobí, že se klient vyplní (například když klient neobdrží odpověď na svůj požadavek), dojde k chybě služby i klienta nebo k chybovým zprávám v rámci stejné aktivity pro přímou korelaci. Na následujícím obrázku služba vyvolá výjimku, která uvádí, že služba odmítá zpracovat tuto žádost v uživatelském kódu. Klient také vyvolá výjimku, která uvádí, že server nemohl zpracovat požadavek z důvodu vnitřní chyby. "

Následující obrázky ukazují, že chyby napříč koncovými body pro daný požadavek se zobrazí ve stejné aktivitě, pokud bylo ID aktivity žádosti rozšířeno:

![Snímek obrazovky, který zobrazuje chyby napříč koncovými body pro daný požadavek.](./media/emitting-user-code-traces/trace-viewer-endpoint-errors.gif)

Dvojím kliknutím na aktivitu vynásobení na levém panelu se zobrazí následující graf s trasováním pro aktivitu vynásobení pro každý proces, který je součástí procesu. Ve službě se zobrazí upozornění, že ve službě došlo k chybě (vyvolána výjimka), která následuje upozornění a chyby v klientovi, protože požadavek nebylo možné zpracovat. Proto můžeme znamenat příčinu chybového vztahu mezi koncovými body a odvodit původní příčinu chyby.

Následující obrázek znázorňuje zobrazení grafu korelace chyb:

![Snímek obrazovky znázorňující zobrazení grafu chyby korelace.](./media/emitting-user-code-traces/trace-viewer-error-correlation.gif)

Abychom získali předchozí trasování, nastavili jsme `ActivityTracing` pro zdroje trasování pro uživatele a `propagateActivity=true` pro `System.ServiceModel` zdroj trasování. `ActivityTracing`Pro zdroj trasování jsme nenastavili, `System.ServiceModel` aby se povolilo šíření aktivity uživatelského kódu. (Když je trasování aktivity ServiceModel on, ID aktivity definované v klientovi se nerozšíří všemi způsoby uživatelského kódu služby; Přenosy ale korelují aktivity uživatelského kódu klienta a služby s mezilehlými aktivitami WCF.)

Definování aktivit a šíření ID aktivity nám umožňuje provádět přímou korelaci chyb napříč koncovými body. Tímto způsobem můžeme najít hlavní příčinu chyby rychleji.

## <a name="see-also"></a>Viz také

- [Rozšíření trasování](../../samples/extending-tracing.md)
