---
title: Azure Monitor
description: Pomocí Azure Monitor uzískat přehled o vašem systému běží.
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805627"
---
# <a name="azure-monitor"></a>Azure Monitor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Žádný jiný poskytovatel cloudu nemá tak vyspělé řešení monitorování cloudových aplikací, jako je řešení v Azure. Azure Monitor je zastřešující název pro kolekci nástrojů navržených tak, aby poskytovaly přehled o stavu vašeho systému, přehled o všech problémech a optimalizaci vaší aplikace.

![Azure Monitor, kolekce nástrojů, které poskytují přehled o tom, jak funguje nativní aplikace cloudu. ](./media/azure-monitor.png)
 **Obrázek 7-12**. Azure Monitor, kolekce nástrojů, které poskytují přehled o tom, jak funguje nativní aplikace cloudu.

## <a name="gathering-logs-and-metrics"></a>Shromažďování protokolů a metrik

Prvním krokem v každém řešení monitorování je shromáždit co nejvíce dat. Čím více dat lze shromáždit, tím hlubší jsou poznatky, které lze získat. Přístrojové systémy byly tradičně obtížné. Simple Network Management Protocol (SNMP) byl zlatý standardní protokol pro sběr informací o úrovni stroje, ale vyžadoval velké množství znalostí a konfiguraci. Naštěstí velká část této tvrdé práce byla odstraněna jako nejběžnější metriky jsou shromažďovány automaticky Azure Monitor.

Metriky a události na úrovni aplikace není možné instrumentovat automaticky, protože jsou specifické pro aplikaci, která se nasazuje. Za účelem shromáždění těchto metrik jsou [k dispozici sady SDK a rozhraní API,](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) které přímo vykazují tyto informace, například když zákazník zaregistruje nebo dokončí objednávku. Výjimky můžete také zachytit a ohlásit zpět do Azure Monitor prostřednictvím Application Insights. Sady SDK podporují většinu všech jazyků nalezených v nativních aplikacích cloudu, včetně go, Pythonu, JavaScriptu a jazyků .NET.

Konečným cílem shromažďování informací o stavu vaší aplikace je zajistit, aby koncoví uživatelé měli dobré zkušenosti. Jaký lepší způsob, jak zjistit, zda uživatelé mají problémy, než dělat [mimo-v webových testů](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)? Tyto testy mohou být stejně jednoduché jako ping na vaše webové stránky z míst po celém světě, nebo jako s agenty přihlásit do webu a simulovat akce uživatelů.

## <a name="reporting-data"></a>Údaje z vykazování

Jakmile jsou data shromážděna, mohou být manipulována, shrnuta a vykreslena do grafů, které uživatelům umožňují okamžitě vidět, když se objeví problémy. Tyto grafy lze shromáždit do řídicích panelů nebo do sešitů, což je vícestránková sestava navržená tak, aby vyprávěla příběh o některých aspektech systému.

Žádná moderní aplikace by nebyla úplná bez umělé inteligence nebo strojového učení. Za tímto účelem mohou být data [předána](https://www.youtube.com/watch?v=Cuza-I1g9tw) různým nástrojům strojového učení v Azure, abyste mohli extrahovat trendy a informace, které by jinak byly skryté.

Application Insights poskytuje výkonný dotazovací jazyk s názvem Kusto, který lze použít k vyhledání záznamů, jejich shrnutí a dokonce i k vykreslení grafů. Tento dotaz například vyhledá všechny záznamy za měsíc listopad 2007, seskupí je podle státu a vykreslí prvních 10 jako výsečový graf.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![Výsledek obrázku dotazu](./media/azure-monitor.png)
Přehledy aplikací**7-13**. Výsledek application insights dotazu.

K dispozici je hřiště pro experimentování s dotazy [Kusto,](https://dataexplorer.azure.com/clusters/help/databases/Samples) což je fantastické místo, kde můžete strávit hodinu nebo dvě. Čtení [ukázkových dotazů](https://docs.microsoft.com/azure/kusto/query/samples) může být také poučné.

## <a name="dashboards"></a>Řídicí panely

Existuje několik různých řídicích paneltechnologií, které mohou být použity k zobrazení informací z Azure Monitoru. Možná nejjednodušší je jen spustit dotazy v Application Insights a [vykreslit data do grafu](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).

![Příklad grafů Application Insights vložených do](./media/azure-monitor.png)
hlavního obrázku řídicího panelu Azure**7-14**. Příklad grafů Application Insights vložených do hlavního řídicího panelu Azure.

Tyto grafy pak můžete vložit do webu Azure portal správné pomocí funkce řídicího panelu. Pro uživatele s náročnějšími požadavky, jako je možnost přejít k podrobnostem do několika úrovní dat, jsou data Azure Monitoru dostupná pro [Power BI](https://powerbi.microsoft.com/). Power BI je špičkový nástroj podnikové třídy business intelligence, který dokáže agregovat data z mnoha různých zdrojů dat.

![Příklad řídicího](./media/azure-monitor.png)
panelu Power BI**Obrázek 7-15**. Ukázkový řídicí panel Power BI.

## <a name="alerts"></a>Výstrahy

Někdy s řídicí panely dat je nedostatečná. Pokud nikdo není vzhůru sledovat řídicí panely, pak to může být ještě mnoho hodin, než je problém vyřešen, nebo dokonce zjištěna. Za tímto účelem Azure Monitor také poskytuje horní zářez [upozorňující řešení](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview). Výstrahy mohou být vyvolány širokou škálou podmínek, včetně:

- Hodnoty metriky
- Vyhledávací dotazy na protokoly
- Události protokolu aktivit
- Stav základní platformy Azure
- Testy dostupnosti webových stránek

Při aktivaci mohou výstrahy provádět širokou škálu úloh. Na jednoduché straně mohou upozornění odeslat e-mailové oznámení do seznamu adresátů nebo textovou zprávu jednotlivci. Další zapojené výstrahy může aktivovat pracovní postup v nástroji, jako je PagerDuty, který si je vědom toho, kdo je na volání pro konkrétní aplikaci. Výstrahy můžou aktivovat akce v [Microsoft Flow,](https://flow.microsoft.com/) které odemykají téměř neomezené možnosti pracovních postupů.

Jako běžné příčiny výstrahy jsou identifikovány, výstrahy mohou být rozšířeny s podrobnostmi o běžné příčiny výstrah a kroky k jejich vyřešení. Vysoce vyspělé nasazení aplikací nativní pro cloud se může rozhodnout zahájit úlohy samoopravitelnosti, které provádějí akce, jako je například odebrání neúspěšných uzlů ze škálovací sady nebo spuštění aktivity automatického škálování. Nakonec již nemusí být nutné probudit personál ve 2:00, aby vyřešil problém s živým místem, protože systém se bude moci přizpůsobit kompenzaci nebo alespoň kulhat, dokud někdo nepřijde do práce druhý den ráno.

Azure Monitor automaticky využívá strojové učení k pochopení běžných provozních parametrů nasazených aplikací. To umožňuje zjistit služby, které pracují mimo jejich normální parametry. Například typický provoz ve všední den na webu může být 10 000 požadavků za minutu. A pak, v daném týdnu, najednou počet žádostí zasáhne velmi neobvyklé 20.000 žádostí za minutu. [Inteligentní detekce](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) si všimne této odchylky od normy a spustí výstrahu. Současně je analýza trendů dostatečně chytrá, aby se vyhnula spouštění falešných poplachů, když se očekává zatížení provozu.

## <a name="references"></a>Odkazy

- [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Předchozí](monitoring-azure-kubernetes.md)
>[další](identity.md)
