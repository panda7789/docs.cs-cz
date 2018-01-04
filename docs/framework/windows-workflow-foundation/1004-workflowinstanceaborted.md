---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1004|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že worfklow instance přerušil s výjimkou.  
  
## <a name="message"></a>Zpráva  
 Instance pracovního postupu Id: '%1' byla přerušena, s výjimkou.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Id instance pracovního postupu|  
|Výjimka|`xs:string`|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
