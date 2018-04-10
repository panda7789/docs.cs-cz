---
title: Analytické trasování s ETW
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a>Analytické trasování s ETW
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]analytické trasování nabízí způsob, jak zachytit diagnostické informace během provádění [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]analytické trasování událostí jsou vygenerované v klíčové body [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zásobníku umožňující řešení potíží s [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby v produkčním prostředí. Analytické trasování pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služeb má minimální dopad na výkon produktu serveru, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služeb jako tyto události jsou velmi efektivně vygenerované relaci události trasování událostí pro Windows (ETW).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled analytického trasování](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Popisuje, jak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytické trasování funguje v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows.  
  
 [Konfigurace trasování toku zpráv](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Popisuje postup konfigurace trasování toku zpráv.  
  
 [Události analytického trasování – přehled](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Příklad ID událostí s úrovní událostí, zprávy o událostech a klíčová slova.  
  
## <a name="see-also"></a>Viz také  
 [Služby WCF a Trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Sledování událostí v Trasování událostí ve Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
