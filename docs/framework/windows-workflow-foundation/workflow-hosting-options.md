---
title: Možnosti hostování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 2a03c7b5e15b76eabc714f44624f04d3385720d4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713316"
---
# <a name="workflow-hosting-options"></a>Možnosti hostování pracovního postupu
Většina ukázky Windows Workflow Foundation (WF) používá pracovní postupy, které jsou hostované v konzolové aplikaci, ale to není realistické scénáře pro pracovní postupy v reálném světě. Pracovní postupy v samotných obchodních aplikací bude hostována v trvalé procesy – služba Windows autoři článku, vývojář nebo serverové aplikace, jako [!INCLUDE[iisver](../../../includes/iisver-md.md)] nebo AppFabric. Rozdíly mezi těmito dvěma způsoby jsou následující.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hostování pracovních postupů ve službě IIS s Windows AppFabric  
 Pomocí služby IIS s AppFabric je upřednostňované hostitele pro pracovní postupy. Hostitelská aplikace pro pracovní postupy pomocí AppFabric je aktivace služby Windows, která odebere závislost na HTTP přes IIS samostatně.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hostování pracovních postupů ve službě IIS samostatně  
 Pomocí [!INCLUDE[iisver](../../../includes/iisver-md.md)] samostatně se nedoporučuje, protože existují správy a monitorování nástroje dostupné ve službě AppFabric, které usnadňují údržbu spuštěných aplikací. Pracovní postupy hostovat pouze v [!INCLUDE[iisver](../../../includes/iisver-md.md)] samostatně, pokud existují starostí o infrastrukturu s přesunem AppFabric.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] pravidelně recykluje fondy aplikací z různých důvodů. Po recyklaci fondu aplikací služby IIS přestane přijímat zprávy do staré fondu a vytvoří nový fond aplikací tak, aby přijímal nové požadavky. Pokud pracovní postup pokračuje práce po odeslání odpovědi, [!INCLUDE[iisver](../../../includes/iisver-md.md)] nebude vědět o práce a mohou recyklace hostování fondu aplikací. Pokud k tomu dojde, pracovní postup se přeruší a sledování služeb zaznamená [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) zprávy s prázdným polem důvod.  
>   
>  Pokud se používá trvalost, restartování hostitele explicitně přerušených instancí z posledního bodu trvalosti.  
>   
>  AppFabric se používá, služby pracovních postupů správy obnoví pracovní postup od posledního úspěšného trvalost bodu nakonec Pokud se používá trvalosti. Pokud se používá vytvořil dočasný a pracovní postup provádí operace mimo vzor žádostí a odpovědí, data se ztratí, když pracovní postup přeruší.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hostování pracovního postupu ve vlastní službě Windows  
 Vytvoření vlastní pracovní postup služby k hostování pracovního postupu se vyžadují pro vývojáře k duplikování spoustu funkce poskytované službou AppFabric out-of-box, ale umožní větší flexibilitu s vlastní funkce. Tuto možnost byste měli uvažovat pouze pokud AppFabric prokáže, nebude možné.
