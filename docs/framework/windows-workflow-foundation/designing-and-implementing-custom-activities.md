---
title: Návrh a implementace vlastních aktivit
description: Tento článek poskytuje prostředky pro vytváření vlastních aktivit v nástroji Workflow Foundation vytvořením složených aktivit nebo vytvářením nových typů aktivit.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419990"
---
# <a name="designing-and-implementing-custom-activities"></a>Návrh a implementace vlastních aktivit
Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] nástroji jsou vytvářeny buď prostřednictvím sestavování systémových aktivit, do složených aktivit, nebo vytvořením nových typů, které jsou odvozeny z <xref:System.Activities.CodeActivity> , <xref:System.Activities.AsyncCodeActivity> nebo <xref:System.Activities.NativeActivity> . Tato část popisuje, jak vytvořit vlastní aktivity pomocí obou metod.  
  
> [!IMPORTANT]
> Vlastní aktivity ve výchozím nastavení se zobrazují v Návrháři pracovních postupů jako jednoduchý obdélník s názvem aktivity. K poskytnutí vlastní vizuální reprezentace vaší aktivity v Návrháři pracovních postupů musíte také vytvořit vlastního návrháře. Další informace najdete v tématu [použití vlastních návrhářů aktivit a šablon](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Možnosti při vytváření aktivit](activity-authoring-options-in-wf.md)  
 Popisuje styly vytváření dostupné v nástroji [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .  
  
 [Použití vlastní aktivity](using-a-custom-activity.md)  
 Popisuje, jak přidat vlastní aktivitu do projektu pracovního postupu.  
  
  [Vytváření asynchronních aktivit](creating-asynchronous-activities-in-wf.md)  
 Popisuje, jak vytvořit asynchronní aktivity.  
  
 [Konfigurace ověřování aktivit](configuring-activity-validation.md)  
 Popisuje, jak lze pomocí ověření aktivity identifikovat a ohlásit chyby v konfiguraci aktivity před jejím spuštěním.  
  
 [Vytvoření aktivity za běhu](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 Popisuje, jak vytvářet aktivity za běhu pomocí <xref:System.Activities.DynamicActivity> .  
  
 [Vlastnosti spuštění pracovního postupu](workflow-execution-properties.md)  
 Popisuje použití vlastností spuštění pracovního postupu k přidání specifických vlastností kontextu do prostředí aktivity.  
  
 [Používání delegátů aktivit](using-activity-delegates.md)  
 Popisuje, jak vytvářet a používat aktivity, které obsahují delegáty aktivit.
  
 [Používání rozšíření aktivit](using-activity-extensions.md)  
 Popisuje, jak vytvářet a používat rozšíření aktivit.  
  
 [Využití informačních kanálů OData z pracovního postupu](consuming-odata-feeds-from-a-workflow.md)  
 Popisuje několik metod pro volání datové služby WCF z pracovního postupu.  
  
 [Určení oboru a viditelnosti definice aktivity](activity-definition-scoping-and-visibility.md)  
 Popisuje možnosti a pravidla pro definování oboru dat a viditelnosti členů pro aktivity.
