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
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje modul bez serveru pro vytváření automatizovaných pracovních postupů pro integraci aplikací a dat mezi cloudovými službami a místními systémy. Pracovní postupy se vytvářejí pomocí vizuálního návrháře. Můžete aktivovat pracovní postupy založené na událostech nebo časovačích a využít konektory pro integrační aplikace a usnadnit komunikaci mezi podniky (B2B). Logic Apps se bezproblémově integruje s funkcemi Azure.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps můžete udělat víc než jen připojit cloudové služby (jako jsou funkce) s cloudovými prostředky (jako jsou fronty a databáze). Můžete také organizovat místní pracovní postupy s místní bránou. Například můžete použít aplikaci logiky k aktivaci místní uložené procedury SQL v reakci na cloudovou událost nebo podmíněnou logiku ve vašem pracovním postupu. Další informace o [připojení k místním zdrojům dat pomocí Místní brány dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architektura logic apps](./media/logic-apps-architecture.png)

Stejně jako Funkce Azure, můžete nastartovat workflowaplikace logiky s aktivační událostí. Existuje mnoho spouští pro vás z čeho vybírat. Následující zachycení ukazuje jen několik z nejpopulárnějších z těch, které jsou k dispozici.

![Triggery Logic Apps](./media/logic-app-triggers.png)

Po aktivaci aplikace můžete pomocí vizuálního návrháře vytvořit kroky, smyčky, podmínky a akce. Všechna data přijatá v předchozím kroku jsou k dispozici pro použití v následujících krocích. Následující pracovní postup načte adresy URL z databáze CosmosDB. Najde ty s řadou `t.co` pak hledá pro ně na Twitteru. Pokud najde odpovídající tweety, aktualizuje dokumenty souvisejícími tweety voláním funkce.

![Pracovní postup aplikace Logika](./media/logic-app-workflow.png)

Řídicí panel Logic Apps zobrazuje historii spuštění pracovních postupů a to, zda bylo každé spuštění úspěšně dokončeno či nikoli. Můžete přejít do libovolného spuštění a zkontrolovat data používaná každým krokem pro řešení potíží. Logic Apps také poskytuje existující šablony, které můžete upravovat a jsou vhodné pro složité podnikové pracovní postupy.

Další informace najdete v [tématu Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Předchozí](application-insights.md)
>[další](event-grid.md)
