---
title: Hostování možnosti pracovní postup
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 7713044e40532c431d090b1cb1795876ead2a899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516549"
---
# <a name="workflow-hosting-options"></a>Hostování možnosti pracovní postup
Většina ukázek Windows Workflow Foundation (WF) používá pracovní postupy, které jsou hostované v konzolové aplikaci, ale tato akce není realistické scénář pro skutečné pracovní postupy. Pracovní postupy v skutečné obchodní aplikace hostované ve trvalé procesy – služba systému Windows, jako vývojář nebo serverová aplikace vytvořené [!INCLUDE[iisver](../../../includes/iisver-md.md)] nebo AppFabric. Rozdíly mezi těmito dvěma způsoby jsou následujícím způsobem.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hostování pracovních postupů v IIS s Windows AppFabric  
 Pomocí služby IIS s AppFabric je upřednostňované hostitele pro pracovní postupy. Hostitelskou aplikaci pro pracovní postupy pomocí AppFabric je aktivace služby Windows, která odebere závislost na HTTP přes samostatné služby IIS.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hostování pracovních postupů v samotné služby IIS  
 Pomocí [!INCLUDE[iisver](../../../includes/iisver-md.md)] samostatně se nedoporučuje, protože existují Správa a sledování dostupné s AppFabric nástroje, které usnadňují údržby spuštěných aplikací. Pracovní postupy pouze hostovat v [!INCLUDE[iisver](../../../includes/iisver-md.md)] samostatně, pokud máte obavy infrastruktury s přesunutím do AppFabric.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] pravidelně recykluje fondy aplikací z různých důvodů. Po recyklaci fondu aplikací služby IIS přestane přijímat zprávy a pokuste se původní fond a vytvoří nový fond aplikací tak, aby přijímal nové požadavky. Pokud pracovní postup pokračovat pracovní po odeslání odpovědi, [!INCLUDE[iisver](../../../includes/iisver-md.md)] nebude mít přehled o práci a může recykluje fond aplikací s hostování. Pokud k tomu dojde, bude přerušeno pracovního postupu a sledování služby bude záznam [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md) zprávu s prázdné pole důvod.  
>   
>  Pokud se používá k stálost, restartování hostitele explicitně přerušených instancí z posledního bodu trvalost.  
>   
>  AppFabric se používá, služba správy pracovního postupu obnoví od vytvoření posledního bodu úspěšné trvalost nakonec Pokud se používá trvalost. Pokud je používáno žádné trvalost a pracovní postup provádí operace mimo vzor požadavků a odpovědí, data budou ztracena, když pracovní postup přeruší.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hostování pracovní postup ve vlastní služby systému Windows  
 Vytvoření vlastního pracovního postupu služby k hostování pracovní postup bude vyžadovat vývojáři duplicitní spoustu funkce poskytované službou AppFabric out-of-box, ale umožňuje větší flexibilitu s vlastní funkce. Tuto možnost byste měli uvažovat pouze pokud AppFabric prokáže, nebude možnost.
