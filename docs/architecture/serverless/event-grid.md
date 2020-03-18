---
title: Azure Event Grid – aplikace bez serveru
description: Azure Event Grid je bezserverové řešení pro spolehlivé doručování událostí a směrování v masivním měřítku na modelu pay-per-event.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522714"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) poskytuje bezserverovou infrastrukturu pro aplikace založené na událostech. Můžete publikovat do event gridu z libovolného zdroje a využívat zprávy z libovolné platformy. Event Grid má také integrovanou podporu událostí z prostředků Azure pro zjednodušení integrace s vašimi aplikacemi. Můžete se například přihlásit k odběru událostí úložiště objektů blob a upozornit aplikaci při nahrání souboru. Vaše aplikace pak můžete publikovat vlastní zprávy mřížky událostí, která je spotřebována jinými cloudovými nebo místními aplikacemi. Event Grid byl postaven tak, aby spolehlivě zvládl masivní měřítko. Získáte výhody publikování a přihlášení k odběru zpráv bez režie nastavení potřebné infrastruktury.

![Logo Event Grid](./media/event-grid-logo.png)

Mezi hlavní rysy mřížky událostí patří:

- Plně spravované směrování událostí.
- Téměř doručení událostí v reálném čase ve velkém měřítku.
- Široké pokrytí uvnitř i vně Azure.

## <a name="scenarios"></a>Scénáře

Event Grid řeší několik různých scénářů. Tato část se týká tří nejběžnějších.

### <a name="ops-automation"></a>Automatizace operací

![Automatizace operací](./media/ops-automation.png)

