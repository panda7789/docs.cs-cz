---
title: Použití jazyka F# v Azure
description: 'Příručka k používání služeb Azure s jazykem F #'
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 1fbb85a07fc057c1b89a4c4a1ad356066cebf2b8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50201501"
---
# <a name="using-f-on-azure"></a>Použití jazyka F# v Azure

F # je vynikající jazyk pro programování v cloudu a se často používá k zápisu webové aplikace, cloudové služby, mikroslužby hostované v cloudu a pro škálovatelné zpracování dat.

V následujících částech najdete prostředky, jak používat škálu služeb Azure s jazykem F #.

> [!NOTE]
> Pokud konkrétní službu Azure není v této sadě dokumentace, najdete dokumentaci k Azure Functions nebo .NET za danou službu. Některé služby Azure jsou jazykově nezávislé a vyžadovat žádná dokumentace specifické pro jazyk a zde nejsou uvedeny.

## <a name="using-azure-virtual-machines-with-f"></a>Pomocí Azure Virtual Machines s jazykem F # #

Azure podporuje širokou škálu konfigurací virtuálních počítačů (VM) naleznete v tématu [virtuální počítače Azure s Linuxem a](https://azure.microsoft.com/services/virtual-machines/).

K instalaci F # na virtuální počítač pro spuštění, kompilace a/nebo skriptování viz [pomocí F # v Linuxu](https://fsharp.org/use/linux) a [pomocí F # ve Windows](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Pomocí Azure Functions s jazykem F # #

[Služba Azure Functions](https://azure.microsoft.com/services/functions/) je řešení umožňující snadno spouštět malé části kódu, nebo "funkce" v cloudu. Můžete napsat přesně takový kód, které potřebujete pro problém aktuální, aniž byste se museli starat o infrastrukturu nebo aplikaci jako celek, ho spustit. Vaše funkce jsou připojené k události v Azure storage a dalším prostředkům hostované v cloudu. Data budou téci do funkce F # prostřednictvím argumentů funkce. Můžete použít vývoj jazyk podle vlastní volby, důvěřující Azure ke škálování podle potřeby.

Služba Azure Functions podporují F # jako prvotřídní jazyk v efektivní, reaktivní a škálovatelná provádění kódu jazyka F #. Zobrazit [Azure Functions F # referenční informace pro vývojáře](/azure/azure-functions/functions-reference-fsharp) referenční dokumentaci, jak používat F # s využitím Azure Functions.

Další materiály týkající se používání Azure Functions a F #:

* [Vertikální navýšení kapacity Azure Functions v F # s použitím Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Jak vytvořit funkci Azure v jazyce F #](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Pomocí zprostředkovatele typu Azure s využitím Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Použití služby Azure Storage s jazykem F # #

Azure Storage je základní vrstvě služby úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost podle potřeb zákazníků. F#programy můžou pracovat přímo s služby Azure storage, pomocí technik popsaných v následujících článcích.

* [Začínáme s Azure Blob Storage s využitím F#](blob-storage.md)
* [Začínáme s Azure File Storage s využitím F#](file-storage.md)
* [Začínáme s Azure Queue Storage s využitím F#](queue-storage.md)
* [Začínáme s Azure Table Storage s využitím F#](table-storage.md)

Úložiště Azure je také možné ve spojení s využitím Azure Functions prostřednictvím deklarativních místo explicitního volání rozhraní API. Zobrazit [aktivační události Azure Functions a vazby pro službu Azure Storage](/azure/azure-functions/functions-bindings-storage) což zahrnuje příklady F #.

## <a name="using-azure-app-service-with-f"></a>Pomocí služby Azure App Service s jazykem F # #

[Azure App Service](https://azure.microsoft.com/services/app-service/) je cloudovou platformou můžete tvořit výkonné webové a mobilní aplikace, které se připojují k datům bez ohledu na, v cloudu nebo místně.

* [Příklad F # webové rozhraní API služby Azure](https://github.com/fsprojects/azure-webapi-example)
* [Hostování F # ve webové aplikaci v Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Pomocí Apache Sparku s jazykem F # s Azure HDInsight

[Apache Spark pro Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) je zpracování opensourcové rozhraní, na kterém běží velkých objemů dat analytických aplikací. Azure vám umožní Apache Sparku jednoduché a nákladově efektivní nasazení. Vývoj aplikace Spark v F # pomocí [Mobius](https://github.com/Microsoft/Mobius), rozhraní .NET API pro Spark.

* [Implementace aplikací Apache Spark v F # s použitím Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Příklad F # Spark aplikace s využitím Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Pomocí služby Azure Cosmos DB pomocí jazyka F # #

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) je služba typu NoSQL pro vysoce dostupnou a globálně distribuované aplikace.

Azure Cosmos DB je možné s jazykem F # dvěma způsoby:

1. Prostřednictvím vytváření sad funkcí Azure F # které reakce na ně nebo způsobit změny v kolekcích Azure Cosmos DB. Zobrazit [vazby Azure Cosmos DB pro službu Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), nebo
2. S použitím [Azure Cosmos DB .NET SDK pro rozhraní SQL API](/azure/cosmos-db/sql-api-sdk-dotnet). Související ukázky jsou v jazyce C#.

## <a name="using-azure-event-hubs-with-f"></a>Pomocí služby Azure Event Hubs s jazykem F # #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) poskytnout cloudového škálovatelného ingestování telemetrických údajů z webů, aplikací a zařízení.

Azure Event Hubs je možné s jazykem F # dvěma způsoby:

1. Prostřednictvím vytváření sad funkcí F # Azure, které jsou aktivovány události. Zobrazit [aktivuje funkce Azure Functions pro službu Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), nebo
2. S použitím [sady .NET SDK pro Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="using-azure-notification-hubs-with-f"></a>Pomocí Azure Notification Hubs s jazykem F # #

[Azure Notification Hubs](/azure/notification-hubs/) jsou multiplatformní a horizontálně škálovanou infrastrukturu, která vám umožní odesílat mobilní nabízená oznámení z jakéhokoli back-endu (v cloudu nebo místně) na libovolnou mobilní platformu.

Azure Notification Hubs je možné s jazykem F # dvěma způsoby:

1. Prostřednictvím vytváření sad funkcí Azure F # který odeslat výsledky do centra oznámení. Zobrazit [funkce Azure Functions výstup aktivační události pro Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), nebo
2. S použitím [sady .NET SDK pro Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Všimněte si, že tyto příklady jsou v jazyce C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementace Webhooky v Azure pomocí jazyka F # #

A [Webhooku](https://en.wikipedia.org/wiki/Webhook) se spouští přes webový požadavek zpětného volání. Webhooky jsou používány webů, jako je GitHub na signál události. 

Webhooky mohou být implementována v jazyce F # a hostované v Azure prostřednictvím [funkce Azure Functions v jazyce F # s Webhooku vazby](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Pomocí Webjobs pomocí jazyka F # #

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) jsou programy, které můžete spustit ve webové aplikaci App Service třemi způsoby: na požádání, průběžně nebo podle plánu.

[Příklad F # webové úlohy](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementace časovače v Azure pomocí jazyka F # #

Časovač spustí podle plánu, jednou nebo opakovaně funkce volání.

Časovače mohou být implementována v jazyce F # a hostované v Azure prostřednictvím [funkce Azure Functions v jazyce F # s triggerem Timer](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Nasazení a správě prostředků Azure pomocí skripty jazyka F # #

Virtuální počítače Azure mohou možné prostřednictvím kódu programu nasadit a spravovat z skripty jazyka F # s použitím rozhraní API a Microsoft.Azure.Management balíčky. Viz například [začít pracovat s knihovnami správy pro .NET](https://msdn.microsoft.com/library/dn722415.aspx) a [pomocí Azure Resource Manageru](/azure/azure-resource-manager/resource-manager-deployment-model).

Další prostředky Azure, také mohou možné nasadit a spravovat z skripty jazyka F # pomocí stejné komponenty. Můžete například vytvořit účty úložiště, nasazení Azure Cloud Services, vytváření instancí služby Azure Cosmos DB a spravovat centra oznámení Azure prostřednictvím kódu programu z skripty jazyka F #.

Použití skripty jazyka F # k nasazení a Správa prostředků není obvykle nutné. Prostředky Azure například může být nasazený přímo z popisů šablony JSON, které mohou být parametrizovány. V tématu [šablon Azure Resource Manageru](/azure/azure-resource-manager/resource-manager-template-best-practices) včetně příkladů, jako [šablony pro rychlý start Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Další zdroje

* [Úplnou dokumentaci ke všem službám Azure](/azure/)
