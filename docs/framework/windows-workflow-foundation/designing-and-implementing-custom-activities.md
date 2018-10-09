---
title: Navrhování a implementace vlastních aktivit
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 673145c856e950c8648a87cb3dcb9665ffa51ba9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873385"
---
# <a name="designing-and-implementing-custom-activities"></a>Navrhování a implementace vlastních aktivit
Vlastní aktivity v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] se vytvoří buď kompletaci poskytované systémem aktivit do složených aktivit nebo vytvoření nových typů, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.NativeActivity>. Tato část popisuje, jak vytvořit vlastní aktivity pomocí některé z metod.  
  
> [!IMPORTANT]
>  Vlastní aktivity ve výchozím nastavení se zobrazí v Návrháři pracovních postupů jako jednoduchý obdélník s názvem aktivity. Poskytnout vlastní vizuální znázornění vaše aktivity v pracovním postupu návrháře musíte také vytvořit vlastní návrháře. Další informace najdete v tématu [použití vlastních návrhářů a šablon aktivity](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Možnosti při vytváření aktivit](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 Tento článek popisuje vytváření styly k dispozici v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Použití vlastní aktivity](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 Popisuje, jak přidat vlastní aktivity do projektu pracovního postupu.  
  
  [Vytváření asynchronních aktivit](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 Popisuje, jak vytvořit asynchronní aktivity.  
  
 [Konfigurace ověřování aktivit](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 Popisuje, jak ověřování aktivit slouží k identifikaci a oznamovat chyby v konfiguraci aktivity před jeho provedením.  
  
 [Vytvoření aktivity za běhu](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 Popisuje způsob vytváření aktivit v modulu runtime pomocí <xref:System.Activities.DynamicActivity>.  
  
 [Vlastnosti spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 Popisuje, jak pomocí vlastnosti spuštění pracovního postupu můžete přidat do prostředí aktivity specifické vlastnosti kontextu  
  
 [Používání delegátů aktivit](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 Popisuje, jak vytvářet a používat aktivity, které obsahují delegátů aktivit.
  
 [Používání rozšíření aktivit](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 Popisuje způsob vytváření a používání rozšíření aktivit.  
  
 [Využití informačních kanálů OData z pracovního postupu](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 Popisuje několik metod pro volání datové služby WCF z pracovního postupu.  
  
 [Určení oboru a viditelnosti definice aktivity](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 Popisuje možnosti a pravidla pro definování dat určení oboru a člen viditelnost pro aktivity.
