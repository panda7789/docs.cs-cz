---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512002"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3502|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
