---
title: Azure Logic Apps – aplikace bez serveru
description: Azure Logic Apps umožňují vytváření automatizovaných škálovatelných pracovních postupů, které integrují aplikace a data napříč cloudovými službami a místními systémy.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676751"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="8c39a-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="8c39a-103">Azure Logic Apps</span></span>

<span data-ttu-id="8c39a-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje modul bez serveru pro vytváření automatizovaných pracovních postupů pro integraci aplikací a dat mezi cloudovými službami a místními systémy.</span><span class="sxs-lookup"><span data-stu-id="8c39a-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="8c39a-105">Pracovní postupy se vytvářejí pomocí vizuálního návrháře.</span><span class="sxs-lookup"><span data-stu-id="8c39a-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="8c39a-106">Můžete aktivovat pracovní postupy založené na událostech nebo časovačích a využít konektory pro integrační aplikace a usnadnit komunikaci mezi podniky (B2B).</span><span class="sxs-lookup"><span data-stu-id="8c39a-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="8c39a-107">Logic Apps se bezproblémově integruje s funkcemi Azure.</span><span class="sxs-lookup"><span data-stu-id="8c39a-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="8c39a-109">Logic Apps můžete udělat víc než jen připojit cloudové služby (jako jsou funkce) s cloudovými prostředky (jako jsou fronty a databáze).</span><span class="sxs-lookup"><span data-stu-id="8c39a-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="8c39a-110">Můžete také organizovat místní pracovní postupy s místní bránou.</span><span class="sxs-lookup"><span data-stu-id="8c39a-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="8c39a-111">Například můžete použít aplikaci logiky k aktivaci místní uložené procedury SQL v reakci na cloudovou událost nebo podmíněnou logiku ve vašem pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8c39a-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="8c39a-112">Další informace o [připojení k místním zdrojům dat pomocí Místní brány dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="8c39a-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Architektura logic apps](./media/logic-apps-architecture.png)

<span data-ttu-id="8c39a-114">Stejně jako Funkce Azure, můžete nastartovat workflowaplikace logiky s aktivační událostí.</span><span class="sxs-lookup"><span data-stu-id="8c39a-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="8c39a-115">Existuje mnoho spouští pro vás z čeho vybírat.</span><span class="sxs-lookup"><span data-stu-id="8c39a-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="8c39a-116">Následující zachycení ukazuje jen několik z nejpopulárnějších z těch, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8c39a-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Triggery Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="8c39a-118">Po aktivaci aplikace můžete pomocí vizuálního návrháře vytvořit kroky, smyčky, podmínky a akce.</span><span class="sxs-lookup"><span data-stu-id="8c39a-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="8c39a-119">Všechna data přijatá v předchozím kroku jsou k dispozici pro použití v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="8c39a-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="8c39a-120">Následující pracovní postup načte adresy URL z databáze CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="8c39a-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="8c39a-121">Najde ty s řadou `t.co` pak hledá pro ně na Twitteru.</span><span class="sxs-lookup"><span data-stu-id="8c39a-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="8c39a-122">Pokud najde odpovídající tweety, aktualizuje dokumenty souvisejícími tweety voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="8c39a-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Pracovní postup aplikace Logika](./media/logic-app-workflow.png)

<span data-ttu-id="8c39a-124">Řídicí panel Logic Apps zobrazuje historii spuštění pracovních postupů a to, zda bylo každé spuštění úspěšně dokončeno či nikoli.</span><span class="sxs-lookup"><span data-stu-id="8c39a-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="8c39a-125">Můžete přejít do libovolného spuštění a zkontrolovat data používaná každým krokem pro řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="8c39a-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="8c39a-126">Logic Apps také poskytuje existující šablony, které můžete upravovat a jsou vhodné pro složité podnikové pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="8c39a-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="8c39a-127">Další informace najdete v [tématu Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="8c39a-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8c39a-128">[Předchozí](application-insights.md)
>[další](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="8c39a-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
