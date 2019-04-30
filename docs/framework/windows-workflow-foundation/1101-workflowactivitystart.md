---
title: 1101 – WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924147"
---
# <a name="1101---workflowactivitystart"></a>1101 – WorkflowActivityStart
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1101|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byla spuštěna aktivita pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 WorkflowInstance Id: '%1' aktivita E2E  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|Id instance pracovního postupu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
