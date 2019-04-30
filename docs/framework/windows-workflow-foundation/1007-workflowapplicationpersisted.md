---
title: 1007 – WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 0b3c290ad06eda6921626c0d7a1c8ec854c30e7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925265"
---
# <a name="1007---workflowapplicationpersisted"></a>1007 – WorkflowApplicationPersisted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1007|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že obsahuje trvalé aplikace pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 WorkflowApplication Id: '%1' byl trvale uložen.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|Id aplikace pracovního postupu|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
