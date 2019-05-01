---
title: 1001 – WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008639"
---
# <a name="1001---workflowapplicationcompleted"></a>1001 – WorkflowApplicationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1001|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu byla dokončena v zavřeném stavu.  
  
## <a name="message"></a>Zpráva  
 WorkflowInstance Id: '%1' byl dokončen v zavřeném stavu.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Id instance pracovního postupu|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
