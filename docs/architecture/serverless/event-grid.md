---
title: Aplikace bez serveru Azure Event Grid
description: Azure Event Grid je řešení bez serveru pro spolehlivé doručování událostí a směrování ve velkém měřítku na modelu plateb za jednotlivé události.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522714"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure/event-grid/overview) poskytuje infrastrukturu bez serveru pro aplikace založené na událostech. Můžete publikovat Event Grid z libovolného zdroje a využívat zprávy z libovolné platformy. Event Grid taky obsahuje integrovanou podporu pro události z prostředků Azure, které umožňují zjednodušit integraci s vašimi aplikacemi. Můžete se třeba přihlásit k odběru událostí služby Blob Storage, abyste aplikaci informovali o odeslání souboru. Vaše aplikace pak může publikovat vlastní zprávu o službě Event Grid, která je spotřebována jinými cloudem nebo místními aplikacemi. Event Grid byla sestavena tak, aby spolehlivě zpracovávala obrovské škálování. Získáte výhody publikování a odběru zpráv bez režie nastavování potřebné infrastruktury.

![Logo Event Grid](./media/event-grid-logo.png)

Mezi hlavní funkce Event gridu patří:

- Plně spravovaná směrování událostí.
- Doručování událostí téměř v reálném čase ve velkém měřítku.
- Široké pokrytí uvnitř i mimo Azure.

## <a name="scenarios"></a>Scénáře

Event Grid řeší několik různých scénářů. Tato část se věnuje třem nejběžnějším šablonám.

### <a name="ops-automation"></a>Automatizace operace

![Automatizace operace](./media/ops-automation.png)

