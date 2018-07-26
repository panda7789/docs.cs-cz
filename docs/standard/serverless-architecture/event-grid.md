---
title: Azure Event Grid - aplikace bez serveru
description: Azure Event Grid je řešení bez serveru pro spolehlivé doručování událostí a směrování ve velkém měřítku na model plateb za události.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b2507da61cbea3b4bdc51c6eecfe4d784737e924
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404903"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure-event-grid/overview) poskytuje infrastruktura bez serveru pro aplikace založené na událostech. Můžete publikovat do služby Event Grid z libovolného zdroje a využívat zprávy z libovolné platformy. Event Grid také obsahuje integrovanou podporu pro události z prostředků Azure, které zjednodušují integraci s vašimi aplikacemi. Například k odběru událostí služby blob storage k vaší aplikaci upozornění, když se nahraje soubor. Aplikace pak můžete publikovat zprávu mřížky vlastní událost, která je využívána jiných cloudových nebo místních aplikací. Event Grid byla založená, aby spolehlivě zpracovávat masivní škálování. Získáte výhody publikování a odběru zpráv bez režie nastavení potřebnou infrastrukturu.

![Event Grid logo](./media/event-grid-logo.png)

Mezi hlavní funkce služby event grid patří:

* Plně spravovaným směrováním událostí.
* Téměř doručování událostí v reálném čase ve velkém měřítku.
* Široký rozsah uvnitř i mimo Azure.

## <a name="scenarios"></a>Scénáře

Event Grid se zabývá několika různých scénářů. Tato část popisuje tři nejběžnější struktur.

### <a name="ops-automation"></a>Automatizace operací

![Automatizace operací](./media/ops-automation.png)

