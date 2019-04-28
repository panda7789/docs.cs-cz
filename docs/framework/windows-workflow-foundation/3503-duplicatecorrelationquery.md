---
title: 3503 – DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755594"
---
# <a name="3503---duplicatecorrelationquery"></a>3503 – DuplicateCorrelationQuery
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3503|  
|klíčová slova|WFServices|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že duplicitní CorrelationQuery byl nalezen. Duplicitní dotaz nebude použit při výpočtu korelace.  
  
## <a name="message"></a>Zpráva  
 Duplicitní CorrelationQuery byl nalezen s klauzulí Where = '%1'. Tento duplicitní dotaz nebude použit při výpočtu korelace.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Where|xs:string|Where korelace dotazu.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