Event Grid může pomáhat zrychlit automatizaci a zjednodušit vynucování zásad tím, že [Azure Automation](https://docs.microsoft.com/azure/automation) při zřizování infrastruktury.

### <a name="application-integration"></a>Integrace aplikací

![Integrace aplikací](./media/app-integration.png)

K připojení aplikace k jiným službám můžete použít Event Grid. Pomocí standardních protokolů HTTP můžete dokonce pro publikování Event Gridch zpráv snadno upravit i starší verze aplikací. Webhooky jsou k dispozici pro jiné služby a platformy pro využívání Event Gridch zpráv.

### <a name="serverless-apps"></a>Aplikace bez serveru

![Aplikace bez serveru](./media/serverless-apps.png)

Event Grid může aktivovat Azure Functions, Logic Apps nebo vlastní kód. Hlavní výhodou použití Event Grid je to, že používá mechanismus *push* k posílání zpráv, když dojde k událostem. Architektura nabízených oznámení spotřebovává méně prostředků a škáluje lepší než mechanizmy *dotazování* . Cyklické dotazování musí v pravidelných intervalech kontrolovat aktualizace.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid vs. další služby zasílání zpráv Azure

Azure poskytuje několik služeb zasílání zpráv, včetně [Event Hubs](https://docs.microsoft.com/azure/event-hubs) a [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging). Každá z nich je navržena tak, aby využívala konkrétní sadu případů použití. Následující diagram poskytuje podrobný přehled rozdílů mezi službami.

![Porovnání zasílání zpráv Azure](./media/azure-messaging-services.png)

Podrobnější porovnání najdete v tématu [porovnání služeb zasílání zpráv](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Cíle výkonnosti

Pomocí Event Grid můžete využít výhod následujících záruk výkonu:

- Koncová druhá sekunda v 99 percentilu.
- 99,99% dostupnost.
- 10 000 000 událostí za sekundu na oblast
- 100 000 000 předplatných na oblast
- 50 – latence MS Publisher
- 24 hodin opakování s exponenciálním zálohováním pro garantované doručení v rámci 1 dne.
- Transparentní místní převzetí služeb při selhání.

## <a name="event-grid-schema"></a>Event Grid schéma

Event Grid používá ke zalamování vlastních událostí standardní schéma. Schéma je jako obálka, která zabalí váš vlastní datový prvek. Tady je příklad Event Grid zpráva:

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

Vše o zprávě je Standard s výjimkou vlastnosti `data`. Můžete zkontrolovat zprávu a použít `eventType` a `dataVersion` k deserializaci vlastní části datové části.

## <a name="azure-resources"></a>Prostředky Azure

Hlavní výhodou použití Event Grid jsou automatické zprávy vytvořené v Azure. V Azure se prostředky automaticky publikují do *tématu* , které vám umožní přihlásit se k odběru různých událostí. V následující tabulce jsou uvedeny typy prostředků, typy zpráv a události, které jsou k dispozici automaticky.

| Prostředek Azure | Typ události | Popis |
| -------------- | ---------- | ----------- |
| Předplatné Azure | Microsoft. Resources. ResourceWriteSuccess | Vyvolá se, když je operace vytvoření nebo aktualizace prostředku úspěšná. |
| | Microsoft. Resources. ResourceWriteFailure | Vyvolá se v případě, že dojde k chybě operace vytvoření nebo aktualizace prostředku. |
| | Microsoft. Resources. ResourceWriteCancel | Vyvolá se při zrušení operace vytvoření nebo aktualizace prostředku. |
|  | Microsoft. Resources. ResourceDeleteSuccess | Vyvolá se, když je operace odstranění prostředku úspěšná. |
|  | Microsoft. Resources. ResourceDeleteFailure | Vyvolá se v případě, že dojde k chybě operace odstranění prostředku. |
| | Microsoft. Resources. ResourceDeleteCancel | Vyvolá se při zrušení operace odstranění prostředku. Tato událost nastane, když se zruší nasazení šablony. |
| Blob Storage | Microsoft. Storage. BlobCreated | Vyvolá se při vytvoření objektu BLOB. |
| | Microsoft. Storage. BlobDeleted | Vyvolá se při odstranění objektu BLOB. |
| Centra událostí | Microsoft. EventHub. CaptureFileCreated | Je aktivována při vytvoření sběrného souboru.
| IoT Hub | Microsoft. Devices. DeviceCreated | Publikováno, když je zařízení zaregistrované do služby IoT Hub. |
| | Microsoft. Devices. DeviceDeleted | Publikováno při odstranění zařízení ze služby IoT Hub. |
| Skupiny prostředků | Microsoft. Resources. ResourceWriteSuccess | Vyvolá se, když je operace vytvoření nebo aktualizace prostředku úspěšná. |
| | Microsoft. Resources. ResourceWriteFailure | Vyvolá se v případě, že dojde k chybě operace vytvoření nebo aktualizace prostředku. |
| | Microsoft. Resources. ResourceWriteCancel | Vyvolá se při zrušení operace vytvoření nebo aktualizace prostředku. |
| | Microsoft. Resources. ResourceDeleteSuccess | Vyvolá se, když je operace odstranění prostředku úspěšná. |
| | Microsoft. Resources. ResourceDeleteFailure | Vyvolá se v případě, že dojde k chybě operace odstranění prostředku. |
| | Microsoft. Resources. ResourceDeleteCancel | Vyvolá se při zrušení operace odstranění prostředku. Tato událost nastane, když se zruší nasazení šablony. |

Další informace najdete v tématu [Azure Event Grid schéma událostí](https://docs.microsoft.com/azure/event-grid/event-schema).

K Event Grid můžete přistupovat z libovolného typu aplikace, a to i v případě, že je místní.

## <a name="conclusion"></a>Závěr

V této kapitole jste se dozvěděli o platformě bez serveru Azure, která se skládá z Azure Functions, Logic Apps a Event Grid. Tyto prostředky můžete použít k vytvoření zcela nové architektury aplikace bez serveru nebo k vytvoření hybridního řešení, které komunikuje s dalšími cloudovým prostředkům a místními servery. V kombinaci s datovou platformou bez serveru, jako je [Azure SQL](https://docs.microsoft.com/azure/sql-database) nebo [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), můžete vytvářet plně spravované nativní cloudové aplikace.

## <a name="recommended-resources"></a>Doporučené prostředky

- [Plány služby App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Analýzy Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: přeneste svou aplikaci do cloudu pomocí Azure Functions bez serveru](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Grid schéma událostí](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Event Hubs Azure](https://docs.microsoft.com/azure/event-hubs)
- [Dokumentace k Azure Functions](https://docs.microsoft.com/azure/azure-functions)
- [Azure Functions triggery a koncepty vazeb](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Table Storage Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Porovnání funkcí 1. x a 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Připojení k místním zdrojům dat s místní bránou dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Vytvoření první funkce v Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Funkce podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Azure Functions monitorování](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Práce s Proxy služby Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Předchozí](logic-apps.md)
>[Další](durable-azure-functions.md)
