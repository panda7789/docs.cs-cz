---
title: Použití jazyka F# v Azure
description: Průvodce používáním služeb Azure sF#
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 6cf2951092074a7fab6707c8ed26bda125ea00b0
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935534"
---
# <a name="using-f-on-azure"></a>Použití jazyka F# v Azure

F#je vynikajícím jazykem pro cloudové programování a často se používá k psaní webových aplikací, cloudových služeb, mikroslužeb hostovaných v cloudu a pro škálovatelné zpracování dat.

V následujících částech najdete zdroje informací o tom, jak používat řadu služeb Azure s nástrojem F#.

> [!NOTE]
> Pokud v této sadě dokumentace není konkrétní služba Azure, vyhledejte ji prosím v dokumentaci Azure Functions nebo .NET této služby. Některé služby Azure jsou nezávislé na jazyce a nevyžadují žádnou dokumentaci specifickou pro konkrétní jazyk a nejsou tady uvedené.

## <a name="using-azure-virtual-machines-with-f"></a>Použití Azure Virtual Machines s F\#

Azure podporuje rozsáhlou škálu konfigurací virtuálních počítačů, viz [Linux a Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).

Pro instalaci F# na virtuální počítač pro spuštění, kompilaci nebo skriptování viz [ F# použití v systému Linux](https://fsharp.org/use/linux) a [ F# použití ve Windows](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Použití Azure Functions s F\#

