---
title: Aplikace bez serveru Azure Logic Apps
description: Azure Logic Apps umožňují vytvářet automatizované škálovatelné pracovní postupy, které integrují aplikace a data napříč službami Cloud Services a místními systémy.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676751"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) poskytuje modul bez serveru pro vytváření automatizovaných pracovních postupů pro integraci aplikací a dat mezi Cloud Services a místními systémy. Pracovní postupy sestavíte pomocí vizuálního návrháře. Můžete aktivovat pracovní postupy založené na událostech nebo časovačích a využívat konektory pro integrační aplikace a usnadnit komunikaci B2B (Business-to-Business). Logic Apps se bez problémů integruje s Azure Functions.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps může dělat víc, než stačí připojit své cloudové služby (jako jsou funkce) k prostředkům cloudu (jako jsou fronty a databáze). Místní pracovní postupy můžete také orchestrovat pomocí místní brány. Pomocí aplikace logiky můžete například aktivovat místní uloženou proceduru SQL v reakci na cloudovou událost nebo podmíněnou logiku ve vašem pracovním postupu. Přečtěte si další informace o [připojení k místním zdrojům dat s místní bránou dat Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architektura Logic Apps](./media/logic-apps-architecture.png)

Stejně jako u Azure Functions jste v triggeru aktivovali pracovní postupy aplikace logiky. Existuje mnoho triggerů, ze kterých si můžete vybrat. Následující záznam obsahuje několik oblíbených z nejoblíbenějších ze stovek, které jsou k dispozici.

![Aktivační události Logic Apps](./media/logic-app-triggers.png)

Po aktivaci aplikace můžete použít vizuálního návrháře k sestavení kroků, smyček, podmínek a akcí. K dispozici jsou všechna data ingestovaná v předchozím kroku, abyste je mohli použít v následujících krocích. Následující pracovní postup načte adresy URL z databáze CosmosDB. Najde ty, které `t.co` hostuje, a pak je vyhledá na Twitteru. Pokud najde odpovídající tweety, aktualizuje dokumenty se souvisejícím tweety voláním funkce.

![Pracovní postup aplikace logiky](./media/logic-app-workflow.png)

Řídicí panel Logic Apps zobrazuje historii spouštění vašich pracovních postupů a to, jestli se každé spuštění úspěšně dokončilo nebo ne. Můžete přejít do libovolného spuštění a zkontrolovat data používaná jednotlivými kroky pro řešení potíží. Logic Apps také nabízí existující šablony, které můžete upravit a jsou vhodné pro složité podnikové pracovní postupy.

Další informace najdete v tématu [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Předchozí](application-insights.md)Další
>[](event-grid.md)
