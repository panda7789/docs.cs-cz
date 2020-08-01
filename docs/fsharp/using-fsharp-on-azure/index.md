---
title: Použití jazyka F# v Azure
description: 'Průvodce používáním služeb Azure s F #'
author: sylvanc
ms.date: 07/29/2020
ms.openlocfilehash: ebf94d724db2c503f27581bf1352bf4fa90f5e2a
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455709"
---
# <a name="using-f-on-azure"></a>Použití jazyka F# v Azure

F # je vynikající jazyk pro cloudové programování a často se používá k psaní webových aplikací, cloudových služeb, mikroslužeb hostovaných v cloudu a pro škálovatelné zpracování dat.

V následujících částech najdete zdroje informací o tom, jak používat řadu služeb Azure s F #.

> [!NOTE]
> Pokud v této sadě dokumentace není konkrétní služba Azure, vyhledejte ji prosím v dokumentaci Azure Functions nebo .NET této služby. Některé služby Azure jsou nezávislé na jazyce a nevyžadují žádnou dokumentaci specifickou pro konkrétní jazyk a nejsou tady uvedené.

## <a name="using-azure-virtual-machines-with-f"></a>Použití Azure Virtual Machines s F\#

Azure podporuje rozsáhlou škálu konfigurací virtuálních počítačů, viz [Linux a Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).

Pro instalaci jazyka F # na virtuální počítač pro spuštění, kompilaci nebo skriptování viz [použití jazyka f # v systému Linux](https://fsharp.org/use/linux) a [použití jazyka f # ve Windows](https://fsharp.org/use/windows).

## <a name="using-azure-functions-with-f"></a>Použití Azure Functions s F\#

