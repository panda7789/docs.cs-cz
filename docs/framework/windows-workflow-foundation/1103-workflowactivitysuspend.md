---
title: 1103 – WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 4311bd8dc1c5e2c43bf21b411a4c52a7bfc7b230
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052778"
---
# <a name="1103---workflowactivitysuspend"></a>1103 – WorkflowActivitySuspend
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1103|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita pracovního postupu je pozastavená.  
  
## <a name="message"></a>Zpráva  
 WorkflowInstance Id: '%1' aktivita E2E  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|Id instance pracovního postupu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
