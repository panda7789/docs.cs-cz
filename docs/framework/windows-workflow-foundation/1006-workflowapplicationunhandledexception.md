---
title: 1006 – WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924706"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 – WorkflowApplicationUnhandledException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1006|  
|klíčová slova|WFRuntime|  
|úroveň|Chyba|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.  
  
## <a name="message"></a>Zpráva  
 WorkflowInstance Id: '%1' došlo k neošetřené výjimce.  Výjimka pochází z aktivity %2, DisplayName: '%3'.  Se provedou následující akce: %4.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Id instance pracovního postupu|  
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimku|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