[Azure Functions](https://azure.microsoft.com/services/functions/) je řešení pro snadné spouštění malých částí kódu nebo "Functions" v cloudu. Můžete napsat přesně takový kód, jaký potřebujete pro aktuální problém, a nestarat se o infrastrukturu k jeho spuštění nebo aplikaci jako celek. Vaše funkce jsou připojené k událostem v Azure Storage a dalších prostředcích hostovaných v cloudu. Data se do funkcí F # převedou prostřednictvím argumentů funkce. Můžete použít svůj vývojářský jazyk podle vlastního výběru, který je důvěryhodný pro Azure ke škálování podle potřeby.

Azure Functions podporuje jazyk F # jako první třídu s efektivním, reaktivním a škálovatelným spouštěním kódu F #. Referenční dokumentaci týkající se použití jazyka F # s Azure Functions najdete v tématu Referenční dokumentace pro [vývojáře v Azure Functions f #](/azure/azure-functions/functions-reference-fsharp) .

Další prostředky pro použití Azure Functions a F #:

* [Horizontální navýšení kapacity Azure Functions v F # pomocí Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Vytvoření funkce Azure Functions v F #](https://www.mnie.me/azurefunctions)
* [Použití poskytovatele typu Azure s Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Použití Azure Storage s F\#

Azure Storage je základní vrstvou služeb úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost, aby splňovaly potřeby zákazníků. Programy v jazyce F # můžou komunikovat přímo se službami Azure Storage pomocí technik popsaných v následujících článcích.

* [Začínáme s Azure Blob Storage s využitím F#](blob-storage.md)
* [Začínáme s Azure File Storage s využitím F#](file-storage.md)
* [Začínáme s Azure Queue Storage s využitím F#](queue-storage.md)
* [Začínáme se službou Azure Table Storage s využitím F#](table-storage.md)

Azure Storage lze také použít ve spojení s Azure Functions prostřednictvím deklarativní konfigurace namísto explicitního volání rozhraní API. Další informace najdete v tématu [Azure Functions triggery a vazby pro Azure Storage](/azure/azure-functions/functions-bindings-storage) obsahující příklady F #.

## <a name="using-azure-app-service-with-f"></a>Použití Azure App Service s F\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) je cloudová platforma pro vytváření výkonných webových a mobilních aplikací, které se připojují k datům kdekoli, v cloudu i v místním prostředí.

* [Příklad webového rozhraní API v jazyce F #](https://github.com/fsprojects/azure-webapi-example)
* [Hostování F # ve webové aplikaci v Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a>Použití Apache Spark s F # v Azure HDInsight nebo Azure Databricks

[Apache Spark pro Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) je open source platforma pro zpracování, která spouští rozsáhlé aplikace pro analýzu dat. [Azure Databricks](https://docs.microsoft.com/azure/databricks/scenarios/what-is-azure-databricks) je analytická platforma založená na Apache Spark optimalizovaná pro platformu Microsoft Azure cloudové služby. Azure přináší Apache Spark snadný a nákladově efektivní nasazení. Vývoj aplikace Spark v jazyce F # pomocí [rozhraní .NET pro Apache Spark](../../spark/what-is-apache-spark-dotnet.md), sady vazeb .net pro Apache Spark.

* [Ukázky rozhraní .NET pro Apache Spark F #](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.FSharp.Examples)
* [Instalace interaktivních poznámkových bloků .NET Interactive Jupyter ve službě Azure HDInsight](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [Odesílání úloh Apache Spark do Azure HDInsight](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [Odeslat Apache Spark úlohy do Azure Databricks](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a>Použití Azure Cosmos DB s F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) je služba NoSQL pro vysoce dostupné a globálně distribuované aplikace.

Azure Cosmos DB lze použít s F # dvěma způsoby:

1. Vytvořením jazyka F # Azure Functions, který reaguje na nebo způsobuje změny v kolekcích Azure Cosmos DB. Viz [Azure Cosmos DB vazby pro Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb)nebo
2. Pomocí [sady Azure Cosmos DB .NET SDK pro rozhraní SQL API](/azure/cosmos-db/sql-api-sdk-dotnet). Související ukázky jsou v C#.

## <a name="using-azure-event-hubs-with-f"></a>Použití Azure Event Hubs s F\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) poskytují ingestování telemetrie na úrovni cloudu z webů, aplikací a zařízení.

Azure Event Hubs lze použít s F # dvěma způsoby:

1. Vytvořením Azure Functions jazyka F #, které jsou aktivovány událostmi. Přečtěte si téma [aktivační události Azure Functions pro Event Hubs](/azure/azure-functions/functions-bindings-event-hubs)nebo
2. Pomocí [sady .NET SDK pro Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="using-azure-notification-hubs-with-f"></a>Použití Azure Notification Hubs s F\#

[Azure Notification Hubs](/azure/notification-hubs/) jsou multiplatformní, vysoce škálovatelná infrastruktura nabízených oznámení, která vám umožní odesílat mobilní nabízená oznámení z jakéhokoli back-endu (v cloudu nebo v místním prostředí) do jakékoli mobilní platformy.

Azure Notification Hubs lze použít s F # dvěma způsoby:

1. Vytvořením jazyka F # Azure Functions, který odesílá výsledky do centra oznámení. Další informace najdete v tématu [triggery výstupu funkce Azure Functions pro Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs).
2. Pomocí [sady .NET SDK pro Azure](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="implementing-webhooks-on-azure-with-f"></a>Implementace webhooků v Azure s F\#

[Webhook](https://en.wikipedia.org/wiki/Webhook) je zpětné volání aktivované prostřednictvím webové žádosti. Webhooky jsou používány weby, jako je GitHub pro události signálu.

Webhooky se dají implementovat v F # a hostovat v Azure pomocí [funkce Azure v F # s vazbou Webhooku](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Použití WebJobs s F\#

[WebJobs](/azure/app-service-web/web-sites-create-web-jobs) jsou programy, které můžete spustit ve vaší App Service webové aplikaci třemi způsoby: na vyžádání, průběžně nebo podle plánu.

[Příklad webové úlohy F #](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementace časovačů v Azure s F\#

Časovač spouští funkce volání na základě plánu, jednorázového nebo opakovaného.

Časovače je možné implementovat v F # a hostovat v Azure pomocí [funkce Azure v F # pomocí triggeru časovače](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Nasazení a Správa prostředků Azure pomocí skriptů F #

Virtuální počítače Azure můžou být programově nasazené a spravované ze skriptů F # pomocí balíčků Microsoft. Azure. Management a rozhraní API. Příklad najdete v tématu [Začínáme s knihovnami pro správu rozhraní .NET](https://msdn.microsoft.com/library/dn722415.aspx) a [pomocí Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Stejně tak mohou být také nasazeny další prostředky Azure a spravovány ze skriptů F # pomocí stejných komponent. Můžete například vytvořit účty úložiště, nasadit Azure Cloud Services, vytvářet Azure Cosmos DB instance a spravovat centra Azure nakonfigurovaná programově ze skriptů F #.

Použití skriptů F # pro nasazení a správu prostředků není normálně nutné. Například prostředky Azure mohou být nasazeny přímo z popisů šablon JSON, které lze parametrizovaně. Viz [šablony Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) , včetně příkladů, jako jsou například [šablony pro rychlý Start Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Další prostředky

* [Úplná dokumentace ke všem službám Azure](/azure/)
