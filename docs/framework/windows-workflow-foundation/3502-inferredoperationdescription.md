---
title: 3502 – InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756088"
---
# <a name="3502---inferredoperationdescription"></a>3502 – InferredOperationDescription
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3502|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že že OperationDescription byl odvozen od implementace WorkflowService.  
  
## <a name="message"></a>Zpráva  
 Popis OperationDescription s názvem = '%1' v kontraktu "%2" byl odvozen od implementace WorkflowService. IsOneWay = %3.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|Název operace.|  
|ContractName|xs:string|Název smlouvy.|  
|IsOneWay|xs:string|Hodnotu true nebo False určující, pokud kontrakt je jednosměrná.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