Event Grid může pomoci urychlit automatizaci a zjednodušit vynucení zásad tím, že upozorní [Azure Automation,](https://docs.microsoft.com/azure/automation) když je zřízena infrastruktura.

### <a name="application-integration"></a>Integrace aplikací

![Integrace aplikací](./media/app-integration.png)

Pomocí služby Event Grid můžete aplikaci připojit k jiným službám. Pomocí standardních protokolů HTTP lze i starší aplikace snadno upravit tak, aby mohly publikovat zprávy v síti událostí. Webové háčky jsou k dispozici pro další služby a platformy využívat zprávy mřížky událostí.

### <a name="serverless-apps"></a>Aplikace bez serveru

![Aplikace bez serveru](./media/serverless-apps.png)

Event Grid může aktivovat Funkce Azure, Logic Apps nebo vlastní kód. Hlavní výhodou použití Event Grid je, že používá *mechanismus push* k odesílání zpráv, když dojde k událostem. Push architektura spotřebovává méně prostředků a škálování lepší než *mechanismy dotazování.* Dotazování musí kontrolovat aktualizace v pravidelných intervalech.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid vs. ostatní služby zasílání zpráv Azure

Azure poskytuje několik služeb zasílání zpráv, včetně [event hubů](https://docs.microsoft.com/azure/event-hubs) a [service bus](https://docs.microsoft.com/azure/service-bus-messaging). Každý z nich je určen k řešení konkrétní sadu případů použití. Následující diagram poskytuje přehled na vysoké úrovni o rozdílech mezi službami.

![Porovnání zpráv Azure](./media/azure-messaging-services.png)

Podrobnější porovnání naleznete v tématu [Porovnání služeb zasílání zpráv](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Výkonnostní cíle

Pomocí funkce Event Grid můžete využít následující záruky výkonu:

- Latence od konce na konec v percentilu 99.
- 99,99 % dostupnost.
- 10 milionů událostí za sekundu za region.
- 100 milionů předplatných na region.
- Latence vydavatele 50 ms.
- 24hodinová retry s exponenciálním back-offem pro zaručené doručení v 1denním okně.
- Transparentní regionální převzetí služeb při selhání.

## <a name="event-grid-schema"></a>Schéma služby Event Grid

Event Grid používá standardní schéma k zabalení vlastních událostí. Schéma je jako obálka, která zabalí vlastní datový prvek. Zde je příklad zprávy Mřížka událostí:

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

Vše o zprávě je `data` standardní kromě vlastnosti. Můžete zkontrolovat zprávu a `eventType` použít `dataVersion` a de-serializovat vlastní část datové části.

## <a name="azure-resources"></a>Prostředky Azure

Hlavní výhodou použití Event Grid je automatické zprávy vytvořené Azure. V Azure se prostředky automaticky publikují na *téma,* které vám umožní přihlásit se k odběru různých událostí. V následující tabulce jsou uvedeny typy prostředků, typy zpráv a události, které jsou k dispozici automaticky.

| Prostředek Azure | Typ události | Popis |
| -------------- | ---------- | ----------- |
| Předplatné Azure | Microsoft.Resources.ResourceWriteSuccess | Je aktivována, když je operace vytvoření nebo aktualizace prostředku úspěšná. |
| | Microsoft.Resources.ResourceWriteFailure | Je aktivována, když se nezdaří operace vytvoření nebo aktualizace prostředku. |
| | Microsoft.Resources.ResourceWriteCancel | Je aktivována při zrušení operace vytvoření nebo aktualizace prostředku. |
|  | Microsoft.Resources.ResourcesDeleteÚspěch | Je aktivována, když je operace odstranění prostředku úspěšná. |
|  | Microsoft.Resources.ResourcesDeleteSelhání | Je aktivována, když se nezdaří operace odstranění prostředku. |
| | Microsoft.Resources.ResourcesDeleteCancel | Je aktivována při zrušení operace odstranění prostředku. K této události dojde, když je nasazení šablony zrušeno. |
| Blob Storage | Microsoft.Storage.BlobVytvořeno | Vyvěšené při vytvoření objektu blob. |
| | Soubor Microsoft.Storage.BlobOdstraněn | Vyvěšené při odstranění objektu blob. |
| Event Hubs | Microsoft.EventHub.CaptureFileCreated | Je aktivována při vytvoření souboru sběru.
| IoT Hub | Microsoft.Devices.DeviceVytvořeno | Publikováno, když je zařízení registrované do centra IoT. |
| | Microsoft.Devices.DeviceOdstraněno | Publikováno při odstranění zařízení z centra IoT. |
| Skupiny prostředků | Microsoft.Resources.ResourceWriteSuccess | Je aktivována, když je operace vytvoření nebo aktualizace prostředku úspěšná. |
| | Microsoft.Resources.ResourceWriteFailure | Je aktivována, když se nezdaří operace vytvoření nebo aktualizace prostředku. |
| | Microsoft.Resources.ResourceWriteCancel | Je aktivována při zrušení operace vytvoření nebo aktualizace prostředku. |
| | Microsoft.Resources.ResourcesDeleteÚspěch | Je aktivována, když je operace odstranění prostředku úspěšná. |
| | Microsoft.Resources.ResourcesDeleteSelhání | Je aktivována, když se nezdaří operace odstranění prostředku. |
| | Microsoft.Resources.ResourcesDeleteCancel | Je aktivována při zrušení operace odstranění prostředku. K této události dojde, když je nasazení šablony zrušeno. |

Další informace najdete v [tématu Schéma událostí služby Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

K event gridu můžete přistupovat z libovolného typu aplikace, dokonce i z té, která běží místně.

## <a name="conclusion"></a>Závěr

V této kapitole jste se dozvěděli o platformě Azure bez serveru, která se skládá z Azure Functions, Logic Apps a Event Grid. Tyto prostředky můžete použít k vytvoření architektury aplikací zcela bez serveru nebo k vytvoření hybridního řešení, které spolupracuje s jinými cloudovými prostředky a místními servery. V kombinaci s datovou platformou bez serveru, jako je [Azure SQL](https://docs.microsoft.com/azure/sql-database) nebo [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), můžete vytvářet plně spravované cloudové nativní aplikace.

## <a name="recommended-resources"></a>Doporučené zdroje

- [Plány služeb aplikace](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Analýza přehledů aplikací](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: Přeneste svou aplikaci do cloudu pomocí funkcí Azure bez serveru](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Schéma událostí sítě Azure](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Centra událostí Azure](https://docs.microsoft.com/azure/event-hubs)
- [Dokumentace ke službě Azure Functions](https://docs.microsoft.com/azure/azure-functions)
- [Azure Functions spouští a vázací koncepty](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Porovnání funkcí 1.x a 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Připojení k místním zdrojům dat s využitím místní brány dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Vytvoření první funkce na webu Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Práce s Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Předchozí](logic-apps.md)
>[další](durable-azure-functions.md)
