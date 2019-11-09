---
title: Aplikace bez serveru Azure Logic Apps
description: Azure Logic Apps umožňují vytvářet automatizované škálovatelné pracovní postupy, které integrují aplikace a data napříč službami Cloud Services a místními systémy.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676751"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="79ed0-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="79ed0-103">Azure Logic Apps</span></span>

<span data-ttu-id="79ed0-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje modul bez serveru pro vytváření automatizovaných pracovních postupů pro integraci aplikací a dat mezi Cloud Services a místními systémy.</span><span class="sxs-lookup"><span data-stu-id="79ed0-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="79ed0-105">Pracovní postupy sestavíte pomocí vizuálního návrháře.</span><span class="sxs-lookup"><span data-stu-id="79ed0-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="79ed0-106">Můžete aktivovat pracovní postupy založené na událostech nebo časovačích a využívat konektory pro integrační aplikace a usnadnit komunikaci B2B (Business-to-Business).</span><span class="sxs-lookup"><span data-stu-id="79ed0-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="79ed0-107">Logic Apps se bez problémů integruje s Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="79ed0-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="79ed0-109">Logic Apps může dělat víc, než stačí připojit své cloudové služby (jako jsou funkce) k prostředkům cloudu (jako jsou fronty a databáze).</span><span class="sxs-lookup"><span data-stu-id="79ed0-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="79ed0-110">Místní pracovní postupy můžete také orchestrovat pomocí místní brány.</span><span class="sxs-lookup"><span data-stu-id="79ed0-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="79ed0-111">Pomocí aplikace logiky můžete například aktivovat místní uloženou proceduru SQL v reakci na cloudovou událost nebo podmíněnou logiku ve vašem pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="79ed0-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="79ed0-112">Přečtěte si další informace o [připojení k místním zdrojům dat s místní bránou dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="79ed0-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura Logic Apps](./media/logic-apps-architecture.png)

<span data-ttu-id="79ed0-114">Stejně jako u Azure Functions jste v triggeru aktivovali pracovní postupy aplikace logiky.</span><span class="sxs-lookup"><span data-stu-id="79ed0-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="79ed0-115">Existuje mnoho triggerů, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="79ed0-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="79ed0-116">Následující záznam obsahuje několik oblíbených z nejoblíbenějších ze stovek, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="79ed0-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Aktivační události Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="79ed0-118">Po aktivaci aplikace můžete použít vizuálního návrháře k sestavení kroků, smyček, podmínek a akcí.</span><span class="sxs-lookup"><span data-stu-id="79ed0-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="79ed0-119">K dispozici jsou všechna data ingestovaná v předchozím kroku, abyste je mohli použít v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="79ed0-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="79ed0-120">Následující pracovní postup načte adresy URL z databáze CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="79ed0-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="79ed0-121">Nalezne ty s hostitelem `t.co` pak je vyhledá na Twitteru.</span><span class="sxs-lookup"><span data-stu-id="79ed0-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="79ed0-122">Pokud najde odpovídající tweety, aktualizuje dokumenty se souvisejícím tweety voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="79ed0-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Pracovní postup aplikace logiky](./media/logic-app-workflow.png)

<span data-ttu-id="79ed0-124">Řídicí panel Logic Apps zobrazuje historii spouštění vašich pracovních postupů a to, jestli se každé spuštění úspěšně dokončilo nebo ne.</span><span class="sxs-lookup"><span data-stu-id="79ed0-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="79ed0-125">Můžete přejít do libovolného spuštění a zkontrolovat data používaná jednotlivými kroky pro řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="79ed0-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="79ed0-126">Logic Apps také nabízí existující šablony, které můžete upravit a jsou vhodné pro složité podnikové pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="79ed0-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="79ed0-127">Další informace najdete v tématu [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="79ed0-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="79ed0-128">[Předchozí](application-insights.md)
>[Další](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="79ed0-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
