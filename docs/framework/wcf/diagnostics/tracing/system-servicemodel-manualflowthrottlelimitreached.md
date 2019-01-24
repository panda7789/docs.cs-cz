---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 86d47ab0a83ff3e4a68bfa8ccf1349cf2b345b23
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597733"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a>System.ServiceModel.ManualFlowThrottleLimitReached
System.ServiceModel.ManualFlowThrottleLimitReached  
  
## <a name="description"></a>Popis  
 Systém dosáhl limitu nastaveného pro omezení ManualFlowControlLimit. Hodnotu omezení lze změnit upravením vlastnosti ManualFlowControlLimit ServiceHost nebo třída InstanceContext, podle potřeby.  
  
 Trasování je vygenerován při limit ruční toku řízení je zpočátku omezená na 0. Následné změny 0 nebudou trasovány. Tok řízení omezený kontext instance trasován jednou pro každý kontext.  
  
## <a name="see-also"></a>Viz také:
- [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Řešení problémů s aplikací pomocí trasování](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Správa a diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)
