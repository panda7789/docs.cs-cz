---
title: 1101 - WorkflowActivityStart
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7687e747d22c4726f11a6d17aa8b719897ab8473
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1101---workflowactivitystart"></a>1101 - WorkflowActivityStart
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1101|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo zahájeno aktivit pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 Instance pracovního postupu Id: '%1' E2E aktivity  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:String|Id instance pracovního postupu.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
