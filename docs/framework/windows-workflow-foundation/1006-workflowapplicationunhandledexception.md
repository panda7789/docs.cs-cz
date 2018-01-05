---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842d6bb6172eed5f7382633119045ea7507fb955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 - WorkflowApplicationUnhandledException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1006|  
|Klíčová slova|WFRuntime|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aplikace pracovního postupu došlo k neošetřené výjimce.  
  
## <a name="message"></a>Zpráva  
 Id instance pracovního postupu: '%1' došlo k neošetřené výjimce.  Výjimka pochází z aktivity %2, DisplayName: '%3'.  Se provedou následující akce: %4.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Id instance pracovního postupu|  
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
