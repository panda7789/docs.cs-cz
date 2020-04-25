---
title: Ukázkové obchodní scénáře a případy použití pro aplikace bez serveru
description: Přístup k ukázkám, které jsou v rozsahu od zpracování obrazu až po mobilní kanály a kanály ETL, se naučíte bez serveru s praktickým přístupem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 3cb3b73325fccc327ccf17f7298048f2eeb3577a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158447"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Obchodní scénáře aplikací bez serveru a případy použití

K dispozici je mnoho případů použití a scénářů pro aplikace bez serveru. Tato kapitola obsahuje ukázky, které ilustrují různé scénáře. Scénáře obsahují odkazy na související dokumentaci a veřejné úložiště zdrojového kódu. Ukázky v této kapitole vám umožní začít pracovat s vlastními vytvářením a implementací řešení bez serveru.

## <a name="big-data-processing"></a>Zpracování velkých objemů dat

![Mapování/zmenšení diagramu](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

V tomto příkladu se používá bez serveru k provedení operace mapování/zmenšování pro sadu velkých objemů dat. Určuje průměrnou rychlost New York Yellow taxislužby TRIPS za den v 2017.

[Zpracování velkých objemů dat: MapReduce bez serveru v Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a>Vytváření aplikací bez serveru: praktická cvičení

Naučte se používat funkce pro spouštění logiky na straně serveru a vytváření architektur bez serveru.

- Výběr nejlepší služby Azure pro vaši firmu
- Vytváření Azure Functions
- Používání triggerů
- Funkce zřetězení
- Dlouhotrvající pracovní postupy
- Monitorování
- Vývoj, testování a nasazení

[Vytváření aplikací bez serveru](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a>Recenze zákazníků

Tato ukázka předvádí nové nástroje Azure Functions pro knihovny tříd jazyka C# v aplikaci Visual Studio. Vytvořte web, kde zákazníci odesílají recenze produktů uložené v Azure Storage BLOBs a CosmosDB. Přidejte funkci Azure, která umožňuje automatizované moderování revizí zákazníka pomocí Cognitive Services Azure. Použijte frontu úložiště Azure k oddělení webu od funkce.

[Aplikace pro revize zákazníků pomocí Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a>Podpora imagí Docker Linux

Tato ukázka demonstruje, jak `Dockerfile` vytvořit a spustit Azure Functions v kontejneru Linux Docker.

[Azure Functions v systému Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a>Zpracování a ověřování souborů

Tento příklad analyzuje sadu souborů CSV od hypotetických zákazníků. Zajišťuje připravenost všech souborů požadovaných pro zákazníka "Batch" a potom ověří strukturu každého souboru. Různá řešení se zobrazují pomocí Azure Functions, Logic Apps a Durable Functions.

[Zpracování a ověřování souborů pomocí Azure Functions, Logic Apps a Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a>Vizualizace herních dat

![Telemetrie her](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

Příklad, jak vývojář může implementovat řešení vizualizace dat v editoru pro svou hru. Ve skutečnosti se modul plug-in a modul plug-in Unreal Engine vyvinul pomocí této ukázky jako jeho back-end. Součást služby je nezávislá herního stroje.

[Vizualizace telemetrie her v editoru](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a>GraphQL

Vytvořte funkci bez serveru, která zpřístupňuje rozhraní GraphQL API.

[Funkce bez serveru pro GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a>Spolehlivý hraniční přenos Internet věcí (IoT)

![Architektura IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

Tato ukázka implementuje nový komunikační protokol, který umožňuje spolehlivou komunikaci ze zařízení IoT. Automatizuje detekci a zpětnou výplň datových mezer.

[IoT Reliable Edge Relay](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a>Referenční architektura mikroslužeb

![Referenční architektura](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

Referenční architektura, která vás provede procesem rozhodování, který se zabývá návrhem, vývojem a poskytováním RideShare aplikací Relecloud (fiktivní společnost). Obsahuje praktické pokyny ke konfiguraci a nasazení všech komponent architektury.

[Referenční architektura mikroslužeb bez serveru](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a>Migrace konzolových aplikací na bez serveru

Tato ukázka je obecná funkce (`.csx` soubor), která se dá použít k převedení jakékoli konzolové aplikace na webovou službu HTTP v Azure Functions. Vše, co musíte udělat, je upravit konfigurační soubor a určit, jaké vstupní parametry se budou předávat jako argumenty `.exe`do.

[Spouštění konzolových aplikací v Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a>Bez serveru pro mobilní zařízení

Azure Functions lze snadno implementovat a udržovat a přistupovat prostřednictvím protokolu HTTP. Jsou skvělým způsobem, jak implementovat rozhraní API pro mobilní aplikace. Microsoft nabízí skvělé nástroje pro více platforem pro iOS, Android a Windows s využitím Xamarin. V takovém případě Xamarin a Azure Functions fungují skvěle společně. Tento článek ukazuje, jak implementovat funkci Azure Functions v Azure Portal nebo v aplikaci Visual Studio poprvé a vytvořit klienta pro různé platformy pomocí Xamarin. Forms běžící v Androidu, iOS a Windows.

[Implementace jednoduché funkce Azure Functions s klientem Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a>Zasílání zpráv bez serveru

V této ukázce se dozvíte, jak použít Durable Functions vzorek ventilátoru pro načtení libovolného počtu zpráv v rámci libovolného počtu relací nebo oddílů. Cílí na Service Bus, Event Hubs nebo fronty úložiště. Ukázka také přidává možnost využít tyto zprávy s jinou funkcí Azure a načíst výsledná časová data do jiného centra událostí. Data se pak ingestují do analytických služeb, jako je Azure Průzkumník dat.

[Vytváření a využívání zpráv prostřednictvím Service Bus, Event Hubs a front úložiště s Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a>Doporučené prostředky

- [Azure Functions v systému Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [Zpracování velkých objemů dat: MapReduce bez serveru v Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [Vytváření aplikací bez serveru](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [Aplikace pro revize zákazníků pomocí Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [Zpracování a ověřování souborů pomocí Azure Functions, Logic Apps a Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [Implementace jednoduché funkce Azure Functions s klientem Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Vizualizace telemetrie her v editoru](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [IoT Reliable Edge Relay](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [Vytváření a využívání zpráv prostřednictvím Service Bus, Event Hubs a front úložiště s Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [Spouštění konzolových aplikací v Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [Funkce bez serveru pro GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [Referenční architektura mikroslužeb bez serveru](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
>[Předchozí](orchestration-patterns.md)
>[Další](serverless-conclusion.md)
