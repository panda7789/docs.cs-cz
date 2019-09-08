---
title: Analytické trasování s ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798087"
---
# <a name="analytic-tracing-with-etw"></a>Analytické trasování s ETW
Analytické trasování Windows Communication Foundation (WCF) nabízí způsob, jak zachytit diagnostické informace během provádění služby WCF. Události analytického trasování WCF se generují na klíčových místech v zásobníku WCF, aby bylo možné řešit potíže se službami WCF v produkčním prostředí. Analytické trasování pro služby WCF má minimální dopad na výkon produktového serveru, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služeb WCF, protože tyto události jsou velmi efektivně generovány do relace trasování událostí pro Windows (ETW).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled analytického trasování](analytic-tracing-overview.md)  
 Popisuje, jak funguje analytické trasování WCF [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]v.  
  
 [Dynamické povolování analytického sledování](dynamically-enabling-analytic-tracing.md)  
 Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí ETW.  
  
 [Konfigurace trasování toku zpráv](configuring-message-flow-tracing.md)  
 Popisuje postup konfigurace trasování toku zpráv.  
  
 [Události analytického trasování – přehled](analytic-trace-event-reference.md)  
 Zobrazuje tabulku ID událostí s jejich úrovněmi události, zprávami o událostech a klíčovými slovy.  
  
## <a name="see-also"></a>Viz také:

- [Služby WCF a Trasování událostí pro Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Sledování událostí v Trasování událostí ve Windows](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
