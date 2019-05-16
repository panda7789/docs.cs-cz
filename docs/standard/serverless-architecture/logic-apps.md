---
title: Azure Logic Apps – aplikace bez serveru
description: Služba Azure Logic Apps umožňují vytváření automatizovaných škálovatelných pracovních postupů, které integrují aplikace a služby a v místních systémech dat napříč cloudem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638807"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="8ac44-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="8ac44-103">Azure Logic Apps</span></span>

<span data-ttu-id="8ac44-104">[Služba Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje bez serveru engine můžete vytvářet automatizované pracovní postupy pro integraci aplikací a dat mezi cloudovými službami a místními systémy.</span><span class="sxs-lookup"><span data-stu-id="8ac44-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="8ac44-105">Můžete vytvářet pracovní postupy pomocí vizuálního návrháře.</span><span class="sxs-lookup"><span data-stu-id="8ac44-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="8ac44-106">Můžete aktivovat pracovní postupy založené na události nebo časovače a využijte konektory pro integraci aplikací a usnadňují komunikace business-to-business (B2B).</span><span class="sxs-lookup"><span data-stu-id="8ac44-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="8ac44-107">Logic Apps se bez problémů integruje s využitím Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="8ac44-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="8ac44-109">Logic Apps můžete provést více než jen připojení vašich cloudových služeb (jako jsou funkce) pomocí cloudové prostředky (jako jsou fronty a databází).</span><span class="sxs-lookup"><span data-stu-id="8ac44-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="8ac44-110">Můžete také orchestrovat pracovní postupy s místními s místní bránou.</span><span class="sxs-lookup"><span data-stu-id="8ac44-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="8ac44-111">Aplikace logiky například můžete použít k aktivaci v místním uložené procedury SQL v reakci na událost založené na cloudu nebo podmíněnou logiku v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8ac44-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="8ac44-112">Další informace o [připojení k místním zdrojům dat s využitím Azure na místní bránu dat](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="8ac44-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura aplikací logiky](./media/logic-apps-architecture.png)

<span data-ttu-id="8ac44-114">Podobně jako Azure Functions můžete pusťte se do postupů workflow Logic Apps s triggerem.</span><span class="sxs-lookup"><span data-stu-id="8ac44-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="8ac44-115">Existuje řada triggerů si můžete vybírat.</span><span class="sxs-lookup"><span data-stu-id="8ac44-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="8ac44-116">Následující snímek zobrazuje jenom některé další oblíbené značky z celkového počtu stovkami, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8ac44-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Triggery aplikace logiky](./media/logic-app-triggers.png)

<span data-ttu-id="8ac44-118">Po aplikaci se aktivuje, může vizuálního návrháře použít k sestavení kroky, smyčky, podmínky a akce.</span><span class="sxs-lookup"><span data-stu-id="8ac44-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="8ac44-119">Všechna data v předchozím kroku je k dispozici pro použití v dalších krocích.</span><span class="sxs-lookup"><span data-stu-id="8ac44-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="8ac44-120">Následující pracovní postup načtení adresy URL v databázi cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="8ac44-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="8ac44-121">Najde ty s celou řadu `t.co` pak vyhledá pro ně na Twitteru.</span><span class="sxs-lookup"><span data-stu-id="8ac44-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="8ac44-122">Pokud najde odpovídající tweety, dokumenty se aktualizuje související tweety voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="8ac44-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Pracovní postup aplikace logiky](./media/logic-app-workflow.png)

<span data-ttu-id="8ac44-124">Na řídicím panelu Logic Apps zobrazuje historii spouštění pracovních postupů a určuje, zda každý dokončil svůj běh úspěšně nebo ne.</span><span class="sxs-lookup"><span data-stu-id="8ac44-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="8ac44-125">Můžete přecházet do jakéhokoli daného běhu a kontrolovat data používá jednotlivých kroků pro řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="8ac44-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="8ac44-126">Logic Apps poskytuje také stávající šablony, můžete upravit a jsou vhodné pro komplexní podnikové pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="8ac44-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="8ac44-127">Další informace najdete v tématu [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="8ac44-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8ac44-128">[Předchozí](application-insights.md)
>[další](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="8ac44-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