[Azure Functions](https://azure.microsoft.com/services/functions/) je řešení pro snadné spouštění malých částí kódu nebo "Functions" v cloudu. Můžete napsat přesně takový kód, jaký potřebujete pro aktuální problém, a nestarat se o infrastrukturu k jeho spuštění nebo aplikaci jako celek. Vaše funkce jsou připojené k událostem v Azure Storage a dalších prostředcích hostovaných v cloudu. Data se do vašich F# funkcí zatoků pomocí argumentů funkce. Můžete použít svůj vývojářský jazyk podle vlastního výběru, který je důvěryhodný pro Azure ke škálování podle potřeby.

Azure Functions podporu F# jako prvotřídní jazyk s efektivním, reaktivním a škálovatelným spouštěním F# kódu. Referenční dokumentaci týkající se použití F# s Azure Functions najdete v [referenčních informacích pro vývojáře Azure Functions F# ](/azure/azure-functions/functions-reference-fsharp) .

Další zdroje informací pro použití Azure Functions F#a:

* [Horizontální navýšení F# kapacity Azure Functions pomocí Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Jak vytvořit funkci Azure Functions vF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Použití poskytovatele typu Azure s Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Použití Azure Storage s F\#

Azure Storage je základní vrstvou služeb úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost, aby splňovaly potřeby zákazníků. F#programy můžou komunikovat přímo se službami Azure Storage pomocí technik popsaných v následujících článcích.

* [Začínáme s Azure Blob Storage s využitím F#](blob-storage.md)
* [Začínáme s Azure File Storage s využitím F#](file-storage.md)
* [Začínáme s Azure Queue Storage s využitím F#](queue-storage.md)
* [Začínáme s Azure Table Storage s využitím F#](table-storage.md)

Azure Storage lze také použít ve spojení s Azure Functions prostřednictvím deklarativní konfigurace namísto explicitního volání rozhraní API. Další informace najdete v tématu [Azure Functions triggery a vazby pro Azure Storage](/azure/azure-functions/functions-bindings-storage) obsahující F# příklady.

## <a name="using-azure-app-service-with-f"></a>Použití Azure App Service s F\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) je cloudová platforma pro vytváření výkonných webových a mobilních aplikací, které se připojují k datům kdekoli, v cloudu i v místním prostředí.

* [F#Příklad webového rozhraní API Azure](https://github.com/fsprojects/azure-webapi-example)
* [Hostování F# ve webové aplikaci v Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Použití Apache Spark s F# Azure HDInsight

[Apache Spark pro Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) je open source platforma pro zpracování, která spouští rozsáhlé aplikace pro analýzu dat. Azure přináší Apache Spark snadný a nákladově efektivní nasazení. Vývoj aplikace Spark v F# systému pomocí [Mobius](https://github.com/Microsoft/Mobius), rozhraní .NET API pro Spark.

* [Implementace aplikací Spark v F# systému pomocí Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Příklady F# aplikací Spark s použitím Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Použití Azure Cosmos DB s F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) je služba NoSQL pro vysoce dostupné a globálně distribuované aplikace.

Azure Cosmos DB lze použít F# dvěma způsoby:

1. Vytvořením F# Azure Functions, které reagují na nebo způsobují změny v kolekcích Azure Cosmos DB. Viz [Azure Cosmos DB vazby pro Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb)nebo
2. Pomocí [sady Azure Cosmos DB .NET SDK pro rozhraní SQL API](/azure/cosmos-db/sql-api-sdk-dotnet). Související ukázky jsou v C#.

## <a name="using-azure-event-hubs-with-f"></a>Použití Azure Event Hubs s F\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) poskytují ingestování telemetrie na úrovni cloudu z webů, aplikací a zařízení.

Službu Azure Event Hubs lze použít F# dvěma způsoby:

1. Vytvořením F# Azure Functions, které jsou aktivovány událostmi. Přečtěte si téma [aktivační události Azure Functions pro Event Hubs](/azure/azure-functions/functions-bindings-event-hubs)nebo
2. Pomocí [sady .NET SDK pro Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Všimněte si, že tyto C#příklady jsou uvedeny v.

## <a name="using-azure-notification-hubs-with-f"></a>Použití Azure Notification Hubs s F\#

[Azure Notification Hubs](/azure/notification-hubs/) jsou multiplatformní, vysoce škálovatelná infrastruktura nabízených oznámení, která vám umožní odesílat mobilní nabízená oznámení z jakéhokoli back-endu (v cloudu nebo v místním prostředí) do jakékoli mobilní platformy.

Službu Azure Notification Hubs lze použít F# dvěma způsoby:

1. Vytváření F# Azure Functions, které odesílají výsledky do centra oznámení. Další informace najdete v tématu [triggery výstupu funkce Azure Functions pro Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs).
2. Pomocí [sady .NET SDK pro Azure](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend). Všimněte si, že tyto C#příklady jsou uvedeny v.

## <a name="implementing-webhooks-on-azure-with-f"></a>Implementace webhooků v Azure s využitím F\#

[Webhook](https://en.wikipedia.org/wiki/Webhook) je zpětné volání aktivované prostřednictvím webové žádosti. Webhooky jsou používány weby, jako je GitHub pro události signálu.

Webhooky se dají implementovat v F# a hostovat v Azure prostřednictvím [funkce Azure v F# rámci s vazbami Webhooku](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Použití WebJobs s F\#

[WebJobs](/azure/app-service-web/web-sites-create-web-jobs) jsou programy, které můžete spustit ve vaší App Service webové aplikaci třemi způsoby: na vyžádání, průběžně nebo podle plánu.

[Příklad F# úlohy WebJob](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementace časovačů v Azure s využitím F\#

Časovač spouští funkce volání na základě plánu, jednorázového nebo opakovaného.

Časovače je možné implementovat F# a hostovat v Azure pomocí [funkce Azure ve F# službě s triggerem časovače](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Nasazení a Správa prostředků Azure pomocí F# skriptů

Virtuální počítače Azure se můžou programově nasazovat a F# spravovat ze skriptů pomocí balíčků Microsoft. Azure. Management a rozhraní API. Příklad najdete v tématu [Začínáme s knihovnami pro správu rozhraní .NET](https://msdn.microsoft.com/library/dn722415.aspx) a [pomocí Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobně je možné nasadit a spravovat taky další prostředky Azure ze F# skriptů pomocí stejných komponent. Můžete například vytvořit účty úložiště, nasadit Azure Cloud Services, vytvářet Azure Cosmos DB instance a spravovat centra Azure nakonfigurovaná programově ze F# skriptů.

Použití F# skriptů k nasazení a správě prostředků není obvykle nutné. Například prostředky Azure mohou být nasazeny přímo z popisů šablon JSON, které lze parametrizovaně. Viz [šablony Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) , včetně příkladů, jako jsou například [šablony pro rychlý Start Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Další zdroje

* [Úplná dokumentace ke všem službám Azure](/azure/)
