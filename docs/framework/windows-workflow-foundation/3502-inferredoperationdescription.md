---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c2464cd8c6f0c16946847a5503270453d5b019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3502|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Označuje, že že OperationDescription byla vyvozena z WorkflowService.  
  
## <a name="message"></a>Zpráva  
 OperationDescription s názvem = '%1' ve smlouvě se z WorkflowService odvodit '%2'. IsOneWay = %3.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Název operace.|  
|ContractName|xs:String|Název smlouvy.|  
|IsOneWay|xs:String|Hodnotu true nebo False indikující, pokud je jednosměrná kontrakt.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
