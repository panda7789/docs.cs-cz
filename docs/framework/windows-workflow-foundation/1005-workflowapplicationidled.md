---
title: 1005 – WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008600"
---
# <a name="1005---workflowapplicationidled"></a>1005 – WorkflowApplicationIdled
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1005|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že má nečinný aplikace pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 WorkflowApplication Id: '%1' Přechod do nečinného režimu.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Id aplikace pracovního postupu|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
