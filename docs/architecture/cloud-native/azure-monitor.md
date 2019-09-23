---
title: Azure Monitor
description: Použití Azure Monitor k získání přehledu o tom, zda je systém spuštěný.
ms.date: 09/23/2019
ms.openlocfilehash: 89c27ffc3ba13194baf7b05e75920bf33dc6c5f3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183572"
---
# <a name="azure-monitor"></a>Azure Monitor 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Žádný jiný poskytovatel cloudu nemá k dispozici řešení monitorování cloudových aplikací, které najdete v Azure. Azure Monitor je zastřešující program pro kolekci nástrojů navržený tak, aby poskytoval přehled o stavu systému, přehledy o všech problémech a optimalizaci vaší aplikace. 

![Azure Monitor kolekce nástrojů, které poskytují přehled o fungování nativní aplikace cloudu. **Obrázek 7-9**. ](./media/azure-monitor.png)
 Azure Monitor kolekce nástrojů, které poskytují přehled o fungování nativní aplikace cloudu.

## <a name="gathering-logs-and-metrics"></a>Shromažďování protokolů a metrik

Prvním krokem v jakémkoli řešení monitorování je shromažďování co nejvíce dat. Víc dat, která se dají shromáždit, získáte hlubší přehledy, které je možné získat. Systémy instrumentace byly tradičně obtížné. Protokol SNMP (Simple Network Management Protocol) byl standardem Gold pro shromažďování informací na úrovni počítače, ale vyžadoval značnou znalost a konfiguraci. Naštěstí je mnoho z těchto pevných prací eliminováno, protože nejběžnější metriky se shromažďují automaticky pomocí Azure Monitor.

Metriky a události na úrovni aplikace nejsou možné automaticky instrumentovat, protože jsou místní pro nasazenou aplikaci. Aby bylo možné shromáždit tyto metriky, jsou [k dispozici sady SDK a rozhraní API](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) pro přímé hlášení takových informací, například když zákazník zaregistruje nebo dokončí objednávku. Výjimky lze také zachytit a nahlásit zpět do Azure Monitor prostřednictvím Application Insights. Sady SDK podporují většinu každého jazyka nalezeného v cloudových nativních aplikacích, včetně jazyků přejít, Python, JavaScript a .NET.

Konečným cílem shromažďování informací o stavu vaší aplikace je zajistit, aby koncoví uživatelé měli dobré zkušenosti. Jaký lepší způsob, jak zjistit, jestli se u uživatelů vyskytují problémy, než dělat [mimo jiné webové testy](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)? Tyto testy můžou být tak jednoduché jako při testování vašeho webu pomocí testu schůzek z umístění po celém světě, nebo v případě, že se agenti přihlašují k lokalitě a provádějí akce.

## <a name="reporting-data"></a>Data vytváření sestav

Jakmile budou data shromážděna, může být manipulována, shrnuta a vykreslena v grafech, což umožňuje uživatelům okamžitě zobrazit, kdy dojde k problémům. Tyto grafy je možné shromažďovat do řídicích panelů nebo do sešitů, což je vícestránkové sestava navržená tak, aby informovala o některých aspektech systému.

