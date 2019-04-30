---
title: 1041 – WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924186"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 – WorkflowApplicationPersistableIdle
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1041|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu je nečinná a trvalá. Aplikace pracovního postupu bude nečinný nebo trvalé.  
  
## <a name="message"></a>Zpráva  
 WorkflowApplication Id: '%1' je nečinná a trvalá.  Se provedou následující akce: %2.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|Id aplikace pracovního postupu|  
|ActionTaken|xs:string|Akce, které se provedou na aplikace pracovního postupu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