Event Grid můžete pomoct rychlost automatizace a zjednodušit vynucování zásad oznámením [Azure Automation](https://docs.microsoft.com/azure/automation) při zřízení infrastruktury.

### <a name="application-integration"></a>Integrace aplikací

![Integrace aplikací](./media/app-integration.png)

Event Grid můžete použít k připojení aplikace k jiným službám. Pomocí standardních protokolů HTTP, můžete snadno upravit i starší verze aplikací k publikování zpráv služby Event Grid. Webhooky jsou k dispozici pro další služby a platformy a využívat zprávy služby Event Grid.

### <a name="serverless-apps"></a>Aplikace bez serveru

![Aplikace bez serveru](./media/serverless-apps.png)

Event Grid můžete aktivovat Azure Functions, Logic Apps nebo vlastním kódem. Hlavní výhodou použití služby Event Grid je, že používá *nabízených* mechanismus pro odesílání zpráv při výskytu události. Architektura nabízených využívá méně prostředků a škáluje líp, než *dotazování* mechanismy. Dotazování musí vyhledat aktualizace v pravidelných intervalech.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid oproti jiným službám Azure zasílání zpráv

Azure poskytuje několik služeb zasílání zpráv, včetně [Event Hubs](https://docs.microsoft.com/azure/event-hubs) a [služby Service Bus](https://docs.microsoft.com/azure/service-bus-messaging). Každý se zaměřuje na konkrétní sadu případy použití řešení. Následující diagram představuje podrobný přehled rozdílů mezi službami.

![Porovnání zasílání zpráv Azure](./media/azure-messaging-services.png)

Podrobné porovnání najdete v tématu [porovnání služeb zasílání zpráv](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Cíle výkonnosti

Pomocí služby Event Grid můžete využít následující výkonu zaručuje:

* Subsecond latence začátku do konce v 99. percentilu.
* 99,99 % dostupnost.
* 10 milionů událostí za sekundu v jedné oblasti.
* 100 milionů předplatná v jedné oblasti.
* latence vydavatele 50 ms.
* 24 hodin opakování s exponenciální regresní pro garantované doručení v okně 1 den.
* Transparentní regionální převzetí služeb při selhání.

## <a name="event-grid-schema"></a>Schéma událostí mřížky

Event Grid používá standardní schéma zabalit vlastních událostí. Schéma je jako obálky, která obaluje vlastní datový prvek. Tady je ukázková zpráva služby Event Grid:

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

Všechno o zprávě je standard s výjimkou `data` vlastnost. Můžete zkontrolovat zprávy a použít `eventType` a `dataVersion` deserializovat vlastní část datové části.

## <a name="azure-resources"></a>Prostředky Azure

Hlavní výhodou použití služby Event Grid je automatické zprávy vytvořené službou Azure. V Azure, prostředky automaticky publikovat *tématu* , který umožňuje přihlášení odběru pro různé události. V následující tabulce jsou uvedeny typy prostředků, typy zpráv a události, které jsou k dispozici automaticky.

| Prostředek Azure | Typ události | Popis |
| -------------- | ---------- | ----------- |
| Předplatné Azure | Microsoft.Resources.ResourceWriteSuccess | Vyvoláno při prostředek vytvořit nebo aktualizovat operace proběhne úspěšně. |
| | Microsoft.Resources.ResourceWriteFailure | Vyvolá se při vytvoření prostředku nebo operace aktualizace se nezdaří. |
| | Microsoft.Resources.ResourceWriteCancel | Vyvoláno při prostředek vytvořit nebo aktualizovat operace se zrušila. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Vyvolá se při úspěšné operaci odstranění prostředku. |
|  | Microsoft.Resources.ResourceDeleteFailure | Vyvoláno, když selže operace odstranění prostředku. |
| | Microsoft.Resources.ResourceDeleteCancel | Vyvoláno, když je zrušena operace odstranění prostředku. Tato událost se stane, když se zruší nasazení šablony. |
| Úložiště objektů BLOB | Microsoft.Storage.BlobCreated | Vyvolá se při vytvoření objektu blob. |
| | Microsoft.Storage.BlobDeleted | Vyvolá se při odstranění objektu blob. |
| Služba Event hubs | Microsoft.EventHub.CaptureFileCreated | Vyvoláno, když se vytvoří zachytávací soubor.
| IoT Hub | Microsoft.Devices.DeviceCreated | Publikuje, když je zařízení zaregistrované do služby IoT hub. |
| | Microsoft.Devices.DeviceDeleted | Publikuje, když zařízení se odstraní ze služby IoT hub. |
| Skupiny prostředků | Microsoft.Resources.ResourceWriteSuccess | Vyvoláno při prostředek vytvořit nebo aktualizovat operace proběhne úspěšně. |
| | Microsoft.Resources.ResourceWriteFailure | Vyvolá se při vytvoření prostředku nebo operace aktualizace se nezdaří. |
| | Microsoft.Resources.ResourceWriteCancel | Vyvoláno při prostředek vytvořit nebo aktualizovat operace se zrušila. |
| | Microsoft.Resources.ResourceDeleteSuccess | Vyvolá se při úspěšné operaci odstranění prostředku. |
| | Microsoft.Resources.ResourceDeleteFailure | Vyvoláno, když selže operace odstranění prostředku. |
| | Microsoft.Resources.ResourceDeleteCancel | Vyvoláno, když je zrušena operace odstranění prostředku. Tato událost se stane, když se zruší nasazení šablony. |

Další informace najdete v tématu [schéma událostí služby Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

Event Grid můžete přistupovat z libovolného typu aplikace, ještě jeden, na kterém běží v místním.

## <a name="conclusion"></a>Závěr

V této kapitole jste se dozvěděli o platformě Azure bez serveru, který se skládá z Azure Functions, Logic Apps a služby Event Grid. Můžete tyto prostředky používat k vytváření architekturu aplikace úplně bez serveru, nebo vytvořte hybridní řešení, která komunikuje s další cloudové prostředky a místní servery. V kombinaci s využitím platformy bez serveru data jako například [Azure SQL](https://docs.microsoft.com/azure/sql-database) nebo [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), plně spravovaná Cloudová můžete vytvářet nativní aplikace.

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Plány služby App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Application Insights Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure: Přeneste svoje aplikace do cloudu s využitím Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure Event Grid](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [Schéma událostí služby Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
* [Dokumentace ke službě Azure Functions](https://docs.microsoft.com/azure/azure-functions)
* [Aktivace Azure Functions a vazby koncepty](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [Funkce porovnání 1.x a 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [Připojení k místním zdrojům dat s využitím Azure na místní bránu dat](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [Vytvoření první funkce na webu Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [Funkce podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [Monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [Práce s proxy služby Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
[Předchozí](logic-apps.md)
[další](durable-azure-functions.md)