---
title: 3501 - InferredContractDescription
ms.date: 03/30/2017
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
ms.openlocfilehash: 47a5d98f4510e8c6092e8533a98366141d4b24db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="3501---inferredcontractdescription"></a>3501 - InferredContractDescription
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3501|  
|Klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že byla vyvozena ContractDescription z WorkflowService.  
  
## <a name="message"></a>Zpráva  
 ContractDescription s názvem = '%1' a Namespace = '%2' byla vyvozena z WorkflowService.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|xs:String|Název ContractDescription.|  
|Obor názvů|xs:String|Obor názvů ContractDescription.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