Žádná moderní aplikace by se nedokončila bez jakýchkoli umělých analytických funkcí nebo strojového učení. K tomuto účelu můžete data [předat](https://www.youtube.com/watch?v=Cuza-I1g9tw) do různých nástrojů pro strojové učení v Azure, aby bylo možné extrahovat trendy a informace, které by jinak byly skryté.

Application Insights poskytuje výkonný dotazovací jazyk s názvem Kusto, který se dá použít k hledání záznamů, jejich sumarizaci a dokonce i vykreslení grafů. Tento dotaz například vyhledá všechny záznamy za měsíc v listopadu 2007, seskupí je podle stavu a vykreslí horní 10 jako výsečový graf.

```
StormEvents 
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart 
```

![Výsledek](./media/azure-monitor.png)
**obrázku Application Insights obrázek 7-10**. Výsledek dotazu Application Insights.

K dispozici je [Playground pro experimentování s dotazy Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) , což je fantastická místo, které stráví hodinu nebo dvěma hodinami. Čtení [ukázkových dotazů](https://docs.microsoft.com/azure/kusto/query/samples) může být také poučené.

## <a name="dashboards"></a>Řídicí panely

K dispozici je několik různých technologií řídicích panelů, které lze použít k obplochy těchto informací z Azure Monitor. Nejjednodušším řešením je pouze spuštění dotazů v Application Insights a [vykreslení dat do grafu](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards). 

![Příklad Application Insights grafů vložených na hlavní řídicí panel](./media/azure-monitor.png)
Azure**Obrázek 7-11**. Příklad Application Insights grafů integrovaných v hlavním řídicím panelu Azure

Tyto grafy pak mohou být vloženy do Azure Portal správně prostřednictvím použití funkce řídicího panelu. Pro uživatele, kteří mají větší požadavky, jako je například schopnost přejít k podrobnostem o několika úrovních dat Azure Monitor dat, je k dispozici pro [Power BI](https://powerbi.microsoft.com/). Power BI je špičková podniková třída, která business intelligence nástroj, který může agregovat data z mnoha různých zdrojů dat.

![Například obrázek řídicího](./media/azure-monitor.png)
panelu Power BI**7-12**. Příklad Power BI řídicího panelu.

## <a name="alerts"></a>Upozornění

V některých případech nejsou data řídicích panelů dostatečná. Pokud nikdo nesleduje řídicí panely, může to být ještě mnoho hodin před adresováním problému nebo dokonce i zjištěným. K tomuto účelu Azure Monitor také nabízí [řešení upozornění](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)na nejvyšší stupeň. Výstrahy se můžou aktivovat v rámci široké škály podmínek, mezi které patří:

* Hodnoty metriky
* Dotazy na hledání v protokolu
* Události protokolu aktivit
* Stav základní platformy Azure
* Testy dostupnosti webu

Při aktivaci můžou výstrahy provádět nejrůznější úlohy. Na jednoduché straně můžou výstrahy jednoduše odeslat e-mailové oznámení do seznamu adresátů nebo textové zprávy pro jednotlivce. Další zahrnuté výstrahy můžou aktivovat pracovní postup v nástroji, jako je PagerDuty, který ví, kdo je na volání konkrétní aplikace. Výstrahy můžou aktivovat akce v [Microsoft Flow](https://flow.microsoft.com/) odemykání téměř omezených možností pro pracovní postupy.

Jak jsou zjištěny běžné příčiny výstrah, lze výstrahy zvýšit s podrobnostmi o běžných příčinách výstrah a krocích, které je třeba provést při jejich řešení. Vysoce vyspělá nasazení cloudových nativních aplikací se můžou rozhodnout, že se odeberou úlohy s automatickým opravou, které provádějí akce, jako je odebrání neúspěšných uzlů ze sady škálování nebo Aktivace aktivity automatického škálování. Nakonec už nemusí být nutné, aby se probudili zaměstnanci na 2AM, aby vyřešili problém s živým webem, protože systém se bude moct přizpůsobit na kompenzaci nebo aspoň Limp a až do chvíle, kdy někdo dorazí v práci na další ráno. 

Azure Monitor automaticky využívá Machine Learning k pochopení normálních provozních parametrů nasazených aplikací. Díky tomu je možné detekovat služby, které fungují mimo jejich normální parametry. Například typický provoz v týdnu v lokalitě může být 10 000 požadavků za minutu. A potom v daném týdnu náhle počet požadavků narazí na velmi neobvyklé 20 000 požadavků za minutu. [Inteligentní zjišťování](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) si všimněte odchylky od normy a aktivuje výstrahu. V současné době je analýza trendů dostatečně chytrá, aby nedocházelo k vypálení falešně pozitivních výsledků, když se očekává zatížení provozu.  

>[!div class="step-by-step"]
>[Předchozí](monitoring-azure-kubernetes.md)
>[Další](identity.md) <!-- Next Chapter -->
