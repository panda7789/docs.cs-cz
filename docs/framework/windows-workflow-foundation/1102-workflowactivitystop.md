---
title: 1102 – WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 44617e9f53be0e601424746f83b171d33956197e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052791"
---
# <a name="1102---workflowactivitystop"></a>1102 – WorkflowActivityStop
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1102|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita pracovního postupu byl zastaven.  
  
## <a name="message"></a>Zpráva  
 WorkflowInstance Id: '%1' aktivita E2E  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|Id instance pracovního postupu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
