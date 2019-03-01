---
title: 'Použití jazyka F# v Azure'
description: 'Příručka k používání služeb Azure sF#'
author: sylvanc
ms.date: 09/22/2016
---
# <a name="using-f-on-azure"></a>Použití jazyka F# v Azure

F#je vynikající jazyk pro programování v cloudu a se často používá k zápisu webové aplikace, cloudové služby, mikroslužby hostované v cloudu a pro škálovatelné zpracování dat.

V následujících částech najdete prostředky, jak používat škálu služeb Azure s F#.

> [!NOTE]
> Pokud konkrétní službu Azure není v této sadě dokumentace, najdete dokumentaci k Azure Functions nebo .NET za danou službu. Některé služby Azure jsou jazykově nezávislé a vyžadovat žádná dokumentace specifické pro jazyk a zde nejsou uvedeny.

## <a name="using-azure-virtual-machines-with-f"></a>Pomocí služby Azure Virtual Machines s F\#

Azure podporuje širokou škálu konfigurací virtuálních počítačů (VM) naleznete v tématu [virtuální počítače Azure s Linuxem a](https://azure.microsoft.com/services/virtual-machines/).

K instalaci F# na virtuálním počítači pro spuštění, kompilace a/nebo skriptování viz [použití F# v Linuxu](https://fsharp.org/use/linux) a [použití F# na Windows](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Pomocí Azure Functions s F\#

[Služba Azure Functions](https://azure.microsoft.com/services/functions/) je řešení umožňující snadno spouštět malé části kódu, nebo "funkce" v cloudu. Můžete napsat přesně takový kód, které potřebujete pro problém aktuální, aniž byste se museli starat o infrastrukturu nebo aplikaci jako celek, ho spustit. Vaše funkce jsou připojené k události v Azure storage a dalším prostředkům hostované v cloudu. Data budou téci do vaší F# funkce prostřednictvím argumentů funkce. Můžete použít vývoj jazyk podle vlastní volby, důvěřující Azure ke škálování podle potřeby.

Podpora Azure Functions F# jako prvotřídní jazyk v efektivní, reaktivní a škálovatelná provádění F# kódu. Zobrazit [Azure Functions F# referenční informace pro vývojáře](/azure/azure-functions/functions-reference-fsharp) referenční dokumentaci, jak používat F# s využitím Azure Functions.

Další materiály týkající se používání Azure Functions a F#:

* [Vertikální navýšení kapacity Azure Functions v F# pomocí Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Jak vytvořit funkci v AzureF#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Pomocí zprostředkovatele typu Azure s využitím Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Použití služby Azure Storage s F\#

Azure Storage je základní vrstvě služby úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost podle potřeb zákazníků. F#programy můžou pracovat přímo s služby Azure storage, pomocí technik popsaných v následujících článcích.

* [Začínáme s Azure Blob Storage s využitím F#](blob-storage.md)
* [Začínáme s Azure File Storage s využitím F#](file-storage.md)
* [Začínáme s Azure Queue Storage s využitím F#](queue-storage.md)
* [Začínáme s Azure Table Storage s využitím F#](table-storage.md)

Úložiště Azure je také možné ve spojení s využitím Azure Functions prostřednictvím deklarativních místo explicitního volání rozhraní API. Zobrazit [aktivační události Azure Functions a vazby pro službu Azure Storage](/azure/azure-functions/functions-bindings-storage) obsahující F# příklady.

## <a name="using-azure-app-service-with-f"></a>Pomocí služby Azure App Service s F\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) je cloudovou platformou můžete tvořit výkonné webové a mobilní aplikace, které se připojují k datům bez ohledu na, v cloudu nebo místně.

* [F#Příklad webového rozhraní API Azure](https://github.com/fsprojects/azure-webapi-example)
* [Hostování F# ve webové aplikaci v Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Pomocí Apache Sparku s využitím F# s Azure HDInsight

[Apache Spark pro Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) je zpracování opensourcové rozhraní, na kterém běží velkých objemů dat analytických aplikací. Azure vám umožní Apache Sparku jednoduché a nákladově efektivní nasazení. Vývoj aplikace Spark v F# pomocí [Mobius](https://github.com/Microsoft/Mobius), rozhraní .NET API pro Spark.

* [Implementace aplikací Apache Spark v F# pomocí Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Příklad F# pomocí Mobius aplikací Spark](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Pomocí služby Azure Cosmos DB s F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) je služba typu NoSQL pro vysoce dostupnou a globálně distribuované aplikace.

Azure Cosmos DB je možné s F# dvěma způsoby:

1. Prostřednictvím vytváření sad F# Azure Functions, která reakce na ně nebo způsobit změny v kolekcích Azure Cosmos DB. Zobrazit [vazby Azure Cosmos DB pro službu Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), nebo
2. S použitím [Azure Cosmos DB .NET SDK pro rozhraní SQL API](/azure/cosmos-db/sql-api-sdk-dotnet). Související ukázky jsou v jazyce C#.

## <a name="using-azure-event-hubs-with-f"></a>Pomocí služby Azure Event Hubs s F\#

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) poskytnout cloudového škálovatelného ingestování telemetrických údajů z webů, aplikací a zařízení.

Azure Event Hubs je možné s F# dvěma způsoby:

1. Prostřednictvím vytváření sad F# Azure Functions, které jsou aktivovány události. Zobrazit [aktivuje funkce Azure Functions pro službu Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), nebo
2. S použitím [sady .NET SDK pro Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="using-azure-notification-hubs-with-f"></a>Pomocí Azure Notification Hubs s F\#

[Azure Notification Hubs](/azure/notification-hubs/) jsou multiplatformní a horizontálně škálovanou infrastrukturu, která vám umožní odesílat mobilní nabízená oznámení z jakéhokoli back-endu (v cloudu nebo místně) na libovolnou mobilní platformu.

Azure Notification Hubs je možné s F# dvěma způsoby:

1. Prostřednictvím vytváření sad F# Azure Functions, která odeslat výsledky do centra oznámení. Zobrazit [funkce Azure Functions výstup aktivační události pro Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), nebo
2. S použitím [sady .NET SDK pro Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Všimněte si, že tyto příklady jsou v jazyce C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementace Webhooky v Azure s využitím F\#

A [Webhooku](https://en.wikipedia.org/wiki/Webhook) se spouští přes webový požadavek zpětného volání. Webhooky jsou používány webů, jako je GitHub na signál události. 

Webhooků je možné implementovat v F# a hostuje ho na Azure prostřednictvím [funkce Azure Functions v F# s Webhooku vazby](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Pomocí Webjobs F\#

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) jsou programy, které můžete spustit ve webové aplikaci App Service třemi způsoby: na požádání, průběžně nebo podle plánu.

[Příklad F# webová úloha.](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementace časovače pro Azure s využitím F\#

Časovač spustí podle plánu, jednou nebo opakovaně funkce volání.

Časovače je možné implementovat v F# a hostuje ho na Azure prostřednictvím [funkce Azure Functions v F# s triggerem Timer](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Nasazení a správě prostředků Azure pomocí F# skriptů

Virtuální počítače Azure mohou být prostřednictvím kódu programu nasazují a spravují z F# skripty pomocí rozhraní API a Microsoft.Azure.Management balíčky. Viz například [začít pracovat s knihovnami správy pro .NET](https://msdn.microsoft.com/library/dn722415.aspx) a [pomocí Azure Resource Manageru](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobně, dalších prostředků Azure může také možné nasadit a spravovat z F# skripty pomocí stejné komponenty. Například můžete vytvořit účty úložiště, nasazení Azure Cloud Services, vytváření instancí služby Azure Cosmos DB a spravovat centra oznámení Azure prostřednictvím kódu programu z F# skripty.

Pomocí F# skripty k nasazení a správě prostředků není obvykle nutné. Prostředky Azure například může být nasazený přímo z popisů šablony JSON, které mohou být parametrizovány. V tématu [šablon Azure Resource Manageru](/azure/azure-resource-manager/resource-manager-template-best-practices) včetně příkladů, jako [šablony pro rychlý start Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Další zdroje

* [Úplnou dokumentaci ke všem službám Azure](/azure/)
