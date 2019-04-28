---
title: Azure Logic Apps – aplikace bez serveru
description: Služba Azure Logic Apps umožňují vytváření automatizovaných škálovatelných pracovních postupů, které integrují aplikace a služby a v místních systémech dat napříč cloudem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 14670a8459db3b80b8fbe3139c2675321cf9592c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712778"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Služba Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje bez serveru engine můžete vytvářet automatizované pracovní postupy pro integraci aplikací a dat mezi cloudovými službami a místními systémy. Můžete vytvářet pracovní postupy pomocí vizuálního návrháře. Můžete aktivovat pracovní postupy založené na události nebo časovače a využijte konektory pro integraci aplikací a usnadňují komunikace business-to-business (B2B). Logic Apps se bez problémů integruje s využitím Azure Functions.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps můžete provést více než jen připojení vašich cloudových služeb (jako jsou funkce) pomocí cloudové prostředky (jako jsou fronty a databází). Můžete také orchestrovat pracovní postupy s místními s místní bránou. Aplikace logiky například můžete použít k aktivaci v místním uložené procedury SQL v reakci na událost založené na cloudu nebo podmíněnou logiku v pracovním postupu. Další informace o [připojení k místním zdrojům dat s využitím Azure na místní bránu dat](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architektura aplikací logiky](./media/logic-apps-architecture.png)

Podobně jako Azure Functions můžete pusťte se do postupů workflow Logic Apps s triggerem. Existuje řada triggerů si můžete vybírat. Následující snímek zobrazuje jenom některé další oblíbené značky z celkového počtu stovkami, které jsou k dispozici.

![Triggery aplikace logiky](./media/logic-app-triggers.png)

Po aplikaci se aktivuje, může vizuálního návrháře použít k sestavení kroky, smyčky, podmínky a akce. Všechna data v předchozím kroku je k dispozici pro použití v dalších krocích. Následující pracovní postup načtení adresy URL v databázi cosmos DB. Najde ty s celou řadu `t.co` pak vyhledá pro ně na Twitteru. Pokud najde odpovídající tweety, dokumenty se aktualizuje související tweety voláním funkce.

![Pracovní postup aplikace logiky](./media/logic-app-workflow.png)

Na řídicím panelu Logic Apps zobrazuje historii spouštění pracovních postupů a určuje, zda každý dokončil svůj běh úspěšně nebo ne. Můžete přecházet do jakéhokoli daného běhu a kontrolovat data používá jednotlivých kroků pro řešení potíží. Logic Apps poskytuje také stávající šablony, můžete upravit a jsou vhodné pro komplexní podnikové pracovní postupy.

Další informace najdete v tématu [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Předchozí](application-insights.md)
>[další](event-grid.md)