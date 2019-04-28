---
title: 3501 – InferredContractDescription
ms.date: 03/30/2017
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
ms.openlocfilehash: 47a5d98f4510e8c6092e8533a98366141d4b24db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755893"
---
# <a name="3501---inferredcontractdescription"></a>3501 – InferredContractDescription
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3501|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že že třídu ContractDescription byl odvozen od implementace WorkflowService.  
  
## <a name="message"></a>Zpráva  
 Popis ContractDescription s názvem = '%1' a Namespace = "%2" byl odvozen od implementace WorkflowService.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název|xs:string|Název třídu ContractDescription.|  
|Obor názvů|xs:string|Obor názvů třídu ContractDescription.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
