---
title: "Pomocí F # na Azure"
description: "Průvodce pomocí služeb Azure s F #"
keywords: "Azure cloud, visual f #, f # funkční programování, .NET, .NET Core"
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: 636604b1a0b645f13ac20d7ed85bde9abae3f9f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-f-on-azure"></a>Pomocí F # na Azure

F # je vynikající jazyk pro programování cloudu a se často používá k zápisu webových aplikací, cloudové služby, mikroslužeb hostovaných v cloudu a pro škálovatelnou zpracování dat.

V následujících částech najdete prostředky na použití služby oblast Azure s F #.

> [!NOTE]
> Pokud konkrétní službu Azure není v této dokumentaci, přečtěte si dokumentaci Azure Functions nebo rozhraní .NET pro tuto službu. Některé služby Azure jsou nezávislé na jazyku a vyžadují žádná konkrétní jazyk dokumentace a zde nejsou uvedeny.

## <a name="using-azure-virtual-machines-with-f"></a>Pomocí virtuální počítače Azure F # #

Azure podporuje širokou škálu konfigurace virtuálních počítačů (VM), najdete v části [Linux a virtuální počítače Azure](https://azure.microsoft.com/services/virtual-machines/).

Chcete-li nainstalovat F # na virtuálním počítači pro spuštění, kompilace a skriptování najdete v tématu [pomocí F # v systému Linux](http://fsharp.org/use/linux) a [pomocí F # v systému Windows](http://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Pomocí Azure Functions F # #

[Azure Functions](https://azure.microsoft.com/services/functions/) je řešení umožňující snadno spouštět malé části kódu, nebo "funkce" v cloudu. Můžete napsat přesně takový kód, potřebujete pro aktuální problém, bez starostí o infrastrukturu nebo aplikaci jako celek ji spustit. Funkce jsou připojené k události v úložišti Azure a dalším prostředkům hostovaných v cloudu. Toky dat do funkce F # prostřednictvím argumenty funkce. Můžete použít svůj vývoj jazyk podle vlastní volby, důvěřující Azure škálovat podle potřeby.

Azure Functions podporovat F # jako první třídy jazyk s efektivní, reaktivní, škálovatelné spuštění kódu F #. Najdete v článku [Azure funkce F # referenční informace pro vývojáře](/azure/azure-functions/functions-reference-fsharp) pro referenční dokumentaci o tom, jak používat F # s Azure Functions.

Další zdroje informací pro používání Azure Functions a F #:

* [Škálování Azure Functions v F # s použitím Suave](http://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Postup vytvoření funkce Azure v jazyce F #](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Zprostředkovatel Azure typu pomocí Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Používání Azure Storage s F # #

Azure Storage je základní vrstvu služby úložiště pro moderní aplikace, které jsou závislé na odolnost, dostupnost a škálovatelnost, abyste splnili požadavky zákazníků. F # programy mohou komunikovat přímo s služby Azure storage, pomocí techinques popsané v následujících článcích.

* [Začínáme s Azure Blob storage pomocí F #](blob-storage.md)
* [Začínáme s Azure File storage pomocí F #](file-storage.md)
* [Začínáme s Azure Queue storage pomocí F #](queue-storage.md)
* [Začínáme s Azure Table storage pomocí F #](table-storage.md)

Úložiště Azure můžete také použít ve spojení s Azure Functions prostřednictvím deklarativní konfigurace spíše než explicitní volání rozhraní API. V tématu [Azure Functions triggerů a vazeb pro Azure Storage](/azure/azure-functions/functions-bindings-storage) což zahrnuje příklady F #.

## <a name="using-azure-app-service-with-f"></a>Pomocí služby Azure App Service F # #

[Aplikační služba Azure](https://azure.microsoft.com/services/app-service/) je Cloudová platforma vytvářet výkonné webové a mobilní aplikace, které se připojují k datům kdekoliv a v cloudu nebo místně.

* [Příklad F # Azure webového rozhraní API](https://github.com/fsprojects/azure-webapi-example)
* [Hostování F # ve webové aplikaci v Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Pomocí Apache Spark F # s Azure HDInsight

[Apache Spark pro Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) je představuje rozhraní s otevřeným zdrojem zpracování, které běží aplikace, rozsáhlé datové analýzy. Azure umožňuje Apache Spark snadný a nákladově efektivní pro nasazení. Vývoj aplikace Spark v F # pomocí [Mobius](https://github.com/Microsoft/Mobius), .NET API pro Spark.

* [Implementace aplikací Spark v F # s použitím Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Příklad F # Spark aplikací pomocí Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-documentdb-with-f"></a>Pomocí Azure DocumentDB F # #

[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) je služba NoSQL pro vysokou dostupnost, globálně distribuované aplikace.

Azure DocumentDB a F # lze použít dvěma způsoby:

1. Prostřednictvím vytváření sad Azure Functions F # které reagovat na nebo mění na kolekce DocumentDB. V tématu [aktivuje funkce Azure documentdb](/azure/azure-functions/functions-bindings-documentdb), nebo
2. Pomocí [.NET SDK pro Azure](/azure/documentdb/documentdb-get-started-quickstart). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="using-azure-event-hubs-with-f"></a>Pomocí služby Azure Event Hubs F # #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) poskytnout cloudového škálovatelného přijímání telemetrie z webů, aplikací a zařízení.

Azure Event Hubs s F # lze použít dvěma způsoby:

1. Prostřednictvím vytváření F # Azure funkcí, které jsou aktivovány události. V tématu [aktivuje funkce Azure pro službu Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), nebo
2. Pomocí [.NET SDK pro Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Všimněte si, že tyto příklady jsou v jazyce C#.

## <a name="using-azure-notification-hubs-with-f"></a>Pomocí Azure Notification Hubs F # #

[Služba Azure Notification Hubs](/azure/notification-hubs/) jsou s více platformami a horizontálně škálovanou infrastrukturu, která vám umožní odesílat mobilní nabízená oznámení z jakékoli back-end (v cloudu nebo místní) na libovolnou mobilní platformu.

Služba Azure Notification Hubs s F # lze použít dvěma způsoby:

1. Prostřednictvím vytváření sad Azure Functions F # který odeslat výsledky do centra oznámení. V tématu [funkce Azure výstup aktivační události služby Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), nebo
2. Pomocí [.NET SDK pro Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Všimněte si, že tyto příklady jsou v jazyce C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementace Webhooky v Azure s F # #

A [Webhooku](https://en.wikipedia.org/wiki/Webhook) je zpětné volání aktivaci prostřednictvím webového požadavku. Webhooky jsou používány webů, jako je Githubu na signál události. 

Webhooky můžete implementovat v jazyce F # a hostované v Azure pomocí [funkce Azure v F # s Webhooku vazbou](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Pomocí Webjobs F # #

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) se o programy, které lze spustit ve vaší webové aplikace služby App Service třemi způsoby: na vyžádání, nepřetržitě, nebo podle plánu.

[Příklad F # webovou úlohu](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a>Implementace časovače v Azure s F # #

Časovač spustí podle plánu, jednorázově nebo opakovaně volat funkce.

Časovače můžete implementovat v jazyce F # a hostované v Azure pomocí [funkce Azure v F # s aktivační událost časovače](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Nasazení a správě prostředků Azure pomocí skriptů F # #

Virtuální počítače Azure mohou prostřednictvím kódu programu nasadit a spravovat z F # skripty pomocí rozhraní API a Microsoft.Azure.Management balíčky. Například v tématu [začít pracovat s knihovnami správu pro platformu .NET](https://msdn.microsoft.com/library/dn722415.aspx) a [pomocí Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Podobně ostatní prostředky služby Azure mohou také nasazení a spravovat z F # skripty s použitím komponenty stejné. Můžete například vytvořit účty úložiště, nasazení Azure Cloud Services, vytváření instancí služby Azure DocumentDB a spravovat centra oznámení Azure prostřednictvím kódu programu z F # skriptů.

Pomocí skriptů F # pro nasazení a správě prostředků není obvykle nutné. Prostředky Azure může být například také nasazené přímo z JSON šablony popisy, které lze nastavit parametry. V tématu [šablon Azure Resource Manageru](/azure/azure-resource-manager/resource-manager-template-best-practices) včetně příkladů, jako [šablon Azure rychlý Start](https://azure.microsoft.com/documentation/templates/).

## <a name="other-resources"></a>Další zdroje

* [Úplnou dokumentaci o všech služeb Azure](/azure/)
